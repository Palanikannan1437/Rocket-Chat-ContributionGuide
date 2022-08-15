>[!Note]
>The file takes the responsiblity to handle the main process's download events, mostly it operates on `downloadItem` object which is provided by the electron API i.e. it works with the operating system to handle download events.

## Handle Events : 
- It starts listening to
	- **show-in-folder**
		- Checks for the download item, if not available return, else select the particular download.
		- use shell library to open the save path of the donwload.
	- **copy-link**
		- Checks for the downlaod.
		- Uses clipboard to write the download link ( aws s3 ) into clipboard.
	- **pause**
		- Uses the items array from electron.
		- Gets the item from the itemID.
		- if the item is present, and is paused, return.
		- Else pause the item.
	- **resume** : 
		- Same as pause, the function used is item.pause() && item.isPaused()
	- **cancel** : 
		- Same as pause, the function used is item.cancel().
	- retry
	- remove.