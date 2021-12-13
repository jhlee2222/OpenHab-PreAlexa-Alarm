# OpenHab-PreAlexa-Alarm
Project to create a simple scripted rule for use in OpenHab3. The general idea is to make it possible to trigger Alexa commands to be performed X minutes before an Alexa alarm goes off.

As best I can tell, OpenHab is one of the only home automation applications that can obtain the time of an alarm a users sets on Alexa using the NextAlarm channel of the Alexa binding. My goal is to take that time, subtract a certain amount of time from it, and have OpenHab cause Alexa to perform certain actions at that time prior to Alexa's alarm going off.

A general use would be for a "gentle wake" routine. I would like to have the lights in a room turn on at the dimmest setting and gradually increase in brightness, reaching maximum brightness once the alarm goes off. The entire routine would be put together in the Alexa app, but OpenHab would be responsible for obtaining the time of the last alarm, tracking it, then having Alexa kick off that routine at the proper time.

Pseudo Code would be:

Trigger: Item NextAlarm changed
Then:
  - Check if an old timer is running and if so cancel it.
  - Check if NextAlarm is more than X minutes in the future (error handling).
  - Set a new timer with an end time of NextAlarm.minusMinutes(X). When the timer reaches zero, Open Hab causes Alexa to start the routine.
 
 I'm new to OpenHab, and overwhelmed by the complexity of coding for it. The purpose of this project is to set up a bounty.
