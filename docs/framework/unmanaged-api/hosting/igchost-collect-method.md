---
title: IGCHost::Collect, méthode
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
ms.openlocfilehash: f32b91f0d47449f80c38542162035999d616813b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670137"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="8b148-102">IGCHost::Collect, méthode</span><span class="sxs-lookup"><span data-stu-id="8b148-102">IGCHost::Collect Method</span></span>

<span data-ttu-id="8b148-103">Force une collection à se produire pour la génération donnée, quel que soit l’état du garbage collection actuel.</span><span class="sxs-lookup"><span data-stu-id="8b148-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b148-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b148-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b148-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8b148-105">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="8b148-106">dans Génération sur laquelle effectuer l’garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8b148-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="8b148-107">La valeur-1 indique que toutes les générations subissent une garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8b148-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b148-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8b148-108">Requirements</span></span>  

 <span data-ttu-id="8b148-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b148-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b148-110">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="8b148-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="8b148-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8b148-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b148-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b148-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b148-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b148-113">See also</span></span>

- [<span data-ttu-id="8b148-114">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="8b148-114">IGCHost Interface</span></span>](igchost-interface.md)
