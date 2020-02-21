---
title: Commande dotnet tool uninstall
description: La commande de désinstallation de l’outil dotnet désinstalle l’outil .NET Core spécifié de votre ordinateur.
ms.date: 02/14/2020
ms.openlocfilehash: 82dad0206d9c3e2ef0f41c353f4a608f10e4f127
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543441"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Name

`dotnet tool uninstall`-désinstalle l' [outil .net Core](global-tools.md) spécifié de votre ordinateur.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Description

La commande `dotnet tool uninstall` vous permet de désinstaller les outils .NET Core de votre ordinateur. Pour utiliser la commande, vous spécifiez l’une des options suivantes :

* Pour désinstaller un outil global qui a été installé à l’emplacement par défaut, utilisez l’option `--global`.
* Pour désinstaller un outil global qui a été installé dans un emplacement personnalisé, utilisez l’option `--tool-path`.
* Pour désinstaller un outil local, omettez les options `--global` et `--tool-path`.

**Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.**

## <a name="arguments"></a>Arguments

- **`PACKAGE_NAME`**

  Nom/ID du package NuGet qui contient l’outil .NET Core à désinstaller. Vous pouvez trouver le nom du package à l’aide de la commande [dotnet tool list](dotnet-tool-list.md).

## <a name="options"></a>Options

- **`-g|--global`**

  Spécifie que l’outil à supprimer se trouve dans une installation à l’échelle de l’utilisateur. Non combinable avec l’option `--tool-path`. L’omission de `--global` et `--tool-path` spécifie que l’outil à supprimer est un outil local. 

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--tool-path <PATH>`**

  Spécifie l’emplacement de désinstallation de l’outil. Le chemin peut être absolu ou relatif. Non combinable avec l’option `--global`. L’omission de `--global` et `--tool-path` spécifie que l’outil à supprimer est un outil local. 

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

- [Outils .NET Core](global-tools.md)
