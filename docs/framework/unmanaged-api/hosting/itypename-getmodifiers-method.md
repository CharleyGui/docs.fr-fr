---
title: ITypeName::GetModifiers, méthode
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
ms.openlocfilehash: 64751032c017473ffd82248b310b14c087f74129
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727833"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="f5bed-102">ITypeName::GetModifiers, méthode</span><span class="sxs-lookup"><span data-stu-id="f5bed-102">ITypeName::GetModifiers Method</span></span>

<span data-ttu-id="f5bed-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="f5bed-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5bed-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f5bed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f5bed-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f5bed-105">Requirements</span></span>  

 <span data-ttu-id="f5bed-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5bed-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5bed-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5bed-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5bed-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5bed-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5bed-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5bed-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5bed-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5bed-110">See also</span></span>

- [<span data-ttu-id="f5bed-111">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="f5bed-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
