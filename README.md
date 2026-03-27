# tp-ci_cd

## 🚀 Release Process

Ce projet suit un processus de versioning et de release strict pour garantir la traçabilite et la reproductibilite.

### 🔁 Continuous Integration (on push to `main`)

- A chaque push sur `main`, la CI se lance.
- Les pull requests doivent passer les tests avant d etre mergees (PR gate).
- Les tests sont executes.
- Si tout passe, l'image Docker est construite et poussee avec deux tags : `latest` et le SHA du commit.

### 🏷 Creating a Release (Versioned Product)

- On cree un tag Git de version (ex : `v1.0.0`).
- Le workflow de release construit et pousse l'image Docker avec ce tag.
- La version publiee correspond exactement au code tagge.

### 📌 Versioning Rules

- On utilise le format `vX.Y.Z` (Semantic Versioning).
- Une version taggée ne doit jamais être reconstruite.
- `latest` n'est pas une version : c'est un pointeur mouvant.

### 🔎 Traceability

- Chaque image est liee a un commit (tag SHA).
- Les releases sont liees a des tags Git versionnes.
- Les logs CI et l'historique Git garantissent l'origine de chaque build.


## Documentation

### Notice d'installation

- Cloner le depot.
- Installer les dependances du service API : `cd api` puis `npm ci`.
- Lancer les tests : `npm test`.

### Description du pipeline (CI et PR)

- CI sur `main` : a chaque push, les tests sont executes. Si tout passe, l image Docker est build et push avec `latest` et le SHA du commit.
- PR gate : sur chaque pull request, les tests sont executes. La PR ne peut etre mergee que si la CI est verte.
- Separation des roles : la CI de PR ne build ni ne pousse d image, elle valide uniquement la qualite.

### Processus de release

- Creer un tag Git de version (ex : `v1.0.0`).
- Le workflow de release build l image et la pousse avec le tag de version.
- La version publiee correspond exactement au commit tagge.

### Utilisation des tags

- `latest` : pointeur mouvant vers la derniere image stable, pas une version.
- `sha` : identifie un commit precis, utile pour la tracabilite.
- `vX.Y.Z` : version immuable, ne doit jamais etre reconstruite.



## Questions écrites

* Pourquoi `latest` n’est pas une version ?
Réponse :
Latest n'est pas une version car ça nous permet pas de déterminer quel version du code exact nous éxécutons.

* Différence tag vs digest ?
Réponse :
Le tag est un alias défini par l'humain qui pointe vers une image. Le digest est un identifiant générer et immuable qui pointe vers un contenu exact.

* Pourquoi séparer staging/prod ?
Réponse :
C'est par principe d'organisation, il faut toujours distinguer la production qui est accessible aux utilisateurs finaux et la préprod qui celle ci représente l'étape de "test" avant de livré l'application.

* Pourquoi une version `vX.Y.Z` ne doit jamais être reconstruite ?

Réponse :
Car on ne respecte pas le principe d'immuabilité.

* Citez les avantages d'une PR gate.
Qualité, car on tests obligatoirement avant d'intégrer le code, on évite la régréssion.

* Qu’est-ce qui garantit la traçabilité ici ?
La traçabilité est maintenu grâce à l'utilisation des tags tel que les versions ou sha.