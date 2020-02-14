---
title: Outils de portage vers .NET Core
description: Découvrez certains des outils que vous pouvez utiliser pour effectuer un portage vers .NET Core
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 3b71c31b4f26b278b2bd1088adc8e9f64d28ab7b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215193"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="6d49d-103">Outils facilitant le portage vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="6d49d-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="6d49d-104">Les outils présentés dans cet article peuvent vous être utiles dans le cadre d’un portage :</span><span class="sxs-lookup"><span data-stu-id="6d49d-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="6d49d-105">[Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md) -chaîne d’outils qui peut générer un rapport sur la portabilité de votre code entre .NET Framework et .net Core :</span><span class="sxs-lookup"><span data-stu-id="6d49d-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="6d49d-106">En tant qu' [outil en ligne de commande](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="6d49d-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="6d49d-107">En tant qu' [extension Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span><span class="sxs-lookup"><span data-stu-id="6d49d-107">As a [Visual Studio extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
- <span data-ttu-id="6d49d-108">[.NET API Analyzer](../../standard/analyzers/api-analyzer.md) : analyseur Roslyn qui découvre les risques potentiels liés à la compatibilité des API C# sur différentes plateformes et détecte les appels aux API dépréciées.</span><span class="sxs-lookup"><span data-stu-id="6d49d-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="6d49d-109">En outre, vous pouvez essayer de porter des solutions plus petites ou des projets individuels au format de fichier de projet .NET Core avec l’outil [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017).</span><span class="sxs-lookup"><span data-stu-id="6d49d-109">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING] 
> <span data-ttu-id="6d49d-110">CsprojToVs2017 est un outil tiers.</span><span class="sxs-lookup"><span data-stu-id="6d49d-110">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="6d49d-111">Il n’existe aucune garantie que cet outil fonctionne pour tous vos projets, et il peut entraîner de légères modifications du comportement dont vous dépendez.</span><span class="sxs-lookup"><span data-stu-id="6d49d-111">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="6d49d-112">CsprojToVs2017 doit être utilisé comme un _point de départ_ qui automatise les tâches de base pouvant être automatisées.</span><span class="sxs-lookup"><span data-stu-id="6d49d-112">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="6d49d-113">Ce n’est pas une solution garantie pour la migration de formats de fichiers projet.</span><span class="sxs-lookup"><span data-stu-id="6d49d-113">It is not a guaranteed solution to migrating project file formats.</span></span>
