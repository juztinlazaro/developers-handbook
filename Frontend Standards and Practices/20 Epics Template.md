## How to Use Templates for Epics

There are pre-made templates that you can use to compose your epic, these templates are located in <i>src/epic-templates</i> directory.

Depending on your need, select which template you will use from <i>src/epic-templates</i> directory. For this example, we will use the <i>getJSON</i> template.

1. On your Epic declaration, add the dependency on the parameter.

```Javascript
export const getActivityStreamSettingsEpic = (action$, state, { getJSON }) =>
```

2. Call the declared parameter on your Epic body.

```Javascript
return getJSON(url, headers, {
  succeeded: getActivityStreamSettingsSucceeded,
  failed: getActivityStreamSettingsFailed,
  startWith: getActivityStreamSettingsReading({
    status: true,
    type: Types.GET_ACTIVITY_STREAM_SETTINGS_EPIC,
  }),
  endsWith: getActivityStreamSettingsReading({
    status: false,
    type: Types.GET_ACTIVITY_STREAM_SETTINGS_EPIC,
  }),
  cancel: action$.ofType(Types.GET_ACTIVITY_STREAM_SETTINGS_CANCEL),
});
```

Parameters:  
<i>url</i> - The endpoint of the API.  
<i>headers</i> - Header you want to include in the http request <i>(e.g. Content-Type: application/json)</i>  
<i>options</i> - Method, actions, and observable use inside your epic template.

- succeeded - Method that will handle the success status of your request.
- failed - Method that will handle the failed status of your request.
- startWith - Redux action for handing the initial observable execution.
- endsWith - Redux action for handling the done observable execution.
- cancel - Action Observable for cancelling request.
