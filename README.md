# covid-alert-dashboard

This site tries to infer the number of COVID-19 infections reported through Canada's COVID Alert app. App users who get infected with COVID-19 can use the app to send its diagnosis keys to a central server. Diagnosis keys are used by the app to generate the Bluetooth identifiers broadcast by the phone. Other COVID Alert app users will retrieve the uploaded diagnosis keys from the server and use them to find matches among the Bluetooth identifers broadcast by nearby smartphones and captured by their phone. This project retrieves the diagnosis keys not to find matches, but to infer the number of app users who reported an infection.

[Estimated daily number of infections reported through COVID Alert](infections.txt)

This project is not affiliated with Health Canada or the Canadian Digital Service maintaining the app.

Next is a quick description of the approach used for making the infection estimates:

1. Once an hour, retrieve the diagnosis keys uploaded so far today with the help of [retrieve-canadian-diagnosis-keys](https://github.com/uhengart/retrieve-canadian-diagnosis-keys).
2. Determine the set of diagnosis keys uploaded in the previous hour. 
3. For each key in the set, analyze whether it was uploaded as part of a newly reported infection or as part of a previously reported infection.

The final step is the trickiest one and requires some guessing so the numbers reported above are just estimates. We make available the result of step 2 so that others can easily reproduce step 3 or come up with better estimation approaches.

[Uploaded diagnosis keys per hour](uploads.txt) (updated once per day)

Information not of relevance for step 3, such as the actual key value or the transmission risk level, which unfortunately is the same for all uploaded keys, has been omitted from the file. Each entry consists of two values: the first one indicating when the key was uploaded, the second one the day when the key was used to generate Bluetooth identifiers. All times are in the UTC timezone. For example, the entry "2020-09-08_14:00 2020-08-31" denotes a key that was uploaded on Sep 9, 2020 sometime between 2 and 3pm (UTC) and that was used on Aug 31.
