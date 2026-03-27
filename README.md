# tp-ci_cd

## 🚀 Release Process

Ce projet suit un processus de versioning et de release strict pour garantir la traçabilite et la reproductibilite.

### 🔁 Continuous Integration (on push to `main`)

- A chaque push sur `main`, la CI se lance.
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
