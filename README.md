# JIRA Survivor

JIRA Survivor is a simple bug dashboard that shows an overview of bugs in a
JIRA project. Based on [GitHub Survivor][1] by 99designs. 

![Screenshot](https://github.com/gengo/jirasurvivor/wiki/screenshot.png)

## Overview

It's easy to forget about bugs when you're knee-deep in feature development.
This dashboard is a good way to keep bugs on people's minds, and to show
at-a-glance information about the current bug situation.

JIRA Survivor scrapes your bug data using the [JIRA API][2] and stores it in
your local Mongo DB for subsequent querying. It shows, at a glance:

 * Top/bottom bug closers for the current reporting period (week, month or sprint)
 * Current open bug count
 * Net difference in open bugs since the last reporting period
 * Charts (yay!):
    * Number of bugs opened/closed for the last 12 reporting periods
    * Number of open bugs over the last 12 reporting periods

There are bug trackers that provide this kind of data, but we wanted something
fun that integrates with our existing bug tracking solution.

## Setup

Requirements:

* Python >= 2.7
* virtualenv
* MongoDB
* lessc
* Make

This command might satisfy the above dependencies on Ubuntu:

    $ sudo apt-get install python2.7 python-virtualenv mongodb lessc make

### Installation

    $ git clone https://github.com/gengo/jirasurvivor.git /path/to/survivor
    $ cd /path/to/survivor
    $ bin/setup
    $ $EDITOR config.py

### Initial data import

    $ bin/runtask sync

You'll probably want to run this periodically, e.g. in an hourly cron job.

### Run

    $ bin/serve

### Development notes

Stylesheets are LESS files. Run `make css` to regenerate CSS from LESS sources.

## License

MIT; see `LICENSE`

[1]: https://github.com/99designs/githubsurvivor
[2]: http://docs.atlassian.com/jira/REST/latest/
