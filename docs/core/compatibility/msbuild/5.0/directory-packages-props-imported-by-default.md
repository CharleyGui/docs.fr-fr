---
title: 'Modification avec rupture : les fichiers Directory. Packages. props sont importés par défaut'
description: Découvrez la modification avec rupture dans .NET 5,0 où les fichiers. props de NuGet importent automatiquement un fichier nommé Directory. Packages. props s’il est trouvé dans le dossier du projet.
ms.date: 09/17/2020
ms.openlocfilehash: ee8a2999b801e81750d96a0bc985e3c8169224a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760947"
---
# <a name="directorypackagesprops-files-is-imported-by-default"></a>Les fichiers Directory. Packages. props sont importés par défaut

Les fichiers *. props* de NuGet importent automatiquement un fichier nommé *Directory. Packages. props* s’il se trouve dans le dossier du projet ou dans l’un de ses ancêtres.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, vous pouviez avoir un fichier nommé *Directory. Packages. props* dans votre fichier projet et il ne sera pas automatiquement importé par le fichier *. props* de NuGet au moment de la génération.

À compter de .NET 5,0, un tel fichier *est* importé automatiquement s’il existe dans le dossier du projet ou dans l’un de ses ancêtres. Si vous avez un fichier portant ce nom dans le dossier de votre projet, cette importation automatique peut modifier le comportement de la Build. Par exemple, le fichier est importé, mais il n’a pas été précédemment, ou l’ordre de son importation peut changer si vous l’importez spécifiquement.

## <a name="reason-for-change"></a>Motif de modification

Cette modification a été apportée afin de prendre en charge le contrôle de [version de package central](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) pour NuGet.

## <a name="recommended-action"></a>Action recommandée

Renommez le fichier *Directory. Packages. props* existant s’il ne doit pas être importé automatiquement.

## <a name="affected-apis"></a>API affectées

N/A

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
