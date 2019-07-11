---
title: DacpReJitData, structure
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 77ef2c65157df4a033700bb8d0295875ede46554
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739108"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="36ef7-102">DacpReJitData, structure</span><span class="sxs-lookup"><span data-stu-id="36ef7-102">DacpReJitData Structure</span></span>

<span data-ttu-id="36ef7-103">Définit les informations de base sur une méthode donnée instrumentée du profileur.</span><span class="sxs-lookup"><span data-stu-id="36ef7-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="36ef7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36ef7-104">Syntax</span></span>

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a><span data-ttu-id="36ef7-105">Membres</span><span class="sxs-lookup"><span data-stu-id="36ef7-105">Members</span></span>

| <span data-ttu-id="36ef7-106">Membre</span><span class="sxs-lookup"><span data-stu-id="36ef7-106">Member</span></span>           | <span data-ttu-id="36ef7-107">Description</span><span class="sxs-lookup"><span data-stu-id="36ef7-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="36ef7-108">Le numéro de révision ReJit pour une méthode.</span><span class="sxs-lookup"><span data-stu-id="36ef7-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="36ef7-109">Un indicateur qui spécifie l’état actuel de l’instrumentation ReJit de la méthode pour la version donnée.</span><span class="sxs-lookup"><span data-stu-id="36ef7-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="36ef7-110">L’adresse de base d’implémentation de rejitted de la méthode.</span><span class="sxs-lookup"><span data-stu-id="36ef7-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="36ef7-111">Notes</span><span class="sxs-lookup"><span data-stu-id="36ef7-111">Remarks</span></span>

<span data-ttu-id="36ef7-112">Cette structure se trouve au sein du runtime et n’est pas exposée par le biais d’en-têtes ou les fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="36ef7-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="36ef7-113">Pour l’utiliser, définir la structure comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="36ef7-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="36ef7-114">La structure doit également être définie à l’aide de `ms_struct` de livraison si ce n’est pas à l’aide de compilateurs Microsoft.</span><span class="sxs-lookup"><span data-stu-id="36ef7-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="36ef7-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="36ef7-115">Requirements</span></span>
<span data-ttu-id="36ef7-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36ef7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="36ef7-117">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="36ef7-117">**Header:** None</span></span>  
<span data-ttu-id="36ef7-118">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="36ef7-118">**Library:** None</span></span>  
<span data-ttu-id="36ef7-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="36ef7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="36ef7-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36ef7-120">See also</span></span>

- [<span data-ttu-id="36ef7-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="36ef7-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="36ef7-122">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="36ef7-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
