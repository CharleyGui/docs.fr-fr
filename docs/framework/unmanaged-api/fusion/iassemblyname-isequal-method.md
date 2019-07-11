---
title: IAssemblyName::IsEqual, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1fc128d15c56981f4bc6122e38e0514d006e29e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768620"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="eeaa5-102">IAssemblyName::IsEqual, méthode</span><span class="sxs-lookup"><span data-stu-id="eeaa5-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="eeaa5-103">Détermine si une certaine [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objet est égal à ce `IAssemblyName`, selon les indicateurs de comparaison spécifié.</span><span class="sxs-lookup"><span data-stu-id="eeaa5-103">Determines whether a specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeaa5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eeaa5-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eeaa5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eeaa5-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="eeaa5-106">[in] Le `IAssemblyName` objet auquel comparer cette `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="eeaa5-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="eeaa5-107">[in] Une combinaison au niveau du bit de [ASM_CMP_FLAGS pour](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) valeurs influencer la comparaison.</span><span class="sxs-lookup"><span data-stu-id="eeaa5-107">[in] A bitwise combination of [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eeaa5-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eeaa5-108">Requirements</span></span>  
 <span data-ttu-id="eeaa5-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeaa5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeaa5-110">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="eeaa5-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="eeaa5-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeaa5-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeaa5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eeaa5-112">See also</span></span>

- [<span data-ttu-id="eeaa5-113">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="eeaa5-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="eeaa5-114">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="eeaa5-114">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
