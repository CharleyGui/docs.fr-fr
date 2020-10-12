---
title: 'NETSDK1073 : FrameworkReference n’a pas été reconnu'
description: Comment résoudre le problème où le FrameworkReference est introuvable.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1073
ms.openlocfilehash: 59b5f63dcfe0115feabc2d87d24a09c6a650cc62
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957146"
---
# <a name="netsdk1073-the-frameworkreference-was-not-recognized"></a><span data-ttu-id="c5d88-103">NETSDK1073 : FrameworkReference n’a pas été reconnu</span><span class="sxs-lookup"><span data-stu-id="c5d88-103">NETSDK1073: The FrameworkReference was not recognized</span></span>

<span data-ttu-id="c5d88-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .NET 2.1.100 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="c5d88-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="c5d88-105">Cette erreur signifie généralement qu’il existe une version d’un FrameworkReference particulier que le kit de développement logiciel (SDK) ne peut pas trouver.</span><span class="sxs-lookup"><span data-stu-id="c5d88-105">This error typically means there is a version of a particular FrameworkReference that the SDK cannot find.</span></span> <span data-ttu-id="c5d88-106">Essayez de supprimer vos dossiers *obj* et *bin* , puis exécutez `dotnet restore` pour retélécharger les derniers packs de ciblage.</span><span class="sxs-lookup"><span data-stu-id="c5d88-106">Try deleting your *obj* and *bin* folders and running `dotnet restore` to redownload the latest targeting packs.</span></span>

<span data-ttu-id="c5d88-107">Sinon, il peut y avoir un problème avec votre installation. Vérifiez donc que vous êtes dans les dernières versions de .NET et de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5d88-107">Alternatively, there could be an issue with your install, so ensure you're on the latest versions of .NET and Visual Studio</span></span>
