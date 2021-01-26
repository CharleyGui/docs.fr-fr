---
title: Gestion de version et bibliothèques .NET
description: Meilleures pratiques recommandées pour la gestion de version des bibliothèques .NET.
ms.date: 01/26/2021
ms.openlocfilehash: 1f3a14a7c32091621dda30a2d86724915d629564
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794732"
---
# <a name="versioning"></a>Contrôle de version

Une bibliothèque de logiciels est rarement terminée dans la version 1.0. Les bonnes bibliothèques évoluent au fil du temps, en ajoutant des fonctionnalités, en corrigeant les bogues et en améliorant les performances. Il est important de publier de nouvelles versions d’une bibliothèque .NET, fournissant une valeur supplémentaire à chaque version, sans interrompre les utilisateurs existants.

## <a name="breaking-changes"></a>Changements cassants

Pour plus d’informations sur la gestion des modifications avec rupture entre les versions, consultez [Modifications avec rupture](./breaking-changes.md).

## <a name="version-numbers"></a>Numéros de version

Une bibliothèque .NET offre de nombreuses façons de spécifier une version. Ces versions sont les plus importantes :

### <a name="nuget-package-version"></a>Version de package NuGet

La [version du package NuGet](/nuget/reference/package-versioning) s’affiche sur NuGet.org, le gestionnaire de package NuGet Visual Studio, et est ajoutée au code source lorsque le package est utilisé. La version du package NuGet correspond au numéro de version que les utilisateurs voient généralement, et ils y feront référence lorsqu’ils évoquent la version d’une bibliothèque qu’ils utilisent. La version du package NuGet est utilisée par NuGet et n’a aucun effet sur le comportement d’exécution.

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

