---
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: 6a83b636dd83534788f3a38971e0fef2919314f5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005634"
---
# <a name="-deterministic"></a>-deterministic

Indique au compilateur de générer un assembly dont la sortie octet-pour-octet est identique dans les compilations pour les entrées identiques.

## <a name="syntax"></a>Syntaxe

```console
-deterministic
```

## <a name="remarks"></a>Notes

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

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
