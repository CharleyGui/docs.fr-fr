---
title: Migration .NET Core à partir de project.json
description: Apprenez à migrer un ancien projet .NET Core à l’aide de project.json
ms.date: 07/19/2017
ms.custom: seodec18
ms.openlocfilehash: 2912262d1191114d2314fed89e31c91c114f1935
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773902"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>Migration de projets .NET Core à partir de project.json

Ce document traite des trois scénarios de migration suivants pour les projets .NET Core :

1. [Migration à partir du schéma valide le plus récent de *project.json* vers *csproj*](#migration-from-projectjson-to-csproj)
2. [Migration à partir de DNX vers csproj](#migration-from-dnx-to-csproj)
3. [Migration de projets csproj .NET Core RC3 et antérieurs vers le format final](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

Ce document s’applique uniquement aux projets .NET Core plus anciens qui utilisent Project. JSON. Elle ne s’applique pas à la migration de .NET Framework à .NET Core.

## <a name="migration-from-projectjson-to-csproj"></a>Migration de project.json vers csproj

La migration à partir de *project.json* vers *.csproj* peut être effectuée à l’aide de l’une des méthodes suivantes :

- [Visual Studio](#visual-studio)
- [Outil de ligne de commande dotnet migrate](#dotnet-migrate)

Les deux méthodes utilisant le même moteur sous-jacent pour migrer les projets, les résultats obtenus sont donc identiques dans les deux cas. Dans la plupart des cas, l’utilisation de l’une de ces deux méthodes pour migrer *Project. JSON* vers *csproj* est la seule chose nécessaire et aucune autre modification manuelle du fichier projet n’est nécessaire. Le fichier *.csproj* obtenu porte le même nom que le répertoire le contenant.

### <a name="visual-studio"></a>Visual Studio

Quand vous ouvrez un fichier *. xproj* ou un fichier solution qui fait référence à des fichiers *. Xproj* dans Visual Studio 2017 ou visual studio 2019 version 16,2 et antérieure, la boîte de dialogue de **mise à niveau unidirectionnelle** s’affiche. La boîte de dialogue affiche les projets à migrer. Si vous ouvrez un fichier solution, tous les projets spécifiés dans le fichier solution sont répertoriés. Passez en revue la liste des projets à migrer, puis sélectionnez **OK**.

![Boîte de dialogue Mise à niveau définitive indiquant la liste des projets à migrer](media/one-way-upgrade.jpg)

Visual Studio migre automatiquement les projets sélectionnés. Lors de la migration d’une solution, si vous ne choisissez pas tous les projets, la même boîte de dialogue s’affiche pour vous demander de mettre à niveau les projets restants à partir de cette solution. Une fois le projet migré, vous pouvez voir et modifier son contenu en double-cliquant sur le projet dans la fenêtre **Explorateur de solutions** et en sélectionnant **Modifier \<nom_projet>.csproj**.

Les fichiers qui ont été migrés (*Project. JSON*, *global. JSON*, *. xproj*et le fichier solution) sont déplacés vers un dossier de *sauvegarde* . Le fichier solution migrée est mis à niveau vers Visual Studio 2017 ou Visual Studio 2019 et vous ne pouvez pas ouvrir ce fichier solution dans Visual Studio 2015 ou versions antérieures. Un fichier nommé *UpgradeLog. htm* qui contient un rapport de migration est également enregistré et ouvert automatiquement.

> [!IMPORTANT]
> Dans Visual Studio 2019 version 16,3 et versions ultérieures, vous ne pouvez pas charger ou migrer un fichier *. xproj* . En outre, Visual Studio 2015 ne permet pas de migrer un fichier *. xproj* . Si vous utilisez l’une de ces versions de Visual Studio, installez une version appropriée de Visual Studio ou utilisez l’outil de migration en ligne de commande décrit ci-après.

### <a name="dotnet-migrate"></a>dotnet migrate

Dans le scénario de ligne de commande, vous pouvez utiliser la commande [`dotnet migrate`](../tools/dotnet-migrate.md). Il migre un projet, une solution ou un ensemble de dossiers dans cet ordre, en fonction de ceux qui ont été trouvés. Quand vous migrez un projet, le projet et toutes ses dépendances sont migrés.

Les fichiers qui ont été migrés (*Project. JSON*, *global. JSON*et *. xproj*) sont déplacés vers un dossier de *sauvegarde* .

> [!NOTE]
> Si vous utilisez Visual Studio Code, la commande `dotnet migrate` ne modifie pas les fichiers spécifiques à la Visual Studio Code, tels que *Tasks. JSON*. Ces fichiers doivent être modifiés manuellement.
> Cela est également vrai si vous utilisez un éditeur ou un environnement de développement intégré (IDE) autre que Visual Studio.

Consultez [un mappage entre les propriétés Project. JSON et csproj](../tools/project-json-to-csproj.md) pour une comparaison des formats *Project. JSON* et *. csproj* .

Si vous obtenez une erreur :

> Aucun fichier exécutable correspondant à la commande dotnet-Migrate n’a été trouvé

Exécutez `dotnet --version` pour afficher la version que vous utilisez. [`dotnet migrate`](../tools/dotnet-migrate.md) a été introduite dans kit SDK .net Core 1.0.0 et supprimée dans la version 3.0.100.
Vous obtiendrez cette erreur si vous avez un fichier *global. JSON* dans le répertoire actif ou parent, et que la version de `sdk` qu’il spécifie est en dehors de cette plage.

## <a name="migration-from-dnx-to-csproj"></a>Migration à partir de DNX vers csproj

Si vous utilisez encore DNX pour le développement .NET Core, votre processus de migration doit être effectué en deux étapes :

1. Utilisez les [conseils de migration DNX existants](from-dnx.md) pour la migration à partir de DNX vers la CLI prenant en charge project-json.
2. Suivez les étapes de la section précédente pour la migration de *project.json* vers *.csproj*.  

> [!NOTE]
> DNX a été officiellement déprécié lors de la version Preview 1 de la CLI .NET Core.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migration de formats csproj .NET Core antérieurs vers le format csproj final

Le format csproj .NET Core est modifié et évolue avec chaque nouvelle version préliminaire des outils. Comme il n’existe aucun outil pour migrer votre fichier projet des versions antérieures de csproj vers la dernière version, vous devez modifier manuellement le fichier projet. Les étapes réelles dépendent de la version du fichier projet que vous migrez. Voici quelques conseils à prendre en compte en fonction des modifications apportées entre les versions :

- Supprimez la propriété de version des outils de l’élément `<Project>`, si elle existe.
- Supprimez l’espace de noms XML (`xmlns`) de l’élément `<Project>`.
- S’il n’existe pas, ajoutez l’attribut `Sdk` à l’élément `<Project>` et affectez-lui la valeur `Microsoft.NET.Sdk` ou `Microsoft.NET.Sdk.Web`. Cet attribut spécifie que le projet utilise le SDK à utiliser. `Microsoft.NET.Sdk.Web` est utilisé pour les applications web.
- Supprimez les instructions `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` et `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` en haut et en bas du projet. Ces instructions d’importation étant indiquées implicitement par le SDK, il est inutile qu’elles figurent dans le projet.
- Si des éléments `<PackageReference>` `Microsoft.NETCore.App` ou `NETStandard.Library` figurent dans votre projet, vous devez les supprimer. Ces références de package sont [indiquées implicitement par le SDK](https://aka.ms/sdkimplicitrefs).
- Supprimez l’élément `<PackageReference>` `Microsoft.NET.Sdk`, s’il existe. La référence SDK est fournie par l’attribut `Sdk` sur l’élément `<Project>`.
- Supprimez les modèles [Glob](https://en.wikipedia.org/wiki/Glob_(programming)) qui sont [indiqués implicitement par le SDK](../tools/csproj.md#default-compilation-includes-in-net-core-projects). En laissant ces modèles Glob dans votre projet, une erreur se produit lors de la génération, car les éléments de compilation sont dupliqués.

Une fois ces étapes effectuées, votre projet doit être entièrement compatible avec le format csproj .NET Core final.

Pour obtenir des exemples antérieurs et postérieurs à la migration de l’ancien format csproj vers le nouveau, consultez l’article [Updating Visual Studio 2017 RC – .NET Core Tooling improvements](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) sur le blog .NET.

## <a name="see-also"></a>Voir aussi

- [Porter, migrer et mettre à niveau des projets Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
