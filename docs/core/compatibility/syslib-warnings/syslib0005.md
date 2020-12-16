---
title: AVERTISSEMENT SYSLIB0005
description: En savoir plus sur le obsoletion qui génère des SYSLIB0005 d’avertissement au moment de la compilation.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 1263a4d327c735268f77ed56bdcea6a4cbed4bfa
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596527"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a><span data-ttu-id="584d8-103">SYSLIB0005 : le Global Assembly Cache (GAC) n’est pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="584d8-103">SYSLIB0005: The global assembly cache (GAC) is not supported</span></span>

<span data-ttu-id="584d8-104">.NET Core et .NET 5,0 et versions ultérieures éliminent le concept de Global Assembly Cache (GAC) qui était présent dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="584d8-104">.NET Core and .NET 5.0 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="584d8-105">Pour aider les développeurs à s’éloigner de ces API, certaines API associées au GAC sont marquées comme obsolètes, à partir de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="584d8-105">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="584d8-106">L’utilisation de ces API génère un avertissement `SYSLIB0005` au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="584d8-106">Using these APIs generates warning `SYSLIB0005` at compile time.</span></span>

<span data-ttu-id="584d8-107">Les API associées au GAC suivantes sont marquées comme obsolètes :</span><span class="sxs-lookup"><span data-stu-id="584d8-107">The following GAC-related APIs are marked obsolete:</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  <span data-ttu-id="584d8-108">Les bibliothèques et les applications ne doivent pas utiliser l' <xref:System.Reflection.Assembly.GlobalAssemblyCache> API pour effectuer des déterminations sur le comportement au moment de l’exécution, car elles sont toujours renvoyées `false` dans .net Core et .net 5 +.</span><span class="sxs-lookup"><span data-stu-id="584d8-108">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5+.</span></span>

## <a name="workarounds"></a><span data-ttu-id="584d8-109">Solutions de contournement</span><span class="sxs-lookup"><span data-stu-id="584d8-109">Workarounds</span></span>

<span data-ttu-id="584d8-110">Si votre application interroge la <xref:System.Reflection.Assembly.GlobalAssemblyCache> propriété, envisagez de supprimer l’appel.</span><span class="sxs-lookup"><span data-stu-id="584d8-110">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="584d8-111">Si vous utilisez la <xref:System.Reflection.Assembly.GlobalAssemblyCache> valeur pour choisir entre un « assembly dans le GAC » et un « assembly qui n’est pas dans le GAC » au moment de l’exécution, reconsidérez si le workflow a toujours un sens pour une application .net 5 +.</span><span class="sxs-lookup"><span data-stu-id="584d8-111">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET 5+ application.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="584d8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="584d8-112">See also</span></span>

- [<span data-ttu-id="584d8-113">Global assembly cache</span><span class="sxs-lookup"><span data-stu-id="584d8-113">Global assembly cache</span></span>](../../../framework/app-domains/gac.md)
