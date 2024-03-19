# Linux crontab
For doing repetive task at scheduled time.

* [Helper to set time](https://crontab.guru/)

* Always use abolute path inside crontab and for your scripts.
* Crontab logs in recent systems like Debian 12

```
$ sudo journalctl -f -u cron.service
```
* Use ```ps aux | grep {process_name}``` to find status of running process.
* 
