---
ms.openlocfilehash: ea2883912907843e4b6d65db5ba186af43f27aaa
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85805774"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

Comme alternative aux gestionnaires de packages, vous pouvez télécharger et installer manuellement le kit de développement logiciel (SDK) et le Runtime. L’installation manuelle est généralement effectuée dans le cadre du test d’intégration continue ou sur une distribution Linux non prise en charge. Pour un développeur ou un utilisateur, il est généralement préférable d’utiliser un gestionnaire de package.

Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant. Tout d’abord, téléchargez une version **binaire** pour le kit de développement logiciel (SDK) ou le runtime à partir de l’un des sites suivants :

- Téléchargements de ✔️ [.net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [téléchargements .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [téléchargements .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Tous les téléchargements .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

Ensuite, extrayez le fichier téléchargé et utilisez la `export` commande pour définir les variables utilisées par .net Core, puis vérifiez que .net Core se trouve dans le chemin d’accès.

Pour extraire le runtime et rendre les commandes CLI .NET Core disponibles sur le terminal, commencez par télécharger une version binaire .NET Core. Ensuite, ouvrez un terminal et exécutez les commandes suivantes à partir du répertoire dans lequel le fichier a été enregistré. Le nom du fichier d’archive peut être différent en fonction de ce que vous avez téléchargé.

**Utilisez la commande suivante pour extraire le runtime**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**Utilisez la commande suivante pour extraire le kit de développement logiciel (SDK)**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-linux-x64.tar.gz -C "$HOME/dotnet"
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
