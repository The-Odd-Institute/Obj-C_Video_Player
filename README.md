# Objective-C Custom Video Player

An iOS video player application built with Objective-C demonstrating how to implement a custom video player using Apple's AVFoundation framework. Supports playback from both local storage and remote URLs.

## Overview

This application provides a clean, functional video player interface with interactive controls for playing MP4 video files. The implementation showcases proper use of AVPlayer, AVPlayerLayer, and Key-Value Observing for monitoring playback state.

## Technologies

- **Language**: Objective-C
- **Framework**: AVFoundation, UIKit
- **Key Classes**: AVPlayer, AVPlayerLayer, AVPlayerItem
- **Patterns**: KVO (Key-Value Observing)
- **Platform**: iOS

## Features

### Video Playback
- Play/Pause toggle functionality
- Support for local MP4 files and remote URLs
- Automatic playback start on view appearance

### Seeking and Scrubbing
- Interactive slider for seeking through video
- Pause during seek for better control
- Resume playback after seek completion

### Status Display
- Real-time remaining time display
- Updates every 0.1 seconds using periodic time observer
- Formatted time display in label

### Loading Indicator
- Activity indicator during video buffering
- KVO monitoring of playback status
- Auto-hides when content is ready

## Implementation Highlights

### Player Setup
```objc
AVPlayer *player = [AVPlayer playerWithURL:videoURL];
AVPlayerLayer *playerLayer = [AVPlayerLayer playerLayerWithPlayer:player];
```

### Periodic Time Observer
```objc
[player addPeriodicTimeObserverForInterval:CMTimeMakeWithSeconds(0.1, NSEC_PER_SEC)
                                     queue:NULL
                                usingBlock:^(CMTime time) { /* update UI */ }];
```

### KVO for Buffering State
```objc
[playerItem addObserver:self forKeyPath:@"playbackBufferEmpty" options:NSKeyValueObservingOptionNew context:nil];
```

## Project Structure

```
Custom Video Player/
├── ViewController.m    # Video player logic and UI
├── ViewController.h    # Interface declaration
├── AppDelegate.m/h     # App lifecycle
├── Tennis.mp4          # Sample video file
└── Main.storyboard     # UI layout
```

## Requirements

- Xcode
- iOS 10.0+

![Video Player Demo](https://github.com/AmirJahan/Obj-C_Video_Player/blob/master/Obj-C_Video_Player.gif?raw=true)
