---
title: 'Modification avec rupture : éblouissant : logique de validation mise à jour pour les ressources Web statiques'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé « éblouissant » : logique de validation mise à jour pour les ressources Web statiques'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f201818c0130739e8da4f42e7b1f3a1987f70d1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760964"
---
# <a name="blazor-updated-validation-logic-for-static-web-assets"></a>Éblouissant : logique de validation mise à jour pour les ressources Web statiques

Un problème est survenu lors de la validation des ressources Web statiques dans ASP.NET Core 3,1 et éblouissant webassembly 3,2. Le problème :

* A empêché la détection de conflit appropriée entre les ressources et les ressources de l’ordinateur hôte à partir des bibliothèques de classes Razor (RCLs) et des applications webassembly éblouissantes.
* Affecte principalement les applications de webassembly éblouissantes, car par défaut, les ressources Web statiques dans RCLs sont traitées sous le `_content/$(PackageId)` préfixe.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="old-behavior"></a>Ancien comportement

Pendant le développement, les ressources Web statiques d’un RCL peuvent être remplacées en mode silencieux par des ressources de projet hôte sur le même chemin d’accès d’ordinateur hôte. Prenons l’exemple d’un RCL qui a défini une ressource Web statique à prendre en charge à */folder/file.txt*. Si l’hôte a placé un fichier sur *wwwroot/dossier/file.txt*, le fichier sur le serveur a remplacé silencieusement le fichier sur l’application RCL ou éblouissant webassembly.

## <a name="new-behavior"></a>Nouveau comportement

ASP.NET Core détecte correctement quand ce problème se produit. Il vous informe de l’utilisateur, du conflit, afin que vous puissiez prendre les mesures appropriées.

## <a name="reason-for-change"></a>Motif de modification

Les ressources Web statiques n’étaient pas destinées à être substituables par des fichiers sur l’hôte *wwwroot* du projet. Le fait d’autoriser le remplacement de ces fichiers peut entraîner des erreurs difficiles à diagnostiquer. Le résultat peut être des modifications de comportement non définies dans les applications publiées.

## <a name="recommended-action"></a>Action recommandée

Par défaut, il n’y a aucune raison pour qu’un fichier RCL soit en conflit avec un fichier sur l’ordinateur hôte. Les fichiers RCL sont précédés du préfixe `_content/${PackageId}` . Les fichiers webassembly éblouissant sont placés à la racine de l’espace d’URL de l’hôte, ce qui facilite les conflits. Par exemple, les applications de webassembly éblouissantes contiennent un fichier *favicon. ico* que l’hôte peut également inclure dans son dossier *wwwroot* .

Si la source du conflit est un fichier RCL, cela signifie souvent que le code copie les ressources de la bibliothèque dans le dossier *wwwroot* du projet. L’écriture de code pour copier des fichiers est à l’encontre d’un objectif principal des ressources Web statiques. Cet objectif est fondamental pour obtenir des mises à jour sur le navigateur lorsque le contenu est mis à jour sans avoir à déclencher une nouvelle compilation.

Vous pouvez choisir de conserver ce comportement et de conserver le fichier sur l’ordinateur hôte. Pour ce faire, supprimez le fichier de la liste des ressources Web statiques avec une cible MSBuild personnalisée.

Pour utiliser le fichier de RCL ou le fichier de l’application éblouissante webassembly au lieu du fichier du projet hôte, supprimez le fichier du projet hôte.

## <a name="affected-apis"></a>API affectées

None

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
