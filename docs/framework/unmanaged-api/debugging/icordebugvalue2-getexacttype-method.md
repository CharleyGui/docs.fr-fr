---
title: ICorDebugValue2::GetExactType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: cb5bec66ab02de248109d8aaf444a93e67c2c6d2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720358"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="2f8dd-102">ICorDebugValue2::GetExactType, méthode</span><span class="sxs-lookup"><span data-stu-id="2f8dd-102">ICorDebugValue2::GetExactType Method</span></span>

<span data-ttu-id="2f8dd-103">Obtient un pointeur d’interface vers un objet « ICorDebugType » qui représente le <xref:System.Type> de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="2f8dd-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f8dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f8dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f8dd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2f8dd-105">Parameters</span></span>  

 `ppType`  
 <span data-ttu-id="2f8dd-106">à Pointeur vers l’adresse d’un `ICorDebugType` objet qui représente le <xref:System.Type> de la valeur représentée par cet objet « ICorDebugValue2 ».</span><span class="sxs-lookup"><span data-stu-id="2f8dd-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f8dd-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="2f8dd-107">Remarks</span></span>  

 <span data-ttu-id="2f8dd-108">La méthode qui prend en charge les génériques `GetExactType` remplace les méthodes [ICorDebugObjectValue :: GetClass](icordebugobjectvalue-getclass-method.md) et [ICorDebugValue :: GetType](icordebugvalue-gettype-method.md) , chacune d’elles retournant des informations sur le type d’une valeur.</span><span class="sxs-lookup"><span data-stu-id="2f8dd-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f8dd-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2f8dd-109">Requirements</span></span>  

 <span data-ttu-id="2f8dd-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f8dd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f8dd-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f8dd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f8dd-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f8dd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f8dd-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f8dd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8dd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f8dd-114">See also</span></span>
