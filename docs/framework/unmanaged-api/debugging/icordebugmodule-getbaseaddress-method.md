---
title: ICorDebugModule::GetBaseAddress, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
ms.openlocfilehash: aff8fb0a2316817e413f10e82215556f1f54fbc4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109639"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="e0fa1-102">ICorDebugModule::GetBaseAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="e0fa1-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="e0fa1-103">Obtient l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="e0fa1-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0fa1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0fa1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0fa1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e0fa1-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="e0fa1-106">à `CORDB_ADDRESS` qui spécifie l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="e0fa1-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0fa1-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e0fa1-107">Remarks</span></span>  
 <span data-ttu-id="e0fa1-108">Si le module est une image native (autrement dit, si le module a été produit par le générateur d’images natives, NGen. exe), son adresse de base sera égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="e0fa1-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0fa1-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="e0fa1-109">Requirements</span></span>  
 <span data-ttu-id="e0fa1-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0fa1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0fa1-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0fa1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0fa1-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0fa1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0fa1-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0fa1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0fa1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0fa1-114">See also</span></span>
