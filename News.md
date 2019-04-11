# Spindump News

## Improved documentation (April 2019)

The documentation and READMEs were improved.

## Support for Google QUIC as currently implemented in Chrome (March 2019)

Szilveszter Nadas from Ericsson helped implemented Google QUIC recognition and Spindump now correctly recognises these sessions that come from current version of Chrome. In the future, of course, Chrome will eventually transition to the IETF QUIC version which was already recognised. At the Hackathon we also started supporting IETF QUIC version 18, and will soon support versions 19 and 20.

## Automated testing (March 2019)

As part of the IETF 104 Hackathon, Spindump is now tested extensively with the help of a set of test cases, directly from running make. Use "make test" to run the tests!

## Privilege downgrade (March 2019)

Spindump is now performing a privilege downgrade as soon as it has opened the PCAP interface. Since on Linux, spindump runs as suid root, reduces the risk of impacts from accidental issues or bugs in the analyzer code that previously run  root. Thank you Loganaden for this contribution!

## Sending measurement information to a collection point (March 2019)

Also, a long-awaited upgrade is in the work: Spindump will be able to collect information and submit it to another Spindump instance elsewhere. As the protocol used to submit measurement data is web-based, this can also be used to submit data to any suitable web server, for instance, in the convenient JSON format. See the [format descripton](https://github.com/EricssonResearch/spindump/blob/master/Format.md) for more information. Note also that the new JSON format includes an array at the top level, rather than merely records following each other without an array. For now, the sending side works but we're still working on the server. To send data from a Spindump instance to a web server, give the command like this:

    spindump --remote-block-size 0 --silent --format json --remote https://httpbin.org/post

This will send every event in JSON format to the webserver in httpbin.org, and make a POST for each of those events.

## CMake (February 2019)

With the help of Lars Eggert, Spindump has switched to the use of cmake! Your compilations will be affected, so next time you get a new version, please install the necessary software (cmake and pkg-config). No Makefiles are provided in the repo anymore, they will be created by cmake. So do this for your next compilation:

    sudo apt-get install pkg-config cmake make gcc libpcap-dev libncurses5-dev
    cmake .
    make