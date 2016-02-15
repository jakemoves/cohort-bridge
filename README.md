## About this application

CohortOSCBridge allows you to trigger sound cues from QLab on devices running apps built with the Cohort framework.

## How to use

To start the bridge running:

- in cohort-bridge.js, set the value of cohortServerURL (line 1) to the URL for your instance of Cohort Server (i.e. replace the existing URL inside the quote marks with your URL)
- open a terminal window and navigate to the folder where cohort-bridge.js is
- type 'node cohort-bridge.js' to start the local bridge running on your computer
- note the first values listed in your terminal window for Host and Port

To set up QLab:

- open your QLab show file
- go to Workspace Settings > OSC 
- for Patch 1, set:
	- Name equal to whatever you want (i.e. Cohort OSC Patch)
	- IP Address equal to the Host value you copied earlier
	- Port equal to the Port value you copied earlier

To trigger cues on Cohort devices:
- make sure you have started the relevant Episode on the Cohort devices (see Tip 1, below)
- add an OSC cue to your cue list
- set the Destination to the patch you created earlier
- set the Message Type to "Custom OSC Message" 
- set the message text to "/cohort COMMAND", where COMMAND is a valid Cohort command like "sound-1-go". So a full cue might be "/cohort sound-1-go"

## Troubleshooting tips

1) cues in Cohort apps are organized into Episodes. You'll need to start a specific episode before any cues will fire in your app — when you start an episode, all the media files for that episode's cues are preloaded. So the first Cohort cue in your QLab file should have the command "episode-X-go", where X is an episode number in your Cohort app.

1) some Cohort apps require a 'check-in' before any cues can be loaded. Make sure your devices are checked in before you send any cues (including an 'episode start' cue).

3) Remember QLab does not know how long a Cohort sound cue lasts, so you will have to manually add Pre Wait or Post Wait time in QLab if you want to use follows or continues on Cohort OSC cues