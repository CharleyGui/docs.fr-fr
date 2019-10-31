---
title: IAssemblyName::GetProperty, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
ms.openlocfilehash: b86828e01fb00b12feff2ed451793c240e16e240
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134380"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="86d1b-102">IAssemblyName::GetProperty, méthode</span><span class="sxs-lookup"><span data-stu-id="86d1b-102">IAssemblyName::GetProperty Method</span></span>
<span data-ttu-id="86d1b-103">Obtient un pointeur vers la propriété référencée par l’identificateur de propriété spécifié.</span><span class="sxs-lookup"><span data-stu-id="86d1b-103">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86d1b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86d1b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="86d1b-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="86d1b-106">dans Identificateur unique de la propriété demandée.</span><span class="sxs-lookup"><span data-stu-id="86d1b-106">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="86d1b-107">à Données de propriété retournées.</span><span class="sxs-lookup"><span data-stu-id="86d1b-107">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="86d1b-108">[in, out] Taille, en octets, de `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="86d1b-108">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86d1b-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="86d1b-109">Requirements</span></span>  
 <span data-ttu-id="86d1b-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86d1b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86d1b-111">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="86d1b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="86d1b-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d1b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d1b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86d1b-113">See also</span></span>

- [<span data-ttu-id="86d1b-114">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="86d1b-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
