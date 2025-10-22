# zabbix-monitoring
# Conclusion sur Zabbix

Zabbix est une solution de supervision robuste et complète, largement utilisée pour surveiller l'état des infrastructures informatiques, des applications et des équipements réseau.  

## Avantages de Zabbix  
- **Interface complète et centralisée** : tableau de bord, graphiques, cartographies.  
- **Support étendu des protocoles** : SNMP, IPMI, agent natif, agent passif.  
- **Alerting puissant** : notifications par email, SMS, scripts personnalisés.  
- **Historisation des données** : collecte et stockage des métriques dans une base relationnelle.  
- **Communauté active** et documentation riche.  

## Limites de Zabbix  
- **Scalabilité limitée** : difficile à gérer efficacement à très grande échelle ou environnements très dynamiques.  
- **Fréquence de collecte** : typiquement toutes les minutes, ce qui peut ne pas suffire pour des métriques nécessitant un suivi temps réel très fin.  
- **Stockage basé sur des bases relationnelles** : peut poser des problèmes de performance pour des volumes très importants de données temporelles.  
- **Complexité de configuration** : montée en charge et intégration parfois plus lourdes.  

Ces limites expliquent en partie pourquoi Prometheus, avec son architecture orientée métriques temps réel, son stockage optimisé en base de données de séries temporelles (TSDB) et sa capacité à scruter (scrape) fréquemment les données, est devenue une solution très prisée dans le monde de la supervision moderne.  

---

## Prérequis et installation

Ce guide est prévu pour un système **Ubuntu** (ou une distribution Linux compatible Docker).

### Installer Docker et Docker Compose

```bash
# Mettre à jour Ubuntu
sudo apt update
sudo apt upgrade -y

# Installer les paquets nécessaires
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common

# Ajouter la clé GPG officielle Docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Ajouter le dépôt Docker stable
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Mettre à jour les paquets et installer Docker Engine
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io

# Vérifier que Docker fonctionne
sudo systemctl status docker

# Installer Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

# Vérifier la version installée de Docker Compose
docker-compose --version

# (Optionnel) Ajouter votre utilisateur au groupe docker pour exécuter docker sans sudo
sudo usermod -aG docker $USER
newgrp docker

---

## Pour commencer rapidement avec Zabbix, vous pouvez cloner le dépôt contenant un fichier `docker-compose.yml` prêt à l'emploi et lancer l’ensemble des services avec la commande suivante :

```bash
git clone https://github.com/NadineAbedrabba/zabbix-monitoring.git
cd zabbix-monitoring
docker-compose up -d



# Essayer le trigger Jenkins
