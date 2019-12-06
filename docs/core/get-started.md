---
title: Bien démarrer avec .NET Core
description: Découvrez des ressources qui vous apprendront à créer des applications .NET Core sur Windows, Linux et macOS.
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 89db6d79336c01315983133d9041904d88cba301
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884252"
---
# <a name="get-started-with-net-core"></a>Bien démarrer avec .NET Core

Cet article fournit des informations pour bien démarrer avec .NET Core. .NET Core peut être installé sur Windows, Linux et macOS. Vous pouvez coder dans l’éditeur de texte de votre choix et produire des bibliothèques et des applications multiplateformes. 

Si vous ne savez pas réellement à quoi sert .NET Core ou comment ce produit s’articule avec les autres technologies .NET, commencez par consulter l’article de présentation [Qu’est-ce que .NET ?](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet). Pour schématiser, .NET Core est une implémentation open source multiplateforme de .NET.

## <a name="create-an-application"></a>Créer une application

Tout d’abord, téléchargez et installez le [kit SDK .NET Core](https://dotnet.microsoft.com/download) sur votre ordinateur.

Ensuite, ouvrez un terminal tel que **PowerShell**, une **invite de commandes** ou **Bash**. Tapez les commandes de `dotnet` suivantes pour créer et exécuter C# une application :

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Vous devez voir la sortie suivante :

```console
Hello World!
```

Félicitations ! Vous avez créé une application .NET Core simple. Vous pouvez aussi utiliser [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows uniquement) ou [Visual Studio pour Mac](tutorials/using-on-mac-vs.md) (macOS uniquement) pour créer une application .NET Core.

## <a name="tutorials"></a>Didacticiels

Vous pouvez commencer à développer des applications .NET Core en suivant ces tutoriels pas à pas.

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Fenêtres](#tab/windows)

- [Générer une application C# « Hello World » avec .NET Core dans Visual Studio 2017.](./tutorials/with-visual-studio.md)
- [Générer une bibliothèque de classes C# avec .NET Core dans Visual Studio 2017.](./tutorials/library-with-visual-studio.md)
- [Générer une application Visual Basic « Hello World » avec .NET Core dans Visual Studio 2017.](./tutorials/vb-with-visual-studio.md)
- [Générer une bibliothèque de classes avec Visual Basic et .NET Core dans Visual Studio 2017.](./tutorials/vb-library-with-visual-studio.md)  
- Visionnez une vidéo qui indique [comment installer et utiliser Visual Studio Code et .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).
- Visionnez une vidéo qui indique [comment installer et utiliser Visual Studio 2017 et .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).
- [Bien démarrer avec .NET Core en utilisant la ligne de commande.](tutorials/cli-create-console-app.md)

Pour obtenir la liste des versions de Windows prises en charge, consultez l’article sur les [dépendances et les exigences de .net Core](install/dependencies.md?tabs=netcore30&pivots=os-windows) .

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Vous pouvez commencer à développer une application .NET Core en suivant ces didacticiels pas à pas :

- [Bien démarrer avec .NET Core en utilisant la ligne de commande.](tutorials/cli-create-console-app.md)
- Visionnez une vidéo qui explique comment [bien démarrer avec Visual Studio Code en utilisant C# et .NET Core sur Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

Pour obtenir la liste des versions et distributions Linux prises en charge, consultez l’article [dépendances et exigences de .net Core](install/dependencies.md?tabs=netcore30&pivots=os-linux) .

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Vous pouvez commencer à développer une application .NET Core en suivant ces didacticiels pas à pas :

- Visionnez une vidéo qui explique comment [bien démarrer avec Visual Studio Code en utilisant C# et .NET Core sur macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).
- [Bien démarrer avec .NET Core sur macOS en utilisant Visual Studio Code.](tutorials/using-on-macos.md)
- [Bien démarrer avec .NET Core en utilisant la ligne de commande.](tutorials/cli-create-console-app.md)
- [Bien démarrer avec .NET Core sur macOS en utilisant Visual Studio pour Mac.](tutorials/using-on-mac-vs.md)
- [Générer une solution .NET Core complète sur macOS en utilisant Visual Studio pour Mac.](tutorials/using-on-mac-vs-full-solution.md)

Pour obtenir la liste des versions OS X/macOS prises en charge, consultez l’article [dépendances et exigences .net Core](install/dependencies.md?tabs=netcore30&pivots=os-macos) .

---
