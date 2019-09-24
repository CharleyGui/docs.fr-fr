---
title: Utilisation de Package Management F# avec pour Azure
description: Utiliser Paket ou NuGet pour gérer F# les dépendances Azure
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 4aa32ace91f30d0e43b9c40067f5f0f456cc4069
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214230"
---
# <a name="package-management-for-f-azure-dependencies"></a>Gestion des packages pour les dépendances F# Azure

L’obtention de packages pour le développement Azure est facile lorsque vous utilisez un gestionnaire de package. Les deux options sont [Paket](https://fsprojects.github.io/Paket/) et [NuGet](https://www.nuget.org/).

## <a name="using-paket"></a>Utilisation de Paket

Si vous utilisez [Paket](https://fsprojects.github.io/Paket/) comme gestionnaire de dépendances, vous pouvez utiliser l' `paket.exe` outil pour ajouter des dépendances Azure. Par exemple :

```console
> paket add nuget WindowsAzure.Storage
```

Ou, si vous utilisez [mono](https://www.mono-project.com/) pour le développement .net multiplateforme :

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

Cela ajoute `WindowsAzure.Storage` à votre ensemble de dépendances de package pour le projet dans le répertoire actif, modifie `paket.dependencies` le fichier et télécharge le package. Si vous avez déjà configuré des dépendances ou si vous travaillez avec un projet dans lequel des dépendances ont été configurées par un autre développeur, vous pouvez résoudre et installer les dépendances localement comme suit :

```console
> paket install
```

Ou, pour le développement mono :

```console
> mono paket.exe install
```

Vous pouvez mettre à jour toutes les dépendances de votre package avec la version la plus récente, comme suit :

```console
> paket update
```

Ou, pour le développement mono :

```console
> mono paket.exe update
```

## <a name="using-nuget"></a>Utilisation de NuGet

Si vous utilisez [NuGet](https://www.nuget.org/) comme gestionnaire de dépendances, vous pouvez utiliser l' `nuget.exe` outil pour ajouter des dépendances Azure. Par exemple :

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

Ou, pour le développement mono :

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

Cela ajoutera `WindowsAzure.Storage` à votre ensemble de dépendances de package pour le projet dans le répertoire actif et téléchargera le package. Si vous avez déjà configuré des dépendances ou si vous travaillez avec un projet dans lequel des dépendances ont été configurées par un autre développeur, vous pouvez résoudre et installer les dépendances localement comme suit :

```console
> nuget restore
```

Ou, pour le développement mono :

```console
> mono nuget.exe restore
```

Vous pouvez mettre à jour toutes les dépendances de votre package avec la version la plus récente, comme suit :

```console
> nuget update
```

Ou, pour le développement mono :

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a>Référencement d'assemblys

Pour pouvoir utiliser vos packages dans votre F# script, vous devez référencer les assemblys inclus dans les packages à l’aide `#r` d’une directive. Par exemple :

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

Comme vous pouvez le voir, vous devez spécifier le chemin d’accès relatif à la DLL et le nom complet de la DLL, qui peut ne pas être exactement le même que le nom du package. Le chemin d’accès inclut une version de Framework et éventuellement un numéro de version de package. Pour rechercher tous les assemblys installés, vous pouvez utiliser une commande semblable à celle-ci sur une ligne de commande Windows :

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

Ou dans un interpréteur de commandes UNIX, comme suit :

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

Vous obtiendrez les chemins d’accès aux assemblys installés. À partir de là, vous pouvez sélectionner le chemin d’accès correct pour la version de votre infrastructure.
