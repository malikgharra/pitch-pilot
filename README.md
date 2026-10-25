# Pitch Pilot

A browser game you steer with your voice. Hum, sing or whistle — **your pitch is your altitude**. Higher note, higher ship.

Plain HTML, CSS and JavaScript in one file: no server, no build step, no API keys. Your microphone is analysed locally in the browser and nothing is recorded or sent anywhere.

Made for *Agentic Programming (67723)*, Hebrew University — Lab 1, "Build Something Live", by describing it in English to an AI coding agent.

## How it works

- **Real-time pitch detection.** The microphone feeds a Web Audio `AnalyserNode`. Every frame, the [YIN algorithm](http://audition.ens.fr/adc/pdf/2002_JASA_YIN.pdf) finds the fundamental frequency, with parabolic interpolation for sub-sample accuracy. A short median filter rejects glitches. Tested accuracy is within a few cents from a low male voice (G2, 98 Hz) up to whistling (A6, 1760 Hz).
- **Tuned to you.** Hum any comfortable note and the flight path is centred on it, with about an octave above and below. Or pick Low voice, High voice or Whistle.
- **Songs are tunnels.** In song mode the walls trace a melody (Ode to Joy, Twinkle Twinkle, Frère Jacques, a major scale). Each song is transposed into your range, choosing a key that keeps the notes natural. Get through the tunnel and you've sung the tune.
- **Piano-roll world.** Lanes are semitones, the keyboard on the left lights up the note you're singing, and your pitch leaves a glowing trail so you can see your own melody line, vibrato and all.

## Controls

- 🎤 **Voice** — hum / sing / whistle. Silence makes the ship sink.
- 🖱 **Mouse / touch** fallback, or ↑ ↓ keys.
- `P` / `Esc` to pause.

## Run locally

Microphone access needs a secure origin, so serve the folder rather than double-clicking the file:

```
python3 -m http.server
```

Then open http://localhost:8000.
