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
ms.openlocfilehash: 8544b8d7b1f23853465bbb2aea697dfe021d77f2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842177"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="3dd22-102">ITypeName::GetModifiers, méthode</span><span class="sxs-lookup"><span data-stu-id="3dd22-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="3dd22-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="3dd22-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dd22-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3dd22-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3dd22-105">Requirements</span></span>  
 <span data-ttu-id="3dd22-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dd22-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dd22-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3dd22-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3dd22-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3dd22-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3dd22-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dd22-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd22-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dd22-110">See also</span></span>

- [<span data-ttu-id="3dd22-111">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="3dd22-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
