This Component subscribes to the isReportEnabled state: 

![[Pasted image 20220807192053.png]]

The reducer function for `SETTINGS_SET_REPORT_OPT_IN_CHANGED` is defined in [[isReportEnabled.ts]] 

> [!NOTE]
useCallback ke dependencies pe we pass those values that change over re-renders (like states that are LEXICALLY SCOPED!!)

- We add dispatch as a dependency to the useCallback function just to be safe, it doesn't make any diff as redux guarantees `dispatch` method won't change across re-renders of the component
- 