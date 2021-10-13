# firebase-repro

## repro steps
1. make sure you have node 14 installed and available:
  ```bash
$ node -v
v14.18.1
  ```
2. call `emulators:start` and note the logged node version:
  ```bash
$ firebase emulators:start --project=demo-app
i  emulators: Starting emulators: functions
i  emulators: Detected demo project ID "demo-app", emulated services will use a demo configuration and attempts to access non-emulated services for this project will fail.
⚠  Your requested "node" version "14" doesn't match your global version "12"
i  ui: Emulator UI logging to ui-debug.log
i  functions: Watching "/Users/modosc/git/firebase-repro/functions" for Cloud Functions...
>  function node version is: v12.18.1
✔  functions[us-central1-helloWorld]: http function initialized (http://localhost:5001/demo-app/us-central1/helloWorld).
  ```
3. call `emaulator:exec` and note the logged node versions:
  ```
$ firebase emulators:exec "node ./version.js" --project=demo-app
i  emulators: Starting emulators: functions
i  emulators: Detected demo project ID "demo-app", emulated services will use a demo configuration and attempts to access non-emulated services for this project will fail.
⚠  Your requested "node" version "14" doesn't match your global version "12"
i  functions: Watching "/Users/modosc/git/firebase-repro/functions" for Cloud Functions...
>  function node version is: v12.18.1
✔  functions[us-central1-helloWorld]: http function initialized (http://localhost:5001/demo-app/us-central1/helloWorld).
i  Running script: node ./version.js
exec node version is v12.18.1
✔  Script exited successfully (code 0)
i  emulators: Shutting down emulators.
i  functions: Stopping Functions Emulator
i  hub: Stopping emulator hub
```

## expected behavior
in both cases the version of node specified in `package.json` should be used

## actual behavior
in both cases node 12 is used.