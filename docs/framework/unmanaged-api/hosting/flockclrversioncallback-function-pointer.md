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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46e3356df6578f2adf2ceee00b1363b65fd014ea
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760232"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="04aa4-102">FLockClrVersionCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="04aa4-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="04aa4-103">Pointe vers une fonction que le common language runtime (CLR) appelle pour indiquer que l’initialisation a démarré ou terminé.</span><span class="sxs-lookup"><span data-stu-id="04aa4-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="04aa4-104">Ce pointeur de fonction a été déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="04aa4-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04aa4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04aa4-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="04aa4-106">Notes</span><span class="sxs-lookup"><span data-stu-id="04aa4-106">Remarks</span></span>  
 <span data-ttu-id="04aa4-107">Cette fonction est implémentée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="04aa4-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04aa4-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="04aa4-108">Requirements</span></span>  
 <span data-ttu-id="04aa4-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04aa4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04aa4-110">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="04aa4-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04aa4-111">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="04aa4-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="04aa4-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04aa4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04aa4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04aa4-113">See also</span></span>

- [<span data-ttu-id="04aa4-114">LockClrVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="04aa4-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="04aa4-115">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="04aa4-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
