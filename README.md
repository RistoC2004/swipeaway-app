# SwipeAway

SwipeAway is an iPhone camera-roll cleaner. Swipe right to keep a photo, swipe left to queue it for removal, and review everything before anything leaves your library.

It is built for large photo libraries and keeps every photo on the device: no account, no uploads and no custom backend.

> The production source code is maintained in a private repository.

## App Preview

Screenshots will be added with the App Store release.

## What SwipeAway Does

SwipeAway turns camera-roll cleanup into short, focused sessions.

Each session shows one photo or video at a time. Swiping builds a removal queue, and a final review step shows every selected item before the cleanup is approved. Approved items move to Photos' Recently Deleted album, where they stay recoverable for 30 days.

Core features include:

- Swipe to keep or remove
- 5-Minute Clean, Recent and This Month sessions
- On This Day memories
- Screenshots and Long Videos categories
- Smart Stacks for similar photos and bursts
- Undo and save-and-resume sessions
- Final review grid before any removal
- Limited Photos access support
- Progress history
- Daily free decisions and a Pro subscription

## Tech Stack

- React Native
- Expo (SDK 57)
- Expo Router
- TypeScript
- Swift (custom Expo native module)
- PhotoKit
- Apple Vision framework
- React Native Reanimated and Gesture Handler
- expo-image and expo-video
- RevenueCat and StoreKit
- Jest, React Native Testing Library and node:test
- EAS Build
- Git / GitHub

## Engineering Highlights

- Built the mobile application using React Native, Expo Router and TypeScript.
- Wrote a custom Swift Expo module that reads PhotoKit metadata in cancellable pages without opening files, decoding thumbnails or downloading iCloud originals.
- Tuned the app against a real 54,000-item photo library: paged library indexing, debounced change handling and targeted re-rendering keep swiping responsive.
- Implemented Smart Stacks with on-device Vision feature prints, comparing photos taken close together in time within bounded, cancellable batches.
- Ran swipe gestures and card animation on the UI thread with Reanimated worklets.
- Persisted every decision with a coalescing snapshot writer, plus a durable save before any Photos deletion.
- Designed safe deletion: explicit final review, confirmed-ID-only deletion, and an interrupted-deletion journal that never retries automatically.
- Reconciled saved sessions by stable asset IDs so edits or deletions in Photos never corrupt a cleanup.
- Covered core logic and screens with 115+ automated tests.

## Cleanup Flow

A SwipeAway cleanup follows a review-first sequence:

1. Choose a session or category.
2. Swipe through photos and videos one at a time.
3. Undo, pause and resume at any point.
4. Review the removal queue and keep anything you changed your mind about.
5. Approve the cleanup.
6. Items move to Recently Deleted in Photos.

Nothing is removed from the library until the final review is approved.

## Privacy

SwipeAway has no account system and no custom backend.

- Photos and videos are read on the device only.
- Similarity analysis runs on the device with Apple's Vision framework.
- No media is uploaded.
- Subscriptions are handled by Apple and RevenueCat.

## Reliability Work

Development has focused on real-device performance and data safety.

Examples include:

- Loading and swiping in a 54,000-item library
- Keeping upcoming photo previews ready ahead of the current card
- Handling iCloud-only photos and missing previews
- Recovering from interrupted deletions
- Keeping sessions valid when photos change in the Photos app
- Letting users switch categories without losing kept progress

## Development Process

SwipeAway is being developed as a production iOS application.

Development has included:

1. Product design
2. Native PhotoKit and Vision module
3. Swipe gestures and session flow
4. Categories and Smart Stacks
5. Safe deletion and review
6. Large-library performance
7. Subscriptions
8. Physical iPhone QA
9. App Store preparation

## Source Code

The main application repository is private because it contains active application and configuration.

This repository provides a public technical and visual overview of the project.

## Developer

**Risto Caissie**  
Software Developer — Calgary, Alberta

📧 ristocaissie1@gmail.com
