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

Nous allons donc découvrir dans la suite comment Prometheus aborde ces défis et améliore la gestion des métriques en environnement dynamique et à grande échelle.

---

Pour commencer rapidement avec Zabbix, vous pouvez cloner le dépôt contenant un fichier `docker-compose.yml` prêt à l'emploi et lancer l’ensemble des services avec la commande suivante :

```bash
git clone https://github.com/NadineAbedrabba/zabbix-monitoring.git
cd zabbix-monitoring
docker-compose up -d
