---
title: ICorDebugProcess5::GetObject, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
ms.openlocfilehash: 540ca78c5548d4fbdd3338671ea02314736f15cd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792361"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="390bd-102">ICorDebugProcess5::GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="390bd-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="390bd-103">Convertit une adresse d’objet en objet « ICorDebugObjectValue ».</span><span class="sxs-lookup"><span data-stu-id="390bd-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="390bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="390bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="390bd-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="390bd-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="390bd-106">dans Adresse de l’objet.</span><span class="sxs-lookup"><span data-stu-id="390bd-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="390bd-107">à Pointeur vers l’adresse d’un objet « ICorDebugObjectValue ».</span><span class="sxs-lookup"><span data-stu-id="390bd-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="390bd-108">Notes</span><span class="sxs-lookup"><span data-stu-id="390bd-108">Remarks</span></span>  
 <span data-ttu-id="390bd-109">Si `addr` ne pointe pas vers un objet managé valide, la méthode `GetObject` retourne `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="390bd-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="390bd-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="390bd-110">Requirements</span></span>  
 <span data-ttu-id="390bd-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="390bd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="390bd-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="390bd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="390bd-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="390bd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="390bd-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="390bd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="390bd-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="390bd-115">See also</span></span>

- [<span data-ttu-id="390bd-116">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="390bd-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="390bd-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="390bd-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
