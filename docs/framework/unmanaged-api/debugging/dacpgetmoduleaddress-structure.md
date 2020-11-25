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
ms.openlocfilehash: a65fa9974165fa36e59a7fb83dca6dd902f7d8dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724392"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="81b9c-102">DacpGetModuleAddress, structure</span><span class="sxs-lookup"><span data-stu-id="81b9c-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="81b9c-103">Définit le conteneur pour une demande d’adresse de module.</span><span class="sxs-lookup"><span data-stu-id="81b9c-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="81b9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81b9c-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="81b9c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="81b9c-105">Members</span></span>

| <span data-ttu-id="81b9c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="81b9c-106">Member</span></span>      | <span data-ttu-id="81b9c-107">Description</span><span class="sxs-lookup"><span data-stu-id="81b9c-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="81b9c-108">Pointeur vers le module.</span><span class="sxs-lookup"><span data-stu-id="81b9c-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="81b9c-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="81b9c-109">Methods</span></span>

| <span data-ttu-id="81b9c-110">Méthode</span><span class="sxs-lookup"><span data-stu-id="81b9c-110">Method</span></span>                                                                                               | <span data-ttu-id="81b9c-111">Description</span><span class="sxs-lookup"><span data-stu-id="81b9c-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="81b9c-112">Requête</span><span class="sxs-lookup"><span data-stu-id="81b9c-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="81b9c-113">Exécute une requête pour remplir la structure à partir de la structure d’exécution donnée.</span><span class="sxs-lookup"><span data-stu-id="81b9c-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="81b9c-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="81b9c-114">Remarks</span></span>

<span data-ttu-id="81b9c-115">Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="81b9c-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="81b9c-116">Pour l’utiliser, définissez la structure comme indiqué ci-dessus, où `CLRDATA_ADDRESS` est un entier non signé 64 bits.</span><span class="sxs-lookup"><span data-stu-id="81b9c-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="81b9c-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="81b9c-117">Requirements</span></span>

<span data-ttu-id="81b9c-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81b9c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="81b9c-119">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="81b9c-119">**Header:** None</span></span>  
<span data-ttu-id="81b9c-120">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="81b9c-120">**Library:** None</span></span>  
<span data-ttu-id="81b9c-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="81b9c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="81b9c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81b9c-122">See also</span></span>

- [<span data-ttu-id="81b9c-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="81b9c-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="81b9c-124">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="81b9c-124">Debugging Structures</span></span>](debugging-structures.md)
