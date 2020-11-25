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
ms.openlocfilehash: ff2913399e1dbeb33bbfb697058db3caf2a8d1fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713104"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="f9faf-102">ICorDebugProcess5::GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="f9faf-102">ICorDebugProcess5::GetObject Method</span></span>

<span data-ttu-id="f9faf-103">Convertit une adresse d’objet en objet « ICorDebugObjectValue ».</span><span class="sxs-lookup"><span data-stu-id="f9faf-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9faf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9faf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9faf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f9faf-105">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="f9faf-106">dans Adresse de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f9faf-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="f9faf-107">à Pointeur vers l’adresse d’un objet « ICorDebugObjectValue ».</span><span class="sxs-lookup"><span data-stu-id="f9faf-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9faf-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="f9faf-108">Remarks</span></span>  

 <span data-ttu-id="f9faf-109">Si `addr` ne pointe pas vers un objet managé valide, la `GetObject` méthode retourne `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="f9faf-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9faf-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f9faf-110">Requirements</span></span>  

 <span data-ttu-id="f9faf-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9faf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9faf-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9faf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9faf-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9faf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9faf-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9faf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9faf-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9faf-115">See also</span></span>

- [<span data-ttu-id="f9faf-116">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="f9faf-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="f9faf-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f9faf-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
