---
title: Prise en main de .NET
description: Créer une application Hello World .NET.
author: adegeo
ms.author: adegeo
ms.date: 09/29/2020
ms.custom: vs-dotnet
ms.openlocfilehash: 6ad2b96e668c52ee80b707e31a63eac2433f3c9e
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756089"
---
# <a name="get-started-with-net"></a>Prise en main de .NET

Cet article explique comment créer et exécuter un « Hello World ! » Application .NET.

Si vous n’êtes pas sûr de .NET, commencez par la [présentation .net](introduction.md).

## <a name="create-an-application"></a>Créer une application

Tout d’abord, téléchargez et installez le [Kit de développement logiciel (SDK) .net](https://dotnet.microsoft.com/download/dotnet-core) sur votre ordinateur.

Ensuite, ouvrez un terminal tel que **PowerShell**, une **invite de commandes** ou **Bash**. Entrez les `dotnet` commandes suivantes pour créer et exécuter une application C# :

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

La sortie suivante s’affiche :

```output
Hello World!
```

Félicitations ! Vous avez créé une application .NET simple.

## <a name="next-steps"></a>Étapes suivantes

Commencez à développer des applications .NET en suivant un [didacticiel pas à pas](../standard/get-started.md) ou en regardant les [vidéos .net 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) sur YouTube.
