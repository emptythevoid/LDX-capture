# LDX-capture
Bash scripts that allow capturing printer output from an LXD cholesterol machine.

LDX cholesterol machines output to an optionally attached printer.  If this data needs to be captured to be used by a computer, this can be done simply by collecting the data by serial. The scripts assume you're using a serial-to-USB cable, but this can be altered.

I have written a simple command-line interface for this process.  This is intended to be used when you a.) need to collect a lot of samples fast, and b.) when you indent to put this information in a csv or process it later.

There are two primary components.  A listener and the interface.  start-v2.sh is the interface.  It will initialize a log file and allows the operator to manually enter in a patient's name, which is then written to the log.  (This is so that when the log file is processed, you can tell which patient the results belong to.)  

listen.sh will read raw data from /dev/ttyUSB0 and append it to a log file.  

The scripts make use of figlet, lolcat, a spinner script, and a draw script to make the interface a little flashy.

This repo does not include any methods to process the resulting log - it's only for capturing it.

Requirements:
lolcat
figlet

To use:
Place all bash scripts in the same directory.  Connect the serial cable to the printer port on the LDX.  Then:

sudo start-v2.sh

(The script has to run as root so that it can get the data out of the ttyUSB.)
