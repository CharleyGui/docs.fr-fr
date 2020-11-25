---
title: ITypeNameFactory::GetTypeNameBuilder, méthode
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.GetTypeNameBuilder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeNameBuilder
helpviewer_keywords:
- ITypeNameFactory::GetTypeNameBuilder method [.NET Framework hosting]
- GetTypeNameBuilder method [.NET Framework hosting]
ms.assetid: c682f744-996e-43c7-a9ea-c57cbc755398
topic_type:
- apiref
ms.openlocfilehash: 67e5e66ae88cfcc777d631268ed555bcb4eb31b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728743"
---
# <a name="itypenamefactorygettypenamebuilder-method"></a><span data-ttu-id="860e0-102">ITypeNameFactory::GetTypeNameBuilder, méthode</span><span class="sxs-lookup"><span data-stu-id="860e0-102">ITypeNameFactory::GetTypeNameBuilder Method</span></span>

<span data-ttu-id="860e0-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="860e0-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="860e0-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="860e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeNameBuilder (  
    [out, retval] ITypeNameBuilder** ppTypeBuilder  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="860e0-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="860e0-105">Requirements</span></span>  

 <span data-ttu-id="860e0-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="860e0-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="860e0-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="860e0-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="860e0-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="860e0-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="860e0-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="860e0-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="860e0-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="860e0-110">See also</span></span>

- [<span data-ttu-id="860e0-111">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="860e0-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
