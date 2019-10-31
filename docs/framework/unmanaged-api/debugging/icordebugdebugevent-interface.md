---
title: ICorDebugDebugEvent, interface
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: ea42faa4001fa880354690df1551de3be767e683
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137037"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="16bd8-102">ICorDebugDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="16bd8-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="16bd8-103">Définit l’interface de base de laquelle dérivent tous les événements de débogage `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="16bd8-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16bd8-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="16bd8-104">Methods</span></span>  
  
|<span data-ttu-id="16bd8-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="16bd8-105">Method</span></span>|<span data-ttu-id="16bd8-106">Description</span><span class="sxs-lookup"><span data-stu-id="16bd8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16bd8-107">GetEventKind, méthode</span><span class="sxs-lookup"><span data-stu-id="16bd8-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="16bd8-108">Indique le type d'événement représenté par cet objet `ICorDebugDebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="16bd8-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="16bd8-109">GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="16bd8-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="16bd8-110">Obtient le thread sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="16bd8-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16bd8-111">Notes</span><span class="sxs-lookup"><span data-stu-id="16bd8-111">Remarks</span></span>  
 <span data-ttu-id="16bd8-112">Les interfaces suivantes sont dérivées de l'interface `ICorDebugDebugEvent` :</span><span class="sxs-lookup"><span data-stu-id="16bd8-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="16bd8-113">Icordebugexceptiondebugevent,</span><span class="sxs-lookup"><span data-stu-id="16bd8-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="16bd8-114">Icordebugmoduledebugevent,</span><span class="sxs-lookup"><span data-stu-id="16bd8-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="16bd8-115">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="16bd8-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="16bd8-116">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="16bd8-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16bd8-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="16bd8-117">Requirements</span></span>  
 <span data-ttu-id="16bd8-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16bd8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16bd8-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16bd8-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16bd8-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16bd8-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16bd8-121">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16bd8-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16bd8-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16bd8-122">See also</span></span>

- [<span data-ttu-id="16bd8-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="16bd8-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="16bd8-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="16bd8-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
