This Component subscribes to the isFlashFrameEnabled state: 
![[Pasted image 20220808122956.png]]
The reducer function for `SETTINGS_SET_FLASHFRAME_OPT_IN_CHANGED` is defined in [[isFlashFrameEnabled.ts]]

> [!ERROR] BUG
> - Flash frame is just for windows(https://github.com/electron/electron/issues/21714)
> - For macOS, using App.dock.bounce("critical") should result in app bouncing constantly on the dock.

Reference solution for the bug: 

```Javascript
App.on('browser-window-blur', () => {
    console.log('blur..')

    setTimeout(() => {
        if (App && App.dock) App.dock.bounce("critical")

        Browser.getAllWindows().forEach(w => {
            w.once('focus', () => {
                w.flashFrame(false)
            })
    
            w.flashFrame(true)
        })
    }, 2000)
})
```
