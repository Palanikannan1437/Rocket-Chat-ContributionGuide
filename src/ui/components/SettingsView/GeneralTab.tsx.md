# Settings View
---

![[Pasted image 20220807181449.png]]

- To trigger the Settings View - we need to dispatch `SIDE_BAR_SETTINGS_BUTTON_CLICKED` action
- This goes to [[CurrentView.ts]] which has the reducer function that changes the state `CurrentViewState` to `'settings'` which is by default `'add-new-server'` 


- We subscribe to the `currentView` state and we return a value i.e. true/false to determine if we want to show a blank page or the four settings present!
![[Pasted image 20220807183536.png]]

- SettingsView is the parent of 4 Components
	- [[ReportErrors.tsx]]
	- [[FlashFrame.tsx]] 
	- [[HardwareAcceleration.tsx]]
	- [[Open Video Chat using Application Window.]]