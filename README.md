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

The provided script `Hostname2Disc.txt` will send the response in plain text because it's not too long (hostname).

However, in the example `SysInfo2Disc.txt` we see how the response will be sent in base64-encoded and in multiple messages as it exceeds the character limit of the POST method message.

Here are some things to consider:
* The `REM` command does not perform any keystroke injection, is just a comment.
* In each payload, remember to replace "`webhookgoeshere`" with your webhook URL for the variable `$webhook`.
* The base64-encoded code generated from the `echo` command contains the compiled PowerShell script. This can also be replaced with other PowerShell commands.
