---
title: DacpGetModuleAddress, structure
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1e3a62de3259c012438c64ece26e696682ec96e6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789201"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="b3eb2-102">DacpGetModuleAddress, structure</span><span class="sxs-lookup"><span data-stu-id="b3eb2-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="b3eb2-103">Définit le conteneur pour une demande d’adresse de module.</span><span class="sxs-lookup"><span data-stu-id="b3eb2-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b3eb2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3eb2-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="b3eb2-105">Members</span><span class="sxs-lookup"><span data-stu-id="b3eb2-105">Members</span></span>

| <span data-ttu-id="b3eb2-106">Member</span><span class="sxs-lookup"><span data-stu-id="b3eb2-106">Member</span></span>      | <span data-ttu-id="b3eb2-107">Description</span><span class="sxs-lookup"><span data-stu-id="b3eb2-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="b3eb2-108">Pointeur vers le module.</span><span class="sxs-lookup"><span data-stu-id="b3eb2-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="b3eb2-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b3eb2-109">Methods</span></span>

| <span data-ttu-id="b3eb2-110">Méthode</span><span class="sxs-lookup"><span data-stu-id="b3eb2-110">Method</span></span>                                                                                               | <span data-ttu-id="b3eb2-111">Description</span><span class="sxs-lookup"><span data-stu-id="b3eb2-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="b3eb2-112">Requête</span><span class="sxs-lookup"><span data-stu-id="b3eb2-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="b3eb2-113">Exécute une requête pour remplir la structure à partir de la structure d’exécution donnée.</span><span class="sxs-lookup"><span data-stu-id="b3eb2-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b3eb2-114">Notes</span><span class="sxs-lookup"><span data-stu-id="b3eb2-114">Remarks</span></span>

<span data-ttu-id="b3eb2-115">Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="b3eb2-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="b3eb2-116">Pour l’utiliser, définissez la structure comme indiqué ci-dessus, où `CLRDATA_ADDRESS` est un entier non signé 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b3eb2-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="b3eb2-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="b3eb2-117">Requirements</span></span>
<span data-ttu-id="b3eb2-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3eb2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b3eb2-119">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="b3eb2-119">**Header:** None</span></span>  
<span data-ttu-id="b3eb2-120">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="b3eb2-120">**Library:** None</span></span>  
<span data-ttu-id="b3eb2-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b3eb2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b3eb2-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3eb2-122">See also</span></span>

- [<span data-ttu-id="b3eb2-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="b3eb2-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="b3eb2-124">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="b3eb2-124">Debugging Structures</span></span>](debugging-structures.md)