L’identificateur de package NuGet combiné avec la version du package NuGet sert à identifier un package dans NuGet. Par exemple : `Newtonsoft.Json` + `11.0.2`. Un package avec un suffixe est un package de préversion et affiche un comportement spécial qui le rend idéal pour les tests. Pour plus d’informations, consultez [Packages de préversion](./nuget.md#pre-release-packages).

Étant donné que la version du package NuGet est la version la plus visible pour les développeurs, il est judicieux de le mettre à jour à l’aide de l’outil [Gestion sémantique de version (SemVer)](https://semver.org/). SemVer indique l’importance des modifications entre la mise en production et aide les développeurs à prendre une décision informée quant au choix de la version à utiliser. Par exemple, le passage de `1.0` à `2.0` indique qu’il existe potentiellement des modifications avec rupture.

✔️ ENVISAGER d’utiliser [SemVer 2.0.0](https://semver.org/) pour versionner votre package NuGet.

✔️ À FAIRE : Utiliser la version du package NuGet dans la documentation publique car il s’agit du numéro de version que les utilisateurs verront couramment.

✔️ À FAIRE : Inclure un suffixe de préversion lors de la publication d’un package non stable.

> Comme les utilisateurs doivent s’abonner pour obtenir les packages de préversion, ils constateront que le package n’est pas terminé.

### <a name="assembly-version"></a>Version de l’assembly

La version de l’assembly est celle utilisée par le CLR au moment de l’exécution pour sélectionner la version de l’assembly à charger. La sélection d’un assembly à l’aide du contrôle de version s’applique uniquement aux assemblys avec un nom fort.

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

Le CLR .NET Framework exige une correspondance exacte pour charger un assembly avec nom fort. Par exemple, `Libary1, Version=1.0.0.0` a été compilé avec une référence à `Newtonsoft.Json, Version=11.0.0.0`. .NET Framework chargera uniquement cette version exacte `11.0.0.0` . Pour charger une version différente au moment de l’exécution, une redirection de liaison doit être ajoutée au fichier de configuration de l’application .NET.

Les noms forts combinés avec la version de l’assembly permet un [chargement strict de la version d’assembly](../assembly/versioning.md). Bien que l’attribution d’un nom fort à une bibliothèque présente un certain nombre d’avantages, il résulte souvent d’exceptions d’exécution qu’un assembly ne peut pas être trouvé et [requiert des redirections de liaison](../../framework/configure-apps/redirect-assembly-versions.md) dans `app.config` ou `web.config` à corriger. Dans .NET Core, le chargement d’assembly est plus souple. Le Runtime .NET Core charge automatiquement les assemblys avec une version plus récente au moment de l’exécution.

✔️ À ENVISAGER : Inclure uniquement une version majeure dans AssemblyVersion.

> Par exemple, Library 1.0 et Library 1.0.1 afficher tous deux une valeur AssemblyVersion de `1.0.0.0`, tandis que Library 2.0 affiche une valeur AssemblyVersion de `2.0.0.0`. Lorsque la version d’assembly change moins souvent, cela réduit les redirections de liaison.

✔️ À ENVISAGER : Synchroniser le numéro de version majeure d’AssemblyVersion et la version du package NuGet.

> La valeur AssemblyVersion est incluse dans certains messages d’information affichées à l’utilisateur, par exemple, le nom de l’assembly et les noms du type d’assembly qualifié dans les messages d’exception. Maintenir une relation entre les versions fournit des informations supplémentaires aux développeurs sur la version qu’ils utilisent.

❌ N’ont pas de AssemblyVersion fixe.

> Bien qu'une valeur AssemblyVersion immuable évite d'avoir à lier des redirections, cela signifie qu'une seule version de l'assembly peut être installée dans le Global Assembly Cache (GAC). En outre, les applications qui font référence à l’assembly dans le GAC s’arrêtent si une autre application met à jour l’assembly GAC avec les dernières modifications.

### <a name="assembly-file-version"></a>Version du fichier d'assembly

La version du fichier d’assembly est utilisée pour afficher une version de fichier dans Windows et n’a aucun effet sur le comportement au moment de l’exécution. La définition de cette version est facultative. Elle apparaît dans la boîte de dialogue Propriétés du fichier dans l’Explorateur Windows :

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Explorateur Windows](./media/versioning/win-properties.png "Explorateur Windows")

✔️ À ENVISAGER : Inclure un numéro de build d’intégration continue en tant que révision AssemblyFileVersion.

> Par exemple, vous générez la version 1.0.0 de votre projet, et comme le numéro de build d’intégration continue est 99, votre AssemblyFileVersion est 1.0.0.99.

✔️ À FAIRE : utiliser le format `Major.Minor.Build.Revision` pour la version du fichier.

> Même si la version du fichier n’est jamais utilisée par .NET, [Windows exige une version du fichier](/windows/desktop/menurc/versioninfo-resource) au format `Major.Minor.Build.Revision`. Un avertissement est généré si la version n’utilise pas ce format.

### <a name="assembly-informational-version"></a>Version des informations sur l'assembly

La version des informations sur l’assembly est utilisée pour enregistrer des informations de version supplémentaires et n’a aucun effet sur le comportement d’exécution. La définition de cette version est facultative. Si vous utilisez Source Link, cette version sera définie sur la build comprenant la version du package NuGet et une version de contrôle de code source. Par exemple, `1.0.0-beta1+204ff0a` inclut le hachage de validation du code source sur lequel l’assembly repose. Pour plus d’informations, consultez [Source Link](./sourcelink.md).

```xml
<InformationalVersion>The quick brown fox jumped over the lazy dog.</InformationalVersion>
```

> [!NOTE]
> Les versions antérieures de Visual Studio déclenchent un avertissement de build si cette version n’utilise pas le format `Major.Minor.Build.Revision`. Vous pouvez ignorer cet avertissement sans risque.

❌ Évitez de définir vous-même la version d’informations de l’assembly.

> Autorisez SourceLink à générer automatiquement la version qui contient les métadonnées de contrôle source et NuGet.

>[!div class="step-by-step"]
>[Précédent](publish-nuget-package.md) 
> [Suivant](breaking-changes.md)
