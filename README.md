# ddns-route53

[![Build Status](https://travis-ci.org/mthssdrbrg/ddns-route53.svg?branch=master)](https://travis-ci.org/mthssdrbrg/ddns-route53)

Simple dynamic DNS updater script using Amazon Route53.

Source is originally from [Roll your own dynamic DNS service using Amazon Route53](https://willwarren.com/2014/07/03/roll-dynamic-dns-service-using-amazon-route53)
though it's been modified to use OpenDNS for getting the current IP address, as
well as usage of command line arguments and environment variables.

## Requirements

* `bash`
* `awscli`

## Installation

```shell
curl -sLO https://github.com/mthssdrbrg/ddns-route53/raw/master/ddns-route53
```

## Usage

```shell
$ ddns-route53 --zone-id=ZONE_ID --record-set=RECORD_SET
```

The above command assumes that the necessary environment variables for `awscli`
are set, an A type record, a TTL of 300 seconds and will use
`/var/log/ddns-route53` for storing logs and state.

See `ddns-route53 --help` for more information about command line arguments.

It's possible to set a number of environment variables instead of using command
line arguments, though command line arguments take precedence over environment
variables.

* `DDNS_ROUTE53_TTL`: TTL for DNS record.
* `DDNS_ROUTE53_TYPE`: DNS record type.
* `DDNS_ROUTE53_LOG_DIR`: directory to store logs and state.
* `DDNS_ROUTE53_COMMENT`: comment set when updating the Route53 record (only
  configurable as environment variable).
* `DDNS_ROUTE53_ZONE_ID`: Amazon Route53 hosted zone ID.
* `DDNS_ROUTE53_RECORD_SET`: Amazon Route53 record set name.

## Copyright

This is free and unencumbered software released into the public domain.

See LICENSE.txt or [unlicense.org](http://unlicense.org) for more information.
