---
title: 'NETSDK1073 : FrameworkReference n’a pas été reconnu'
description: Comment résoudre le problème où le FrameworkReference est introuvable.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 2b2dbf2a0d3e13dca4fe634529b7951f2333ce28
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713026"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a><span data-ttu-id="28ca4-103">NETSDK1073 : FrameworkReference n’a pas été reconnu</span><span class="sxs-lookup"><span data-stu-id="28ca4-103">NETSDK1073: The FrameworkReference was not recognized</span></span>

<span data-ttu-id="28ca4-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 2.1.100 .net Core et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="28ca4-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="28ca4-105">Cette erreur signifie généralement qu’il existe une version d’un FrameworkReference particulier que le kit de développement logiciel (SDK) ne peut pas trouver.</span><span class="sxs-lookup"><span data-stu-id="28ca4-105">This error typically means there is a version of a particular FrameworkReference that the SDK cannot find.</span></span> <span data-ttu-id="28ca4-106">Essayez de supprimer vos dossiers *obj* et *bin* , puis exécutez `dotnet restore` pour retélécharger les derniers packs de ciblage.</span><span class="sxs-lookup"><span data-stu-id="28ca4-106">Try deleting your *obj* and *bin* folders and running `dotnet restore` to redownload the latest targeting packs.</span></span>

<span data-ttu-id="28ca4-107">Sinon, il peut y avoir un problème avec votre installation. Vérifiez donc que vous êtes dans les dernières versions de .NET et de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="28ca4-107">Alternatively, there could be an issue with your install, so ensure you're on the latest versions of .NET and Visual Studio</span></span>
