# RepoCoach

**Comprendre un dépôt de code, tout en réapprenant à coder par soi-même.**

RepoCoach est un projet personnel à vocation open source : un assistant qui permet d’explorer des fichiers de code et de poser des questions sur leur fonctionnement. Les réponses s’appuieront sur les fichiers importés et présenteront les extraits utilisés comme sources.

Le projet est en cours de construction. Ce README présente sa direction et ses objectifs, sans supposer que les fonctionnalités sont déjà disponibles.

## Pourquoi ce projet ?

Après avoir beaucoup utilisé les assistants de programmation, j’ai ressenti le besoin de retrouver mes réflexes et mon autonomie.

Avec RepoCoach, je veux reprendre le développement d’une application de A à Z : réfléchir au problème, écrire le code, comprendre les erreurs, construire une API, gérer des données, sécuriser les accès et déployer le résultat.

Mon objectif est de pouvoir expliquer chaque partie de l’application, les choix réalisés et les limites rencontrées.

## Engagement : zéro code généré par intelligence artificielle

**Tout le code applicatif que j’ajoute au projet doit être écrit manuellement, sans génération par intelligence artificielle.**

Cette règle concerne également les tests, les scripts et la configuration que je rédige pour le projet.

Je m’engage à :

- Désactiver les suggestions de code générées par IA.
- Ne pas copier de solutions produites par un assistant IA.
- Ne pas déléguer l’implémentation, la correction ou la refactorisation à un agent.
- Comprendre les modifications avant de les intégrer.
- Documenter mes difficultés et les solutions trouvées.

La documentation officielle, les recherches, les ressources pédagogiques, les outils de débogage et les échanges avec d’autres développeurs restent autorisés.

Les dépendances et les fichiers de démarrage produits par des outils classiques, comme un générateur de projet ou un outil de migration, restent autorisés. Leur rôle doit être compris.

**Transparence :** une IA peut m’aider à organiser le parcours d’apprentissage, expliquer un concept ou fournir un indice sans écrire la solution. Ce README a été rédigé avec son assistance. L’engagement de zéro code généré concerne le code du projet.

## Une application d’IA développée manuellement

RepoCoach utilisera des modèles d’IA comme fonctionnalité du produit.

Leur rôle sera de répondre aux questions des utilisateurs à partir des documents fournis. Le code qui prépare ces documents, recherche les passages, appelle les modèles et affiche les résultats sera écrit manuellement.

## Fonctionnement prévu

1. L’utilisateur se connecte et crée un espace.
2. Il importe un petit ensemble de fichiers texte ou de code.
3. Le serveur découpe les fichiers en passages et conserve leurs références.
4. Ces passages sont indexés pour permettre une recherche sémantique.
5. L’utilisateur pose une question.
6. Le serveur retrouve les extraits pertinents et les fournit au modèle.
7. L’application affiche une réponse accompagnée de références vérifiables.

Exemples de questions :

- « À quoi sert ce projet ? »
- « Où est gérée la connexion ? »
- « Quels fichiers dois-je lire pour comprendre cette fonctionnalité ? »

Lorsque les documents ne contiennent pas assez d’informations, l’assistant devra le signaler.

## Un périmètre volontairement petit

La première version vise :

- Un maximum de vingt petits fichiers texte par espace.
- Une liste de fichiers et un lecteur de contenu.
- Une recherche dans les documents.
- Des questions et réponses avec références aux fichiers et aux lignes.
- Une progression d’indexation visible.
- Un historique simple des échanges.

L’import automatique depuis GitHub, l’exécution de code, les modifications automatiques et les agents autonomes restent hors du périmètre initial.

## Stack technique prévue

| Partie | Technologie |
|---|---|
| Environnement de développement | macOS, VS Code et Terminal |
| Interface | React, TypeScript et Vite |
| Mise en forme | CSS classique au départ |
| API | C# et ASP.NET Core |
| Comptes | ASP.NET Core Identity |
| Base de données | PostgreSQL |
| Accès aux données | Entity Framework Core |
| Recherche vectorielle | pgvector |
| Génération et embeddings | API d’un fournisseur à sélectionner |
| Événements en temps réel | SignalR |
| Serveur MCP | C# et SDK MCP |
| Tests du serveur | xUnit |
| Versionnement | Git et GitHub |
| Intégration et déploiement continus | GitHub Actions |
| Conteneurisation | Docker |

