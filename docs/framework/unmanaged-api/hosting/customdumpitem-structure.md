---
title: CustomDumpItem, structure
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: ae64edd8a3a628100d4c51d0b78be1bc8d49fc17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138283"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="b677a-102">CustomDumpItem, structure</span><span class="sxs-lookup"><span data-stu-id="b677a-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="b677a-103">Décrit un élément à ajouter à un dump personnalisé dans le rapport d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="b677a-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b677a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b677a-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="b677a-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b677a-105">Members</span></span>  
  
|<span data-ttu-id="b677a-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b677a-106">Member</span></span>|<span data-ttu-id="b677a-107">Description</span><span class="sxs-lookup"><span data-stu-id="b677a-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="b677a-108">Valeur [ECustomDumpItemKind,](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) qui indique le type d’élément à ajouter.</span><span class="sxs-lookup"><span data-stu-id="b677a-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="b677a-109">Non utilisé actuellement.</span><span class="sxs-lookup"><span data-stu-id="b677a-109">Not currently used.</span></span> <span data-ttu-id="b677a-110">Tout élément ajouté à l’Union ne doit pas être supérieur à la taille du pointeur.</span><span class="sxs-lookup"><span data-stu-id="b677a-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="b677a-111">Si un `struct` est requis, vous devez l’allouer séparément et pointer dessus.</span><span class="sxs-lookup"><span data-stu-id="b677a-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b677a-112">Notes</span><span class="sxs-lookup"><span data-stu-id="b677a-112">Remarks</span></span>  
 <span data-ttu-id="b677a-113">[ICLRErrorReportingManager :: BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) prend un paramètre de type `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="b677a-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b677a-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="b677a-114">Requirements</span></span>  
 <span data-ttu-id="b677a-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b677a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b677a-116">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="b677a-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="b677a-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b677a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b677a-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b677a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b677a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b677a-119">See also</span></span>

- [<span data-ttu-id="b677a-120">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="b677a-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
