---
title: Installer manuellement .NET sur Linux-.NET
description: Montre comment installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sans le gestionnaire de package sur Linux. Utilisez le script d’installation ou extrayez manuellement les fichiers binaires.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 5879d4d66aba8bfa00caadbe3c33d6df0d7da59a
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970966"
---
# <a name="install-the-net-sdk-or-the-net-runtime-manually"></a>Installer manuellement le kit de développement logiciel (SDK) .NET ou le Runtime .NET

.NET est pris en charge sur Linux et cet article explique comment installer .NET sur Linux à l’aide du script d’installation ou en extrayant les fichiers binaires. Pour obtenir la liste des distributions qui prennent en charge le gestionnaire de package intégré, consultez [installer .net sur Linux](linux.md).

Vous pouvez également installer .NET avec le composant logiciel enfichable. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) .net ou le Runtime .net avec le composant logiciel enfichable](linux-snap.md).

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="net-releases"></a>Versions de .NET

Le tableau suivant répertorie les versions de .NET (et .NET Core) :

| ✔️ pris en charge | ❌ Pris en charge |
|-------------|---------------|
| 5.0         | 3.0           |
| 3,1 (LTS)   | 2.2           |
| 2,1 (LTS)   | 2,0           |
|             | 1,1           |
|             | 1.0           |

Pour plus d’informations sur le cycle de vie des versions de .NET, consultez [stratégie de support .net Core et .net 5](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="dependencies"></a>Dépendances

Lorsque vous installez .NET, il est possible que des dépendances spécifiques ne soient pas installées, par exemple lors de [l’installation manuelle](#manual-install). La liste suivante répertorie les distributions Linux prises en charge par Microsoft et qui présentent des dépendances que vous devrez peut-être installer. Consultez la page distribution pour plus d’informations :

- [Alpine](linux-alpine.md#dependencies)
- [Debian](linux-debian.md#dependencies)
- [CentOS](linux-centos.md#dependencies)
- [Fedora](linux-fedora.md#dependencies)
- [RHEL](linux-rhel.md#dependencies)
- [SLES](linux-sles.md#dependencies)
- [Ubuntu](linux-ubuntu.md#dependencies)

Pour obtenir des informations générales sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

### <a name="rpm-dependencies"></a>Dépendances RPM

Si votre distribution n’a pas été précédemment listée et est basée sur RPM, vous pouvez avoir besoin des dépendances suivantes :

- krb5-libs
- libicu
- openssl-libs

Si la version OpenSSL de l’environnement d’exécution cible est 1,1 ou une version plus récente, vous devez installer **compat-openssl10**.

### <a name="deb-dependencies"></a>Dépendances DEB

Si votre distribution n’a pas été précédemment listée et est basée sur Debian, vous pouvez avoir besoin des dépendances suivantes :

- libc6
- libgcc1
- libgssapi-krb5-2
- libicu67
- libssl 1.1
- libstdc + + 6
- zlib1g

### <a name="common-dependencies"></a>Dépendances courantes

Pour les applications .NET qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :

- [libgdiplus (version 6.0.1 ou ultérieure)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système. Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.

## <a name="scripted-install"></a>Installation par script

Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du **Kit de développement logiciel (SDK)** et du **Runtime**. Vous pouvez télécharger le script depuis <https://dot.net/v1/dotnet-install.sh>.

Par défaut, le script installe la version la plus récente du kit de développement logiciel [(SDK) LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1. Pour installer la version actuelle, qui ne peut pas être une version (LTS), utilisez le `-c Current` paramètre.

```bash
./dotnet-install.sh -c Current
```

Pour installer le Runtime .NET au lieu du kit de développement logiciel (SDK), utilisez le `--runtime` paramètre.

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

Vous pouvez installer une version spécifique en modifiant le `-c` paramètre pour indiquer la version spécifique. La commande suivante installe le kit de développement logiciel (SDK) .NET 5,0.

```bash
./dotnet-install.sh -c 5.0
```

Pour plus d’informations, consultez informations de référence sur les [scripts dotnet-install](../tools/dotnet-install-script.md).

## <a name="manual-install"></a>Installation manuelle

<!-- Note, this content is copied in macos.md. Any fixes should be applied there too, though content may be different -->

Comme alternative aux gestionnaires de packages, vous pouvez télécharger et installer manuellement le kit de développement logiciel (SDK) et le Runtime. L’installation manuelle est couramment utilisée dans le cadre du test d’intégration continue ou sur une distribution Linux non prise en charge. Pour un développeur ou un utilisateur, il est préférable d’utiliser un gestionnaire de package.

Si vous installez le kit de développement logiciel (SDK) .NET, vous n’avez pas besoin d’installer le runtime correspondant. Tout d’abord, téléchargez une version **binaire** pour le kit de développement logiciel (SDK) ou le runtime à partir de l’un des sites suivants :

- [téléchargements .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0) ✔️
- ✔️ [téléchargements .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [téléchargements .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Tous les téléchargements .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

Ensuite, extrayez le fichier téléchargé et utilisez la `export` commande pour définir les variables utilisées par .net, puis vérifiez que .net est dans le chemin d’accès.

Pour extraire le runtime et rendre les commandes de l’interface de commande .NET CLI disponibles sur le terminal, commencez par télécharger une version binaire .NET. Ensuite, ouvrez un terminal et exécutez les commandes suivantes à partir du répertoire dans lequel le fichier a été enregistré. Le nom du fichier d’archive peut être différent en fonction de ce que vous avez téléchargé.

**Utilisez la commande suivante pour extraire le runtime**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**Utilisez la commande suivante pour extraire le kit de développement logiciel (SDK)**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Les `export` commandes précédentes rendent uniquement les commandes de l’interface de commande .net CLI disponibles pour la session Terminal dans laquelle elle a été exécutée.
>
> Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes. Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent. Par exemple :
>
> - **Interpréteur** de commandes bash : *~/.bash_profile*, *~ fichier/.bashrc*
> - **Shell Korn**: *~/.kshrc* ou *. Profile*
> - **Z Shell**: *~/.zshrc* ou *. zprofile*
>
> Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l' `PATH` instruction existante. Si aucune `PATH` instruction n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet` .
>
> Ajoutez également `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.

Cette approche vous permet d’installer différentes versions dans des emplacements distincts et de choisir explicitement celle qui doit être utilisée par l’application.

## <a name="next-steps"></a>Étapes suivantes

- [Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI](../tools/enable-tab-autocomplete.md)
- [Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code](../tutorials/with-visual-studio-code.md)
