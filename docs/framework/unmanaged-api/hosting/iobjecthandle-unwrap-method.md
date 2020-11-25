---
title: IObjectHandle::Unwrap, méthode
ms.date: 03/30/2017
api_name:
- IObjectHandle.Unwrap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type:
- apiref
ms.openlocfilehash: 32b6d2c05a96658ab2b8ec1df288d2be05bb947f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730667"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="729dc-102">IObjectHandle::Unwrap, méthode</span><span class="sxs-lookup"><span data-stu-id="729dc-102">IObjectHandle::Unwrap Method</span></span>

<span data-ttu-id="729dc-103">Désencapsule un objet marshalé-par-valeur à partir de l’indirection.</span><span class="sxs-lookup"><span data-stu-id="729dc-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="729dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="729dc-104">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="729dc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="729dc-105">Parameters</span></span>  

 `ppv`  
 <span data-ttu-id="729dc-106">à Pointeur vers l’objet à désencapsuler.</span><span class="sxs-lookup"><span data-stu-id="729dc-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="729dc-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="729dc-107">Requirements</span></span>  

 <span data-ttu-id="729dc-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="729dc-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="729dc-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="729dc-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="729dc-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="729dc-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="729dc-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="729dc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
