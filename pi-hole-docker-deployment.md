# Pi-hole Docker Deployment

1. First we need to stop the DNS built in on the Ubuntu machine.

```bash
systemctl stop systemd-resolved
systemctl disable systemd-resolved
```

2. Next create a new directory named <mark style="color:red;">`pihole`</mark>and inside that directory create a <mark style="color:red;">`docker-compose.yml`</mark> file.

```bash
mkdir pihole
cd pihole
nano docker-compose.yml
```

3. After that populate the file with the information bellow, you can change the <mark style="color:red;">`WEBPASSWORD`</mark>.

```yaml
version: "3"

services:
  pihole:
    container_name: pihole
    image: pihole/pihole:latest
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "67:67/udp"
      - "80:80/tcp"
    environment:
      TZ: 'Europe/Lisbon'
      WEBPASSWORD: 'adminpassword'
    volumes:
      - './etc-pihole:/etc/pihole'
      - './etc-dnsmasq.d:/etc/dnsmasq.d'
    restart: unless-stopped
```

## Docker Compose

1. Start the WordPress deployment using docker-compose:

```bash
docker-compose up -d
```

2. After that navigate to the dashboard with <mark style="color:red;">`http://your_ip_address/admin`</mark> with the credentials of the <mark style="color:red;">`WEBPASSWORD`</mark>.
