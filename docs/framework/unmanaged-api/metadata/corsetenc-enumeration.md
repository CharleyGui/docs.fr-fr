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
ms.openlocfilehash: 93a194ea72ab894544927cf96304397b7211b5ac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009156"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="3f9ec-102">CorSetENC, énumération</span><span class="sxs-lookup"><span data-stu-id="3f9ec-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="3f9ec-103">Contient des valeurs utilisées pour influencer le comportement pendant la génération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3f9ec-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f9ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f9ec-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3f9ec-105">Membres</span><span class="sxs-lookup"><span data-stu-id="3f9ec-105">Members</span></span>  
  
|<span data-ttu-id="3f9ec-106">Membre</span><span class="sxs-lookup"><span data-stu-id="3f9ec-106">Member</span></span>|<span data-ttu-id="3f9ec-107">Description</span><span class="sxs-lookup"><span data-stu-id="3f9ec-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="3f9ec-108">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="3f9ec-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="3f9ec-109">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="3f9ec-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="3f9ec-110">Indique que les métadonnées peuvent être mises à jour et que les jetons ne peuvent pas être déplacés.</span><span class="sxs-lookup"><span data-stu-id="3f9ec-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="3f9ec-111">Indique que les jetons peuvent être déplacés pendant les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="3f9ec-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="3f9ec-112">Indique que les mises à jour ne peuvent comporter que des ajouts.</span><span class="sxs-lookup"><span data-stu-id="3f9ec-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="3f9ec-113">Les jetons ne peuvent pas être déplacés.</span><span class="sxs-lookup"><span data-stu-id="3f9ec-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="3f9ec-114">Indique que la compilation est incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="3f9ec-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="3f9ec-115">Indique que seules les métadonnées modifiées doivent être enregistrées.</span><span class="sxs-lookup"><span data-stu-id="3f9ec-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="3f9ec-116">Comprend `MDUpdateENC` , `MDUpdateFull` et `MDUpdateIncremental` .</span><span class="sxs-lookup"><span data-stu-id="3f9ec-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f9ec-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3f9ec-117">Requirements</span></span>  
 <span data-ttu-id="3f9ec-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f9ec-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f9ec-119">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="3f9ec-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3f9ec-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f9ec-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f9ec-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f9ec-121">See also</span></span>

- [<span data-ttu-id="3f9ec-122">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="3f9ec-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
