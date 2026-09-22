# 🚀 Guide Complet de Déploiement - MarketBénin

## Phase 1: Préparation Local (5 minutes)

### Étape 1: Cloner/Préparer le dossier

```bash
# Créer un dossier
mkdir marketbenin
cd marketbenin

# OU cloner depuis Git (si vous avez un repo)
git clone https://github.com/votreusername/marketbenin.git
cd marketbenin
```

### Étape 2: Initialiser Git

```bash
git init
git add .
git commit -m "Initial MarketBénin E-commerce Setup"
```

---

## Phase 2: Créer un compte Netlify (5 minutes)

### 1. S'inscrire sur Netlify

- Aller à: **https://www.netlify.com**
- Cliquer "Sign Up"
- Choisir "Sign up with GitHub" (plus facile)
  - Si vous n'avez pas GitHub, créer un compte d'abord: https://github.com

### 2. Autoriser Netlify

- Cliquer "Authorize Netlify by Netlify"
- Vérifier votre email
- Vous êtes prêt !

---

## Phase 3: Pousser le code sur GitHub (10 minutes)

### 1. Créer un repo GitHub

- Aller à: **https://github.com/new**
- Repository name: `marketbenin`
- Description: "Platform E-commerce pour le Bénin"
- Choisir "Public" ou "Private"
- Cliquer "Create repository"

### 2. Pousser votre code

```bash
# Se positionner dans votre dossier
cd marketbenin

# Ajouter le remote GitHub
git remote add origin https://github.com/votreusername/marketbenin.git

# Renommer la branche si nécessaire
git branch -M main

# Pousser le code
git push -u origin main
```

---

## Phase 4: Déployer sur Netlify (3 minutes)

### 1. Connecter votre repo

- Aller à: **https://app.netlify.com**
- Cliquer "New site from Git"
- Choisir GitHub
- Autoriser si demandé
- Chercher "marketbenin"
- Cliquer dessus

### 2. Configuration de build

Les paramètres sont automatiquement détectés depuis `netlify.toml` :

- **Build command:** (vide - site statique)
- **Publish directory:** `.` (racine)
- Cliquer "Deploy site"

### 3. Votre site est EN LIGNE ! 🎉

Netlify génère une URL temporaire :
`https://vibrant-lovelace-abc123.netlify.app`

---

## Phase 5: Configuration des Variables d'Environnement

Ces variables sont nécessaires pour les paiements et emails.

### 1. Aller aux paramètres du site

- Cliquer sur votre site dans Netlify
- Aller à **Settings** > **Environment variables**

### 2. Ajouter les variables

Cliquer "Add a variable" pour chaque ligne :

| Clé | Valeur | Notes |
|-----|--------|-------|
| `CHARIOT_API_KEY` | `sk_test_xxxxx` | De votre compte Chariot |
| `MTN_API_KEY` | `api_key_xxxxx` | De MTN Money |
| `MOOV_API_KEY` | `api_key_xxxxx` | De Moov Money |
| `SENDGRID_API_KEY` | `SG.xxxxx` | Pour les emails |
| `BANK_ACCOUNT_NUMBER` | `XX XX XXXXX` | Vos coordonnées |
| `BANK_IBAN` | `BJ62 XXXX...` | Votre IBAN |

Pour les tests, vous pouvez laisser les clés API vides provisoirement.

### 3. Redéployer

- Cliquer "Redeploy site" pour appliquer les changements

---

## Phase 6: Configurer un Domaine Personnalisé (Optional)

### 1. Connecter votre domaine

- Dans Netlify > **Settings** > **Domain management**
- Cliquer "Add custom domain"
- Entrer votre domaine: `marketbenin.bj`

### 2. Configurer les DNS

Selon votre registrar (OVH, Namecheap, etc.):

- Ajouter les DNS records que Netlify suggère
- Attendre 24h pour la propagation

### 3. HTTPS automatique

