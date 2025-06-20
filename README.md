# vps-infra-ynov

# Projet Serveur Web - Infrastructure Dockerisée

Ce projet met en place un serveur web complet auto-hébergé, utilisant Docker pour faire fonctionner plusieurs applications web réparties sur des sous-domaines distincts. Le tout est exposé au public via un reverse proxy sécurisé par HTTPS (certificats auto-signés).

## Services déployés

| Application   | Domaine                | Langage     |
|--------------|------------------------|-------------|
| WordPress    | https://b1vps.com       | PHP + MySQL |
| Wekan        | https://wekan.b1vps.com | Node.js     |
| Uptime Kuma  | https://uptime.b1vps.com| Node.js     |
| Forgejo      | https://forgejo.b1vps.com | Go + MySQL |

## Arborescence du projet

```
webinfra/
├── docker-compose.yml
├── reverse-proxy/
│ ├── nginx.conf
│ └── certs/
│ ├── selfsigned.crt
│ └── selfsigned.key
```

## Sécurité appliquée
- Reverse proxy NGINX avec TLS
- UFW : ports 80, 443, 22 uniquement
- SSH sécurisé : accès root désactivé
- Fail2Ban configuré sur SSH
- Noms de domaine simulés avec `/etc/hosts`

## Supervision
- **Uptime Kuma** : état de santé des services
- **Optionnel** : Netdata, Grafana + Prometheus
