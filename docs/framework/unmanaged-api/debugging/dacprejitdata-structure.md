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
ms.openlocfilehash: 4436ece72b0a6a405fc41cba5413093fc42ce750
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860782"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="dcc6e-102">DacpReJitData, structure</span><span class="sxs-lookup"><span data-stu-id="dcc6e-102">DacpReJitData Structure</span></span>

<span data-ttu-id="dcc6e-103">Définit les informations de base sur une méthode instrumentée de profileur donnée.</span><span class="sxs-lookup"><span data-stu-id="dcc6e-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="dcc6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcc6e-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="dcc6e-105">Membres</span><span class="sxs-lookup"><span data-stu-id="dcc6e-105">Members</span></span>

| <span data-ttu-id="dcc6e-106">Membre</span><span class="sxs-lookup"><span data-stu-id="dcc6e-106">Member</span></span>           | <span data-ttu-id="dcc6e-107">Description</span><span class="sxs-lookup"><span data-stu-id="dcc6e-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="dcc6e-108">Numéro de révision ReJit pour une méthode.</span><span class="sxs-lookup"><span data-stu-id="dcc6e-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="dcc6e-109">Indicateur qui spécifie l’état actuel de l’instrumentation ReJit de la méthode pour la version donnée.</span><span class="sxs-lookup"><span data-stu-id="dcc6e-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="dcc6e-110">Adresse de base de l’implémentation rejitted de la méthode.</span><span class="sxs-lookup"><span data-stu-id="dcc6e-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="dcc6e-111">Notes </span><span class="sxs-lookup"><span data-stu-id="dcc6e-111">Remarks</span></span>

<span data-ttu-id="dcc6e-112">Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="dcc6e-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="dcc6e-113">Pour l’utiliser, définissez la structure comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="dcc6e-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="dcc6e-114">La structure doit également être définie à `ms_struct` l’aide de l’empaquetage si vous n’utilisez pas les compilateurs Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dcc6e-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="dcc6e-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dcc6e-115">Requirements</span></span>
<span data-ttu-id="dcc6e-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcc6e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="dcc6e-117">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="dcc6e-117">**Header:** None</span></span>  
<span data-ttu-id="dcc6e-118">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="dcc6e-118">**Library:** None</span></span>  
<span data-ttu-id="dcc6e-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dcc6e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="dcc6e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcc6e-120">See also</span></span>

- [<span data-ttu-id="dcc6e-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="dcc6e-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="dcc6e-122">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="dcc6e-122">Debugging Structures</span></span>](debugging-structures.md)
