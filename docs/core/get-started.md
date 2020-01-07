---
title: Bien démarrer avec .NET Core
description: Trouvez des ressources pour apprendre à créer des applications .NET Core sur Windows, Linux et macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bcf9ea0bb9a8346284c49060786afefa0f77745e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341391"
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

Félicitations ! Vous avez créé une application .NET Core simple. Vous pouvez aussi utiliser [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows uniquement) ou [Visual Studio pour Mac](./tutorials/using-on-mac-vs.md) (macOS uniquement) pour créer une application .NET Core.

## <a name="tutorials"></a>Didacticiels

Commencez à développer des applications .NET Core en suivant ces didacticiels pas à pas :

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Fenêtres](#tab/windows)

- [Créer votre première application de console .NET Core dans Visual Studio 2019](./tutorials/with-visual-studio.md)
- [Créer une bibliothèque de classes avec .NET Standard dans Visual Studio](./tutorials/library-with-visual-studio.md)
- [Prise en main de .NET Core à l’aide de l’CLI .NET Core](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regardez une vidéo") | Regardez la vidéo sur l' [installation et l’utilisation de Visual Studio code et](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) de la vidéo .net Core sur Channel 9. |
| ![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regardez une vidéo") | Regardez les vidéos [.net Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) sur YouTube. |

Pour obtenir la liste des versions de Windows prises en charge, consultez l’article sur les [dépendances et les exigences de .net Core](install/dependencies.md?tabs=netcore30&pivots=os-windows) .

Pour obtenir la liste des versions de Windows prises en charge, consultez l’article [dépendances du kit SDK .net Core et du runtime](install/dependencies.md?pivots=os-windows) .

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Commencez à développer des applications .NET Core en suivant ces didacticiels pas à pas :

- [Prise en main de .NET Core à l’aide de la ligne de commande](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regardez une vidéo") | Visionnez une vidéo qui explique comment [bien démarrer avec Visual Studio Code en utilisant C# et .NET Core sur Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu). |

Pour obtenir la liste des versions et distributions Linux prises en charge, consultez l’article [dépendances du kit SDK .net Core et du runtime](install/dependencies.md?pivots=os-linux) .

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Commencez à développer des applications .NET Core en suivant ces didacticiels pas à pas :

- [Prise en main de .NET Core sur macOS à l’aide de Visual Studio Code](./tutorials/using-on-macos.md)
- [Prise en main de .NET Core à l’aide de la ligne de commande](./tutorials/cli-create-console-app.md)
- [Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac](./tutorials/using-on-mac-vs.md)
- [Créez une solution .NET Core complète sur macOS à l’aide de Visual Studio pour Mac](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| ![Icône représentant une caméra pour les vidéos](media/video-icon.png "Regardez une vidéo") | Regardez une vidéo sur la prise en main de [Visual Studio code à l’aide C# de et de .net Core sur MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac). |

Pour obtenir la liste des versions OS X/macOS prises en charge, consultez l’article [dépendances du kit SDK .net Core et du runtime](install/dependencies.md?pivots=os-macos) .

---
