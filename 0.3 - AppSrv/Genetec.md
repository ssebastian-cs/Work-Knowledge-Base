We use Genetec for timeclock and building access cards. The Genetec system is the source of truth for the Timeclock Badge Number on our Okta profiles. These Badge Numbers are stored in a staging table called `Genetec Report (Badge Number, GUID)`. 

`Genetec - Badge Number Trigger (v2)` parses the card number, and employee number and then sends it to `Genetec - Update Badge Number (v2)` flow which finds the Okta profile and updates the card number. 

The `Timeclock Update Workflow` is how the seasonal and part-time people clock-in and clock-out with the badge number being passed from the access card to the station. 