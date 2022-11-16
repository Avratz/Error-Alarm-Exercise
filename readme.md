# Error Alarm Exercise

The simplest solution I can think of is to run a function every 1 minute (with setInterval or a cronjob) that checks if there are more than 10 errors and if so, sends the email alert.

Following the same idea to save errors in .txt the function would be something like this:

function checkErrors () {
	if (exists latestErrorsCount.txt) {
		const totalErrors = errorsFile.txt.count();
		const errorsInLastMinute = totalErrors - latestErrorsCount.txt.count();
		if (errorsInLastMinute > 10) {
			sendAlert();
		}
	}
	// replace or create file if it doesn’t exists
	latestErrorsCount.txt = errorsFile.txt;
}
