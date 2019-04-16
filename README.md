# Virtuální síť za pomocí Vagrantu
Vytvořte virtuální síť složenou z DHCP- serveru, DNS serveru a databáze. K jejímu vytvoření je nejjednoduší využít nástroj Vagrant, který automatizuje jednotlivé skripty.

## Vagrant
HashiCorp Vagrant poskytuje stejné, snadné pracovní postupy bez ohledu na vaši roli vývojáře, operátora nebo návrháře. Využívá deklarativní konfigurační soubor, který popisuje všechny požadavky na software, balíčky, konfiguraci operačního systému, uživatele a další.

## Ansible
Ansible je univerzální jazyk, který odhaluje tajemství toho, jak se práce dělá. Jedním stisknutím tlačítka můžete zavést podnikové protokoly. Dejte svému týmu nástroje pro automatizaci, řešení a sdílení.
Pomocí Ansible se spouští virtuální počítače.¨

## DHCP
Používá se pro automatickou konfiguraci počítačů připojených do počítačové sítě. DHCP server přiděluje počítačům pomocí DHCP protokolu zejména IP adresu, masku sítě, implicitní bránu (default gateway) a adresu DNS serveru.
DHCP server je v nefunkčním stavu.

## Přidání clienta
```
  config.vm.define "client" do |client|
    client.vm.box = "centos/7"
    client.vm.hostname = "client"
    client.vm.network "private_network", ip:"192.168.200.10"
    client.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "client.yml"
    end
  end
```

Klient musí mít nastavenou statickou ip, kterou mu následně ansible odebere a přiřadí mu adresu od vlasního DHCP serveru.
Řeším to tímto způsobem, protože jinak Vagrant stroji přiřadí adresu z jeho DHCP poolu, tímto způsobem tento pool
obejdu a můžu použít svůj DHCP server.

## DNS
DNS je hierarchický systém doménových jmen, který je realizován servery DNS a protokolem stejného jména, kterým si vyměňují informace. Jeho hlavním úkolem a příčinou vzniku jsou vzájemné převody doménových jmen a IP adres uzlů sítě. Později ale přibral další funkce a slouží dnes de facto jako distribuovaná databáze síťových informací. 
DNS server a SQL by mělo fungovat, ale i tak je program dost nestabilní.

## Dnsko má dva záznamy
  - private.vagrantjeblbost.net
  - nenavidimsvujzivot.net

## Lukáš: SQLko
## Marek: Dnsko a složení všeho dokupy
## Vojtěch: Dhcp
## Filip: Dokumentace a řízení, ne úplně dobře