Netlify génère un certificat SSL gratuit (Let's Encrypt) automatiquement.

---

## Phase 7: Configurer les Paiements

### Option A: Chariot (Recommandé pour Bénin)

1. Créer un compte: https://chariot.bj
2. Obtenir votre API Key
3. Ajouter aux variables d'environnement Netlify
4. Intégrer l'endpoint dans la fonction `payment-chariot.js`

### Option B: Mobile Money (MTN/Moov)

**MTN Money:**
- Contact: +229 21 14 14 14
- Obtenir les APIs de paiement
- Documenter : https://mtn.bj

**Moov Money:**
- Contact: +229 40 14 14 14
- Obtenir les APIs de paiement
- Documenter : https://moov.bj

### Option C: Stripe/PayPal

Si vous voulez accepter les paiements internationaux :

1. Créer un compte Stripe: https://stripe.com
2. Activer le support XOF (Franc CFA)
3. Intégrer dans le checkout

---

## Phase 8: Configuration Email (Important!)

### Utiliser SendGrid (Gratuit)

1. Créer un compte: https://sendgrid.com
2. Vérifier votre domaine
3. Obtenir votre API Key
4. Ajouter dans Netlify Environment Variables
5. Les clients recevront des confirmations par email

**Alternative:** Mailgun, Brevo (anciennement Sendinblue)

---

## 🔍 Vérifier que tout fonctionne

### Checklist:

- ✅ Le site charge: `https://votresite.netlify.app`
- ✅ Le menu fonctionne
- ✅ Ajouter un produit au panier
- ✅ Le panier s'ouvre
- ✅ Les filtres marchent
- ✅ Responsive sur mobile (F12)

### Tester les paiements:

1. Ajouter des produits au panier
2. Cliquer "Procéder au paiement"
3. Choisir un mode de paiement
4. Les APIs simulation doivent retourner une réponse

---

## 📊 Monitoring & Analytics

### 1. Ajouter Google Analytics

```html
<!-- Ajouter avant </head> dans index.html -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G_YOUR_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G_YOUR_ID');
</script>
```

### 2. Netlify Analytics (Payant)

- Settings > Analytics
- Activer Netlify Analytics
- Voir stats de trafic

### 3. Logs des Functions

- Dans Netlify > Functions
- Voir les logs d'exécution
- Déboguer les erreurs

---

## 🔄 Mise à Jour du Site

### Après des changements locaux:

```bash
# Modifier un fichier (ex: ajouter un produit)
# Puis:

git add .
git commit -m "Ajouter nouveaux produits"
git push origin main

# Netlify redéploiera automatiquement! ✨
```

Pas besoin de toucher à Netlify, tout est automatisé.

---

## 🆘 Troubleshooting

### "Le site ne charge pas"

- Vérifier: https://app.netlify.app > Deploys
- Chercher les erreurs rouges
- Vérifier que tous les fichiers sont versionnés

### "Les fonctions ne marchent pas"

- Vérifier les logs: **Functions** > **Logs**
- Les fichiers sont dans `netlify/functions/` ?
- Les variables d'environnement sont définies ?

### "Les paiements ne passent"

- Vérifier l'API Key dans les variables d'environnement
- Tester en sandbox d'abord
- Vérifier les logs de la fonction

### "L'email de confirmation n'arrive pas"

- SendGrid API Key est correct ?
- Votre email est vérifié dans SendGrid ?
- Vérifier le spam

---

## 📱 Tester sur Mobile

```bash
# Votre site Netlify est directement accessible sur mobile
# Depuis le mobile, ouvrir:
https://votresite.netlify.app

# OU utiliser Netlify CLI pour tester localement:
netlify dev
# Puis ouvrir http://localhost:8888 sur mobile connecté au même réseau
```

---

## 💡 Tips Importants

1. **Sauvegarde**: Toujours committer les changements importants
2. **Testing**: Tester les paiements en sandbox avant la prod
3. **Sécurité**: Ne JAMAIS committer les clés API réelles (utiliser les variables d'environnement)
4. **Performance**: Utiliser le CDN de Netlify (automatique)
5. **Backup**: GitHub est votre sauvegarde

---

## 📞 Support

Si vous avez des problèmes:

1. **Netlify Support**: https://support.netlify.com
2. **GitHub Issues**: Créer un issue sur votre repo
3. **Chariot Support**: https://chariot.bj/support
4. **Votre Email**: support@marketbenin.bj

---

## 🎉 Prochaines étapes

1. ✅ Configurer les vraies APIs de paiement
2. ✅ Ajouter des vrais produits/descriptions
3. ✅ Mettre à jour les couleurs/logo
4. ✅ Connecter Google Analytics
5. ✅ Configurer un domaine personnalisé
6. ✅ Lancer une campagne marketing !

---

**Déploiement réussi ! Votre site e-commerce est en ligne ! 🚀**
