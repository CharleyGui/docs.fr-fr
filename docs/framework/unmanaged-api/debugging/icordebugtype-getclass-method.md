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
ms.openlocfilehash: 1cb9729f175a2e82e88386b0694467c6fe05636a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684458"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="9ff92-102">ICorDebugType::GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="9ff92-102">ICorDebugType::GetClass Method</span></span>

<span data-ttu-id="9ff92-103">Obtient un pointeur d’interface vers une ICorDebugClass qui représente le type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="9ff92-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ff92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ff92-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ff92-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ff92-105">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="9ff92-106">à Pointeur vers l’adresse d’une `ICorDebugClass` interface qui représente le type générique non instancié.</span><span class="sxs-lookup"><span data-stu-id="9ff92-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ff92-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ff92-107">Remarks</span></span>  

 <span data-ttu-id="9ff92-108">`GetClass` peut être appelé uniquement sous certaines conditions.</span><span class="sxs-lookup"><span data-stu-id="9ff92-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="9ff92-109">Appelez [ICorDebugType :: GetType](icordebugtype-gettype-method.md) avant d’appeler `GetClass` .</span><span class="sxs-lookup"><span data-stu-id="9ff92-109">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="9ff92-110">Si `ICorDebugType::GetType` retourne une valeur CorElementType qui est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, `GetClass` peut être appelé pour obtenir le type non instancié d’un type générique.</span><span class="sxs-lookup"><span data-stu-id="9ff92-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ff92-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9ff92-111">Requirements</span></span>  

 <span data-ttu-id="9ff92-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ff92-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ff92-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ff92-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ff92-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ff92-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ff92-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ff92-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
