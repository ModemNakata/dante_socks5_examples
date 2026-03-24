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


Measure perfomance of socks server bandwidth usage with vnstat:

# Debian/Ubuntu
sudo apt update && sudo apt install vnstat

This saves historical data of network load.

sudo systemctl enable --now vnstat
(though neabled by default)

Hourly History (The last 24 hours):
vnstat -h
This provides a text-based bar graph showing exactly which hour had the highest rx (received) and tx (transmitted) traffic.

Daily History:
vnstat -d
Useful to see if specific days of the week are heavier than others.

Top 10 Days:
vnstat -t
Shows your all-time record-breaking traffic days.



Live performance:
vnstat -l -i eth0

(eth0 from `ip a`)

Options for low-end `alerts`

Because your VPS is low-end, you might want to know if Dante is pushing the bandwidth limit without having to log in and check. You can output the data as JSON for a simple script:

vnstat --json h 1

This gives you the last hour's data in a parseable format. You could write a tiny Python or Bash script that runs via cron and sends you a notification if tx exceeds a certain threshold (e.g., if your VPS has a 1TB monthly cap).


