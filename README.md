QZ Tray
========

 [![Build Status](https://travis-ci.org/qzind/tray.svg)](https://travis-ci.org/qzind/tray) [![Downloads](https://img.shields.io/github/downloads/qzind/tray/latest/total.svg)](../../releases) [![Issues](https://img.shields.io/github/issues/qzind/tray.svg)](../../issues) [![Commits](https://img.shields.io/github/commit-activity/m/qzind/tray.svg)](../../commits)

Browser plugin for sending documents and raw commands to a printer or attached device

## Getting Started
  * Download here https://qz.io/download/
  * See our [Getting Started](../../wiki/2.0-getting-started) guide.
  * Visit our home page https://qz.io.
  
## Support
  * File a bug via our [issue tracker](../../issues)
  * Ask the community via our [community support page](https://qz.io/support/)
  * Ask the developers via [premium support](https://qz.io/contact/) (fees may apply)

## Changelog
  * See our [most recent releases](../../releases)

## Java Developer Resources
  * [Install dependencies](../../wiki/install-dependencies)
  * [Compile, Package](../../wiki/compiling)
  
  
##Just suppress warning
If you're using QZ Tray in an isolated machine (like in my case), local environment or for any reason you don't need to encrypt messages and just wanna get rid of the warning message you can disable the warning dialog itself.

Disclaimer: This method is not supposed to be used in production, messages won't be signed, any website can talk to your hardware, use under your own risk.

Clone the QZ Tray repository ( https://github.com/qzind/tray.git ).
Fulfill the compiling dependencies: Ant, Java, NSIS (Windows). If you're using windows I recommend you use Chocolatey, with Chocolatey it's straightforward to install those dependencies.
Get a code editor or IDE (I used IntelliJ Idea community edition).
Navigate and edit /src/qz/ws/PrintSocketClient.java change line 476

From this:

if (cert.isTrusted() && cert.isSaved()) {
into

if (cert.isSaved()) {
Navigate and edit /src/qz/ui/GatewayDialog.java change line 92

From

allowButton.setEnabled(!persistentCheckBox.isSelected() || cert.isTrusted());
into

allowButton.setEnabled(true);
Compile using:

ant nsis for windows
ant pkgbuild for MacOS
ant makeself for linux
Actually this won't only compile but also creates the installer. QZ team did a great job automatizing everything.

Install QZ tray using the installer just created.

The first time you'll see the warning but now you can Remember the decision to Allow forever.

I suggest to use self-signed certificates or pay premium support if you need a truly secure setup.
