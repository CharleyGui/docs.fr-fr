---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804486"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="2e6de-101">Instruction IL ret non autorisée dans une zone try</span><span class="sxs-lookup"><span data-stu-id="2e6de-101">IL ret not allowed in a try region</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2e6de-102">Détails</span><span class="sxs-lookup"><span data-stu-id="2e6de-102">Details</span></span>|<span data-ttu-id="2e6de-103">À la différence du compilateur juste-à-temps JIT 64 bits, RyuJIT (utilisé dans .NET Framework 4.6) n’autorise pas une instruction IL ret dans une zone try.</span><span class="sxs-lookup"><span data-stu-id="2e6de-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="2e6de-104">Le retour à partir d’une zone try n’est pas autorisé par la spécification ECMA-335. Par ailleurs, aucun compilateur managé connu ne génère ce type de code IL.</span><span class="sxs-lookup"><span data-stu-id="2e6de-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="2e6de-105">Toutefois, le compilateur JIT64 exécute ce code IL, s'il est généré à l'aide de l'émission de réflexion.</span><span class="sxs-lookup"><span data-stu-id="2e6de-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>|
|<span data-ttu-id="2e6de-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="2e6de-106">Suggestion</span></span>|<span data-ttu-id="2e6de-107">Si une application génère du code IL qui inclut un opcode ret dans une zone try, l’application peut cibler .NET Framework 4.5 pour utiliser l’ancien JIT et éviter cette interruption de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2e6de-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="2e6de-108">Il est également possible de mettre à jour le code IL généré pour qu’il soit retourné après la zone try.</span><span class="sxs-lookup"><span data-stu-id="2e6de-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>|
|<span data-ttu-id="2e6de-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="2e6de-109">Scope</span></span>|<span data-ttu-id="2e6de-110">Edge</span><span class="sxs-lookup"><span data-stu-id="2e6de-110">Edge</span></span>|
|<span data-ttu-id="2e6de-111">Version</span><span class="sxs-lookup"><span data-stu-id="2e6de-111">Version</span></span>|<span data-ttu-id="2e6de-112">4.6</span><span class="sxs-lookup"><span data-stu-id="2e6de-112">4.6</span></span>|
|<span data-ttu-id="2e6de-113">Type</span><span class="sxs-lookup"><span data-stu-id="2e6de-113">Type</span></span>|<span data-ttu-id="2e6de-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="2e6de-114">Retargeting</span></span>|
