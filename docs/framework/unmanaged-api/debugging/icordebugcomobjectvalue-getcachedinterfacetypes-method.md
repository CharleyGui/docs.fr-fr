---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
ms.openlocfilehash: f720b06581ac60c8bd68dc5e85f15843fd9425f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788904"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="d9cce-102">ICorDebugComObjectValue::GetCachedInterfaceTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="d9cce-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="d9cce-103">Fournit un énumérateur pour les types d’interface sur lesquels l’objet actuel a fait l’objet d’un cast ou utilisé.</span><span class="sxs-lookup"><span data-stu-id="d9cce-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9cce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9cce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9cce-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d9cce-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="d9cce-106">dans Valeur qui indique si la méthode retourne uniquement des interfaces Windows Runtime (interfaces`IInspectable`) ou toutes les interfaces COM mises en cache par le wrapper RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="d9cce-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="d9cce-107">à Pointeur vers l’adresse d’un énumérateur ICorDebugTypeEnum qui fournit l’accès aux objets ICorDebugType qui représentent des types d’interfaces mis en cache filtrés en fonction de `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="d9cce-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9cce-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d9cce-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9cce-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d9cce-109">Requirements</span></span>  
 <span data-ttu-id="d9cce-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9cce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9cce-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9cce-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9cce-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9cce-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9cce-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9cce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9cce-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9cce-114">See also</span></span>

- [<span data-ttu-id="d9cce-115">ICorDebugComObjectValue, interface</span><span class="sxs-lookup"><span data-stu-id="d9cce-115">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="d9cce-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d9cce-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
