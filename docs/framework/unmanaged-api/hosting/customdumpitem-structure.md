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
ms.openlocfilehash: 154beef9398029f31dcb4d081019b9f292238af4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176472"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="0a651-102">CustomDumpItem, structure</span><span class="sxs-lookup"><span data-stu-id="0a651-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="0a651-103">Décrit un élément à ajouter à un dépotoir personnalisé dans les rapports d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0a651-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a651-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a651-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="0a651-105">Membres</span><span class="sxs-lookup"><span data-stu-id="0a651-105">Members</span></span>  
  
|<span data-ttu-id="0a651-106">Membre</span><span class="sxs-lookup"><span data-stu-id="0a651-106">Member</span></span>|<span data-ttu-id="0a651-107">Description</span><span class="sxs-lookup"><span data-stu-id="0a651-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="0a651-108">Une valeur [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) qui indique le type d’élément à ajouter.</span><span class="sxs-lookup"><span data-stu-id="0a651-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="0a651-109">Pas utilisé pour l'instant.</span><span class="sxs-lookup"><span data-stu-id="0a651-109">Not currently used.</span></span> <span data-ttu-id="0a651-110">Tous les articles ajoutés au syndicat ne doivent pas être plus grands que la taille du pointeur.</span><span class="sxs-lookup"><span data-stu-id="0a651-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="0a651-111">Si `struct` un a est nécessaire, vous devez l’allouer séparément et le pointer vers elle.</span><span class="sxs-lookup"><span data-stu-id="0a651-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a651-112">Notes </span><span class="sxs-lookup"><span data-stu-id="0a651-112">Remarks</span></span>  
 <span data-ttu-id="0a651-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) prend un `CustomDumpItem`paramètre de type .</span><span class="sxs-lookup"><span data-stu-id="0a651-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a651-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0a651-114">Requirements</span></span>  
 <span data-ttu-id="0a651-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a651-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a651-116">**En-tête:** MSCorEE.idl MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="0a651-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0a651-117">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a651-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a651-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a651-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a651-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a651-119">See also</span></span>

- [<span data-ttu-id="0a651-120">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="0a651-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
