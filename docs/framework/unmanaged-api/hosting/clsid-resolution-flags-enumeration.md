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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5274e70c5bead201beb158ee2895415d7ec9e53c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779130"
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="5c206-102">CLSID_RESOLUTION_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="5c206-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="5c206-103">Contient des valeurs qui indiquent comment le common language runtime (CLR) doit résoudre un `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="5c206-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c206-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c206-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="5c206-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5c206-105">Members</span></span>  
  
|<span data-ttu-id="5c206-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5c206-106">Member</span></span>|<span data-ttu-id="5c206-107">Description</span><span class="sxs-lookup"><span data-stu-id="5c206-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="5c206-108">Indique le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="5c206-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="5c206-109">Indique que le runtime recherche dans le Registre et applique la stratégie de shim.</span><span class="sxs-lookup"><span data-stu-id="5c206-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c206-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5c206-110">Requirements</span></span>  
 <span data-ttu-id="5c206-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c206-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c206-112">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c206-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c206-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c206-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c206-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c206-114">See also</span></span>

- [<span data-ttu-id="5c206-115">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="5c206-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
