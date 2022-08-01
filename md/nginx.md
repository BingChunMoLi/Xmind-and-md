重写路径
```conf
rewrite "^/api/(.*)$" /$1 break;
```

设置api代理
```conf
location ^~/api/ {
	proxy_set_header Host $host;
}
```