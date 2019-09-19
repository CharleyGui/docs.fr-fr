---
title: Créer un package NuGet avec des outils de l’interface de ligne de commande (CLI) de .NET Core
description: Découvrez comment créer un package NuGet avec la commande « dotnet pack ».
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: d36a6ee7d524933577928daa9993fba8ce62f6c7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116697"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>Guide pratique pour créer un package NuGet avec des outils de l’interface de ligne de commande (CLI) de .NET Core

> [!NOTE]
> Voici des exemples de ligne de commande avec Unix. La commande `dotnet pack` montrée ici fonctionne de la même façon sur Windows.

Les bibliothèques .NET Standard et .NET Core devraient être distribuées sous forme de packages NuGet. Il s’agit en fait de la façon dont toutes les bibliothèques .NET Standard sont distribuées et consommées. Cette opération est plus facile avec la commande `dotnet pack`.

Imaginez que vous venez d’écrire une nouvelle bibliothèque que vous voulez distribuer via NuGet. Pour cela, vous pouvez créer un package NuGet avec les outils multiplateformes. L’exemple suivant suppose une bibliothèque nommée **SuperAwesomeLibrary** ciblant `netstandard1.0`.

Si vous avez des dépendances transitives (c’est-à-dire un projet qui dépend d’un autre package), veillez à restaurer les packages de l’ensemble de votre solution avec la commande `dotnet restore` avant de créer un package NuGet. Si vous ne le faites pas, la commande `dotnet pack` ne fonctionne pas correctement.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Après avoir vérifié que les packages sont restaurés, vous pouvez accéder au répertoire où se trouve une bibliothèque :

```console
cd src/SuperAwesomeLibrary
```

Il s’agit d’une seule commande à partir de la ligne de commande :

```dotnetcli
dotnet pack
```

Votre dossier `/bin/Debug` doit maintenant ressembler à ceci :

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Notez que ceci génère un package qui peut être débogué. Pour générer un package NuGet avec des fichiers binaires compilés, il suffit d’ajouter le commutateur `--configuration` (ou `-c`) et d’utiliser `release` comme argument.

```dotnetcli
dotnet pack --configuration release
```

Votre dossier `/bin` a désormais un dossier `release` contenant votre package NuGet avec les fichiers binaires compilés :

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Vous avez maintenant les fichiers nécessaires pour publier un package NuGet !

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Ne confondez pas `dotnet pack` et `dotnet publish`

Il est important de noter qu’à aucun moment, la commande `dotnet publish` n’est impliquée. La commande `dotnet publish` sert à déployer des applications avec toutes leurs dépendances dans le même bundle, et non pas à générer un package NuGet à distribuer et à consommer sur NuGet.

## <a name="see-also"></a>Voir aussi

- [Démarrage rapide : Créer et publier un package](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
