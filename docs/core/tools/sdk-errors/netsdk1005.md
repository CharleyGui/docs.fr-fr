---
title: 'NETSDK1005 et NETSDK1047 : la cible est manquante dans le fichier d’élément multimédia'
description: La résolution du problème d’un fichier de ressources n’a pas de cible.
author: sfoslund
ms.topic: error-reference
ms.date: 12/17/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: e3e7389adf6a9a715d44661a5f7cbae5efe299e4
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678167"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a>NETSDK1005 et NETSDK1047 : la cible est manquante dans le fichier d’élément multimédia

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 2.1.100 .net Core et versions ultérieures

Lorsque le kit de développement logiciel (SDK) .NET émet une erreur NETSDK1005 ou NETSDK1047, le fichier de ressources du projet ne contient pas d’informations sur l’un de vos frameworks cibles. NuGet écrit un fichier nommé *project.assets.js* dans le dossier *obj* , et le kit de développement logiciel (SDK) .net l’utilise pour obtenir des informations sur les packages à passer au compilateur. Dans .NET 5, NuGet a ajouté un nouveau champ nommé `TargetFrameworkAlias` , de sorte que les versions antérieures de MSBuild ou NuGet génèrent un fichier de ressources sans le nouveau champ. Pour plus d’informations, consultez l' [erreur NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html).

Voici quelques actions que vous pouvez effectuer, susceptibles de résoudre l’erreur :

* Assurez-vous que vous utilisez MSBuild version 16,8 ou ultérieure et NuGet version 5,8 ou ultérieure, puis restaurez le projet après avoir mis à jour vos outils. Lorsque vous utilisez NuGet version 5,8 ou ultérieure, vous devez utiliser Visual Studio 2019 version 16,8 ou ultérieure, MSBuild version 16,8 ou ultérieure et .NET 5,0 SDK ou version ultérieure.

* Si vous recevez l’erreur lors de la première génération d’un projet dans Visual Studio 2019 après l’installation de la version 16,8 ou après avoir modifié le Framework cible du projet, générez le projet une deuxième fois.

* Supprimez le dossier *obj* avant de générer le projet.

* Assurez-vous que la valeur cible manquante est incluse dans la `TargetFrameworks` propriété de votre projet.
