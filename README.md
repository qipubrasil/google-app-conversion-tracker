# GoogleAppTracking Plugin

Google App Install Conversion tracking plugin for iOS and Android. Phonegap integration for AdMob Conversion tracking.

(June 2 2015: updated with current Google sdk and new cordova plugin.xml format. Credits to christoph-neumann mlegenhausen.)

## Preparation:

This plugin integrates with your AdMob account and AdWords campaigns.  See Google docs for more details.
See https://developers.google.com/app-conversion-tracking/.

## Installation:

Install with cordova cli:

    cordova plugin add cordova-plugin-google-conversion-tracker

Google SDK libraries are included in the plugin. You'll need to make sure the AdSupport.framework is linked in xcode for the iOS app.

## Usage

The plugin creates a `GappTracker` object, with just one method `track()`:

    GappTrack.track(conversion_id, label, value, repeatable);

Values for conversion_id, label, value, and repeatable are generated by Google when you
create a mobile app conversion in your AdWords account.  After onDeviceReady, you can track the
conversion by calling track, e.g.

    GappTrack.track("0123456789", "abCDEFG12hIJk3Lm4nO", "0.99", false);

### The 'repeatable' argument

The value for repeatable is converted to a boolean in the platform native code before passing through to the SDK's AdWordsConversionReporter.reportWithConversionId() call.

On iOS anything _other_ than true, "TRUE", "YES", "Y", and others (see the doc for boolValue) should also set repeatable to false, though some problems have been reported with this. Simple true/false is therefore probably the safest value to use, though others should work.  If you're getting any odd crashes, check that this value is coming through to the native source appropriately

See ObjectiveCs boolValue (ios) JSONArray.getBoolean (android) for acceptable true/false values.  true, false, 'true', 'false', 1, 0 should probably work in all cases.

## More Info

see https://developers.google.com/app-conversion-tracking

## License ##

Apache 2.0 License

Copyright (c) 2014 Paul Nock, MyHealthTeams
