# Ora

> polychain hf0residency hashkey_capital sevenxventures tarafından 20M $ yatırım aldı

> Donanım: En az 8 GB RAM ve 50 GB Disk gereklidir.

#

> Ora node'u için sıfır bir account metamask oluşturun.

> [Buradan](https://www.ora.io/app/tasks/dashboard/) hesap oluşturun.

> Sağ altta ref kısmına `ZFIC47` kodunu girerek 5 puan alabilirsiniz. (Davetler 'direkt' puan vermiyor, davet edilen alıyor.)

> Bu cüzdan hem node puanları hem de diğer puanları toplamak için kullanın.

#

## Kurulum

```console

# sorun yaşamamak için komutları adım adım girebilirsiniz
sudo apt-get update && sudo apt-get upgrade -y
apt install curl iptables build-essential git wget jq make gcc nano tmux htop nvme-cli pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev screen -y

sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# bu kısmı toplu girelim.
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

#

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
```

```console
# tora kurulumu
git clone https://github.com/ora-io/tora-docker-compose
cd tora-docker-compose
cp .env.example .env
nano .env
````

> `.env` içinde sadece RPC'leri ve private keyi değişelim.

> Yukarıdaki oluşturduğumuz cüzdanın hesap bilgiler kısmından özel anahtarı alalım.

<img width="337" alt="Ekran Resmi 2024-09-14 19 20 09" src="https://github.com/user-attachments/assets/fe908e3f-91c0-44c2-b0bb-8dcff31cb323">

> Ethereum Mainnet wss, http ve sepolia wss, http kısmına [alchemyden](https://dashboard.alchemy.com/) aldığınız api linklerini girin ardından CTRL X Y ENTER ile çıkın.

![image](https://github.com/user-attachments/assets/1c292743-8334-4b96-9dcc-9bf027f3f005)

#

```console
screen -S ora
cd tora-docker-compose
sysctl vm.overcommit_memory=1
docker compose up
```

> compose up yaklaşık 5-10 dk arası sürüyor.

![image](https://github.com/user-attachments/assets/071706d3-78fe-47e9-b5b5-470dcbef84a4)

> Prompt üretip loglarınızı kontrol edin https://www.ora.io/app/opml/openlm

> Loglarda confirm at txhash : 0x gibi bir mesaj görürseniz nodunuz başarılı şekilde çalışıyor demektir.







