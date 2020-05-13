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
ms.openlocfilehash: 0d98df05291ed8405addcfd183d7e02332e4e025
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209693"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="d8f82-102">ICorDebugProcess5::EnumerateGCReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="d8f82-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="d8f82-103">Obtient un énumérateur pour tous les objets qui doivent être récupérés par le garbage collector dans un processus.</span><span class="sxs-lookup"><span data-stu-id="d8f82-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8f82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8f82-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8f82-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8f82-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="d8f82-106">dans Valeur booléenne qui indique si les références faibles doivent également être énumérées.</span><span class="sxs-lookup"><span data-stu-id="d8f82-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="d8f82-107">Si `enumerateWeakReferences` est `true` , l' `ppEnum` énumérateur contient à la fois des références fortes et des références faibles.</span><span class="sxs-lookup"><span data-stu-id="d8f82-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="d8f82-108">Si `enumerateWeakReferences` est `false` , l’énumérateur comprend uniquement des références fortes.</span><span class="sxs-lookup"><span data-stu-id="d8f82-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="d8f82-109">à Pointeur vers l’adresse d’un [icordebuggcreferenceenum,](icordebuggcreferenceenum-interface.md) qui est un énumérateur pour les objets qui doivent être récupérés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="d8f82-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8f82-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="d8f82-110">Remarks</span></span>  
 <span data-ttu-id="d8f82-111">Cette méthode fournit un moyen de déterminer la chaîne de racine complète pour tout objet managé dans un processus et peut être utilisée pour déterminer la raison pour laquelle un objet est toujours actif.</span><span class="sxs-lookup"><span data-stu-id="d8f82-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8f82-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d8f82-112">Requirements</span></span>  
 <span data-ttu-id="d8f82-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8f82-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8f82-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8f82-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8f82-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8f82-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8f82-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8f82-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f82-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8f82-117">See also</span></span>

- [<span data-ttu-id="d8f82-118">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="d8f82-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="d8f82-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d8f82-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
