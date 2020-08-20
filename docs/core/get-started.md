---
title: Bien démarrer avec .NET Core
description: Trouvez des ressources pour apprendre à créer des applications .NET Core sur Windows, Linux et macOS.
author: adegeo
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 56eebc0fc5bad6f57d93358cbbef389d6355d66b
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656688"
---
# <a name="get-started-with-net-core"></a>Bien démarrer avec .NET Core

Cet article fournit des informations pour bien démarrer avec .NET Core. .NET Core peut être installé sur Windows, Linux et macOS. Vous pouvez coder dans l’éditeur de texte de votre choix et produire des bibliothèques et des applications multiplateformes.

Si vous n’êtes pas certain du .NET Core ou de son lien avec d’autres technologies .NET, commencez par la vue d’ensemble de [.net](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) . Pour schématiser, .NET Core est une implémentation open source multiplateforme de .NET.

## <a name="create-an-application"></a>Créer une application

Tout d’abord, téléchargez et installez le [kit SDK .NET Core](https://dotnet.microsoft.com/download) sur votre ordinateur.

Ensuite, ouvrez un terminal tel que **PowerShell**, une **invite de commandes** ou **Bash**. Entrez les `dotnet` commandes suivantes pour créer et exécuter une application C# :

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

La sortie suivante s’affiche :

```console
Hello World!
```

Félicitations ! Vous avez créé une application .NET Core simple. Vous pouvez aussi utiliser [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows uniquement) ou [Visual Studio pour Mac](tutorials/with-visual-studio-mac.md) (macOS uniquement) pour créer une application .NET Core.

## <a name="tutorials"></a>Tutoriels

Commencez à développer des applications .NET Core en suivant ces didacticiels pas à pas :

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

- [Créer votre première application de console .NET Core dans Visual Studio 2019](./tutorials/with-visual-studio.md)
- [Créer une bibliothèque de classes avec .NET Standard dans Visual Studio](./tutorials/library-with-visual-studio.md)
- [Didacticiel : créer une application console .NET Core à l’aide de Visual Studio Code](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo") | Regardez la vidéo sur l' [installation et l’utilisation de Visual Studio code et](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) de la vidéo .net Core sur Channel 9. |
| ![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo") | Regardez les vidéos [.net Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) sur YouTube. |

Pour obtenir la liste des versions de Windows prises en charge, consultez l’article sur les [dépendances et les exigences de .net Core](install/dependencies.md?pivots=os-windows) .

# <a name="linux"></a>[Linux](#tab/linux)

Commencez à développer des applications .NET Core en suivant ces didacticiels pas à pas :

- [Didacticiel : créer une application console .NET Core à l’aide de Visual Studio Code](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo") | Visionnez une vidéo qui explique comment [bien démarrer avec Visual Studio Code en utilisant C# et .NET Core sur Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu). |

Pour obtenir la liste des versions et distributions Linux prises en charge, consultez l’article [dépendances et exigences de .net Core](install/dependencies.md?pivots=os-linux) .

# <a name="macos"></a>[macOS](#tab/macos)

Commencez à développer des applications .NET Core en suivant ces didacticiels pas à pas :

- [Didacticiel : créer une application console .NET Core à l’aide de Visual Studio Code](tutorials/with-visual-studio-code.md)
- [Didacticiel : créer une application console .NET Core à l’aide de Visual Studio pour Mac](tutorials/with-visual-studio-mac.md)
- [Créer une bibliothèque de .NET Standard sur macOS à l’aide de Visual Studio pour Mac](tutorials/library-with-visual-studio-mac.md)

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](media/video-icon.png "Regarder une vidéo") | Regardez une vidéo sur la prise en main de [Visual Studio code à l’aide de C# et de .net Core sur MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac). |

Pour obtenir la liste des versions OS X/macOS prises en charge, consultez l’article [dépendances et exigences .net Core](install/dependencies.md?pivots=os-macos) .

---
