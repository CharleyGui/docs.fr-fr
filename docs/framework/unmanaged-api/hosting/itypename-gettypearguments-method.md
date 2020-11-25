---
title: ITypeName::GetTypeArguments, méthode
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArguments
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type:
- apiref
ms.openlocfilehash: bcc1cb2755c4c0a2beb0829ce58b921f073f63d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727781"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="2e738-102">ITypeName::GetTypeArguments, méthode</span><span class="sxs-lookup"><span data-stu-id="2e738-102">ITypeName::GetTypeArguments Method</span></span>

<span data-ttu-id="2e738-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="2e738-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e738-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2e738-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2e738-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2e738-105">Requirements</span></span>  

 <span data-ttu-id="2e738-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e738-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e738-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e738-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e738-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e738-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e738-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e738-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e738-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e738-110">See also</span></span>

- [<span data-ttu-id="2e738-111">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="2e738-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
