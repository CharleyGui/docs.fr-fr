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
ms.openlocfilehash: de570507c4312f09def0908b9d56e5371c63527e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207290"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="8ac59-102">ICorDebugProcess5::GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="8ac59-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="8ac59-103">Convertit une adresse d’objet en objet « ICorDebugObjectValue ».</span><span class="sxs-lookup"><span data-stu-id="8ac59-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ac59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ac59-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ac59-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ac59-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="8ac59-106">dans Adresse de l’objet.</span><span class="sxs-lookup"><span data-stu-id="8ac59-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="8ac59-107">à Pointeur vers l’adresse d’un objet « ICorDebugObjectValue ».</span><span class="sxs-lookup"><span data-stu-id="8ac59-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ac59-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="8ac59-108">Remarks</span></span>  
 <span data-ttu-id="8ac59-109">Si `addr` ne pointe pas vers un objet managé valide, la `GetObject` méthode retourne `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="8ac59-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ac59-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8ac59-110">Requirements</span></span>  
 <span data-ttu-id="8ac59-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ac59-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ac59-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ac59-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ac59-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ac59-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ac59-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ac59-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac59-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ac59-115">See also</span></span>

- [<span data-ttu-id="8ac59-116">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="8ac59-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="8ac59-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8ac59-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
