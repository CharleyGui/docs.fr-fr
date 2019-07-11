---
title: ICorDebugRegisterSet::GetRegistersAvailable, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d600b4687b86f5872f94a60ad3422be764cf5307
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747205"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="da6cd-102">ICorDebugRegisterSet::GetRegistersAvailable, méthode</span><span class="sxs-lookup"><span data-stu-id="da6cd-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="da6cd-103">Obtient un masque de bits indiquant les registres dans ce [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) sont actuellement disponibles.</span><span class="sxs-lookup"><span data-stu-id="da6cd-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da6cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da6cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da6cd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="da6cd-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="da6cd-106">[out] Un masque de bits qui indique quels registres sont actuellement disponibles.</span><span class="sxs-lookup"><span data-stu-id="da6cd-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da6cd-107">Notes</span><span class="sxs-lookup"><span data-stu-id="da6cd-107">Remarks</span></span>  
 <span data-ttu-id="da6cd-108">Un Registre est peut-être indisponible si sa valeur ne peut pas être déterminée pour la situation donnée.</span><span class="sxs-lookup"><span data-stu-id="da6cd-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="da6cd-109">Le masque retourné contient un bit pour chaque registre (1 << l’index du Registre).</span><span class="sxs-lookup"><span data-stu-id="da6cd-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="da6cd-110">La valeur de bit est 1 si le Registre est disponible, ou 0 s’il n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="da6cd-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da6cd-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="da6cd-111">Requirements</span></span>  
 <span data-ttu-id="da6cd-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da6cd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da6cd-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da6cd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da6cd-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da6cd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da6cd-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da6cd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da6cd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da6cd-116">See also</span></span>

- [<span data-ttu-id="da6cd-117">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="da6cd-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="da6cd-118">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="da6cd-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
