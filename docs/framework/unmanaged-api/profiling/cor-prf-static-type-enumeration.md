---
title: COR_PRF_STATIC_TYPE, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
ms.openlocfilehash: 80d72aefc736054afcee152c55e941c0f8f3c6a8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500765"
---
# <a name="cor_prf_static_type-enumeration"></a><span data-ttu-id="62bb8-102">COR_PRF_STATIC_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="62bb8-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="62bb8-103">Indique si un champ est statique et si oui, la qualité statique qui s'y applique.</span><span class="sxs-lookup"><span data-stu-id="62bb8-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="62bb8-104">Ces valeurs peuvent être combinées à l’aide de l’opération or au niveau du bit pour indiquer que le champ a plusieurs qualités statiques différentes.</span><span class="sxs-lookup"><span data-stu-id="62bb8-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62bb8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62bb8-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="62bb8-106">Membres</span><span class="sxs-lookup"><span data-stu-id="62bb8-106">Members</span></span>  
  
|<span data-ttu-id="62bb8-107">Membre</span><span class="sxs-lookup"><span data-stu-id="62bb8-107">Member</span></span>|<span data-ttu-id="62bb8-108">Description</span><span class="sxs-lookup"><span data-stu-id="62bb8-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="62bb8-109">Le champ n’est pas statique.</span><span class="sxs-lookup"><span data-stu-id="62bb8-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="62bb8-110">Le champ est un domaine d’application statique.</span><span class="sxs-lookup"><span data-stu-id="62bb8-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="62bb8-111">Le champ est thread-static.</span><span class="sxs-lookup"><span data-stu-id="62bb8-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="62bb8-112">Le champ est context-static.</span><span class="sxs-lookup"><span data-stu-id="62bb8-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="62bb8-113">Le champ est adresse virtuelle relative (RVA)-static.</span><span class="sxs-lookup"><span data-stu-id="62bb8-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62bb8-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="62bb8-114">Requirements</span></span>  
 <span data-ttu-id="62bb8-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62bb8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62bb8-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62bb8-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62bb8-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62bb8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62bb8-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62bb8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62bb8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62bb8-119">See also</span></span>

- [<span data-ttu-id="62bb8-120">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="62bb8-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
