# Error Alarm Exercise

The simplest solution I can think of is to run a function every 1 minute (with setInterval or a cronjob) that checks if there are more than 10 errors and if so, sends the email alert.

Following the same idea to save errors in .txt the function would be something like this:

	function checkErrors
	
		if exists latestErrorsCount.txt then
		
			totalErrors = count("errorsFile.txt")
			errorsInLastMinute = totalErrors - count("latestErrorsCount.txt")
			
			if errorsInLastMinute > 10 then
				// assuming there is a function sendAlert that sends the email alert.
				sendAlert()
			endif
		endif
		
		// replace or create file if it doesn’t exists
		writeFile("latestErrorsCount.txt", "errorsFile.txt")
		
	end function
	
	function count(_file)
		file = readFile(_file)
		// count the number of errors as the number of lines in the file
		return file.split(/\r?\n/).length
	end function
