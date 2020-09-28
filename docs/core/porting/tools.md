---
title: Outils de portage vers .NET Core
description: Découvrez certains des outils que vous pouvez utiliser pour effectuer un portage vers .NET Core
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: b8678ec72fe5d910d5f8cff4768106e7496f9276
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406126"
---
# <a name="tools-to-help-with-porting-to-net-core"></a>Outils facilitant le portage vers .NET Core

Les outils présentés dans cet article peuvent vous être utiles dans le cadre d’un portage :

- [Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md) -chaîne d’outils qui peut générer un rapport sur la portabilité de votre code entre .NET Framework et .net Core :
  - En tant qu' [outil en ligne de commande](https://github.com/Microsoft/dotnet-apiport/releases)
  - En tant qu' [extension Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Platform Compatibility Analyzer](../../standard/analyzers/platform-compat-analyzer.md) : analyseur de Roslyn qui informe les développeurs lorsqu’ils utilisent des API spécifiques à la plateforme à partir de sites d’appel où l’API n’est peut-être pas disponible.
- [Analyseur d’API .net](../../standard/analyzers/api-analyzer.md) : analyseur Roslyn qui peut aider à détecter les problèmes de compatibilité de plateforme dans les applications et les bibliothèques multiplateforme.
- [essayez-Convert](https://www.nuget.org/packages/try-convert/) -un outil Global .net core qui peut convertir un projet ou une solution complète en kit de développement logiciel (SDK) .net, y compris le déplacement d’applications de bureau vers .net core. Cela n’est pas recommandé si vous avez une build plus compliquée établie (par exemple, des tâches personnalisées, des cibles ou des importations) et qu’elle rejette de nombreux types de projets qui ne sont pas compatibles avec .NET Core.
