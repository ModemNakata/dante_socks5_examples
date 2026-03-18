# VPS Benchmarking tool

https://github.com/masonr/yet-another-bench-script

How to run:

curl -sL https://yabs.sh | bash

or 

wget -qO- yabs.sh | bash


# How to test max connections (e.g. stress-test dante socks5 server)

from: https://www.inet.no/dante/doc/latest/config/capacity.html

download & run this perl script: https://www.inet.no/dante/files/maxconn.pl

 maxconn.pl -w 100 -b 10.0.0.1 -c 2000 -s 10.0.0.2:1080


=======
