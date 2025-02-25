# TP git Worflow

## 1. Objectifs pédagogiques

- **Maîtrise approfondie de Git :** Utiliser et comprendre les commandes de base et avancées (commit, branch, merge, rebase, etc.).
- **Gestion fine des fichiers et versions :** Savoir configurer et utiliser le fichier `.gitignore` et les tags pour marquer des versions stables.
- **Workflow collaboratif sur GitHub :** Organiser le travail en équipe, utiliser les pull requests, gérer les issues et documenter les processus.
- **Intégration avec Docker :** Appréhender la gestion d’un projet Docker en parallèle de la gestion Git.

---

## 2. Contexte et motivation

Le dépôt `docker_tp` correspond à un projet Docker qui peut déployer une application containerisée. L'enjeu est double :  
- D'une part, comprendre comment gérer le code avec Git et GitHub en exploitant des fonctionnalités avancées.  
- D'autre part, apprendre à travailler sur un projet Docker en gérant la configuration (Dockerfileà et en automatisant des tâches via des scripts et l'intégration continue avec github action (préalablement fourni).   

Ce TP vous permettra de consolider vos compétences en gestion de versions et en déploiement containerisé tout en vous habituant aux pratiques de collaboration sur GitHub.

---

## 3. Énoncé du problème

Vous devez travailler sur le dépôt existant `docker_tp` qui contient déjà une base de projet Docker. Vous devez le clonner en local et l'association à un nouveau répo distant.
Votre mission consiste à améliorer la gestion du code et l'organisation du projet en :

- Configurant un fichier `.gitignore` optimisé,
- Utilisant des branches pour développer et intégrer de nouvelles fonctionnalités,
- Marquant des versions stables avec des tags Git,
- Exploitant des commandes avancées (rebase, cherry-pick) et en explorant d'autres outils Git pour la collaboration,
- Et en intégrant/ou automatisant des processus liés à Docker avec github action

---

## 4. Tâches à réaliser

#### **Tâche 1 : Préparation de l'environnement et vérification du dépôt**
- **Clonage et configuration :**
  - Clonez le dépôt `docker_tp` depuis GitHub sur votre machine.
  - Vérifiez la configuration de Git avec `git config --list` et ajustez le nom et l'email si nécessaire.
---

#### **Tâche 2 : Configuration avancée du fichier `.gitignore`**
- **Création et ajustement du `.gitignore` :**
  - Ajoutez des fichiers et dossiers spécifiques à Docker comme les logs, caches, dossiers de build ou les fichiers temporaires générés par Docker (ex. : `*.log`, `tmp/`, `build/`, etc.).
  - Vérifiez que ces fichiers ne sont pas suivis par Git à l’aide de `git status` après modification.
- **Exemple d’entrées à inclure :**
  - Fichiers de build (ex. : `/build/`)
  - Fichiers temporaires (ex. : `*.tmp`)
  - Fichiers de logs (ex. : `*.log`)
---

#### **Tâche 3 : Mise en place d'un workflow de développement collaboratif**
- **Création de branches thématiques :**
  - Créez des branches spécifiques pour chaque nouvelle fonctionnalité ou correction, par exemple :
    - `feature/nouvau-graph`
    - `feature/new-model`
    - `bugfix/correction-config`
    
- **Développement sur ces branches :**
  - Sur chaque branche, effectuez des commits réguliers décrivant clairement vos modifications.
	  - Chque message de commit doit commencer par : "feat:", "fix:", "perf", "BREAKING CHANGE:" en fonction de la modification apportée
  - Chaque étudiant ou groupe doit implémenter une fonctionnalité ou corriger un bug en utilisant sa branche dédiée.
- **Pull Requests et Fusion :**
  - Une fois une fonctionnalité achevée, ouvrez une pull request pour l'intégrer à la branche principale.
  - Commenter et revoir le code des pull requests de vos coéquipiers, en résolvant les conflits éventuels lors du merge.

---

