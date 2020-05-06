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
ms.openlocfilehash: e460264e2393858c028ba51aec4a4f2c01649994
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860825"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="99946-102">DacpGetModuleAddress, structure</span><span class="sxs-lookup"><span data-stu-id="99946-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="99946-103">Définit le conteneur pour une demande d’adresse de module.</span><span class="sxs-lookup"><span data-stu-id="99946-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="99946-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99946-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="99946-105">Membres</span><span class="sxs-lookup"><span data-stu-id="99946-105">Members</span></span>

| <span data-ttu-id="99946-106">Membre</span><span class="sxs-lookup"><span data-stu-id="99946-106">Member</span></span>      | <span data-ttu-id="99946-107">Description</span><span class="sxs-lookup"><span data-stu-id="99946-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="99946-108">Pointeur vers le module.</span><span class="sxs-lookup"><span data-stu-id="99946-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="99946-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="99946-109">Methods</span></span>

| <span data-ttu-id="99946-110">Méthode</span><span class="sxs-lookup"><span data-stu-id="99946-110">Method</span></span>                                                                                               | <span data-ttu-id="99946-111">Description</span><span class="sxs-lookup"><span data-stu-id="99946-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="99946-112">Requête</span><span class="sxs-lookup"><span data-stu-id="99946-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="99946-113">Exécute une requête pour remplir la structure à partir de la structure d’exécution donnée.</span><span class="sxs-lookup"><span data-stu-id="99946-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="99946-114">Notes </span><span class="sxs-lookup"><span data-stu-id="99946-114">Remarks</span></span>

<span data-ttu-id="99946-115">Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="99946-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="99946-116">Pour l’utiliser, définissez la structure comme indiqué ci-dessus `CLRDATA_ADDRESS` , où est un entier non signé 64 bits.</span><span class="sxs-lookup"><span data-stu-id="99946-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="99946-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="99946-117">Requirements</span></span>
<span data-ttu-id="99946-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99946-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="99946-119">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="99946-119">**Header:** None</span></span>  
<span data-ttu-id="99946-120">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="99946-120">**Library:** None</span></span>  
<span data-ttu-id="99946-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="99946-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="99946-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99946-122">See also</span></span>

- [<span data-ttu-id="99946-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="99946-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="99946-124">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="99946-124">Debugging Structures</span></span>](debugging-structures.md)
