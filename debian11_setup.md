apt update
apt upgrade
apt install sudo
apt install vim
useradd --create-home --groups sudo --shell /bin/bash vlada 
passwd vlada
sudo update-alternatives --config editor #choose vim
passwd
visudo
vlada ALL=(ALL) NOPASSWD:ALL
vim /etc/ssh/sshd_config
  Port 23052
  PermitRootLogin no
  PasswordAuthentication no
  UsePAM no
su vlada
cd
mkdir ssh
chmod 700 .ssh
cd .ssh
touch authorized_keys
chmod 600 authorized_keys
echo "ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAgEAuapBjm3SySpHQLQGKgjMtW2IfsERVfx7PE4PhqZ7Jv/ZsZcFW6M9+QMjWmUiDd7yGQkhH8AP/mGAzTj7Q3GPjA6sG24VImkKYOjY0th0UCC3L7mITAptdjVgEiDXM/4/rBeDkQFrV3Lkjaf7yflpOSZEORlyNQlJgmtwBHAEeEx7qI28/fmuat/VSTRPx/lMj4lkpSdcCMyVbyf2oFuSjmACsELDAY2vYNxwu+qY0pkj/9mII6JRBXaaik5H2ZVaE+P284CC5QQljFDWZsRZnd9cEsaAOPQ68Y4ejS8CTD0POgIKKj1nEj/gFdt38W+n/OEU7aryBWD1+q7aX5ZNPvYiPrPCu3J6TEc08tWy8F603N6zqu/sQ5kGIijJ9o54Q4TGCoQqLi5gjELWFCYa34uI0wVJcwxzs1dcCRFCkStLVYYcpUz+nz/Qy57WbPs5lkwU2iMAUF3e4R8BlltrcOMMFQDoU2lviYptHIat3Ow6Dg3w+zBh3p25N/rHSNz1vDqWCZkGsvMYEsNvy4gxPqXys2kSfdtLdVnfxmXdbEDD1skzkOxJ/0867ueG8fKvW2tS017DMkxrBD+BIuaM7DU4iC34h4bBSUUy5H1sbBxRzoUzPXrcAcd2F2IPzXTzWUIGgGEB97s/wKqceNcsMvXO/6Vzn8l/SHScMu6+P7s= rsa-key-20220715" > authorized_keys
sudo systemctl restart sshd
apt install ufw
ufw default deny incoming 
ufw allow in 23052
ufw enable


* searxng
sudo apt install docker -y
sudo apt install docker-compose -y
cd /usr/local
sudo git clone https://github.com/searxng/searxng-docker.git
cd searxng-docker
