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
ms.openlocfilehash: 926bdcee3a3c3974c8546f3a6dfe98f0b62c93c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796570"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="aebeb-102">IAssemblyName::IsEqual, méthode</span><span class="sxs-lookup"><span data-stu-id="aebeb-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="aebeb-103">Détermine si un objet [IAssemblyName](iassemblyname-interface.md) spécifié est égal à ce `IAssemblyName`, en fonction des indicateurs de comparaison spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aebeb-103">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aebeb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aebeb-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aebeb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aebeb-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="aebeb-106">dans Objet auquel comparer ce `IAssemblyName`. `IAssemblyName`</span><span class="sxs-lookup"><span data-stu-id="aebeb-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="aebeb-107">dans Combinaison d’opérations de bits de valeurs [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) qui influencent la comparaison.</span><span class="sxs-lookup"><span data-stu-id="aebeb-107">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aebeb-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aebeb-108">Requirements</span></span>  
 <span data-ttu-id="aebeb-109">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aebeb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aebeb-110">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="aebeb-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="aebeb-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aebeb-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aebeb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aebeb-112">See also</span></span>

- [<span data-ttu-id="aebeb-113">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="aebeb-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="aebeb-114">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="aebeb-114">Fusion Enumerations</span></span>](fusion-enumerations.md)