#### **Tâche 4 : Utilisation et gestion des tags Git**
- **Création de tags pour marquer les versions :**
  - Lorsqu'une version stable est atteinte (par exemple, après l'intégration d'une fonctionnalité majeure ou la finalisation d'une itération), créez un tag annoté avec une commande telle que :
    ```
    git tag -a v1.0.0 -m "Version 1.0.0 - Première release stable avec Dockerfile fonctionnel"
    ```
  - Poussez ensuite le tag sur GitHub :
    ```
    git push origin --tags
    ```
- **Vérification et listing :**
  - Utilisez `git tag -l` pour lister tous les tags et documentez dans le README quelle version correspond à quelles fonctionnalités.

- **Récupérez l'image docker:**
    - Récuprérer l'image builder deupuis github et executer la en local
---

#### **Tâche 5 : Expérimentation avec des commandes Git avancées**
- **Rebase interactif :**
  - Sur une branche de fonctionnalité, utilisez `git rebase -i` pour revoir et réorganiser vos commits (fusionner certains commits, modifier les messages, etc.).  
  - Expliquez dans un document annexe (par exemple, `ADVANCED.md`) quels bénéfices cet exercice apporte à l’historique du projet.
- **Commande cherry-pick :**
  - Identifiez dans l’historique un commit sur une branche qui apporte une correction ou une fonctionnalité utile.
  - Appliquez ce commit sur une autre branche en utilisant `git cherry-pick <commit_hash>`.
  - Décrivez la situation qui a motivé l’utilisation de cherry-pick et son impact sur le suivi de version.
- **Exploration d’autres commandes utiles :**
  - Utilisez `git stash` pour stocker temporairement des modifications non validées, puis réappliquez-les.
  - Testez `git log --graph --all` pour visualiser l’historique des branches et comprendre la topologie du projet.
  - Faites la même chose avec l'extension git graph de vscoduim


#### **Tâche 8 : Documentation et suivi du projet sur GitHub**
- **Utilisation des Issues et du Project Board :**
  - Créez plusieurs issues sur GitHub pour les tâches à réaliser
  - Organisez ces tâches dans un Project Board pour suivre l’avancement du projet.

---

### 5. Questions théoriques supplémentaires

1. **Quels sont les avantages et les risques d'utiliser `git rebase` par rapport à `git merge` dans un contexte collaboratif ?**  
   Expliquez les situations où l'un serait préféré à l'autre et comment minimiser les risques liés à un rebase mal utilisé.

2. **Comment les sous-modules Git peuvent-ils améliorer la réutilisabilité du code, et quelles sont les bonnes pratiques pour les maintenir ?**  
   Discutez de la gestion de versions entre projet parent et sous-module ainsi que des éventuels pièges à éviter.

3. **Décrivez l'impact d'une mauvaise configuration du fichier `.gitignore` sur l'historique du projet.**  
   Quelles conséquences peut-on observer et comment rectifier la situation une fois le problème identifié ?

---

### 6. Évaluation

Les critères d'évaluation de ce TP seront :

- **Qualité de la configuration et des pratiques Git :**
  - Exactitude et pertinence du fichier `.gitignore`.
  - Utilisation judicieuse des branches et des tags.
  - Efficacité de l'utilisation des commandes avancées (rebase, cherry-pick, etc.).

- **Documentation et communication :**
  - Clarté du `README.md` et de la documentation associée (`ADVANCED.md`, `ENV.md`).
  - Bonne gestion et suivi du projet via les Issues et le Project Board sur GitHub.

- **Collaboration et résolution de conflits :**
  - Qualité des échanges via les pull requests.
  - Capacité à résoudre les conflits et à documenter les processus via les commits.

- **Réponses aux questions théoriques :**
  - Pertinence, clarté et profondeur des explications fournies.

---

### 7. Extensions (facultatif)

- **Mise en place d'une intégration continue CI :**
  - Configurez GitHub Actions ou un autre outil CI pour automatiser le build (inspirez vous de celui qui existe déjà sur le repo docker_tp)
