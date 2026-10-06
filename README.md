# OpenLDAP & Authentification SSH Centralisée avec Docker

## 📋 Présentation
Ce projet met en place une infrastructure d'authentification centralisée basée sur **OpenLDAP**, déployée via **Docker Compose**, avec une interface de gestion **phpLDAPadmin**. Un serveur **SSH** est configuré comme client LDAP pour gérer l'authentification et l'autorisation des utilisateurs (`PAM` + `NSS` + `nslcd`).

---

## 🏗️ Architecture Réseau

| Composant | Adresse IP | Rôle |
| :--- | :--- | :--- |
| **Serveur OpenLDAP** | `192.168.1.195` | Annuaire centralisé (Conteneur Docker) |
| **Serveur SSH** | `192.168.1.108` | Client LDAP / Serveur d'accès SSH |
| **Machine Cliente** | `192.168.1.162` | Poste utilisateur pour les tests |

---

## 🚀 1. Déploiement Docker (Serveur OpenLDAP : `192.168.1.195`)

### Service OpenLDAP & phpLDAPadmin
Le fichier `docker-compose.yml` définit deux conteneurs :
* **openldap** (ports 389/636) avec la base `dc=universite,dc=local`
* **phpldapadmin** (ports 8080/8443) pour l'administration web

### Lancement
```bash
docker compose up -d
