---
title: Créez un package NuGet avec le CLI Core .NET
description: Découvrez comment créer un package NuGet avec la commande « dotnet pack ».
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920919"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a>Comment créer un package NuGet avec le CLI Core .NET

> [!NOTE]
> Voici des exemples de ligne de commande avec Unix. La commande `dotnet pack` montrée ici fonctionne de la même façon sur Windows.

Les bibliothèques .NET Standard et .NET Core devraient être distribuées sous forme de packages NuGet. Il s’agit en fait de la façon dont toutes les bibliothèques .NET Standard sont distribuées et consommées. Cette opération est plus facile avec la commande `dotnet pack`.

Imaginez que vous venez d’écrire une nouvelle bibliothèque que vous voulez distribuer via NuGet. Vous pouvez créer un package NuGet avec des outils multiplateformes pour faire exactement cela! L’exemple suivant suppose une bibliothèque appelée **SuperAwesomeLibrary** qui cible `netstandard1.0`.

Si vous avez des dépendances transitoires, c’est-à-dire un projet qui dépend `dotnet restore` d’un autre paquet, assurez-vous de restaurer des paquets pour l’ensemble de la solution avec la commande avant de créer un paquet NuGet. À défaut de le `dotnet pack` faire, la commande ne fonctionnera pas correctement.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Après avoir vérifié que les packages sont restaurés, vous pouvez accéder au répertoire où se trouve une bibliothèque :

```console
cd src/SuperAwesomeLibrary
```

Il s’agit d’une seule commande à partir de la ligne de commande :

```dotnetcli
dotnet pack
```

Votre *dossier /bin/Debug* ressemblera désormais à ceci :

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Cela produit un paquet qui est capable d’être débogé. Pour générer un package NuGet avec des fichiers binaires compilés, il suffit d’ajouter le commutateur `--configuration` (ou `-c`) et d’utiliser `release` comme argument.

```dotnetcli
dotnet pack --configuration release
```

Votre *dossier /bin* aura désormais un dossier *de dégagement* contenant votre paquet NuGet avec binaires de libération :

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
