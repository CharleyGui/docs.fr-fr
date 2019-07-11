---
title: ITypeName::GetNames, méthode
ms.date: 03/30/2017
api_name:
- ITypeName.GetNames
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetNames
helpviewer_keywords:
- ITypeName::GetNames method [.NET Framework hosting]
- GetNames method [.NET Framework hosting]
ms.assetid: e2a3637b-d1e9-4d93-9e9b-0555fbff793d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c8ca51a9b1875e28a6e4824da40090f17e38f07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780540"
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="36dfc-102">ITypeName::GetNames, méthode</span><span class="sxs-lookup"><span data-stu-id="36dfc-102">ITypeName::GetNames Method</span></span>
<span data-ttu-id="36dfc-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="36dfc-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36dfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36dfc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="36dfc-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="36dfc-105">Requirements</span></span>  
 <span data-ttu-id="36dfc-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36dfc-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36dfc-107">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="36dfc-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36dfc-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36dfc-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36dfc-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36dfc-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36dfc-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36dfc-110">See also</span></span>

- [<span data-ttu-id="36dfc-111">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="36dfc-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
