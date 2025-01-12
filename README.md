# Expo Linking API Event Listener Unreliability

This repository demonstrates a bug in Expo's `Linking` API where the event listener for deep links may not fire reliably or might be delayed when the app is already open, specifically on Android.  This can lead to missed deep links and unexpected application behavior.

## Problem
The `Linking.addEventListener` callback is not consistently triggered when the app receives a deep link while already running.  This issue appears more frequently on Android than iOS.

## Solution
The proposed solution involves checking for initial deep links and using `Linking.getInitialURL()` to handle them.  This ensures that the initial URL (if any) is processed correctly. Furthermore, using a more robust event listener implementation helps in handling events more reliably. This involves adding a more resilient logic in the event listener to address any potential delay or inconsistency in receiving the deep link event. 

## Reproduction
1. Clone this repository.
2. Run `npm install` or `yarn install`.
3. Run the app on an Android device or emulator.
4. Send a deep link to the app while it's already open.
5. Observe that the deep link might not be handled correctly.

## Note
This issue has been observed on various Expo versions.  Please refer to the bug.js and bugSolution.js for code samples illustrating the problem and the proposed solution respectively.