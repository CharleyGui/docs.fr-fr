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
ms.openlocfilehash: 84b5da043f9bd437ee9099135ba865c1ab23bb9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129671"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="3d7b9-102">ICorDebugProcess5::EnumerateGCReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="3d7b9-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="3d7b9-103">Obtient un énumérateur pour tous les objets qui doivent être récupérés par le garbage collector dans un processus.</span><span class="sxs-lookup"><span data-stu-id="3d7b9-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d7b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d7b9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d7b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d7b9-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="3d7b9-106">dans Valeur booléenne qui indique si les références faibles doivent également être énumérées.</span><span class="sxs-lookup"><span data-stu-id="3d7b9-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="3d7b9-107">Si `enumerateWeakReferences` est `true`, l’énumérateur `ppEnum` contient à la fois des références fortes et des références faibles.</span><span class="sxs-lookup"><span data-stu-id="3d7b9-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="3d7b9-108">Si `enumerateWeakReferences` est `false`, l’énumérateur comprend uniquement des références fortes.</span><span class="sxs-lookup"><span data-stu-id="3d7b9-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="3d7b9-109">à Pointeur vers l’adresse d’un [icordebuggcreferenceenum,](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) qui est un énumérateur pour les objets qui doivent être récupérés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="3d7b9-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d7b9-110">Notes</span><span class="sxs-lookup"><span data-stu-id="3d7b9-110">Remarks</span></span>  
 <span data-ttu-id="3d7b9-111">Cette méthode fournit un moyen de déterminer la chaîne de racine complète pour tout objet managé dans un processus et peut être utilisée pour déterminer la raison pour laquelle un objet est toujours actif.</span><span class="sxs-lookup"><span data-stu-id="3d7b9-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d7b9-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="3d7b9-112">Requirements</span></span>  
 <span data-ttu-id="3d7b9-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d7b9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d7b9-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d7b9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d7b9-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d7b9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d7b9-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d7b9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d7b9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d7b9-117">See also</span></span>

- [<span data-ttu-id="3d7b9-118">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="3d7b9-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="3d7b9-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3d7b9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
