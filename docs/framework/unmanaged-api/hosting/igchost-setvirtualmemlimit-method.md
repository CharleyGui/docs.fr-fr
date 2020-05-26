---
title: IGCHost::SetVirtualMemLimit, méthode
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
ms.openlocfilehash: 93ed63b4abacce1d8943434965aacf67190631b6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805185"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="4febe-102">IGCHost::SetVirtualMemLimit, méthode</span><span class="sxs-lookup"><span data-stu-id="4febe-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="4febe-103">Définit la taille maximale de la mémoire virtuelle du Runtime.</span><span class="sxs-lookup"><span data-stu-id="4febe-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4febe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4febe-104">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4febe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4febe-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="4febe-106">dans Taille maximale, en mégaoctets, de la mémoire virtuelle du Runtime.</span><span class="sxs-lookup"><span data-stu-id="4febe-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4febe-107">Notes</span><span class="sxs-lookup"><span data-stu-id="4febe-107">Remarks</span></span>  
 <span data-ttu-id="4febe-108">La taille maximale de la mémoire virtuelle du runtime peut être modifiée dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="4febe-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4febe-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4febe-109">Requirements</span></span>  
 <span data-ttu-id="4febe-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4febe-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4febe-111">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="4febe-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="4febe-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4febe-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4febe-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4febe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4febe-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4febe-114">See also</span></span>

- [<span data-ttu-id="4febe-115">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="4febe-115">IGCHost Interface</span></span>](igchost-interface.md)
