---
date: 2019-04-17
title: WIP Mode ou comment éviter les grosses pulls requests
author: remithomas
slug: wip-mode-ou-comment-eviter-les-grosses-pulls-requests
---

## Les bases

Commençons cet article par les bases, et ouais de temps en temps ça fait du bien..

### Les pull/merge requests

Faire des _Pull Requests_ (ou _Merge Requests_ si vous êtes fan de Gitlab), je parlerai ici de PR (Pull Requests). À quoi ça sert ? Nous essayons d'améliorer un codebase en itératif.

### Le code review

Commençons par le début, c'est quoi l'objectif d'une code review ?

Pour certains c'est peut-être l'étape chiante avant de mettre son code super beau et super long dans le codebase... Chiante parce que on va avoir plein de commentaires... Ou encore on va passer 2h à lire du code incompréhensible pour laisser à la fin un pauvre LGTM (Looks Good To Me) et votre like.
Et bien non c'est pas du tout ça. C'est le moment d'apprendre, de valider que l'on a fait de la qualité, d'intéragir.

J'ai dis `apprendre` car on va reviewer et on va comprendre de nouvelle façon d'écrire du code etc.. d
J'ai dis `valider` car on va essayer que ce soit plus parfait possible
J'ai dis `qualité` car on va faire que ce soit maintenanble sans erreur
J'ai dis `intéragir` car on va avoir un échange avec nos collègues (autre que pendant la pause café)

le code est vivant, c'est


En gros, on essaie d'éviter 
donc faire des commits sur develop ça ne sert à personne sauf si vous êtes sur votre projet tout seul.. l'idée est de montrer le code aux autres meme si vous êtes le meilleur, de cette façon vous allez apprendre aux autres à coder.

que ce ne soit pas chiant pour tout le monde, que ça ne fait pas perdre du temps à tous 

Un reviewer c'est donc toi ou un de tes collègues

## Les grosses pull/merge requests

Entrons maintenant dans le vif du sujet, le probème des pavés de code de type roman __Les Misérables__..

Faire des GROSSES `pull-requests` ou les `merge-requests` si vous voulez, c'est pas bien. Si vous êtes du genre fier d'avoir ajouté des milliers de lignes de codes en une seule fois... et bien changer de métier (signé vos collègues).

Pourquoi c'est pas bien ?

- Ça prend beaucoup de temps à comprendre au reviewer
    > Donc on ralentit tout le monde
- Ça fait beaucoup de commentaires (à corriger)
    > Donc on ralentit tout le monde
- Ça fait des reviews non-optimales et du mauvais code peut passer (au bout de 200 lignes lues de code, pourquoi je suis dans ce IF)
    > Donc on ralentit tout le monde (au final)

L'idée est simple, on essaie de faire du code en itératif avec des petits bouts à chaque fois donc pas des romans. Et d'avoir la meilleure review possible et obtenir un code de qualité dans la

On peut toujours éviter de faire des grosses PRs, voilà une petite liste d'excuse :
- Les fichiers sont interconnectés alors je ne pouvais pas (donc pas capable de le faire en une fois)
- C’était plus simple (pour toi, pas pour le reviewer)
- Ça ne marche pas ()
- Pourquoi pas (donc pas essayer)
- On se disperserait en codant les features
- On aura beaucoup de pullrequests ()

## Le concept WIP Mode

Le nom...
J'ai pas vraiment de nom pour ça, le nom vient du fait que l'on préfixe devant notre PR le mot `WIP` (Work In Progress) et lorsque tout est fini on retire le préfix. Si vous avez un meilleur nom, _you tell me_

Comment ça marche

Voici la version courte: 
> Une branche parente qui va recevoir plein de petites PRs bien reviewées qui avaient été optimisées pour la revue. 

Et maintenant la version longue:

Je vais illuster avec un exemple, disons que ma feature est un formulaire avec 5 champs et un bouton. pas de quoi s'affoler, nommé _Création profil_.

Étape 1:
Créer une branche depuis votre master nommé `feature/create_profile`. Et créer une Pull Request de cette branche.

Le titre sera `WIP - Création profil`. Noté le préfix devant le titre qui tue.

La description est l'élément le plus important car on va expliquer ce qui va être mergé dans cette PR. Donc potentiellement notre liste de taches devrait être, créer page formulaire, créer formulaire avec 1 champ, service vers le backend, ajouter les 4 autres champs et pour finir un peu de design. Relisons:
- créer page formulaire (notre intégration dans le code base existant)
- créer formulaire avec 1 champ et son bouton (le strict minimum pour avoir un formulaire: 1 input et 1 button)
- service vers le backend (la couche qui va envoyer vers le backend)
- ajouter les 4 autres champs (le reste des champs)
- design (appliquer un peu CSS-in-JS)

maintenant la description complète:

```md
Création profil

- [ ] Page formulaire 
- [ ] Créer formulaire avec 1 champ input et 1 submit
- [ ] Service creation vers le backend
- [ ] Ajouter les 4 autres champs
- [ ] Design
```

Note: il est possible que vous ayez à modifier du code pour créer votre PR, n'hésitez pas à améliorer le README.md (la meilleur documentation)

Étape 2:


## Pourquoi

Une question qui peut se poser, c'est pourquoi faire/utiliser cette méthode ? Pourquoi se prendre la tête à découper le code de cette façon:

- un des concepts qui permet d'écrire une application de qualité est de ne pas insérer de code mort ([Dead Code](https://blog.ndepend.com/no-excuse-dead-code/)) 
- c'est une feature branch que vous créé
- vous êtes capable de planifier votre écriture de code (vous deviendrez encore meilleur developpeur)

## Autres solutions pour éviter les grosses PRs

par commits: (des commits) ça marche mais si vous avez des changements demandés dans votre review il vous faudra corriger (git-amend) vos commits et non en rajoutés... sinon ça ne vaut pas le coup de découper par commits.

## Final notes
J'ai appris cette méthode de ... 
