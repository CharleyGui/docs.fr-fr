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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc5bed553ac54eb708beae23f5c29cbedcb2b4e0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749063"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="e1394-102">IObjectHandle::Unwrap, méthode</span><span class="sxs-lookup"><span data-stu-id="e1394-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="e1394-103">Désencapsule un objet marshalé par valeur à partir de l’indirection.</span><span class="sxs-lookup"><span data-stu-id="e1394-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1394-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1394-104">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1394-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e1394-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="e1394-106">[out] Pointeur vers l’objet à désencapsuler.</span><span class="sxs-lookup"><span data-stu-id="e1394-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1394-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e1394-107">Requirements</span></span>  
 <span data-ttu-id="e1394-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1394-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1394-109">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e1394-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1394-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1394-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1394-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1394-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
