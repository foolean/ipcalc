# ipcalc

IP Subnet Calculator

# Description

Calculate IP subnet information from an IP address and a CIDR prefix.

## Usage

    usage: ipcalc [-h] [-i INT] [-I IP] [-v] [-p [INT]] [-n [INT]] cidr

    IPv4 Subnet Calculator

    positional arguments:
      cidr                  CIDR notation of the address to use (e.g. 192.168.127.10/24)

    optional arguments:
      -h, --help            show this help message and exit
      -i INT, --index INT   Index for which to print the corresponding IP address (use CSV or multiple times)
      -I IP, --ip IP        IP addresses for which to print the corresponding index (use CSV or multiple times)
      -v, --verbose         Print more verbose information
      -p [INT], --previous [INT]
                            Print the (n) previous CIDR ranges
      -n [INT], --next [INT]
                            Print the (n) next CIDR ranges

### Previous and next ranges

Use the [-p|--previous] and [-n|--next] flags to print the list of CIDR ranges
that precede and/or follow the range currently being examined.

Example:
    $ ./ipcalc 10.128.0.0/20 -n 3 -p 3
    network:                  10.128.0.0
    prefixlen:                /20
    netmask:                  255.255.240.0
    host range:               10.128.0.1 to 10.128.15.254
    broadcast addresss:       10.128.15.255
    total IP addresses:       4094


    CIDR list:
    previous: 10.127.208.0/20
    previous: 10.127.224.0/20
    previous: 10.127.240.0/20
    current:  10.128.0.0/20
    next:     10.128.16.0/20
    next:     10.128.32.0/20
    next:     10.128.48.0/20


### Verbosity

Verbose mode [-v|--verbose] will display additional information such as the
hex, binary, or reverse DNS representation of the IP address.

Example:
    $ ./ipcalc 10.128.0.0/20 -v
    network:                  10.128.0.0
    prefixlen:                /20
    netmask:                  255.255.240.0
    wildcard mask:            0.0.15.255
    host range:               10.128.0.1 to 10.128.15.254
    broadcast addresss:       10.128.15.255
    total IP addresses:       4094

    hex:                      0x0a800000
    binary:                   0b00001010100000000000000000000000
    in-addr.arpa format:      0/20.0.128.10.in-addr.arpa


## Linting

    pylint ipcalc


## License

    ipcalc - IP Subnet Calculator
    Copyright (C) 2023 Bennett Samowich

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>.
