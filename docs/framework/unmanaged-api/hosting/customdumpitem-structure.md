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
ms.openlocfilehash: c77e93686c7d121e9fe2a92f03970404ab823dc0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673239"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="c16fe-102">CustomDumpItem, structure</span><span class="sxs-lookup"><span data-stu-id="c16fe-102">CustomDumpItem Structure</span></span>

<span data-ttu-id="c16fe-103">Décrit un élément à ajouter à un dump personnalisé dans le rapport d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="c16fe-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c16fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c16fe-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="c16fe-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c16fe-105">Members</span></span>  
  
|<span data-ttu-id="c16fe-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c16fe-106">Member</span></span>|<span data-ttu-id="c16fe-107">Description</span><span class="sxs-lookup"><span data-stu-id="c16fe-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="c16fe-108">Valeur [ECustomDumpItemKind,](ecustomdumpitemkind-enumeration.md) qui indique le type d’élément à ajouter.</span><span class="sxs-lookup"><span data-stu-id="c16fe-108">An [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="c16fe-109">Pas utilisé pour l'instant.</span><span class="sxs-lookup"><span data-stu-id="c16fe-109">Not currently used.</span></span> <span data-ttu-id="c16fe-110">Tout élément ajouté à l’Union ne doit pas être supérieur à la taille du pointeur.</span><span class="sxs-lookup"><span data-stu-id="c16fe-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="c16fe-111">Si un `struct` est requis, vous devez l’allouer séparément et pointer dessus.</span><span class="sxs-lookup"><span data-stu-id="c16fe-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c16fe-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="c16fe-112">Remarks</span></span>  

 <span data-ttu-id="c16fe-113">[ICLRErrorReportingManager :: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) prend un paramètre de type `CustomDumpItem` .</span><span class="sxs-lookup"><span data-stu-id="c16fe-113">[ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c16fe-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c16fe-114">Requirements</span></span>  

 <span data-ttu-id="c16fe-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c16fe-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c16fe-116">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="c16fe-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c16fe-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c16fe-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c16fe-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c16fe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c16fe-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c16fe-119">See also</span></span>

- [<span data-ttu-id="c16fe-120">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="c16fe-120">Hosting Structures</span></span>](hosting-structures.md)
