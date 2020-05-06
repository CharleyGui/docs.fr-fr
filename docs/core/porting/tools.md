---
title: Outils de portage vers .NET Core
description: Découvrez certains des outils que vous pouvez utiliser pour effectuer un portage vers .NET Core
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: d0cf0abf206950beb34556ca3ba7243d8cad241e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795584"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>Outils facilitant le portage vers .NET Core

Les outils présentés dans cet article peuvent vous être utiles dans le cadre d’un portage :

- [Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md) -chaîne d’outils qui peut générer un rapport sur la portabilité de votre code entre .NET Framework et .net Core :
  - En tant qu' [outil en ligne de commande](https://github.com/Microsoft/dotnet-apiport/releases)
  - En tant qu' [extension Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [.NET API Analyzer](../../standard/analyzers/api-analyzer.md) : analyseur Roslyn qui découvre les risques potentiels liés à la compatibilité des API C# sur différentes plateformes et détecte les appels aux API dépréciées.
- [essayez-Convert](https://www.nuget.org/packages/try-convert/) -un outil Global .net core qui peut convertir un projet ou une solution complète en kit de développement logiciel (SDK) .net, y compris le déplacement d’applications de bureau vers .net core. Cela n’est pas recommandé si vous avez une build plus compliquée établie (par exemple, des tâches personnalisées, des cibles ou des importations) et qu’elle rejette de nombreux types de projets qui ne sont pas compatibles avec .NET Core.
