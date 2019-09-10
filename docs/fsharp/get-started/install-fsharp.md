---
title: Installer F#
description: Découvrez comment installer F# en fonction de votre environnement.
ms.date: 09/05/2019
ms.openlocfilehash: dffa30eac0bdb59c85a66dca6cafd62b25daa572
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855805"
---
# <a name="install-f"></a>Installer F\#

Vous pouvez installer F# de plusieurs façons, en fonction de votre environnement.

## <a name="install-f-with-visual-studio"></a>Installer F# avec Visual Studio

Si vous téléchargez [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) pour la première fois, le programme d’installation de Visual Studio est tout d’abord installé. Installez la référence SKU appropriée de Visual Studio à partir du programme d’installation. Si vous l’avez déjà installé, cliquez sur **modifier**.

Vous verrez ensuite une liste de charges de travail. Sélectionnez **ASP.net et développement Web** pour installer F# la prise en charge et la prise en charge de .net Core pour les projets ASP.net core.

Ensuite, cliquez sur **modifier** dans la partie inférieure droite.  Cela permet d’installer tout ce que vous avez sélectionné. Vous pouvez ensuite ouvrir Visual Studio 2017 avec F# prise en charge des langues en cliquant sur **lancer**.

## <a name="install-f-with-visual-studio-for-mac"></a>Installer F# avec Visual Studio pour Mac

F#est installé par défaut dans [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), quelle que soit la configuration choisie.

Une fois l’installation terminée, choisissez « démarrer Visual Studio ». Vous pouvez également le lancer par le biais de Finder sur macOS.

## <a name="install-f-with-visual-studio-code"></a>Installer F# avec Visual Studio code

Git doit être [installé](https://git-scm.com/download) et disponible sur votre chemin d’accès pour pouvoir utiliser les modèles de projet. Vous pouvez vérifier qu’il est correctement installé en tapant `git --version` à l’invite de commandes et en appuyant sur **entrée**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Mono](https://www.mono-project.com) est utilisé pour [ F# ](../tutorials/fsharp-interactive/index.md) la prise en charge interactive. Le moyen le plus simple d’installer mono sur macOS est d’utiliser homebrew. Il vous suffit de taper ce qui suit dans votre terminal :

```console
brew install mono
```

Installez également le [Kit SDK .net Core](https://dotnet.microsoft.com/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Mono](https://www.mono-project.com) est utilisé pour [ F# ](../tutorials/fsharp-interactive/index.md) la prise en charge interactive. Si vous utilisez Debian ou Ubuntu, vous pouvez utiliser les éléments suivants :

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Installez également le [Kit SDK .net Core](https://dotnet.microsoft.com/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Installez [Visual Studio avec F# la prise en charge](#install-f-with-visual-studio). Cela installe tous les composants nécessaires pour écrire, compiler et exécuter F# du code.

Installez également le [Kit SDK .net Core](https://dotnet.microsoft.com/download).

---

Vous devez ensuite [Visual Studio code](https://code.visualstudio.com) installé.

Ensuite, cliquez sur l’icône extensions et recherchez « Ionide » :

Le seul plug-in F# requis pour la prise en charge de Visual Studio code est [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Toutefois, vous pouvez également installer [Ionide-factice](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) pour avoir une prise en charge [factice](https://fsharp.github.io/FAKE/) et [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pour bénéficier de la prise en charge d' [Paket](https://fsprojects.github.io/Paket/) . FACTICE et Paket sont des F# outils de la communauté supplémentaires pour la génération de projets et la gestion des dépendances, respectivement.

## <a name="install-f-on-a-build-server"></a>Installer F# sur un serveur de builds

Si vous utilisez .NET Core ou .NET Framework via le kit de développement logiciel (SDK) .NET, il vous suffit d’installer le kit de développement logiciel (SDK) .NET sur votre serveur de builds. C’est tout ce dont vous avez besoin.

Si vous utilisez .NET Framework et que vous n’utilisez **pas** le kit de développement logiciel (SDK) .net, vous devez installer la [référence SKU Visual Studio Build Tools](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) sur votre serveur Windows. Dans le programme d’installation, sélectionnez **outils de génération de bureaux .net** , puis sélectionnez le  **F# composant compilateur** sur le côté droit du menu installer.
