# dart-launch-config


```dart
"configurations": [
	{
		// A name for the launch config. This will show in the dropdown on the Run side bar.
		"name": "Current File (release mode)",

		// This should always be "dart" for Dart/Flutter apps.
		// This selects the Dart debugger.
		"type": "dart",

		// This can be "launch" to start an app, or "attach" to attach to an existing app.
		"request": "launch",

		// The directory to start running the app from.
		"cwd": "/foo/bar",

		// The entry script to execute when running the app.
		// Set to a "web" in a Dart web app to run in web move.
		// Set to "test" in an app with tests to run all tests.
		"program": "bin/main.dart",

		// Any custom environment variables to set when running the app with this
		// launch config.
		"env": {
			"RELEASE_MODE": true
		}

		// Arguments to be passed to the Dart VM when running Dart CLI scripts.
		// 
		// These arguments appear between "dart" and "run":
		//
		//     dart (vmAdditionalArgs) run (toolArgs) bin/main.dart (args)
		"vmAdditionalArgs": [
			"--vm_name=foo",
		],
		
		// Arguments to be passed to the Dart or Flutter tool.
		// 
		// These arguments appear after "dart run" or "flutter run":
		//
		//     dart (vmAdditionalArgs) run (toolArgs) bin/main.dart (args)
		//     flutter run (toolArgs) -t lib/main.dart (args)
		"toolArgs": [
			"--dart-define", "MY_VAR=foo",
			"--enable-experiment=patterns",
		],

		// Arguments to be passed to the Dart script being run (passed to `main()`).
		//
		// These arguments appear after the script being run.
		//
		//     dart (vmAdditionalArgs) run (toolArgs) bin/main.dart (args)
		//     flutter run (toolArgs) -t lib/main.dart (args)
		"args": [
			"one", "two",
		],

		// Setting "templateFor" to a relative path will cause this config to be used for
		// all default Run/Debug CodeLens links and running tests from the test runner.
		// - Setting an empty string "" will apply it to the whole project (this is different
		//   to not being set, where it will not be used as a template at all).
		// - Setting it to "test" will apply only to files inside the "test" folder, etc.
		"templateFor": "test",

		// "debugConsole" or "terminal". If set to "terminal", will run in the built-in
		// terminal and will support reading from `stdin`. However some other debug
		// features may be limited.
		"console": "debugConsole",

		// Set to run a Flutter app on a specific device, ignoring the device selected
		// in the status bar.
		"deviceId": "iphone",

		// "debug", "profile" or "release".
		"flutterMode": "debug",

		// Allows running Flutter tests on a real device instead of the default headless
		// flutter-tester device.
		"runTestsOnDevice": false,

		// If codeLens is defined, this launch configuration can be launched from custom
		// CodeLens links in the editor (see the page linked above for more info).
		"codeLens": {

			// This array sets where custom CodeLens links will be rendered:
			// - run-test: Above test functions as a Run link
			// - debug-test: Above test functions as a Debug link
			// - run-test-file: Above main functions in test files as a Run link
			// - debug-test-file: Above main functions in test files as a Debug link
			// - run-file: Above main functions in bin/tool/lib files as a Run link
			// - debug-file: Above main functions in bin/tool/lib files as a Debug link
			"for": [ "run-test", "run-test-file", "debug-test", "debug-test-file" ],

			// If specificed, the custom CodeLens will only appear for files that begin
			// with this path.
			"path": "test/integration_tests",

			// Text for the custom CodeLens. If not specified, will use the name field
			// from the parent launch configuration. The string "${debugType}" here will
			// be replaced with "run" or "debug" depending on the rendered position
			// (see the for field above).
			"title": "${debugType} (release)"
		},

		// customTool is to support some specific complex configurations where instead of running
		// "dart" or "flutter" when starting debug sessions, another tool/script should be invoked.
		// Custom tools must be completely compatible with the process they are replacing (in many
		// cases they may just be wrapper scripts).
		//
		// See https://github.com/dart-lang/sdk/tree/master/pkg/dds/tool/dap#readme for more details
		// on how these values are used by the debug adapter.
		"customTool": "my_custom_dart",
		"customToolReplacesArgs": 1,
	}
]
```
