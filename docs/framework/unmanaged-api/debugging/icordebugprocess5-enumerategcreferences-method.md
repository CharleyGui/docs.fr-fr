---
title: ICorDebugProcess5::EnumerateGCReferences, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: a97c14d83f99c847bb8569a33e175ab6eb5bccd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178618"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="ac495-102">ICorDebugProcess5::EnumerateGCReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="ac495-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="ac495-103">Obtient un enumérateur pour tous les objets qui doivent être collectés dans les ordures dans un processus.</span><span class="sxs-lookup"><span data-stu-id="ac495-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac495-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac495-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac495-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ac495-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="ac495-106">[dans] Une valeur Boolean qui indique si des références faibles doivent également être énumérées.</span><span class="sxs-lookup"><span data-stu-id="ac495-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="ac495-107">Si `enumerateWeakReferences` `true`c’est le cas, l’énumérateur `ppEnum` comprend à la fois des références fortes et des références faibles.</span><span class="sxs-lookup"><span data-stu-id="ac495-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="ac495-108">Si `enumerateWeakReferences` `false`c’est le cas, l’énumérateur ne comprend que des références fortes.</span><span class="sxs-lookup"><span data-stu-id="ac495-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="ac495-109">[out] Un pointeur à l’adresse d’un [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) qui est un enumérateur pour les objets à collecter.</span><span class="sxs-lookup"><span data-stu-id="ac495-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac495-110">Notes </span><span class="sxs-lookup"><span data-stu-id="ac495-110">Remarks</span></span>  
 <span data-ttu-id="ac495-111">Cette méthode fournit un moyen de déterminer la chaîne d’enracinement complète pour tout objet géré dans un processus et peut être utilisé pour déterminer pourquoi un objet est encore en vie.</span><span class="sxs-lookup"><span data-stu-id="ac495-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac495-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ac495-112">Requirements</span></span>  
 <span data-ttu-id="ac495-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac495-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac495-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac495-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac495-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac495-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac495-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac495-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac495-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac495-117">See also</span></span>

- [<span data-ttu-id="ac495-118">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="ac495-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="ac495-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ac495-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
