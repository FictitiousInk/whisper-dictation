# Multilingual Dictation App based on OpenAI Whisper
Multilingual dictation app based on the powerful OpenAI Whisper ASR model(s) to provide accurate and efficient speech-to-text conversion in any application. The app runs in the background and is triggered through a keyboard shortcut. It is also entirely offline, so no data will be shared. It allows users to set up their own keyboard combinations and choose from different Whisper models, and languages.

## Prerequisites
The PortAudio library is required for this app to work. You can install it on macOS using the following command:

```bash
brew install portaudio
```

## Permissions
The app requires accessibility permissions to register global hotkeys and permission to access your microphone for speech recognition:

1. Go to System Settings > Privacy & Security > Accessibility and add Terminal.app
2. Go to System Settings > Privacy & Security > Input Monitoring and add Terminal.app
3. During Installation you will also receive a request to allow access to the Microphone, enable this to add it to System Settings > Privacy & Security > Microphone

## Installation
Clone the repository:

```bash
git clone https://github.com/foges/whisper-dictation.git
cd whisper-dictation
```

\[Optional] Create a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate
```

Install the required packages:

```bash
pip install -r requirements.txt
```

## Usage
Run the application:

```bash
python whisper-dictation.py
```
To start dictation, use the key combination <kbd>option</kbd> + <kbd>command</kbd> (on macOS) or <kbd>Ctrl</kbd> + <kbd>Alt</kbd> on other platforms.

You can change the key combination and which model is used using command-line arguments (see below). By default, the app uses the "base" Whisper ASR model. Note that models other than `tiny` and `base` can be slow to transcribe and are not recommended unless you're using a powerful computer, ideally one with a CUDA-enabled GPU. 

### Command-line arguments:
```
[-h]
[-m {tiny,tiny.en,base,base.en,small,small.en,medium,medium.en,large}]
[-k KEY_COMBINATION] # Type this out as a string, with `+` between keys, e.g. **cmd_l+shift**. Note the difference between cmd_l and cmd_r. 
[-l LANGUAGE]        # Two-letter language codes. For multiple languages, separate with a comma, no spaces.
[-t MAX_TIME]        # An integer denoting a maximum number of seconds to record for.
```

Example:

```bash
python whisper-dictation.py -m large -k cmd_r+shift -l en,no
```

The models are multilingual, and you can specify a two-letter language code (e.g., "no" for Norwegian) with the `-l` or `--language` option. Specifying the language can improve recognition accuracy, especially for smaller model sizes.

## Setting the App as a Startup Item
To have the app run automatically when your computer starts, follow these steps:

 1. Open System Preferences.
 2. Go to Users & Groups.
 3. Click on your username, then select the Login Items tab.
 4. Click the + button and add the `run.sh` script from the whisper-dictation folder.
