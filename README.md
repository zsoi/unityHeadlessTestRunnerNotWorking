# unityHeadlessTestRunnerNotWorking
Bug reproduction of an issue with the test runner not running tests in headless mode on 5.6

# 1. What happened
The editor test runner does no longer run tests in headless mode (did work with 5.5 but apparently broke in 5.6)

# 2. How we can reproduce it using the example you attached
Run the projects tests on the command line (windows):

"U:\Unity 5.6.0f3\Editor\Unity.exe" -batchmode -quit -logFile - -projectPath D:\headless-test-runner-not-working -runEditorTests -editorTestsResultFile .\test.xml -editorTestsVerboseLog teamcity

Expected: Teamcity formatted log messages about test progress and a test.xml result file
Actual:

- No log messages but

  Running tests for EditMode
  UnityEngine.DebugLogHandler:Internal_Log(LogType, String, Object)
  UnityEngine.DebugLogHandler:LogFormat(LogType, Object, String, Object[])
  UnityEngine.Logger:Log(LogType, Object)
  UnityEngine.Debug:Log(Object)
  UnityEditor.TestTools.TestRunner.Batch:InitiateRun(String, String, String[]) (at C:\buildslave\unity\build\Extensions\TestRunner\UnityEditor.TestRunner\Batch.cs:87)
  UnityEditor.TestTools.TestRunner.Batch:RunTests(String, String, String[]) (at C:\buildslave\unity\build\Extensions\TestRunner\UnityEditor.TestRunner\Batch.cs:28)

- No XML file generated about test results.
