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
ms.openlocfilehash: 73c531378355100fdfca264ea9f96ff4d7c7ceda
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796686"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="8280a-102">IAssemblyEnum::GetNextAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="8280a-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="8280a-103">Obtient un pointeur vers l' [IAssemblyName](iassemblyname-interface.md) suivant contenu dans cet objet [IAssemblyEnum](iassemblyenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8280a-103">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8280a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8280a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8280a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8280a-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="8280a-106">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="8280a-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="8280a-107">`pvReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="8280a-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="8280a-108">à Pointeur retourné `IAssemblyName` .</span><span class="sxs-lookup"><span data-stu-id="8280a-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8280a-109">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="8280a-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="8280a-110">`dwFlags`doit avoir la valeur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="8280a-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8280a-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8280a-111">Requirements</span></span>  
 <span data-ttu-id="8280a-112">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8280a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8280a-113">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="8280a-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8280a-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8280a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8280a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8280a-115">See also</span></span>

- [<span data-ttu-id="8280a-116">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="8280a-116">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="8280a-117">IAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="8280a-117">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
