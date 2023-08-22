# Syslog Server 

* Configuration to get message from another program

```/etc/rsyslog.conf```

    module(load="imudp")
    input(type="imudp" port="10514")

    module(load="imtcp")
    input(type="imtcp" port="10514")

* Send message

    echo "myapp.sh: This is a test message" | nc -w1 -u 127.0.0.1 10514
