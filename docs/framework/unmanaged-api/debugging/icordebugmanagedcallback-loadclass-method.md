---
title: ICorDebugManagedCallback::LoadClass, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: 5d35ab4610ffa04d15dd2404fdf8010308bcb42a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212728"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="3b5d5-102">ICorDebugManagedCallback::LoadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="3b5d5-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="3b5d5-103">Notifie le débogueur qu’une classe a été chargée.</span><span class="sxs-lookup"><span data-stu-id="3b5d5-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b5d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b5d5-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b5d5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b5d5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3b5d5-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel la classe a été chargée.</span><span class="sxs-lookup"><span data-stu-id="3b5d5-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="3b5d5-107">dans Pointeur vers un objet ICorDebugClass qui représente la classe.</span><span class="sxs-lookup"><span data-stu-id="3b5d5-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b5d5-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="3b5d5-108">Remarks</span></span>  
 <span data-ttu-id="3b5d5-109">Ce rappel se produit uniquement si le chargement de la classe a été activé pour le module qui contient la classe.</span><span class="sxs-lookup"><span data-stu-id="3b5d5-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="3b5d5-110">Le chargement de classe est toujours activé pour les modules dynamiques.</span><span class="sxs-lookup"><span data-stu-id="3b5d5-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="3b5d5-111">Le `LoadClass` rappel fournit un moment approprié pour lier les points d’arrêt aux classes nouvellement générées dans les modules dynamiques.</span><span class="sxs-lookup"><span data-stu-id="3b5d5-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b5d5-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3b5d5-112">Requirements</span></span>  
 <span data-ttu-id="3b5d5-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b5d5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b5d5-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b5d5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b5d5-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b5d5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b5d5-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b5d5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b5d5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b5d5-117">See also</span></span>

- [<span data-ttu-id="3b5d5-118">UnloadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="3b5d5-118">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="3b5d5-119">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="3b5d5-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
