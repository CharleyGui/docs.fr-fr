---
title: FLockClrVersionCallback (pointeur fonction)
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
ms.openlocfilehash: f1ad414c30788801e14a33e98a0893e2a0f58d0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136516"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="491fc-102">FLockClrVersionCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="491fc-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="491fc-103">Pointe vers une fonction que le common language runtime (CLR) appelle pour indiquer que l’initialisation a démarré ou est terminée.</span><span class="sxs-lookup"><span data-stu-id="491fc-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="491fc-104">Ce pointeur de fonction est déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="491fc-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="491fc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="491fc-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="491fc-106">Notes</span><span class="sxs-lookup"><span data-stu-id="491fc-106">Remarks</span></span>  
 <span data-ttu-id="491fc-107">Cette fonction est implémentée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="491fc-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="491fc-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="491fc-108">Requirements</span></span>  
 <span data-ttu-id="491fc-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="491fc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="491fc-110">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="491fc-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="491fc-111">**Bibliothèque :** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="491fc-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="491fc-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="491fc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491fc-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="491fc-113">See also</span></span>

- [<span data-ttu-id="491fc-114">LockClrVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="491fc-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="491fc-115">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="491fc-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
