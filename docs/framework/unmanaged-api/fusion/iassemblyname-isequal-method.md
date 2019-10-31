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
ms.openlocfilehash: 23bc251053dd27a7c5accb48ab4759ecdb79fe09
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134307"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="b4a8a-102">IAssemblyName::IsEqual, méthode</span><span class="sxs-lookup"><span data-stu-id="b4a8a-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="b4a8a-103">Détermine si un objet [IAssemblyName](iassemblyname-interface.md) spécifié est égal à cet `IAssemblyName`, en fonction des indicateurs de comparaison spécifiés.</span><span class="sxs-lookup"><span data-stu-id="b4a8a-103">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4a8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4a8a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4a8a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b4a8a-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="b4a8a-106">dans Objet `IAssemblyName` auquel comparer ce `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="b4a8a-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="b4a8a-107">dans Combinaison d’opérations de bits de valeurs [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) qui influencent la comparaison.</span><span class="sxs-lookup"><span data-stu-id="b4a8a-107">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4a8a-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="b4a8a-108">Requirements</span></span>  
 <span data-ttu-id="b4a8a-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4a8a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4a8a-110">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b4a8a-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b4a8a-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4a8a-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4a8a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4a8a-112">See also</span></span>

- [<span data-ttu-id="b4a8a-113">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="b4a8a-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="b4a8a-114">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="b4a8a-114">Fusion Enumerations</span></span>](fusion-enumerations.md)
