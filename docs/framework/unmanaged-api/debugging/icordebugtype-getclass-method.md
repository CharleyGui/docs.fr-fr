---
title: ICorDebugType::GetClass, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: d403a8bfba3599a60d8af72307590f5a569480dd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791295"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="cc492-102">ICorDebugType::GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="cc492-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="cc492-103">Obtient un pointeur d’interface vers une ICorDebugClass qui représente le type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="cc492-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc492-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc492-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc492-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="cc492-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="cc492-106">à Pointeur vers l’adresse d’une interface `ICorDebugClass` qui représente le type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="cc492-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc492-107">Notes</span><span class="sxs-lookup"><span data-stu-id="cc492-107">Remarks</span></span>  
 <span data-ttu-id="cc492-108">les `GetClass` peuvent être appelées uniquement sous certaines conditions.</span><span class="sxs-lookup"><span data-stu-id="cc492-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="cc492-109">Appelez [ICorDebugType :: GetType](icordebugtype-gettype-method.md) avant d’appeler `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="cc492-109">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="cc492-110">Si `ICorDebugType::GetType` retourne une valeur CorElementType qui est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, `GetClass` peut être appelée pour obtenir le type non instancié d’un type générique.</span><span class="sxs-lookup"><span data-stu-id="cc492-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc492-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="cc492-111">Requirements</span></span>  
 <span data-ttu-id="cc492-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc492-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc492-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc492-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc492-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc492-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc492-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc492-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
