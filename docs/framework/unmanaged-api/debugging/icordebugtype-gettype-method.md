---
title: ICorDebugType::GetType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: 7f3010cccc584288608b3f6ba95efbeb95f271fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132059"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="ea02e-102">ICorDebugType::GetType, méthode</span><span class="sxs-lookup"><span data-stu-id="ea02e-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="ea02e-103">Obtient une valeur CorElementType qui décrit le type natif du <xref:System.Type> common language runtime (CLR) représenté par ce ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="ea02e-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea02e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea02e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea02e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ea02e-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="ea02e-106">à Pointeur vers une valeur de l’énumération `CorElementType` qui indique la <xref:System.Type> CLR que cette `ICorDebugType` représente.</span><span class="sxs-lookup"><span data-stu-id="ea02e-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea02e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="ea02e-107">Remarks</span></span>  
 <span data-ttu-id="ea02e-108">Si la valeur de `ty` est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, la méthode [ICorDebugType :: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) peut être appelée pour obtenir le type non instancié d’un type générique ; Sinon, n’appelez pas `ICorDebugType::GetClass`.</span><span class="sxs-lookup"><span data-stu-id="ea02e-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea02e-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="ea02e-109">Requirements</span></span>  
 <span data-ttu-id="ea02e-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea02e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea02e-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea02e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea02e-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea02e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea02e-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea02e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
