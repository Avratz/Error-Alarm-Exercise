# Error Alarm Exercise

The simplest solution I can think of is to run a function every 1 minute (with setInterval or a cronjob) that checks if there are more than 10 errors and if so, sends the email alert.

Following the same idea to save errors in .txt the function would be something like this:

	function checkErrors
	
		if exists latestErrorsCount.txt then
		
			// assuming there is a count function that returns the total errors in a file.
			totalErrors = errorsFile.txt.count()
			errorsInLastMinute = totalErrors - latestErrorsCount.txt.count()
			
			if errorsInLastMinute > 10 then
				// assuming there is a function sendAlert that sends the email alert.
				sendAlert()
			endif
		endif
		
		// replace or create file if it doesn’t exists
		latestErrorsCount.txt = errorsFile.txt
		
	end function
