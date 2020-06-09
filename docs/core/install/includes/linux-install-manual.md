---
ms.openlocfilehash: e7d35045892c62f759aad5067962ac5c15a9fb8b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602928"
---

Les kit SDK .NET Core et le Runtime .NET Core peuvent être installés manuellement après avoir été téléchargés. Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant. Tout d’abord, téléchargez une version binaire pour le kit de développement logiciel (SDK) ou le runtime à partir de l’un des sites suivants :

- Téléchargements de ✔️ [.net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [téléchargements .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ❌[Téléchargements .net Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- ❌[Téléchargements .net Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- ✔️ [téléchargements .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

Ensuite, extrayez le fichier téléchargé et utilisez la `export` commande pour définir les variables utilisées par .net Core, puis vérifiez que .net Core se trouve dans le chemin d’accès.

Pour extraire le runtime et rendre les commandes CLI .NET Core disponibles sur le terminal, commencez par télécharger une version binaire .NET Core. Ensuite, ouvrez un terminal et exécutez les commandes suivantes à partir du répertoire dans lequel le fichier a été enregistré.

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Les `export` commandes précédentes rendent uniquement les commandes CLI .net Core disponibles pour la session Terminal dans laquelle elles ont été exécutées.
>
> Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes. Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent. Par exemple :
>
> - **Interpréteur**de commandes bash : *~/. bash_profile*, *~ fichier/.bashrc*
> - **Shell Korn**: *~/.kshrc* ou *. Profile*
> - **Z Shell**: *~/.zshrc* ou *. zprofile*
>
> Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l' `PATH` instruction existante. Si aucune `PATH` instruction n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet` .
>
> Ajoutez également `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.

Cette approche vous permet d’installer différentes versions dans des emplacements distincts et de choisir explicitement celle qui doit être utilisée par l’application.
