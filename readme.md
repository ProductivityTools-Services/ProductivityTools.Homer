
## Docker

docker run -d -p 8082:8080 -v ~/bin/Home.Homer/Assets:/www/assets/ --restart=always b4bz/homer:latest

## Open firewall

sudo ufw status verbose
sudo ufw allow 7000/tcp

