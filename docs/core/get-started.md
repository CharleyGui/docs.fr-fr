---
title: Bien démarrer avec .NET Core
description: Trouvez des ressources pour apprendre à créer des applications .NET Core sur Windows, Linux et macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714396"
---
# <a name="get-started-with-net-core"></a>Bien démarrer avec .NET Core

Cet article fournit des informations pour bien démarrer avec .NET Core. .NET Core peut être installé sur Windows, Linux et macOS. Vous pouvez coder dans l’éditeur de texte de votre choix et produire des bibliothèques et des applications multiplateformes.

Si vous ne savez pas réellement à quoi sert .NET Core ou comment ce produit s’articule avec les autres technologies .NET, commencez par consulter l’article de présentation [Qu’est-ce que .NET ?](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet). Pour schématiser, .NET Core est une implémentation open source multiplateforme de .NET.

## <a name="create-an-application"></a>Créer une application

Tout d’abord, téléchargez et installez le [kit SDK .NET Core](https://dotnet.microsoft.com/download) sur votre ordinateur.

Ensuite, ouvrez un terminal tel que **PowerShell**, une **invite de commandes** ou **Bash**. Tapez `dotnet` les commandes suivantes pour créer et exécuter une application CMD :

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Vous devez normalement voir la sortie suivante.

```console
Hello World!
```

Félicitations ! Vous avez créé une application .NET Core simple. Vous pouvez aussi utiliser [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows uniquement) ou [Visual Studio pour Mac](./tutorials/using-on-mac-vs.md) (macOS uniquement) pour créer une application .NET Core.

## <a name="tutorials"></a>Tutoriels

Commencer à développer des applications .NET Core en suivant ces tutoriels étape par étape:

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

- [Créez votre première application console .NET Core dans Visual Studio 2019](./tutorials/with-visual-studio.md)
- [Construire une bibliothèque de classe avec .NET Standard en Visual Studio](./tutorials/library-with-visual-studio.md)
- [Démarrer avec .NET Core en utilisant le CLI .NET Core](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo") | Regardez comment [installer et utiliser Visual Studio Code et .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) vidéo sur Channel 9. |
| ![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo") | Regardez les vidéos [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) sur YouTube. |

Consultez l’article [.NET Core sur les dépendances et les exigences pour](install/dependencies.md?pivots=os-windows) une liste des versions Windows prises en charge.

# <a name="linux"></a>[Linux](#tab/linux)

Commencer à développer des applications .NET Core en suivant ces tutoriels étape par étape:

- [Démarrer avec .NET Core en utilisant la ligne de commande](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo") | Visionnez une vidéo qui explique comment [bien démarrer avec Visual Studio Code en utilisant C# et .NET Core sur Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu). |

Voir l’article [.NET Core dépendances et exigences](install/dependencies.md?pivots=os-linux) pour une liste des distros linux pris en charge et les versions.

# <a name="macos"></a>[macOS](#tab/macos)

Commencer à développer des applications .NET Core en suivant ces tutoriels étape par étape:

- [Bien démarrer avec .NET Core sur macOS en utilisant Visual Studio Code](./tutorials/using-on-macos.md)
- [Démarrer avec .NET Core en utilisant la ligne de commande](./tutorials/cli-create-console-app.md)
- [Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac](./tutorials/using-on-mac-vs.md)
- [Construire une solution complète .NET Core sur macOS à l’aide de Visual Studio pour Mac](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](media/video-icon.png "Regarder une vidéo") | Regardez une vidéo sur [le démarrage avec Visual Studio Code à l’aide de C et .NET Core sur macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac). |

Voir l’article [.NET Core dépendances et exigences](install/dependencies.md?pivots=os-macos) pour une liste des versions OS X / macOS prises en charge.

---
