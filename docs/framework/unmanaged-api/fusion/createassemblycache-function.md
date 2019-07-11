---
title: CreateAssemblyCache, fonction
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffeb04ddcec290f899556bf0d8078acfb06707ac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778604"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="dc0a3-102">CreateAssemblyCache, fonction</span><span class="sxs-lookup"><span data-stu-id="dc0a3-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="dc0a3-103">Obtient un pointeur vers un nouveau [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance qui représente le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="dc0a3-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc0a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc0a3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc0a3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dc0a3-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="dc0a3-106">[out] Retourné `IAssemblyCache` pointeur.</span><span class="sxs-lookup"><span data-stu-id="dc0a3-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="dc0a3-107">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="dc0a3-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="dc0a3-108">`dwReserved` doit être 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="dc0a3-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc0a3-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dc0a3-109">Requirements</span></span>  
 <span data-ttu-id="dc0a3-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc0a3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc0a3-111">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="dc0a3-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="dc0a3-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc0a3-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc0a3-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc0a3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc0a3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc0a3-114">See also</span></span>

- [<span data-ttu-id="dc0a3-115">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="dc0a3-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="dc0a3-116">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="dc0a3-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="dc0a3-117">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="dc0a3-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
