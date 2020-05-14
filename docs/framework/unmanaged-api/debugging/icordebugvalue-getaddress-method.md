---
title: ICorDebugValue::GetAddress, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 467ba53f90081f0c3499fb22acab96b5e380a3f4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395842"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="53d39-102">ICorDebugValue::GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="53d39-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="53d39-103">Obtient l’adresse de cet objet « ICorDebugValue », qui est en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="53d39-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53d39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53d39-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53d39-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="53d39-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="53d39-106">à Pointeur vers un `CORDB_ADDRESS` objet qui spécifie l’adresse de cet objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="53d39-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53d39-107">Notes</span><span class="sxs-lookup"><span data-stu-id="53d39-107">Remarks</span></span>  
 <span data-ttu-id="53d39-108">Si la valeur n’est pas disponible, 0 (zéro) est retourné.</span><span class="sxs-lookup"><span data-stu-id="53d39-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="53d39-109">Cela peut se produire si la valeur est au moins partiellement dans les registres ou stockée dans un handle de garbage collector ( `GCHandle` ).</span><span class="sxs-lookup"><span data-stu-id="53d39-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53d39-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="53d39-110">Requirements</span></span>  
 <span data-ttu-id="53d39-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53d39-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53d39-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53d39-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53d39-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53d39-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53d39-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53d39-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d39-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53d39-115">See also</span></span>
