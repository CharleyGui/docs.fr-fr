---
title: 'NETSDK1005 et NETSDK1047 : la cible est manquante dans le fichier d’élément multimédia'
description: La résolution du problème d’un fichier de ressources n’a pas de cible.
author: sfoslund
ms.topic: error-reference
ms.date: 12/17/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: e3e7389adf6a9a715d44661a5f7cbae5efe299e4
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678167"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="2c6e8-103">NETSDK1005 et NETSDK1047 : la cible est manquante dans le fichier d’élément multimédia</span><span class="sxs-lookup"><span data-stu-id="2c6e8-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="2c6e8-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 2.1.100 .net Core et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="2c6e8-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="2c6e8-105">Lorsque le kit de développement logiciel (SDK) .NET émet une erreur NETSDK1005 ou NETSDK1047, le fichier de ressources du projet ne contient pas d’informations sur l’un de vos frameworks cibles.</span><span class="sxs-lookup"><span data-stu-id="2c6e8-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="2c6e8-106">NuGet écrit un fichier nommé *project.assets.js* dans le dossier *obj* , et le kit de développement logiciel (SDK) .net l’utilise pour obtenir des informations sur les packages à passer au compilateur.</span><span class="sxs-lookup"><span data-stu-id="2c6e8-106">NuGet writes a file named *project.assets.json* in the *obj* folder, and the .NET SDK uses it to get information about packages to pass into the compiler.</span></span> <span data-ttu-id="2c6e8-107">Dans .NET 5, NuGet a ajouté un nouveau champ nommé `TargetFrameworkAlias` , de sorte que les versions antérieures de MSBuild ou NuGet génèrent un fichier de ressources sans le nouveau champ.</span><span class="sxs-lookup"><span data-stu-id="2c6e8-107">In .NET 5, NuGet added a new field named `TargetFrameworkAlias`, so earlier versions of MSBuild or NuGet generate an assets file without the new field.</span></span> <span data-ttu-id="2c6e8-108">Pour plus d’informations, consultez l' [erreur NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html).</span><span class="sxs-lookup"><span data-stu-id="2c6e8-108">For more information, see [error NETSDK1005](https://developercommunity.visualstudio.com/content/problem/1248649/error-netsdk1005-assets-file-projectassetsjson-doe.html).</span></span>

<span data-ttu-id="2c6e8-109">Voici quelques actions que vous pouvez effectuer, susceptibles de résoudre l’erreur :</span><span class="sxs-lookup"><span data-stu-id="2c6e8-109">Here are some actions you can take that may resolve the error:</span></span>

* <span data-ttu-id="2c6e8-110">Assurez-vous que vous utilisez MSBuild version 16,8 ou ultérieure et NuGet version 5,8 ou ultérieure, puis restaurez le projet après avoir mis à jour vos outils.</span><span class="sxs-lookup"><span data-stu-id="2c6e8-110">Make sure that you're using MSBuild version 16.8 or later and NuGet version 5.8 or later, and restore the project after updating your tools.</span></span> <span data-ttu-id="2c6e8-111">Lorsque vous utilisez NuGet version 5,8 ou ultérieure, vous devez utiliser Visual Studio 2019 version 16,8 ou ultérieure, MSBuild version 16,8 ou ultérieure et .NET 5,0 SDK ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="2c6e8-111">When you're using NuGet version 5.8 or later, you should be using Visual Studio 2019 version 16.8 or later, MSBuild version 16.8 or later, and .NET 5.0 SDK or later.</span></span>

* <span data-ttu-id="2c6e8-112">Si vous recevez l’erreur lors de la première génération d’un projet dans Visual Studio 2019 après l’installation de la version 16,8 ou après avoir modifié le Framework cible du projet, générez le projet une deuxième fois.</span><span class="sxs-lookup"><span data-stu-id="2c6e8-112">If you get the error while building a project in Visual Studio 2019 for the first time after installing version 16.8 or after changing the project's target framework, build the project a second time.</span></span>

* <span data-ttu-id="2c6e8-113">Supprimez le dossier *obj* avant de générer le projet.</span><span class="sxs-lookup"><span data-stu-id="2c6e8-113">Delete the *obj* folder before building the project.</span></span>

* <span data-ttu-id="2c6e8-114">Assurez-vous que la valeur cible manquante est incluse dans la `TargetFrameworks` propriété de votre projet.</span><span class="sxs-lookup"><span data-stu-id="2c6e8-114">Make sure that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>
