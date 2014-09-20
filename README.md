Ghost Sitemap Generator
===================

![Ghost Sitemap Generator](https://github.com/jsinh/needy-ghost-sitemap/raw/master/ghost-logo.png "Ghost Sitemap Generator")

##Generate simple ghost sitemap.

---

###Works on:

 *	Linux (Redhat  - Tested in production - http://ghost.ohmygizmos.com/)

---

###Requires:

*	A blog hosted on [ghost blogging platform](https://ghost.org) (duh)
*	The blog should be using MySQL as backend (this script works with MySQL only...for now)
*	[Ruby](https://www.ruby-lang.org/en/installation/) (I used verion: 1.9.3)

###Some gem information:
*	optparse
*	pp
*	mysql
*	[sitemap_generator](https://github.com/kjvarga/sitemap_generator)

---

###Usage:

**Step:** [Download](https://github.com/febsameer/ghost-sitemap-generator/archive/master.zip) the script on your machine.

	sudo apt-get update
	sudo apt-get install ruby ruby-dev
	sudo apt-get install wget
	sudo wget https://github.com/febsameer/ghost-sitemap-generator/raw/master/ghost-sitemap-generator.rb
	sudo chown root:root ghost-sitemap-generator.rb
	sudo chmod +x ghost-sitemap-generator.rb

**Step:** Display help for usage

	ghost-sitemap-generator.rb
	OR
	ghost-sitemap-generator.rb -h
	OR
	ghost-sitemap-generator.rb --help

**Step:** Input option information

*	-h, --help					Display help options for sitemap generator.

*	-w, --version				Displays scripts version information

*	-v, --verbose				Display verbose information during execution.

*	-s, --ping					Specify this option if you want to ping search engines (google, bing, apple).
								Will not ping if this option is not specified.

*	-d, --domain <domain-name>	Specify your Ghost blog domain name / url, E.g.: blog.jsinh.in (required)

*	-m, --mysql <hostname>		Specify your Ghost blog MySQL host name / IP Address. (required)

*	-r, --dbname <database>		Specify your Ghost blog MySQL database name. (required)

*	-u, --user <username>		Specify your Ghost blog MySQL username. (required)

*	-c, --password <password>	Specify your Ghost blog MySQL password. (required)

*	-f, --frequency <option>	Specify sitemap generated links update frequency. (required)
								Possible values: always, hourly, daily, weekly, monthly, yearly, never

*	-p, --priority <value>		Specify sitemap generated links priority. (required)
								Possible value range: 0.0 to 1.0

*	-o, --output <path>			Specify path where the newly generated sitemap should be placed. Do not include sitemap file name.


**Step:** Sample usage with ping and verbose mode

	sudo ghost-sitemap-generator.rb -d http://ghost.ohmygizmos.com/ -m 127.0.0.1 -r ghostdb -u ghostuser -c ghostpassword -o /var/www/ -f daily -p 0.5 -s -v

**Step:** Sample usage with ping only

	sudo ghost-sitemap-generator.rb -d http://ghost.ohmygizmos.com/ -m 127.0.0.1 -r ghostdb -u ghostuser -c ghostpassword -o /var/www/ -f daily -p 0.5 -s

**Step:** Sample usage with verbose only

	sudo ghost-sitemap-generator.rb -d http://ghost.ohmygizmos.com/ -m 127.0.0.1 -r ghostdb -u ghostuser -c ghostpassword -o /var/www/ -f daily -p 0.5 -v

**Step:** Sample usage without ping or verbose

	sudo ghost-sitemap-generator.rb -d http://ghost.ohmygizmos.com/ -m 127.0.0.1 -r ghostdb -u ghostuser -c ghostpassword -o /var/www/ -f daily -p 0.5

---

###Scheduled execution setup:

I am using CRONTAB for scheduled execution of this script.

**Step:** Install CRONTAB

	sudo apt-get update
	sudo apt-get gnome-schedule

**Step:** Edit crontab and add this script for execution.

	sudo crontab -e

Add the following at end of the file:
	
	* */6 * * * ruby <full-path-to-ghost-sitemap-generator.rb> -d <domainame> -m <mysqlhostname> -r <dbname> -u <username> -c <password> -o <output-file-path> -f daily -p 0.9 -s

This executes the script (with ping and no verbose) every 6 hours.

You can collect execution information from CRONTAB execution schedule by using following command instead of the above:

	* */6 * * * ruby <full-path-to-ghost-sitemap-generator.rb> -d <domainame> -m <mysqlhostname> -r <dbname> -u <username> -c <password> -o <output-file-path> -f daily -p 0.9 -s >> <path-to-log-filename> 2>&1

---


###Credits:

Option 2 was the best one I can rely on, so I took the idea and decided to groom it to my needs.

Base idea and [original code](https://github.com/mmornati/ghost-sitemap-generator) credits to : [Macro Mornati](http://blog.mornati.net/optimize-ghost-for-seo-sitemap-generator/), thanks !!
Forked from [forked code](https://github.com/jsinh/needy-ghost-sitemap) credits to : [Jaspalsinh Chauhan](blog.jsinh.in/seo-for-ghost-needy-sitemap-generator/), thanks !!
Life became cool with [Sitemap_generator](https://github.com/kjvarga/sitemap_generator) gem in ruby, thanks !!

---

###License

This work is [licensed](https://github.com/jsinh/needy-ghost-sitemap/raw/master/LICENSE) under:

The MIT License (MIT)
Copyright (c) 2014 Jaspalsinh Chauhan

---

