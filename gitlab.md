# gitlab ee docker password reset

```
# gitlab-rake "gitlab:password:reset[root]"
```
root
password more than 8 charachter.

# Install on Debian Based machines

* https://github.com/esmaeelE/gitlab-docker-local
* 
## Steps

### Add sources list
```
curl --silent "https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh" | sudo bash
curl -L "https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh" | sudo bash
```

```
sudo apt install gitlab-runner gitlab-ce gitlab-cli
```

### Check
```
sudo gitlab-ctl reconfigure
sudo gitlab-ctl status
sudo gitlab-ctl start/stop
```
All service must be up
```
$ sudo gitlab-ctl status 
run: alertmanager: (pid 24796) 2233s; run: log: (pid 24446) 2242s
run: gitaly: (pid 22191) 2311s; run: log: (pid 22342) 2308s
run: gitlab-exporter: (pid 24724) 2235s; run: log: (pid 23924) 2262s
run: gitlab-kas: (pid 22767) 2299s; run: log: (pid 22779) 2298s
run: gitlab-workhorse: (pid 24610) 2236s; run: log: (pid 23423) 2278s
run: logrotate: (pid 2116) 2911s; run: log: (pid 2115) 2911s
run: nginx: (pid 23472) 2275s; run: log: (pid 23505) 2274s
run: node-exporter: (pid 24623) 2236s; run: log: (pid 23770) 2266s
run: postgres-exporter: (pid 24810) 2233s; run: log: (pid 24607) 2237s
run: postgresql: (pid 22490) 2305s; run: log: (pid 22523) 2304s
run: prometheus: (pid 24786) 2234s; run: log: (pid 24257) 2250s
run: puma: (pid 22955) 2293s; run: log: (pid 22986) 2290s
run: redis: (pid 22010) 2317s; run: log: (pid 22138) 2316s
run: redis-exporter: (pid 24744) 2234s; run: log: (pid 24125) 2254s
run: sidekiq: (pid 23084) 2287s; run: log: (pid 23148) 2285s
```


