# Atelier de faire-part — Invitations de mariage

Site statique (un seul fichier `index.html`, aucun serveur, aucune base de
données) pour générer des invitations de mariage personnalisées.

- **Espace comité** (protégé par un code) : renseigner les infos du mariage
  et récupérer le lien à partager.
- **Espace invité** (sans code) : l'invité tape juste son prénom et son nom,
  puis télécharge sa carte en **PDF** ou en **image (PNG)**.

Aucune information n'est stockée sur un serveur : tout est encodé
directement dans le lien envoyé aux invités.

---

## 1. Avant de déployer : changez le code d'accès du comité

Ouvrez `index.html`, cherchez cette ligne (vers le début de la balise
`<script>`) :

```js
var COMMITTEE_ACCESS_CODE = "MARIAGE2026";
```

Remplacez `"MARIAGE2026"` par le code de votre choix, puis enregistrez le
fichier. Partagez ce code uniquement avec les membres du comité
d'organisation — ce n'est pas un vrai système de compte sécurisé, juste une
protection légère contre la curiosité.

## 2. Mettre le projet sur GitHub

Si vous n'avez pas encore de dépôt :

```bash
cd wedding-invites
git init
git add .
git commit -m "Site d'invitations de mariage"
```

Puis, sur [github.com](https://github.com), créez un nouveau dépôt vide
(sans README ni .gitignore, puisque vous en avez déjà), et suivez les
instructions affichées pour le lier et pousser votre code, du style :

```bash
git remote add origin https://github.com/VOTRE-COMPTE/wedding-invites.git
git branch -M main
git push -u origin main
```

## 3. Déployer sur Vercel

1. Allez sur [vercel.com](https://vercel.com) et connectez-vous avec votre
   compte GitHub.
2. Cliquez sur **Add New → Project**.
3. Sélectionnez le dépôt `wedding-invites` que vous venez de pousser.
4. Vercel détecte un projet statique : laissez les réglages par défaut
   (aucune commande de build n'est nécessaire, il n'y a qu'un fichier HTML).
5. Cliquez sur **Deploy**.

Après quelques secondes, Vercel vous donne une URL du type
`https://wedding-invites-xxxx.vercel.app`. C'est votre site en ligne.

## 4. Utilisation

1. Ouvrez l'URL Vercel dans votre navigateur → l'écran de code d'accès
   s'affiche.
2. Entrez le code que vous avez défini à l'étape 1 → le formulaire du
   comité apparaît.
3. Remplissez les informations du mariage, cliquez sur **"Mettre à jour
   l'aperçu et le lien"**.
4. Copiez le lien affiché dans l'encart "Lien à partager avec vos
   invités" et envoyez-le à vos invités (SMS, WhatsApp, e-mail...).
5. Chaque invité qui ouvre ce lien arrive directement sur l'espace invité
   (sans jamais voir l'écran de code), tape son prénom et son nom, puis
   télécharge sa carte en PDF ou en image.

### Important : si vous modifiez les informations plus tard

Le lien contient toutes les informations du mariage. Si vous changez la
date, le lieu ou tout autre détail après avoir déjà envoyé le lien, un
**nouveau lien est généré** — pensez à le renvoyer à vos invités, sinon
certains garderont l'ancienne version.

## Fichiers du projet

```
wedding-invites/
├── index.html   → le site complet (HTML + CSS + JS, tout-en-un)
└── README.md    → ce guide
```

Aucune dépendance à installer, aucun `package.json` nécessaire : Vercel
sert `index.html` tel quel.
