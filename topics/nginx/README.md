
# Fast introduction to nginx

Nginx is a webserver that use for loadballancing.

## Install on Debian.

`$ sudo apt install nginx`

## Start service

`$ sudo systemctl start nginx`

check is running?

open localhost address in webbrowser or

`$ lynx localhost`
`$ firefox localhost`
`$ curl -I 127.0.0.1`

## Inspect logs

`sudo tail -F /var/log/nginx/access.log`
`sudo tail -F /var/log/nginx/error.log`


## Use nginx as loadballancer

First of all we need to some simple server application.

one of the simplest way to achieve that is nc command that provides with netcat package on Debian.

`$ sudo apt install netcat`

To run many server in one terminal I use tmux as a good termianl multiplexer.

Here is the terminal output with ascinema


### one pane tmux 

	nc -l 1111
	nc -l 2222
	nc -l 3333
	nc -l 4444


[nc tutorial](https://www.tecmint.com/netcat-nc-command-examples/)


## [Loadballancer](https://github.com/esmaeelE/LB)

