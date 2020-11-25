---
title: CLSID_RESOLUTION_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- CLSID_RESOLUTION_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLSID_RESOLUTION_FLAGS
helpviewer_keywords:
- CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type:
- apiref
ms.openlocfilehash: 19731f34d259757e6de62dd4b4f0d4735d1c2e61
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706162"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="5f3da-102">CLSID_RESOLUTION_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="5f3da-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>

<span data-ttu-id="5f3da-103">Contient des valeurs qui indiquent comment le common language runtime (CLR) doit résoudre un `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="5f3da-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f3da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f3da-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="5f3da-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5f3da-105">Members</span></span>  
  
|<span data-ttu-id="5f3da-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5f3da-106">Member</span></span>|<span data-ttu-id="5f3da-107">Description</span><span class="sxs-lookup"><span data-stu-id="5f3da-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="5f3da-108">Indique le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="5f3da-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="5f3da-109">Indique que le runtime effectue une recherche dans le registre et applique la stratégie shim.</span><span class="sxs-lookup"><span data-stu-id="5f3da-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f3da-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5f3da-110">Requirements</span></span>  

 <span data-ttu-id="5f3da-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f3da-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f3da-112">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5f3da-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f3da-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f3da-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f3da-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f3da-114">See also</span></span>

- [<span data-ttu-id="5f3da-115">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="5f3da-115">Hosting Enumerations</span></span>](hosting-enumerations.md)
