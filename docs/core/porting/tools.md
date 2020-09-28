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
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="b2181-103">Outils facilitant le portage vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2181-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="b2181-104">Les outils présentés dans cet article peuvent vous être utiles dans le cadre d’un portage :</span><span class="sxs-lookup"><span data-stu-id="b2181-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="b2181-105">[Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md) -chaîne d’outils qui peut générer un rapport sur la portabilité de votre code entre .NET Framework et .net Core :</span><span class="sxs-lookup"><span data-stu-id="b2181-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="b2181-106">En tant qu' [outil en ligne de commande](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="b2181-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="b2181-107">En tant qu' [extension Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span><span class="sxs-lookup"><span data-stu-id="b2181-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="b2181-108">[Platform Compatibility Analyzer](../../standard/analyzers/platform-compat-analyzer.md) : analyseur de Roslyn qui informe les développeurs lorsqu’ils utilisent des API spécifiques à la plateforme à partir de sites d’appel où l’API n’est peut-être pas disponible.</span><span class="sxs-lookup"><span data-stu-id="b2181-108">[Platform compatibility analyzer](../../standard/analyzers/platform-compat-analyzer.md) - A Roslyn analyzer that informs developers when they use platform-specific APIs from call sites where the API might not be available.</span></span>
- <span data-ttu-id="b2181-109">[Analyseur d’API .net](../../standard/analyzers/api-analyzer.md) : analyseur Roslyn qui peut aider à détecter les problèmes de compatibilité de plateforme dans les applications et les bibliothèques multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="b2181-109">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that can help detect platform compatibility issues in cross-platform apps and libraries.</span></span>
- <span data-ttu-id="b2181-110">[essayez-Convert](https://www.nuget.org/packages/try-convert/) -un outil Global .net core qui peut convertir un projet ou une solution complète en kit de développement logiciel (SDK) .net, y compris le déplacement d’applications de bureau vers .net core.</span><span class="sxs-lookup"><span data-stu-id="b2181-110">[try-convert](https://www.nuget.org/packages/try-convert/) - A .NET Core global tool that can convert a project or entire solution to the .NET SDK, including moving desktop apps to .NET Core.</span></span> <span data-ttu-id="b2181-111">Cela n’est pas recommandé si vous avez une build plus compliquée établie (par exemple, des tâches personnalisées, des cibles ou des importations) et qu’elle rejette de nombreux types de projets qui ne sont pas compatibles avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2181-111">It is not recommended if you have a more complicated build established (such as custom tasks, targets, or imports), and it rejects many project types that are incompatible with .NET Core.</span></span>
