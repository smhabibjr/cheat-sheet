## Status check

```bash
sudo systemctl status nginx
```
```bash
sudo /etc/init.d/nginx status
```
## Stop nginx
```bash
sudo systemctl stop nginx
```
## Start nginx
```bash
sudo systemctl start nginx
```
## Restart  nginx
```bash
sudo systemctl reload nginx
```

## Restart  nginx

If you’re refreshing Nginx after changing the configuration, it’s best to gracefully reload the service. That shuts down old processes and restarts new ones with the new configuration.
```bash
sudo systemctl reload nginx
```

## Force Restart Nginx
For major configuration changes, you can force a full restart of Nginx. This force-closes the whole service and sub-processes, and restarts the whole package.
```bash
sudo systemctl restart nginx
```
## Restart vs Reload Nginx
The reload command keeps the Nginx server running as it reloads updated configuration files. If Nginx notices a syntax error in any of the configuration files, the reload is aborted and the server keeps running based on old config files. Reloading is safer than restarting Nginx.

The restart command will shut down the server including all related services and power it on again. Restart Nginx only when making significant configuration updates, such as changing ports or interfaces. This command will force shut down all worker processes.

## Configure Nginx to Launch on Boot
Use the enable option with the systemctl command to enable Nginx:

```bash
sudo systemctl enable nginx
```

Use the disable option with the systemctl command to disable Nginx:

```bash
sudo systemctl disable nginx
```
