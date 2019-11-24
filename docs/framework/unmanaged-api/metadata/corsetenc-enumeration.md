---
title: CorSetENC, énumération
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: 39f72e670ddc700c257f50f6bad6fab702ec21b6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432773"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="79434-102">CorSetENC, énumération</span><span class="sxs-lookup"><span data-stu-id="79434-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="79434-103">Contient des valeurs utilisées pour influencer le comportement pendant la génération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="79434-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79434-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79434-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="79434-105">Membres</span><span class="sxs-lookup"><span data-stu-id="79434-105">Members</span></span>  
  
|<span data-ttu-id="79434-106">Membre</span><span class="sxs-lookup"><span data-stu-id="79434-106">Member</span></span>|<span data-ttu-id="79434-107">Description</span><span class="sxs-lookup"><span data-stu-id="79434-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="79434-108">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="79434-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="79434-109">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="79434-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="79434-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span><span class="sxs-lookup"><span data-stu-id="79434-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="79434-111">Indicates that tokens can be moved during updates.</span><span class="sxs-lookup"><span data-stu-id="79434-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="79434-112">Indicates that updates can consist only of additions.</span><span class="sxs-lookup"><span data-stu-id="79434-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="79434-113">Tokens cannot be moved.</span><span class="sxs-lookup"><span data-stu-id="79434-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="79434-114">Indicates that compilation is incremental.</span><span class="sxs-lookup"><span data-stu-id="79434-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="79434-115">Indicates that only changed metadata should be saved.</span><span class="sxs-lookup"><span data-stu-id="79434-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="79434-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="79434-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79434-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="79434-117">Requirements</span></span>  
 <span data-ttu-id="79434-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79434-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79434-119">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="79434-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="79434-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79434-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79434-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79434-121">See also</span></span>

- [<span data-ttu-id="79434-122">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="79434-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
