---
title: IAssemblyEnum::GetNextAssembly, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57d64096ea693be41359aef63c04674ca77769c6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760974"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="4683c-102">IAssemblyEnum::GetNextAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="4683c-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="4683c-103">Obtient un pointeur vers la prochaine [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contenues dans cette [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="4683c-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4683c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4683c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4683c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4683c-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="4683c-106">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="4683c-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4683c-107">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="4683c-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="4683c-108">[out] Retourné `IAssemblyName` pointeur.</span><span class="sxs-lookup"><span data-stu-id="4683c-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4683c-109">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="4683c-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4683c-110">`dwFlags` doit être 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="4683c-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4683c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4683c-111">Requirements</span></span>  
 <span data-ttu-id="4683c-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4683c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4683c-113">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4683c-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4683c-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4683c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4683c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4683c-115">See also</span></span>

- [<span data-ttu-id="4683c-116">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="4683c-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="4683c-117">IAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="4683c-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
