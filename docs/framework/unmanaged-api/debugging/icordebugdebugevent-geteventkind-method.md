---
title: ICorDebugDebugEvent::GetEventKind, méthode
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 7876dc6ec5ecee52b64e54e1c42533f8348e4dc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713676"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="81a61-102">ICorDebugDebugEvent::GetEventKind, méthode</span><span class="sxs-lookup"><span data-stu-id="81a61-102">ICorDebugDebugEvent::GetEventKind Method</span></span>

<span data-ttu-id="81a61-103">Indique le type d'événement représenté par cet objet `ICorDebugDebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="81a61-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81a61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81a61-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="81a61-105">Parameters</span></span>  

 <span data-ttu-id="81a61-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="81a61-106">pDebugEventKind</span></span>  
 <span data-ttu-id="81a61-107">Pointeur vers un membre de l’énumération [cordebugdebugeventkind,](cordebugdebugeventkind-enumeration.md) qui indique le type d’événement.</span><span class="sxs-lookup"><span data-stu-id="81a61-107">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81a61-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="81a61-108">Remarks</span></span>  

 <span data-ttu-id="81a61-109">En fonction de la valeur de `pDebugEventKind`, vous pouvez appeler `QueryInterface` pour obtenir une interface d'événement de débogage plus précise qui fournit des données supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="81a61-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81a61-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="81a61-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81a61-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="81a61-111">Requirements</span></span>  

 <span data-ttu-id="81a61-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81a61-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81a61-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81a61-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81a61-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81a61-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81a61-115">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81a61-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a61-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81a61-116">See also</span></span>

- [<span data-ttu-id="81a61-117">ICorDebugDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="81a61-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="81a61-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="81a61-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