Les choix pourront évoluer. Les changements significatifs seront documentés avec leur justification.

## Concepts étudiés

### Développement full stack

Construire une interface, concevoir une API, valider les entrées, gérer les erreurs et faire communiquer le navigateur, le serveur et la base de données.

### Programmation asynchrone

Comprendre les promesses, `async/await`, les appels réseau, l’annulation et le traitement en arrière-plan. Distinguer les opérations asynchrones des problèmes de concurrence.

### RAG

Construire progressivement une chaîne de recherche et de génération : découpage, embeddings, recherche des passages, préparation du contexte et références aux sources.

### MCP

Exposer des capacités limitées à un client compatible :

- Lister les documents autorisés.
- Rechercher des passages.
- Lire un extrait précis.

Le serveur MCP réutilisera la logique de l’application et ses contrôles d’accès.

### SignalR

Transmettre la progression de l’indexation et comprendre les connexions, les groupes, les événements et la reconnexion.

### Sécurité et protection des données

Comprendre l’authentification, l’autorisation, l’isolation des espaces, la gestion des secrets et la suppression des données.

### Livraison

Apprendre à tester, construire, configurer et déployer l’application, puis automatiser les étapes comprises.

## Roadmap

- [ ] Préparer l’environnement sur Mac et initialiser Git.
- [ ] Construire un explorateur de fichiers fictifs en React.
- [ ] Créer une API permettant d’importer et de lire un fichier.
- [ ] Ajouter PostgreSQL et les migrations.
- [ ] Ajouter les comptes et les contrôles d’accès.
- [ ] Construire une recherche textuelle simple.
- [ ] Découper les documents en passages avec leurs références.
- [ ] Ajouter les embeddings et la recherche vectorielle.
- [ ] Générer des réponses avec les extraits retrouvés.
- [ ] Afficher la progression avec SignalR.
- [ ] Exposer les outils du serveur MCP.
- [ ] Évaluer la recherche et la qualité des références.
- [ ] Ajouter les tests et l’intégration continue.
- [ ] Déployer une première version de démonstration.
- [ ] Automatiser le déploiement.

## Protection des données

Le développement commencera avec des fichiers fictifs ou publics, sans informations confidentielles.

Les objectifs sont de :

- Vérifier les permissions avant chaque accès aux documents.
- Limiter les types, tailles et nombres de fichiers.
- Garder les clés API côté serveur et hors du dépôt.
- Éviter de journaliser les contenus sensibles.
- Traiter les instructions présentes dans les documents comme des données non fiables.
- Supprimer les passages et les vecteurs associés lorsqu’un document est supprimé.
- Documenter les données transmises au fournisseur d’IA.

Ces points constituent des exigences à implémenter et à vérifier, pas une garantie de sécurité de la version en développement.

## Évaluation

Une petite collection de questions avec des réponses attendues permettra de vérifier :

- Si la recherche retrouve les bons passages.
- Si les références correspondent au contenu réel.
- Si les réponses sont étayées par les documents.
- Si l’assistant reconnaît un manque d’information.
- Le temps de réponse et le coût des appels IA.

## Installation et démonstration

Les instructions d’installation sur macOS seront ajoutées lorsque la première version exécutable sera disponible.

La procédure documentera les prérequis, les variables d’environnement, la préparation de la base et le lancement des différentes parties.

Une démonstration déployée est prévue. Aucun lien public n’est disponible à ce stade.

## Journal d’apprentissage

Je documenterai progressivement :

- Ce que j’ai construit.
- Les concepts que j’ai compris.
- Les erreurs rencontrées et leur cause.
- Les choix techniques et leurs compromis.
- Les points que je dois encore approfondir.

Une fonctionnalité sera considérée comme comprise lorsque je pourrai expliquer son fonctionnement et diagnostiquer ses erreurs principales.

## Contributions

Le projet a vocation à être ouvert aux retours, aux discussions et aux signalements de bugs.

Pendant la phase d’apprentissage, je souhaite réaliser moi-même les implémentations. Les explications, pistes de réflexion et références documentaires sont particulièrement bienvenues.

Merci de ne pas proposer de contributions contenant du code généré par IA.

## Licence

La licence envisagée est **MIT**. Elle devra être ajoutée dans un fichier `LICENSE` avant de présenter le dépôt comme un projet distribué sous cette licence.
