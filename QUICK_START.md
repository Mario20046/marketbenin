# ⚡ Démarrage Rapide (10 minutes)

## 📦 Ce que vous avez

```
marketbenin/
├── 📄 index.html              ← Votre site complet
├── 📄 netlify.toml            ← Configuration Netlify
├── 📄 .env.example            ← Variables d'environnement
├── 📁 netlify/
│   └── 📁 functions/
│       ├── payment-chariot.js ← API Chariot
│       ├── payment-momo.js    ← API Mobile Money
│       └── payment-bank.js    ← API Virement bancaire
├── 📄 README.md               ← Documentation complète
└── 📄 DEPLOYMENT_GUIDE.md     ← Guide détaillé déploiement
```

## 🚀 En 3 étapes

### 1️⃣ Créer un compte GitHub (5 min)

```bash
# Si vous n'avez pas GitHub:
1. Aller à https://github.com
2. S'inscrire avec email
3. Vérifier email
```

### 2️⃣ Pousser votre code (3 min)

```bash
# Dans le dossier marketbenin:

git init
git add .
git commit -m "Initial setup"
git remote add origin https://github.com/VOTREUSERNAME/marketbenin.git
git branch -M main
git push -u origin main
```

### 3️⃣ Déployer sur Netlify (2 min)

```bash
1. Aller à https://app.netlify.com
2. Cliquer "New site from Git"
3. Choisir GitHub → marketbenin
4. Cliquer "Deploy site"

✨ Votre site est LIVE !
```

---

## 🎨 Personnaliser en 5 minutes

### Changer le logo/titre

Ouvrir `index.html`, chercher:

```html
<div class="logo">Market<span>Bénin</span></div>
```

Remplacer par:

```html
<div class="logo">Votre<span>Marque</span></div>
```

### Ajouter un produit

Chercher dans `index.html`:

```javascript
const products = [
    {
        id: 1,
        name: "Pack 2000 E-books...",
```

Ajouter avant la dernière `]`:

```javascript
    {
        id: 7,
        name: "Mon Produit",
        category: "ebooks",  // ou "formation", "services"
        price: 5000,
        description: "Description...",
        icon: "🎯"
    }
```

### Changer les couleurs

Chercher dans `<style>`:

```css
:root {
    --color-primary: #1a3a52;    /* Changer bleu */
    --color-accent: #d4af37;     /* Changer or */
```

Puis pousser:

```bash
git add .
git commit -m "Personnalisations"
git push
```

Netlify redéploiera automatiquement !

---

## 💳 Intégrer les paiements

### Chariot (Meilleure option Bénin)

1. Créer compte: https://chariot.bj
2. Obtenir API Key
3. Dans Netlify > Settings > Environment variables
4. Ajouter: `CHARIOT_API_KEY` = votre clé
5. Redéployer

### Mobile Money

MTN / Moov contactez directement.

### Virement bancaire

1. Ouvrir `netlify/functions/payment-bank.js`
2. Remplacer les coordonnées:

```javascript
const bankDetails = {
    bankName: "Votre Banque",
    accountName: "Votre Nom",
    accountNumber: "XX XX XXXXX",
    iban: "BJ62...",
    bicCode: "XXXX"
};
```

3. Pousser le changement

---

## 📊 Voir les stats

### Google Analytics

1. Créer compte: https://analytics.google.com
2. Obtenir ID (ex: G-XXXXXXXXXX)
3. Dans `index.html`, ajouter avant `</head>`:

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### Netlify Analytics

1. Dans Netlify > Settings > Billing
2. Ajouter Netlify Analytics ($10/mois)
3. Voir stats en temps réel

---

## 🔐 Domaine personnalisé

### Avez-vous un domaine ?

Si OUI:
1. Netlify > Settings > Domain management
2. "Add custom domain"
3. Entrer `votresite.bj`
4. Suivre instructions DNS

Si NON:
1. Acheter domaine: https://namecheap.com (ou autre)
2. Puis faire l'étape ci-dessus

---

## ✅ Checklist Final

- [ ] Site visible sur https://votresite.netlify.app
- [ ] Logo personnalisé
- [ ] Produits ajoutés
- [ ] Couleurs changées
- [ ] Paiement testé
- [ ] Email de contact mis à jour
- [ ] Analytics configuré (optional)
- [ ] Domaine personnalisé (optional)

---

## 🆘 Problèmes courants

| Problème | Solution |
|----------|----------|
| "Site ne charge pas" | Vérifier Netlify Deploys pour erreurs |
| "Pas de produits" | Vérifier la section `const products = [` |
| "Paiement ne marche pas" | Vérifier variables d'environnement Netlify |
| "Email ne marche pas" | Ajouter SENDGRID_API_KEY |

---

## 📚 Plus de détails

- **README.md** - Documentation complète
- **DEPLOYMENT_GUIDE.md** - Guide détaillé étape par étape

---

## 🎉 Vous êtes prêt !

Votre site e-commerce est prêt à accueillir vos clients.

**Prochaines étapes:**
1. Personnaliser le design
2. Ajouter vos produits
3. Intégrer paiements réels
4. Lancer une campagne marketing
5. Suivre les ventes

---

**Questions ?** Consultez la documentation ou contactez support@marketbenin.bj
