## Selectors : 
---
- View Selector : currentView == "downloads"
	- ![[Pasted image 20220811095555.png|650x100]]
- Getting the last entered search term in downloads from the localStorage : 
	- Actually it uses  `uselocalStorage`  hooks which takes :
		- Key
		- Initial Value
		If the key is not avalable in the [localStorage from FuseLage](https://github.com/RocketChat/fuselage/commit/7c9a92046f5d7bd01ea9f421470333785ba97ee2#diff-35e24ab2605eda2a9b2c4a039a375a6a0195d9d5e6dd28bc53fc90def1201082) then it returns the initial values else the content of the key (Parsed).
		*The key to find the downloads from the localStorage is "download-search"*
>[!Note]
		>See the thing is, if you are thinking that it will persist the value in some sort of database and the value will remain even after the app is destroyed, you're wrong.
		>Use local Storage is used for persisting the values only through reloads, not restarts!!
- **HandleSearchFilterChange** : Simple Function to handle the change in input values.

- **serverFilterOptions** : 
	![[Pasted image 20220812190835.png|600x300]]
	- The objective of this function is to return a list of all existing servers from where downloads have occured
	- The function options takes `RootState` as the argument and extracts `downloads` state to work with! 
	- `useSelector<RootState, [string, string][]>`  means that we get the RootState as the input and we return a 2D array of form `[string, string][]`
	- `['*', t('downloads.filters.all')]` just appends a `[*,All]` sub array to the main 2D Array!
	- `.filter(({ serverUrl, serverTitle }) => serverUrl && serverTitle)` this basically maps through the list of downloads(an object with multiple objects signifying each download(which has properties like serverUrl,serverTitle) ) and removes all the downloads without a valid `serverUrl` and `serverTitle` 
	- We then map through the Main 2D Array and create a new 2-D array by removing the extra parameters in each object 
	- We then filter through the array to remove duplicate download elements!

> [!NOTE]
> - handleTabChange --> handleStatusChange
> - Feature Request --> Autocompletion while searching!
> - Applications type missing!

