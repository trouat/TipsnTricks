# OneLiner Tips'n Tricks
The capitalized elements must be adjusted to fit your context. The commands below must be executed with bash or zsh.

## tracepath (tracert) for TCP
```target="IP"; port="PORT"; ttl=1; while ( echo -ne "$ttl " && hping3 -c 1 --ttl $ttl --syn -p $port $target 2>&1 | grep "TTL\|100% packet loss" ); do ttl=$(( $ttl + 1 )); done;```

## Find MTU for OpenVPN
The target is the VPN access point.

```target="IP"; i=1500; while ping -M do -W1 -s $i -c1 $target 2>&1 | grep "too long"; do i=$(( $i - 10 )); done; while ! ping -M do -W1 -s $i -c1 $target 2>&1 | grep "too long"; do i=$(( $i + 1 )); done; i=$(( $i - 1 )); echo ">> MTU $i <<\n>> VPN $(( $i - 40 )) <<";```

Edit the `/etc/openvpn/client/client.conf` file to introduce the following directive:
```mssfix <VPN_VALUE>```
