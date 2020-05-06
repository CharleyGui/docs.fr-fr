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
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="2b70f-103">Outils facilitant le portage vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="2b70f-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="2b70f-104">Les outils présentés dans cet article peuvent vous être utiles dans le cadre d’un portage :</span><span class="sxs-lookup"><span data-stu-id="2b70f-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="2b70f-105">[Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md) -chaîne d’outils qui peut générer un rapport sur la portabilité de votre code entre .NET Framework et .net Core :</span><span class="sxs-lookup"><span data-stu-id="2b70f-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="2b70f-106">En tant qu' [outil en ligne de commande](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="2b70f-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="2b70f-107">En tant qu' [extension Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span><span class="sxs-lookup"><span data-stu-id="2b70f-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="2b70f-108">[.NET API Analyzer](../../standard/analyzers/api-analyzer.md) : analyseur Roslyn qui découvre les risques potentiels liés à la compatibilité des API C# sur différentes plateformes et détecte les appels aux API dépréciées.</span><span class="sxs-lookup"><span data-stu-id="2b70f-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>
- <span data-ttu-id="2b70f-109">[essayez-Convert](https://www.nuget.org/packages/try-convert/) -un outil Global .net core qui peut convertir un projet ou une solution complète en kit de développement logiciel (SDK) .net, y compris le déplacement d’applications de bureau vers .net core.</span><span class="sxs-lookup"><span data-stu-id="2b70f-109">[try-convert](https://www.nuget.org/packages/try-convert/) - A .NET Core global tool that can convert a project or entire solution to the .NET SDK, including moving desktop apps to .NET Core.</span></span> <span data-ttu-id="2b70f-110">Cela n’est pas recommandé si vous avez une build plus compliquée établie (par exemple, des tâches personnalisées, des cibles ou des importations) et qu’elle rejette de nombreux types de projets qui ne sont pas compatibles avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b70f-110">It is not recommended if you have a more complicated build established (such as custom tasks, targets, or imports), and it rejects many project types that are incompatible with .NET Core.</span></span>
