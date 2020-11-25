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
ms.openlocfilehash: 554f47cc4bd948e2b6106c1d71a2a4b7968d43f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718863"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="a57cb-102">CorEventAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="a57cb-102">CorEventAttr Enumeration</span></span>

<span data-ttu-id="a57cb-103">Contient des valeurs qui décrivent les métadonnées d'un événement.</span><span class="sxs-lookup"><span data-stu-id="a57cb-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a57cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a57cb-104">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="a57cb-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a57cb-105">Members</span></span>  
  
|<span data-ttu-id="a57cb-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a57cb-106">Member</span></span>|<span data-ttu-id="a57cb-107">Description</span><span class="sxs-lookup"><span data-stu-id="a57cb-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="a57cb-108">Spécifie que l’événement est spécial et que son nom décrit comment.</span><span class="sxs-lookup"><span data-stu-id="a57cb-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="a57cb-109">Réservé à un usage interne par la common language runtime.</span><span class="sxs-lookup"><span data-stu-id="a57cb-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="a57cb-110">Spécifie que le common language runtime doit vérifier l’encodage du nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="a57cb-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a57cb-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a57cb-111">Requirements</span></span>  

 <span data-ttu-id="a57cb-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a57cb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a57cb-113">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a57cb-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a57cb-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a57cb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a57cb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a57cb-115">See also</span></span>

- [<span data-ttu-id="a57cb-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="a57cb-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
