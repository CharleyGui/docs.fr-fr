---
title: ICorThreadpool::CorGetMaxThreads, méthode
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
ms.openlocfilehash: 46ffdb21c1f3b501cc28afffc224349887af5644
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762746"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="64b08-102">ICorThreadpool::CorGetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="64b08-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="64b08-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="64b08-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64b08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64b08-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="64b08-105">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="64b08-105">Requirements</span></span>  
 <span data-ttu-id="64b08-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64b08-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64b08-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="64b08-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64b08-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="64b08-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64b08-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64b08-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64b08-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64b08-110">See also</span></span>

- [<span data-ttu-id="64b08-111">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="64b08-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
