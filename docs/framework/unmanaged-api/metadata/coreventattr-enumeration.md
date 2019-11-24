---
title: CorEventAttr, énumération
ms.date: 03/30/2017
api_name:
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
ms.openlocfilehash: ec2972605c40f4ba292f5a5f58d6d3efed53f966
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443556"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="add3b-102">CorEventAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="add3b-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="add3b-103">Contient des valeurs qui décrivent les métadonnées d'un événement.</span><span class="sxs-lookup"><span data-stu-id="add3b-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="add3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="add3b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="add3b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="add3b-105">Members</span></span>  
  
|<span data-ttu-id="add3b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="add3b-106">Member</span></span>|<span data-ttu-id="add3b-107">Description</span><span class="sxs-lookup"><span data-stu-id="add3b-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="add3b-108">Specifies that the event is special, and that its name describes how.</span><span class="sxs-lookup"><span data-stu-id="add3b-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="add3b-109">Reserved for internal use by the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="add3b-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="add3b-110">Specifies that the common language runtime should check the encoding of the event name.</span><span class="sxs-lookup"><span data-stu-id="add3b-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="add3b-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="add3b-111">Requirements</span></span>  
 <span data-ttu-id="add3b-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="add3b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="add3b-113">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="add3b-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="add3b-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="add3b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add3b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="add3b-115">See also</span></span>

- [<span data-ttu-id="add3b-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="add3b-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
