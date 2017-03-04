# RPi RFID Reader

c code to listen to an RFID reader on the hardware UART of the raspberry pi 2. This comes from the [BLABFridge FridgeController](https://github.com/BLABFridge/FridgeController) and was written specifically for that use, however the c code is fairly generic and shouldn't require much modification

This uses some code found on the net for setting up the termios tty.

As per the wiki of the seeed RFID reader, it prints as follows:

    ---------------------------------
    | 02 | 10 chars | 04 | checksum |
    ---------------------------------

The code at the moment ignores everything extra contained in the packet, takes just the 10 character tag, and does not check it with the checksum. I personally do not plan on adding that functionality, but a pull request will be accepted if it adds such functionality


This code writes into a FIFO that it creates, at /var/run/RFID_FIFO. Since it is a FIFO, it blocks until the other end is opened, and therefore will not read tags unless there is a listener (see the fridgecontroller's ReaderClass for a listener implemented in java)


As always, this README will be updated (6-20 times before I get something that I like, and then occasionally after that), and pull requests are more than welcome.
