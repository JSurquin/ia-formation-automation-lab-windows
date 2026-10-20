# Lab n8n — Windows (formation assistants IA)

Script PowerShell **autonome** pour le module 7 : lancer **n8n** en local avec Docker (ou Podman), installer **cloudflared** pour un tunnel webhook, et ouvrir les liens **Make** / **Zapier**.

## Prérequis

- Windows 10 ou 11 (64 bits)
- Connexion Internet
- Compte utilisateur avec droits d’installation (winget / WSL si besoin)

## Installation en une ligne

Ouvrez **PowerShell** (pas obligatoire « administrateur » au premier essai) :

```powershell
irm https://raw.githubusercontent.com/JSurquin/ia-formation-automation-lab-windows/main/setup-automation-lab.ps1 | iex
```

## Depuis un clone

```powershell
.\setup-automation-lab.ps1
```

## Options

| Option | Effet |
|--------|--------|
| `-NoBrowser` | N’ouvre pas make.com / zapier.com |
| `-SkipN8n` | Liens cloud uniquement (pas de conteneur) |
| `-SkipCloudflared` | N’installe pas cloudflared |
| `-Help` | Aide |

## Après le script

- **n8n** : [http://127.0.0.1:5678](http://127.0.0.1:5678) — créez un compte admin à la première visite.
- **Tunnel temporaire** (webhooks depuis Internet) :

```powershell
cloudflared tunnel --url http://127.0.0.1:5678
```

Copiez l’URL `https://….trycloudflare.com` affichée dans le terminal.

## Dépannage

1. **Docker ne démarre pas** : ouvrez Docker Desktop, attendez l’icône stable, relancez le script (il est relançable).
2. **Redémarrage demandé** : après WSL / Docker, redémarrez Windows puis relancez la même commande `irm … | iex`.
3. **winget introuvable** : installez « App Installer » depuis le Microsoft Store.

## Formation complète

Slides et exercices : dépôt [ia-formation](https://github.com/JSurquin/ia-formation).

Scripts curl Linux/macOS : dépôt [ia-formation-scripts](https://github.com/JSurquin/ia-formation-scripts).
