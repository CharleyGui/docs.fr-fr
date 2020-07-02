---
ms.openlocfilehash: 4a65e721e5639f12445a9a44f46baa0d26898a88
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615676"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="d6628-101">Instruction IL ret non autorisée dans une zone try</span><span class="sxs-lookup"><span data-stu-id="d6628-101">IL ret not allowed in a try region</span></span>

#### <a name="details"></a><span data-ttu-id="d6628-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d6628-102">Details</span></span>

<span data-ttu-id="d6628-103">À la différence du compilateur juste-à-temps JIT 64 bits, RyuJIT (utilisé dans .NET Framework 4.6) n’autorise pas une instruction IL ret dans une zone try.</span><span class="sxs-lookup"><span data-stu-id="d6628-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="d6628-104">Le retour à partir d’une zone try n’est pas autorisé par la spécification ECMA-335. Par ailleurs, aucun compilateur managé connu ne génère ce type de code IL.</span><span class="sxs-lookup"><span data-stu-id="d6628-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="d6628-105">Toutefois, le compilateur JIT64 exécute ce code IL, s'il est généré à l'aide de l'émission de réflexion.</span><span class="sxs-lookup"><span data-stu-id="d6628-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d6628-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d6628-106">Suggestion</span></span>

<span data-ttu-id="d6628-107">Si une application génère du code IL qui inclut un opcode ret dans une zone try, l’application peut cibler .NET Framework 4.5 pour utiliser l’ancien JIT et éviter cette interruption de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d6628-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="d6628-108">Il est également possible de mettre à jour le code IL généré pour qu’il soit retourné après la zone try.</span><span class="sxs-lookup"><span data-stu-id="d6628-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>

| <span data-ttu-id="d6628-109">Nom</span><span class="sxs-lookup"><span data-stu-id="d6628-109">Name</span></span>    | <span data-ttu-id="d6628-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="d6628-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d6628-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="d6628-111">Scope</span></span>   | <span data-ttu-id="d6628-112">Edge</span><span class="sxs-lookup"><span data-stu-id="d6628-112">Edge</span></span>        |
| <span data-ttu-id="d6628-113">Version</span><span class="sxs-lookup"><span data-stu-id="d6628-113">Version</span></span> | <span data-ttu-id="d6628-114">4.6</span><span class="sxs-lookup"><span data-stu-id="d6628-114">4.6</span></span>         |
| <span data-ttu-id="d6628-115">Type</span><span class="sxs-lookup"><span data-stu-id="d6628-115">Type</span></span>    | <span data-ttu-id="d6628-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="d6628-116">Retargeting</span></span> |
