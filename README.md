# web-audio-labs

This project is a browser-based tool for testing the capabilities of the Web Audio API's `AudioContext` and the browser's WebAssembly support.

## Features

- **AudioContext Testing**  
  - Allows you to specify `renderSizeHint`, `latencyHint`, and `sampleRate` for the `AudioContext` constructor.
  - Requests microphone access and creates an `AudioContext` with the provided options.
  - Dynamically loads an `AudioWorklet` processor to report the actual render quantum size (buffer size) used by the browser.
  - Displays the resulting `sampleRate`, `baseLatency`, and actual render quantum size.

- **WebAssembly Capabilities Check**  
  - Checks for basic WebAssembly support.
  - Tests if the browser can execute a minimal WebAssembly binary.
  - Checks for `SharedArrayBuffer` and `Atomics` support (required for WebAssembly threads).
  - Inspects for partial WASI (WebAssembly System Interface) support.

## Usage

1. **Visit the deployed web app:** https://lmiguelgato.github.io/web-audio-labs/
2. **AudioContext Test:**
   - Enter a value for `renderSizeHint` (integer or `"hardware"`).
   - Enter a value for `latencyHint` (`"interactive"`, `"playback"`, `"balanced"`, or a number in seconds).
   - Optionally, enter a `sampleRate`.
   - Click **Test AudioContext**.
   - Grant microphone access when prompted.
   - View the results in the output area.

3. **WebAssembly Capabilities Test:**
   - Click **Check WebAssembly Capabilities**.
   - View the results in the output area.

## Example

**Microsoft Edge 136.0.3240.64 (Official build) (64-bit):**

![Screenshot of the UI and output area](screenshots/Edge%20136.0.3240.64%20(Official%20build)%20(64-bit)/AudioContextCapabilities.png)

![Screenshot of the UI and output area](screenshots/Edge%20136.0.3240.64%20(Official%20build)%20(64-bit)/WebAssemblyCapabilities.png)

## How It Works

- The AudioContext test uses the [AudioWorklet API](https://developer.mozilla.org/en-US/docs/Web/API/AudioWorklet) to determine the actual buffer size used for audio rendering.
- The WebAssembly test runs a minimal binary and checks for advanced features like threads and WASI.

## Requirements

- A modern web browser with support for the Web Audio API and WebAssembly.
- Microphone access is required for the AudioContext test.
