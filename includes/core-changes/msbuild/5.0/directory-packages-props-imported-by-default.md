---
ms.openlocfilehash: 4a916a4178535763712ebd58fde1a81e456da0d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538815"
---
### <a name="directorypackagesprops-files-is-imported-by-default"></a>Les fichiers Directory. Packages. props sont importés par défaut

Les fichiers *. props* de NuGet importent automatiquement un fichier nommé *Directory. Packages. props* s’il se trouve dans le dossier du projet ou dans l’un de ses ancêtres.

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 8

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, vous pouviez avoir un fichier nommé *Directory. Packages. props* dans votre fichier projet et il ne sera pas automatiquement importé par le fichier *. props* de NuGet au moment de la génération.

À compter de .NET 5,0, un tel fichier *est* importé automatiquement s’il existe dans le dossier du projet ou dans l’un de ses ancêtres. Si vous avez un fichier portant ce nom dans le dossier de votre projet, cette importation automatique peut modifier le comportement de la Build. Par exemple, le fichier est importé, mais il n’a pas été précédemment, ou l’ordre de son importation peut changer si vous l’importez spécifiquement.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification a été apportée afin de prendre en charge le contrôle de [version de package central](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) pour NuGet.

#### <a name="recommended-action"></a>Action recommandée

Renommez le fichier *Directory. Packages. props* existant s’il ne doit pas être importé automatiquement.

#### <a name="category"></a>Category

MSBuild

#### <a name="affected-apis"></a>API affectées

N/A

<!--

#### Affected APIs

Not detectable via API analysis.

-->
