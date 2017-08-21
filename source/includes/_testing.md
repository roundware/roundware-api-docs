# Testing

We love tests, but need more, so feel free to contribute(!).

## Unit tests
We have unit tests, but no where near full coverage at this point, so we need to do additional testing.

To run unit tests:

`./scripts/tests.sh`

To run individual unit test (for example):

`./tests.sh tests.roundwared.test_recording_collection.TestRecordingCollection`

## Stream testing script

We have a script that starts up a stream and then moves the listener in and out of range of the default asset at lat/lon 1/1.  To run this test:

`./scripts/stream-test.sh`

You can add additional ambient test assets to project #1 using this script:

`./scripts/add-test-audio.py`
