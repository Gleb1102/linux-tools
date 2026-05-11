# linux-tools
pve:
cd /root
git clone https://github.com/Gleb1102/linux-tools.git
cd linux-tools && chmod +x *.sh

hq-srv:
nano /etc/resolv.conf
nameserver 8.8.8.8

apt-get update
apt-get install dnsmasq -y
systemctl enable --now dnsmasq

systemctl status dnsmasq

hq-cli:
ip a (vlan)
nmcli con delete "Wired connection 1" 2>/dev/null || true
nmcli con add type vlan con-name vlan200 dev ens18 id 200 ipv4.method auto ipv6.method ignore
nmcli con up vlan200

hostnamectl set-hostname hq-cli.au-team.irpo
timedatectl set-timezone Asia/Yekaterinburg
