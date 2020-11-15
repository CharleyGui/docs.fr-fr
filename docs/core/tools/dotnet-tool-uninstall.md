---
title: Commande dotnet tool uninstall
description: La commande de désinstallation de l’outil dotnet désinstalle l’outil .NET spécifié de votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: 34dffde8f9c930327c6b42d1d89bb4f511959fb2
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634088"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Name

`dotnet tool uninstall` -Désinstalle l' [outil .net](global-tools.md) spécifié de votre ordinateur.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a>Description

La `dotnet tool uninstall` commande vous permet de désinstaller les outils .net de votre ordinateur. Pour utiliser la commande, vous spécifiez l’une des options suivantes :

* Pour désinstaller un outil global qui a été installé à l’emplacement par défaut, utilisez l' `--global` option.
* Pour désinstaller un outil global qui a été installé dans un emplacement personnalisé, utilisez l' `--tool-path` option.
* Pour désinstaller un outil local, omettez `--global` les `--tool-path` options et.

**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**

## <a name="arguments"></a>Arguments

- **`PACKAGE_NAME`**

  Nom/ID du package NuGet qui contient l’outil .NET à désinstaller. Vous pouvez trouver le nom du package à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Options

- **`-g|--global`**

  Spécifie que l’outil à supprimer se trouve dans une installation à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. En omettant les deux `--global` et `--tool-path` spécifie que l’outil à supprimer est un outil local.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--tool-path <PATH>`**

  Spécifie l’emplacement de désinstallation de l’outil. Le chemin peut être absolu ou relatif. Non combinable avec l’option `--global`. En omettant les deux `--global` et `--tool-path` spécifie que l’outil à supprimer est un outil local.

## <a name="examples"></a>Exemples

- **`dotnet tool uninstall -g dotnetsay`**

  Désinstalle l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  Désinstalle l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) d’un répertoire Windows spécifique.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  Désinstalle l’outil Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) d’un répertoire Linux/MacOS spécifique.

- **`dotnet tool uninstall dotnetsay`**

  Désinstalle l’outil local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) du répertoire actif.

## <a name="see-also"></a>Voir aussi

- [Outils .NET](global-tools.md)
- [Didacticiel : installer et utiliser un outil .NET global à l’aide de l’interface de commande .NET](global-tools-how-to-use.md)
- [Didacticiel : installer et utiliser un outil local .NET à l’aide de l’interface de commande .NET](local-tools-how-to-use.md)
