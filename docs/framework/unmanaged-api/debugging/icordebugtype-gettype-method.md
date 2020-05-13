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
ms.openlocfilehash: ac42c6254182ea775377a448a54d527b234c97dc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379926"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="425a2-102">ICorDebugType::GetType, méthode</span><span class="sxs-lookup"><span data-stu-id="425a2-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="425a2-103">Obtient une valeur CorElementType qui décrit le type natif du common language runtime (CLR) <xref:System.Type> représenté par ce ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="425a2-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="425a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="425a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="425a2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="425a2-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="425a2-106">à Pointeur vers une valeur de l' `CorElementType` énumération qui indique le CLR <xref:System.Type> que ce `ICorDebugType` représente.</span><span class="sxs-lookup"><span data-stu-id="425a2-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="425a2-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="425a2-107">Remarks</span></span>  
 <span data-ttu-id="425a2-108">Si la valeur de `ty` est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, la méthode [ICorDebugType :: GetClass](icordebugtype-getclass-method.md) peut être appelée pour obtenir le type non instancié pour un type générique ; sinon, n’appelez pas `ICorDebugType::GetClass` .</span><span class="sxs-lookup"><span data-stu-id="425a2-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="425a2-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="425a2-109">Requirements</span></span>  
 <span data-ttu-id="425a2-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="425a2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="425a2-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="425a2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="425a2-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="425a2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="425a2-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="425a2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
