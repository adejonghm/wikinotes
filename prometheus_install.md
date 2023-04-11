# Install Prometheus

### Download Pometheus
```sh
curl -LO https://github.com/prometheus/prometheus/releases/download/v2.37.5/prometheus-2.37.5.linux-amd64.tar.gz
```

### Copy binares
```sh
sudo cp prometheus-2.37.5.linux-amd64/prometheus /usr/local/bin/
sudo cp prometheus-2.37.5.linux-amd64/promtool /usr/local/bin/
```

### Copy configuration files
```sh
sudo mkdir /etc/prometheus
sudo cp prometheus-2.37.5.linux-amd64/prometheus.yml /etc/prometheus
sudo cp prometheus-2.37.5.linux-amd64/consoles /etc/prometheus
sudo cp prometheus-2.37.5.linux-amd64/console_libraries /etc/prometheus
```

### Create prometheus service
```sh
sudo vim /etc/systemd/prometheus.service
```
**note**: You have and example [here](./files/prometheus/prometheus.service).

### Set permissions
```sh
sudo chown -R prometheus:prometheus /etc/prometheus
sudo chown -R prometheus:prometheus /var/lib/prometheus
sudo chown -R prometheus:prometheus /usr/local/bin/promtool
sudo chown -R prometheus:prometheus /usr/local/bin/prometheus
```

### Create a file for data
```sh
mkdir /var/lib/prometheus
```

### Create a user for Prometheus
```sh
sudo addgroup --system prometheus
sudo adduser --shell /sbin/nologin --system --group prometheus
```

### Restart systemd & enable prometheus
```sh
sudo systemctl daemon-reload
sudo systemctl enable prometheus
sudo systemctl start prometheus
```

### Command to analice logs 
```sh
journalctl -u prometheus
```
