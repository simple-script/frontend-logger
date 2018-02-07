[![license](https://img.shields.io/github/license/simple-script/simple-script.svg)]()

# Frontend Logger
Frontend logger allows you to add logs and send them to your server where they are processed (for example saved into the file).

## Usage
Install
````
npm i @simple-script/frontend-logger
````

## Example
**Frontend part**
````HTML
<script src="logger.js"></script>

<!-- We will use the simple-error-logger module-->
<script src="modules/simple-error-logger.js"></script>
<script>
window.addEventListener('load', function () {
	initSimpleErrorLogger();

	function initSimpleErrorLogger()
	{
		var loggerName =  'simpleErrorLogger';
		sendLogs();

		setInterval(function () {
			sendLogs();
		}, 5000);

		function sendLogs() {
			if (FrontendLogger.getLog(loggerName) !== null) {
				FrontendLogger.sendLog(loggerName, window.simpleErrorLoggerUrl);
			}
		}
	}
});

</script>
````

**Backend part**
````PHP
$frontendLoggerData = $_POST['frontendLogger'];

if (isset($_POST['frontendLogger'])) {
    $frontendLoggerData = json_decode($frontendLoggerData, TRUE);

    if ( ! isset($frontendLoggerData['module']) || ! isset($frontendLoggerData['data'])) {
        return;
    }

    if ($frontendLoggerData['module'] === 'simpleErrorLogger' && is_array($frontendLoggerData['data'])) {
        $this->simpleFrontendErrorLogger->process($frontendLoggerData['data']);
        $data = implode(PHP_EOL, $frontendLoggerData['data']) . PHP_EOL;
        file_put_contents('path/to/file.log', $data, FILE_APPEND);
    }
}
````

**Result**
````
[3-1-2018 23:12:27] - Message: Uncaught ReferenceError: test is not defined - URL: http://somepage.com - File: http://somepage.com/test.js - Line: 1 - Browser:Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/64.0.3282.140 Safari/537.36
````
