# Visual Block Editor

## 📋 **Table des Matières**
- [📖 Description](#-description)  
- [🚀 Fonctionnalités](#-fonctionnalités)  
- [🔧 Installation](#-installation)  
- [🛠️ Utilisation](#️-utilisation)  
- [⚙️ Configuration](#-configuration)  
- [🐞 Résolution des Problèmes](#-résolution-des-problèmes)  
- [⚠️ Avertissements Importants](#️-avertissements-importants)  
- [📄 Licence](#-licence)  
- [🙏 Remerciements](#-remerciements)

---

## 📖 **Description**

**Visual Block Editor** est une extension pour un IDE web (type Next.js/React) permettant de **transformer du code source** en **blocs visuels** à la manière de Scratch. L’éditeur offre une **synchronisation bidirectionnelle** : toute modification dans les blocs se répercute dans le code, et inversement.

> **⚠️ Remarque :** Bien qu’il s’inspire du concept de Scratch, cet éditeur est conçu pour un usage **professionnel** et **avancé**, avec prise en charge d’un **éditeur de code intégré** (Monaco Editor ou CodeMirror), d’une **analyse AST** (Babel, TypeScript) et d’une interface **responsive**.

---

## 🚀 **Fonctionnalités**

- **Transformation du Code en Blocs :**  
  Convertit automatiquement un script en une arborescence de blocs interconnectés (fonctions, conditions, boucles, etc.).

- **Édition de Code Directement dans les Blocs :**  
  Chaque bloc peut contenir un éditeur de code avec coloration syntaxique, autocomplétion et numérotation des lignes.

- **Synchronisation Bidirectionnelle :**  
  Toute modification dans la vue bloc se répercute dans le fichier source, et les modifications dans le code sont reflétées côté bloc.

- **Navigation Avancée :**  
  - **Pan & Zoom** : Se déplacer librement dans un espace de travail (quasi) illimité.  
  - **Minimap** (optionnel) : Vue d’ensemble de l’arborescence.  
  - **Recherche/Filtrage** : Trouver rapidement un fichier ou un bloc spécifique.

- **Connexion Visuelle entre Blocs :**  
  Lignes de connexion animées (SVG ou Canvas) indiquant le flux logique. Indicateurs de direction et état actif/inactif.

- **Menu Contextuel :**  
  Clic droit pour **supprimer**, **dupliquer**, **modifier** ou **remplacer** un bloc.  

- **Exportation/Importation :**  
  Possibilité de sauvegarder la configuration de blocs, ou de réimporter un script pour le convertir à nouveau.

- **Interface Moderne et Responsive :**  
  - **Grille d’alignement** avec un thème sombre.  
  - **Transitions fluides** et **indicateurs visuels** pour la sélection, l’édition et la connexion.

---

## 🔧 **Installation**

### **Prérequis**

- **Node.js** (version 14 ou supérieure)  
- **NPM** ou **Yarn**  
- **Next.js** / **React** déjà configurés dans votre projet  
- (Optionnel) **TypeScript** si vous comptez utiliser l’analyse AST TS  

### **Étapes d’Installation**

1. **Cloner ou Ajouter le Module :**
   ```bash
   git clone https://github.com/MonCompte/visual-block-editor.git
   cd visual-block-editor
   ```

2. **Installer les Dépendances :**
   ```bash
   npx next dev
   ```

3. **Intégrer dans votre Projet Next.js/React :**  
   - Copiez les dossiers `components/`, `lib/`, `styles/` (ou tout autre dossier requis) dans votre projet.  
   - Vérifiez que les dépendances (Babel, framer-motion, @radix-ui/react-scroll-area, etc.) sont bien installées dans votre `package.json`.  

4. **Configurer l’AST Parser (si nécessaire) :**  
   - Installez et configurez **Babel** ou **TypeScript** AST pour la conversion code ↔ blocs.  

---

## 🛠️ **Utilisation**

1. **Lancer le Projet :**
   ```bash
   npm run dev
   ```
   ou
   ```bash
   yarn dev
   ```
   Ouvrez ensuite [http://localhost:3000](http://localhost:3000).

2. **Ouvrir l’Éditeur Visuel :**
   - Dans la barre d’outils de votre IDE (ou via un bouton spécifique), cliquez sur **“Visual Block Editor”**.  
   - Une fenêtre (ou modal) s’ouvre, affichant :  
     - **Palette de Blocs** à gauche (catégories : Variables, Fonctions, Loops, etc.).  
     - **Espace de Travail** central infini.  
     - **Propriétés/Code** à droite (ou en bas, selon la configuration).

3. **Importer un Fichier de Code :**
   - Choisissez un fichier de votre **explorateur de projet** (scrollable).  
   - Cliquez sur **“Importer”** pour analyser le code et générer les blocs correspondants.  

4. **Manipuler les Blocs :**
   - **Glisser-déposer** les blocs pour les réorganiser.  
   - **Relier** les blocs via des points de connexion (ligne en courbe).  
   - **Clic droit** sur un bloc pour le **modifier**, **dupliquer** ou **supprimer**.  
   - **Double-clic** (ou un bouton dédié) pour **éditer** le code interne du bloc (Monaco Editor intégré).  

5. **Synchronisation avec le Code Source :**
   - Les modifications dans l’éditeur de blocs s’appliquent **instantanément** à votre fichier (vous pouvez l’observer dans l’éditeur textuel).  
   - Si vous modifiez le fichier textuel, les blocs se mettent à jour (autant que possible) en temps réel.

6. **Zoom et Navigation :**
   - **Molette + Ctrl/Cmd** ou des boutons de zoom pour agrandir/réduire l’espace de travail.  
   - Cliquer + glisser sur un fond vide (ou maintenir Espace) pour **pan**/déplacer la vue.  
![image](https://github.com/user-attachments/assets/e473e172-05d8-4c4a-bfa8-c84c8c65d0ba)
![image](https://github.com/user-attachments/assets/8dd753e6-a0b6-4477-a3c5-aec720e984aa)

---

## ⚙️ **Configuration**

### **Paramètres de l’AST Parser**
- Configurez `lib/utils/ast.ts` pour choisir le langage (JS/TS) et les règles de parsing.  
- Personnalisez la façon dont sont détectées les fonctions, variables, boucles, etc.

### **Palette de Blocs Personnalisés**
- Modifiez `components/editor/blocks/block-templates.ts` (ou équivalent) pour ajouter vos propres blocs.  
- Spécifiez les propriétés par défaut, l’icône, la catégorie, etc.

### **Stockage des Blocs**
- Le **block-store** (ou tout autre store Redux/MobX/Context) peut enregistrer l’état des blocs.  
- Vous pouvez aussi **sauvegarder** la configuration dans un fichier JSON ou en base de données.

### **Style et Thème**
- Utilisez **Tailwind CSS**, **Chakra UI** ou votre librairie préférée pour personnaliser la charte graphique.  
- Ajustez les classes ou variables CSS pour correspondre au **thème sombre** de votre IDE.

---

## 🐞 **Résolution des Problèmes**

1. **Mismatch SSR/Hydratation :**  
   - Si vous voyez un warning “Prop `className` did not match...”, assurez-vous que les classes conditionnelles sont **identiques** côté serveur et client.  
   - Évitez `Date.now()` ou `Math.random()` dans le rendu SSR.

2. **Erreur `Cannot read properties of undefined` :**  
   - Vérifiez que la fonction (ou la variable) est bien détectée par l’AST.  
   - Assurez-vous que votre code source contient bien le pattern pris en charge (ex. : `function maFonction() {...}`).

3. **Performance Lente avec de Gros Scripts :**  
   - Évitez d’importer des fichiers massifs (des milliers de lignes) d’un seul coup.  
   - Optimisez le parsing (pré-filtrage, chunking).

4. **Problèmes de Zoom ou de Déplacement :**  
   - Vérifiez que les **events** (wheel, pointerdown) ne sont pas bloqués par d’autres composants.  
   - Ajustez les limites de zoom si nécessaire.

5. **Blocs Ne Se Synchronisent Pas avec le Code Textuel :**  
   - Assurez-vous d’avoir activé la logique de mise à jour bidirectionnelle dans le store (ou le hook `use-block-editor`).  
   - Vérifiez que votre code source n’a pas de **caractéristiques hors-scope** pour le parseur (ex. : macros, préprocesseurs complexes).

---

## ⚠️ **Avertissements Importants**

- **Compatibilité Langage :**  
  - Le **Babel** parser ou TypeScript AST peut ne pas gérer toutes les syntaxes (versions très récentes, décorateurs spéciaux, etc.).  
  - Assurez-vous de tester avec les syntaxes supportées.

- **Synchronisation Incomplète :**  
  - Certains changements majeurs dans le code textuel (refactoring massif) peuvent rendre la synchronisation *partielle*.  
  - Dans de rares cas, vous devrez recharger ou réimporter le fichier pour regénérer correctement les blocs.

- **Dépendances Externes :**  
  - L’éditeur nécessite plusieurs bibliothèques (Babel, framer-motion, Radix-UI, etc.).  
  - Vérifiez régulièrement les mises à jour pour maintenir la compatibilité.

---

## 📄 **Licence**

Ce projet est distribué sous licence **MIT**. Consultez le fichier [`LICENSE`](./LICENSE) (ou le lien dans votre dépôt) pour plus de détails.

---

## 🙏 **Remerciements**

- **[React](https://reactjs.org/)** et **[Next.js](https://nextjs.org/)** : pour la base du framework web.  
- **[Monaco Editor](https://microsoft.github.io/monaco-editor/)** : pour l’éditeur de code avancé intégré.  
- **[Babel](https://babeljs.io/)** et/ou **[TypeScript](https://www.typescriptlang.org/)** : pour l’AST et l’analyse du code.  
- **[Framer Motion](https://www.framer.com/motion/)** : pour les animations fluides des blocs et connexions.  
- **[Radix UI](https://www.radix-ui.com/)** : pour les composants d’interface bas niveau (ScrollArea, etc.).  
- **[Tailwind CSS](https://tailwindcss.com/)** : pour la rapidité de stylisation, surtout en thème sombre.

---

**Bon développement avec votre Visual Block Editor !** N’hésitez pas à contribuer ou à signaler les bugs via des **Issues** ou **Pull Requests** dans le dépôt GitHub.
