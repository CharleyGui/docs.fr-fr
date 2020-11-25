---
title: ITypeNameFactory::ParseTypeName, méthode
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
ms.openlocfilehash: 2b4d22fac7125ad113aaef5b093396a065f682c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728717"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="98eea-102">ITypeNameFactory::ParseTypeName, méthode</span><span class="sxs-lookup"><span data-stu-id="98eea-102">ITypeNameFactory::ParseTypeName Method</span></span>

<span data-ttu-id="98eea-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="98eea-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98eea-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="98eea-104">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="98eea-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="98eea-105">Requirements</span></span>  

 <span data-ttu-id="98eea-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98eea-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98eea-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="98eea-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98eea-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98eea-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98eea-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98eea-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98eea-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98eea-110">See also</span></span>

- [<span data-ttu-id="98eea-111">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="98eea-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
