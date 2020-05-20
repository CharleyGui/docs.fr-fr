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
ms.openlocfilehash: 5ac015f958d9504bbd14a66ead86548b8df32764
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616773"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="a8b82-102">CLSID_RESOLUTION_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="a8b82-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="a8b82-103">Contient des valeurs qui indiquent comment le common language runtime (CLR) doit résoudre un `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="a8b82-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8b82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8b82-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="a8b82-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a8b82-105">Members</span></span>  
  
|<span data-ttu-id="a8b82-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a8b82-106">Member</span></span>|<span data-ttu-id="a8b82-107">Description</span><span class="sxs-lookup"><span data-stu-id="a8b82-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="a8b82-108">Indique le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="a8b82-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="a8b82-109">Indique que le runtime effectue une recherche dans le registre et applique la stratégie shim.</span><span class="sxs-lookup"><span data-stu-id="a8b82-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8b82-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="a8b82-110">Requirements</span></span>  
 <span data-ttu-id="a8b82-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8b82-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8b82-112">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a8b82-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8b82-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8b82-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8b82-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8b82-114">See also</span></span>

- [<span data-ttu-id="a8b82-115">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="a8b82-115">Hosting Enumerations</span></span>](hosting-enumerations.md)
