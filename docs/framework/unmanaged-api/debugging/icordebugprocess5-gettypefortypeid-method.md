---
title: ICorDebugProcess5::GetTypeForTypeID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: bb25c9235e4fcded5c230d2d417b9d41bbdd9b19
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792336"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="7e72b-102">ICorDebugProcess5::GetTypeForTypeID, méthode</span><span class="sxs-lookup"><span data-stu-id="7e72b-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="7e72b-103">Convertit un identificateur de type en valeur ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="7e72b-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e72b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e72b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e72b-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="7e72b-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="7e72b-106">dans Identificateur de type.</span><span class="sxs-lookup"><span data-stu-id="7e72b-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="7e72b-107">à Pointeur vers l’adresse d’un objet ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="7e72b-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e72b-108">Notes</span><span class="sxs-lookup"><span data-stu-id="7e72b-108">Remarks</span></span>  
 <span data-ttu-id="7e72b-109">Dans certains cas, les méthodes qui retournent un identificateur de type peuvent retourner une valeur de `COR_TYPEID` null.</span><span class="sxs-lookup"><span data-stu-id="7e72b-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="7e72b-110">Si cette valeur est passée comme argument `id`, la méthode `GetTypeForTypeID` échoue et retourne `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="7e72b-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e72b-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="7e72b-111">Requirements</span></span>  
 <span data-ttu-id="7e72b-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e72b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e72b-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e72b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e72b-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e72b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e72b-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e72b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e72b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e72b-116">See also</span></span>

- [<span data-ttu-id="7e72b-117">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="7e72b-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="7e72b-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7e72b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
