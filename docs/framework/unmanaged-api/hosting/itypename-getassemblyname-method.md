---
title: ITypeName::GetAssemblyName, méthode
ms.date: 03/30/2017
api_name:
- ITypeName.GetAssemblyName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type:
- apiref
ms.openlocfilehash: 0c8f540e5d835b4874cc55b789804d0ce30f208d
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842203"
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="21cc1-102">ITypeName::GetAssemblyName, méthode</span><span class="sxs-lookup"><span data-stu-id="21cc1-102">ITypeName::GetAssemblyName Method</span></span>
<span data-ttu-id="21cc1-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="21cc1-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21cc1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21cc1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="21cc1-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="21cc1-105">Requirements</span></span>  
 <span data-ttu-id="21cc1-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21cc1-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21cc1-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="21cc1-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21cc1-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="21cc1-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21cc1-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21cc1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21cc1-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21cc1-110">See also</span></span>

- [<span data-ttu-id="21cc1-111">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="21cc1-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
