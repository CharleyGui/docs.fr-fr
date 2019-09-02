---
title: -deterministic (Options du compilateur C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e77c14a1c3a4ba11b8ae6556be4f1c3c0cd42788
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202921"
---
# <a name="-deterministic"></a>-deterministic

Indique au compilateur de générer un assembly dont la sortie octet-pour-octet est identique dans les compilations pour les entrées identiques.

## <a name="syntax"></a>Syntaxe

```console
-deterministic
```

## <a name="remarks"></a>Remarques

Par défaut, le résultat de la compilation d’un ensemble défini d’entrées est unique, étant donné que le compilateur ajoute un horodatage et un GUID qui est généré à partir de nombres aléatoires. Utilisez l’option `-deterministic` pour générer un *assembly déterministe*, dont le contenu binaire sera identique dans les compilations tant que l’entrée restera la même.

Le compilateur considère les entrées suivantes à des fins déterministes :

- La séquence des paramètres de ligne de commande.
- Le contenu du fichier réponse .rsp du compilateur.
- La version précise du compilateur utilisée et ses assemblys référencés.
- Le chemin de répertoire actif.
- Le contenu binaire de tous les fichiers explicitement passés au compilateur directement ou indirectement, notamment :
  - Fichiers sources
  - Assemblys référencés
  - Modules référencés
  - Ressources
  - Fichier de clé de nom fort
  - Fichiers réponse @
  - Analyseurs
  - Ensembles de règles
  - Autres fichiers susceptibles d’être utilisés par les analyseurs
- La culture actuelle (pour le langage dans lequel les diagnostics et les messages d’exception sont produits).
- L’encodage par défaut (ou la page de codes active) si l’encodage n’est pas spécifié.
- L’existence, la non-existence et le contenu des fichiers sur les chemins de recherche du compilateur (spécifiés, par exemple, par `/lib` ou `/recurse`).
- La plateforme CLR sur laquelle est exécuté le compilateur.
- La valeur de `%LIBPATH%`, qui peut affecter le chargement des dépendances de l’analyseur.

Quand les sources sont accessibles à tous, la compilation déterministe peut servir à établir si un fichier binaire est compilé à partir d’une source approuvée. Il peut aussi être utile dans un système de génération en continu pour déterminer si les étapes de génération qui sont dépendantes des changements apportés à un binaire doivent être exécutées.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
