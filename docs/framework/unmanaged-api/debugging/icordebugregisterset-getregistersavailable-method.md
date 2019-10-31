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
ms.openlocfilehash: 9d8bd6ab13fa408fd7390aaeb76baee274742f48
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137702"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="332a6-102">ICorDebugRegisterSet::GetRegistersAvailable, méthode</span><span class="sxs-lookup"><span data-stu-id="332a6-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="332a6-103">Obtient un masque de bits indiquant les registres actuellement disponibles dans ce [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="332a6-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="332a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="332a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="332a6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="332a6-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="332a6-106">à Masque de bits qui indique les registres actuellement disponibles.</span><span class="sxs-lookup"><span data-stu-id="332a6-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="332a6-107">Notes</span><span class="sxs-lookup"><span data-stu-id="332a6-107">Remarks</span></span>  
 <span data-ttu-id="332a6-108">Un registre peut ne pas être disponible si sa valeur ne peut pas être déterminée pour la situation donnée.</span><span class="sxs-lookup"><span data-stu-id="332a6-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="332a6-109">Le masque retourné contient un bit pour chaque registre (1 < < l’index du registre).</span><span class="sxs-lookup"><span data-stu-id="332a6-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="332a6-110">La valeur de bit est 1 si le Registre est disponible, ou 0 s’il n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="332a6-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="332a6-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="332a6-111">Requirements</span></span>  
 <span data-ttu-id="332a6-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="332a6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="332a6-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="332a6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="332a6-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="332a6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="332a6-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="332a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="332a6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="332a6-116">See also</span></span>

- [<span data-ttu-id="332a6-117">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="332a6-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="332a6-118">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="332a6-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
