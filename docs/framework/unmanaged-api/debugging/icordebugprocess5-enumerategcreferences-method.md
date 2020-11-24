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
ms.openlocfilehash: 0f2f5acfc6a23398b15af3a63345050eb0dfd5b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687188"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="8ae11-102">ICorDebugProcess5::EnumerateGCReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="8ae11-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>

<span data-ttu-id="8ae11-103">Obtient un énumérateur pour tous les objets qui doivent être récupérés par le garbage collector dans un processus.</span><span class="sxs-lookup"><span data-stu-id="8ae11-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ae11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ae11-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ae11-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ae11-105">Parameters</span></span>  

 `enumerateWeakReferences`  
 <span data-ttu-id="8ae11-106">dans Valeur booléenne qui indique si les références faibles doivent également être énumérées.</span><span class="sxs-lookup"><span data-stu-id="8ae11-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="8ae11-107">Si `enumerateWeakReferences` est `true` , l' `ppEnum` énumérateur contient à la fois des références fortes et des références faibles.</span><span class="sxs-lookup"><span data-stu-id="8ae11-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="8ae11-108">Si `enumerateWeakReferences` est `false` , l’énumérateur comprend uniquement des références fortes.</span><span class="sxs-lookup"><span data-stu-id="8ae11-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="8ae11-109">à Pointeur vers l’adresse d’un [icordebuggcreferenceenum,](icordebuggcreferenceenum-interface.md) qui est un énumérateur pour les objets qui doivent être récupérés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="8ae11-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ae11-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="8ae11-110">Remarks</span></span>  

 <span data-ttu-id="8ae11-111">Cette méthode fournit un moyen de déterminer la chaîne de racine complète pour tout objet managé dans un processus et peut être utilisée pour déterminer la raison pour laquelle un objet est toujours actif.</span><span class="sxs-lookup"><span data-stu-id="8ae11-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ae11-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8ae11-112">Requirements</span></span>  

 <span data-ttu-id="8ae11-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ae11-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ae11-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ae11-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ae11-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ae11-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ae11-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ae11-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae11-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ae11-117">See also</span></span>

- [<span data-ttu-id="8ae11-118">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="8ae11-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="8ae11-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8ae11-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
