# MarketBénin - Plateforme E-Commerce

Site e-commerce multilingue pour la vente de produits et services au Bénin.

## 🚀 Déploiement sur Netlify

### Option 1 : Déploiement via Git (Recommandé)

1. **Créer un compte Netlify**
   - Aller à https://www.netlify.com
   - S'inscrire avec GitHub, GitLab ou Bitbucket

2. **Pousser votre code sur GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial MarketBénin setup"
   git remote add origin https://github.com/votreusername/marketbenin.git
   git branch -M main
   git push -u origin main
   ```

3. **Connecter Netlify à votre repo**
   - Aller à https://app.netlify.com
   - Cliquer "New site from Git"
   - Choisir votre repo
   - Les paramètres sont déjà configurés (netlify.toml)
   - Cliquer "Deploy site"

4. **Votre site est en ligne !**
   - Netlify génère automatiquement une URL (ex: vibrant-lovelace-abc123.netlify.app)
   - Vous pouvez ajouter un domaine personnalisé

### Option 2 : Déploiement manuel (Netlify CLI)

1. **Installer Netlify CLI**
   ```bash
   npm install -g netlify-cli
   ```

2. **Se connecter à Netlify**
   ```bash
   netlify login
   ```

3. **Déployer le site**
   ```bash
   netlify deploy --prod
   ```

### Option 3 : Drag & Drop

1. Aller à https://app.netlify.com
2. Drag & drop le dossier du projet dans la zone de dépôt
3. Votre site est déployé !

## 📋 Structure du Projet

```
ecommerce/
├── index.html          # Site complet (HTML + CSS + JS)
├── netlify.toml        # Configuration Netlify
└── README.md           # Ce fichier
```

## ✨ Fonctionnalités

✅ **Catalogue Multi-Produits**
- Affichage responsive des produits
- Filtrage par catégorie
- Images et descriptions détaillées

✅ **Panier d'Achat**
- Ajout/suppression de produits
- Modification des quantités
- Stockage local (localStorage)
- Calcul automatique des frais

✅ **Paiements Locaux Bénin**
- Chariot (paiement en ligne)
- Mobile Money (MTN/Moov)
- Virement bancaire

✅ **Design Professionnel**
- Interface corporative et minimaliste
- Responsive (mobile, tablette, desktop)
- Accessibilité (WCAG 2.1)
- Animations subtiles et fluides

## 🔧 Personnalisation

### Modifier les produits

Ouvrir `index.html`, chercher la section "DONNÉES PRODUITS" et modifier le tableau `products[]` :

```javascript
{
    id: 7,
    name: "Votre Produit",
    category: "ebooks",  // ou "formation", "services"
    price: 5000,
    description: "Description courte",
    icon: "🎯"  // emoji au choix
}
```

### Modifier les couleurs

Dans le `:root` de la section `<style>` :

```css
:root {
    --color-primary: #1a3a52;      /* Bleu principal */
    --color-accent: #d4af37;       /* Doré accent */
    --color-text: #2c3e50;         /* Texte */
}
```

### Modifier les coordonnées de contact

Chercher la section "CONTACT" et mettre à jour :
- Email: `support@marketbenin.bj`
- WhatsApp: `+229 XX XX XX XX`
- Adresse: `Cotonou, Bénin`

## 📱 Intégrations de Paiement

### Chariot
1. Créer un compte vendeur: https://chariot.bj
2. Obtenir votre clé API
3. Intégrer l'endpoint de paiement dans les Netlify Functions

### Mobile Money
Pour MTN Money et Moov Money, contacter:
- **MTN Bénin**: +229 XX XX XX XX
- **Moov Bénin**: +229 XX XX XX XX

### Virement Bancaire
Ajouter vos coordonnées bancaires:
- Banque
- Numéro de compte
- Nom du titulaire

## 🔒 Sécurité

- ✅ HTTPS automatique (Netlify SSL gratuit)
- ✅ Pas de données sensibles stockées localement
- ✅ Validation des paiements côté serveur (à ajouter)

## 📊 Analytics

Connecter Google Analytics :

1. Créer un compte Google Analytics
2. Obtenir votre ID de tracking
3. Ajouter avant la fermeture du `</head>` :

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

## 💡 Tips

- **SEO**: Modifier le titre et la description dans le `<head>`
- **Domaine personnalisé**: Aller à Settings > Domain management dans Netlify
- **Email**: Configurer un formulaire de contact avec Netlify Forms
- **Blog**: Ajouter des pages supplémentaires en HTML statique

## 🆘 Support & Troubleshooting

**Le site ne charge pas ?**
- Vérifier les fichiers sont bien uploadés
- Vérifier la console (F12 > Console)
- Vérifier que netlify.toml est présent

**Les paiements ne marchent pas ?**
- Intégrer les API officielles des prestataires
- Tester en mode sandbox d'abord
- Vérifier les identifiants API

**Performance lente ?**
- Optimiser les images
- Minifier CSS/JS
- Utiliser le CDN de Netlify (automatique)

## 📈 Prochaines étapes

1. ✅ Intégrer les APIs de paiement réels
2. ✅ Ajouter un backend pour les commandes
3. ✅ Mettre en place un système d'email
4. ✅ Ajouter une page d'administration
5. ✅ Connecter une base de données

## 📝 License

MarketBénin © 2026 - Tous droits réservés

---

**Besoin d'aide ?** Contactez support@marketbenin.bj
