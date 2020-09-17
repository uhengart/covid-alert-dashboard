# covid-alert-dashboard

This site tries to infer the number of COVID-19 infections reported through Canada's COVID Alert app. App users who get infected with COVID-19 can use the app to send its diagnosis keys to a central server. Diagnosis keys are used by the app to generate the Bluetooth identifiers broadcast by the phone. Other COVID Alert app users will retrieve the uploaded diagnosis keys from the server and use them to find matches among the Bluetooth identifers broadcast by nearby smartphones and captured by their phone. This project retrieves the diagnosis keys not to find matches, but to infer the number of app users who reported an infection.

[Estimated daily number of infections reported through COVID Alert](infections.txt)

This project is not affiliated with Health Canada or the Canadian Digital Service maintaining the app.

Next is a quick description of the approach used for making the infection estimates:

1. Once an hour, retrieve the diagnosis keys uploaded so far today with the help of [retrieve-canadian-diagnosis-keys](https://github.com/uhengart/retrieve-canadian-diagnosis-keys).
2. Determine the set of diagnosis keys uploaded in the previous hour.
3. For each key in the set, analyze whether it is sent as part of a newly reported infection or as part of a previously reported infection.

The final step is the trickiest one and requires some guessing so the numbers reported above are just estimates.




