overture service配置
```service
[Unit]
Description=overture
After=network.target
[Service]
ExecStart=/soft/dns/overture-linux-amd64 -c /soft/dns/config.yml
Restart=on-abort
[Install]
WantedBy=multi-user.target
```

config.yaml

```config
bindAddress: :5353
debugHTTPAddress: 127.0.0.1:5555
dohEnabled: false
primaryDNS:
  - name: DNSPod
    address: 119.29.29.29:53
    protocol: udp
    socks5Address:
    timeout: 6
    ednsClientSubnet:
      policy: disable
      externalIP:
      noCookie: true
alternativeDNS:
  - name: iqdns
    address: a.passcloud.xyz/dns-query
    protocol: https
    socks5Address:
    timeout: 6
    ednsClientSubnet:
      policy: disable
      externalIP:
      noCookie: true
  - name: opendns2
    address: 208.67.220.220:5353
    protocol: udp
    socks5Address:
    timeout: 6
    ednsClientSubnet:
      policy: auto
      externalIP:
      noCookie: true
onlyPrimaryDNS: false
ipv6UseAlternativeDNS: false
alternativeDNSConcurrent: false
whenPrimaryDNSAnswerNoneUse: primaryDNS
ipNetworkFile:
  primary: ./china_ip_list.txt
  alternative: ./ip_network_alternative_sample
domainFile:
  primary: ./china_list.txt
  alternative: ./gfw_all_domain.txt
  matcher: full-map
hostsFile:
  hostsFile: ./hosts_sample
  finder: full-map
minimumTTL: 0
domainTTLFile: ./domain_ttl_sample
cacheSize: 0
cacheRedisUrl:
cacheRedisConnectionPoolSize:
rejectQType:
  - 255
```