# subjack

[![Build Status](https://api.travis-ci.org/haccer/subjack.svg?branch=master)](https://travis-ci.org/haccer/subjack) [![Go Report Card](https://goreportcard.com/badge/github.com/haccer/subjack)](https://goreportcard.com/report/github.com/haccer/subjack) [![GitHub license](https://img.shields.io/github/license/haccer/subjack.svg)](https://github.com/haccer/subjack/blob/master/LICENSE)

subjack is a Hostile Subdomain Takeover tool written in Go designed to scan a list of subdomains concurrently and identify ones that are able to be hijacked. With Go's speed and efficiency, this tool really stands out when it comes to mass-testing. Always double check the results manually to rule out false positives. 

## Installing

You need have [Go](https://golang.org/) installed. Full details of installation and set up can be found [here](https://golang.org/doc/install). 

`go get github.com/haccer/subjack`

## How To Use:

`./subjack -w domains.txt -t 100 -timeout 30 -o results.txt -https`
- `-w domains.txt` is your list of subdomains. I recommend using `cname.sh` (included in repository) to sift through your subdomain list for ones that have CNAME records attached and use that list to optimize and speed up testing.
- `-t` is the number of threads (Default: 10 threads). 
- `-timeout` is the seconds to wait before timeout connection (Default: 10 seconds).
- `-o results.txt` where to save results to (Optional).
- `-https` enforces https requests which may return a different set of results and increase accuracy (Optional).
- `-strict` sends HTTP requests to every URL (Optional).

Currently checks for:
- Amazon S3 Bucket
- Amazon Cloudfront
- Bitbucket
- Cargo
- Fastly
- FeedPress 
- Ghost
- Github 
- Helpjuice 
- Help Scout
- Heroku 
- Mashery
- Pantheon.io
- Shopify
- Surge 
- Tumblr
- UserVoice
- WordPress  
- WP Engine

<!--
## Screenshots
<img src="https://i.imgur.com/xfjSuwW.jpg" />
<img src="https://i.imgur.com/2bZF0Ge.png" />
-->

## In Action
![realtime](https://github.com/haccer/haccer.github.io/blob/master/img/subjack1.gif)

## Practical Use

You can use [scanio.sh](https://gist.github.com/haccer/3698ff6927fc00c8fe533fc977f850f8) which is kind of a PoC script to mass-locate vulnerable subdomains using results from Rapid7's Project Sonar. This script parses and greps through the dump for desired CNAME records and makes a large list of subdomains to check with subjack if they're vulnerable to Hostile Subdomain Takeover. Of course this isn't the only method to get a large amount of data to test. **Please use this responsibly ;)**

## FAQ
**Q:** What should my wordlist look like?

**A:** Your wordlist should include a list of subdomains you're checking and should look something like:
```
assets.cody.su
assets.github.com
b.cody.su
big.example.com
cdn.cody.su
dev.cody.su
dev2.twitter.com
```

**Q:** I ran my scan and nothing happened. What does this mean?

**A:** In most cases, this means that subjack didn't discover any vulnerable subdomains in your wordlist or your wordlist of is formatted weird.

## Contact

Shout me out on Twitter: [@now](https://twitter.com/now)
