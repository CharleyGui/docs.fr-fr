---
title: ICorDebugDebugEvent, interface
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: a66012651d4b307d06a5a3bff675a248cc0ee376
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976354"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="c47ea-102">ICorDebugDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="c47ea-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="c47ea-103">Définit l’interface de base de laquelle dérivent tous les événements de débogage `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="c47ea-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c47ea-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c47ea-104">Methods</span></span>  
  
|<span data-ttu-id="c47ea-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="c47ea-105">Method</span></span>|<span data-ttu-id="c47ea-106">Description</span><span class="sxs-lookup"><span data-stu-id="c47ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c47ea-107">GetEventKind, méthode</span><span class="sxs-lookup"><span data-stu-id="c47ea-107">GetEventKind Method</span></span>](icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="c47ea-108">Indique le type d'événement représenté par cet objet `ICorDebugDebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="c47ea-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="c47ea-109">GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="c47ea-109">GetThread Method</span></span>](icordebugdebugevent-getthread-method.md)|<span data-ttu-id="c47ea-110">Obtient le thread sur lequel l'événement s'est produit.</span><span class="sxs-lookup"><span data-stu-id="c47ea-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c47ea-111">Notes </span><span class="sxs-lookup"><span data-stu-id="c47ea-111">Remarks</span></span>  
 <span data-ttu-id="c47ea-112">Les interfaces suivantes sont dérivées de l'interface `ICorDebugDebugEvent` :</span><span class="sxs-lookup"><span data-stu-id="c47ea-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="c47ea-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="c47ea-113">ICorDebugExceptionDebugEvent</span></span>](icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="c47ea-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="c47ea-114">ICorDebugModuleDebugEvent</span></span>](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="c47ea-115">L'interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c47ea-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="c47ea-116">Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c47ea-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c47ea-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c47ea-117">Requirements</span></span>  
 <span data-ttu-id="c47ea-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c47ea-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c47ea-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c47ea-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c47ea-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c47ea-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c47ea-121">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c47ea-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c47ea-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c47ea-122">See also</span></span>

- [<span data-ttu-id="c47ea-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c47ea-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c47ea-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="c47ea-124">Debugging</span></span>](index.md)
