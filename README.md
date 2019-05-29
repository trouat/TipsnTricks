# OneLiner Tips'n Tricks
The capitalized elements must be adjusted to fit your context.
## tracepath (tracert) for TCP
```target="IP"; port="PORT"; ttl=1; while ( echo -ne "$ttl " && hping3 -c 1 --ttl $ttl --syn -p $port $target 2>&1 | grep "TTL\|100% packet loss" ); do ttl=$(( $ttl + 1 )); done;```
