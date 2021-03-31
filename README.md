# open-ondd 
An open source file decoder for the Othernet data broadcast.

This is an open source file decoder for [Othernet](http://othernet.is/) which aims to provide an open source alternative to `ondd`. This software is the result of a third-party reverse-engineering effort: https://github.com/daniestevez/free-outernet

With open-ondd you can receive the files and time packets that are broadcast by the Othernet file broadcast service.

`open-ondd.py` receives UDP packets in real-time from a designated UDP port.  `open-ondd.py` recovers the files and time packets that are transmitted by
Othernet and relayed over UDP. It also prints some interesting debug info.


Things that are not implemented/supported:

 * X.509 signature checking. The file announcements of the Othernet file service
   are signed with the Othernet X.509 certificate to prevent spoofing. 
 * Using the time packets to set the system time. 
 * Automatic decompression of received files. Previously, most files sent by
   the Othernet broadcast were `.tar.bz2` files. `ondd` extracts those files
   automatically. Othernet no longer sends .tar.bz2 files. 

## Dependencies

To install all dependencies just run: `pip3 install -r requirements.txt`

 * [crcmod](https://pypi.python.org/pypi/crcmod)
 * [zfec](https://pypi.python.org/pypi/zfec)

## Sample KISS files

You can use some [sample KISS files](https://drive.google.com/open?id=0B2pPGQkeEAfdbXFZNThCb1BLMzg) for testing.

## About LDPC decoding for files

LDPC decoding has been [implemented by George
Hopkins](https://github.com/daniestevez/free-outernet/pull/4) by reverse
engineering `ondd`.

The performance of `open-ondd` regarding FEC and LDPC decoding should
be the same as the performance of `ondd`.
