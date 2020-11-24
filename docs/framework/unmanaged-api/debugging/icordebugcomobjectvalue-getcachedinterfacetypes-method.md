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
ms.openlocfilehash: f5f0f11683043f1c287dd3ca3071830bcfb46502
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677555"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="d598a-102">ICorDebugComObjectValue::GetCachedInterfaceTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="d598a-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>

<span data-ttu-id="d598a-103">Fournit un énumérateur pour les types d’interface sur lesquels l’objet actuel a fait l’objet d’un cast ou utilisé.</span><span class="sxs-lookup"><span data-stu-id="d598a-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d598a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d598a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d598a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d598a-105">Parameters</span></span>  

 `bIInspectableOnly`  
 <span data-ttu-id="d598a-106">dans Valeur qui indique si la méthode retourne uniquement Windows Runtime interfaces ( `IInspectable` interfaces) ou toutes les interfaces com mises en cache par le wrapper RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="d598a-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="d598a-107">à Pointeur vers l’adresse d’un énumérateur ICorDebugTypeEnum qui fournit l’accès aux objets ICorDebugType qui représentent des types d’interfaces mis en cache filtrés en fonction de `bIInspectableOnly` .</span><span class="sxs-lookup"><span data-stu-id="d598a-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d598a-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d598a-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d598a-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d598a-109">Requirements</span></span>  

 <span data-ttu-id="d598a-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d598a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d598a-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d598a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d598a-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d598a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d598a-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d598a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d598a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d598a-114">See also</span></span>

- [<span data-ttu-id="d598a-115">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="d598a-115">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="d598a-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d598a-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
