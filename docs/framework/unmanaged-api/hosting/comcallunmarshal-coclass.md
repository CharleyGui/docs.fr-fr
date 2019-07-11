---
title: Coclasse ComCallUnmarshal
ms.date: 03/30/2017
api_name:
- ComCallUnmarshal Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ComCallUnmarshal
helpviewer_keywords:
- ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fde42e3ecfac81a168920bc152833be7ba72b995
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779085"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="4f877-102">Coclasse ComCallUnmarshal</span><span class="sxs-lookup"><span data-stu-id="4f877-102">ComCallUnmarshal Coclass</span></span>
<span data-ttu-id="4f877-103">Fournit des interfaces pour gérer le marshaling de pointeurs d’interface.</span><span class="sxs-lookup"><span data-stu-id="4f877-103">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f877-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f877-104">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="4f877-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="4f877-105">Interfaces</span></span>  
  
|<span data-ttu-id="4f877-106">Interface</span><span class="sxs-lookup"><span data-stu-id="4f877-106">Interface</span></span>|<span data-ttu-id="4f877-107">Description</span><span class="sxs-lookup"><span data-stu-id="4f877-107">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="4f877-108">Fournit des méthodes pour créer, de l’initialisation et de gérer un proxy dans un processus client.</span><span class="sxs-lookup"><span data-stu-id="4f877-108">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f877-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4f877-109">Requirements</span></span>  
 <span data-ttu-id="4f877-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f877-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f877-111">**En-tête :** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="4f877-111">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4f877-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f877-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f877-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f877-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f877-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f877-114">See also</span></span>

- [<span data-ttu-id="4f877-115">Coclasses d’hébergement</span><span class="sxs-lookup"><span data-stu-id="4f877-115">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
