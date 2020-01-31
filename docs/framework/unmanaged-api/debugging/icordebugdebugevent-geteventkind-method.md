---
title: Méthode ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 0c67f8bdce49b4e9200b501aaf00ae293cced7d7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783412"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="0e885-102">Méthode ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="0e885-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="0e885-103">Indique le type d'événement représenté par cet objet `ICorDebugDebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="0e885-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e885-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e885-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e885-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="0e885-105">Parameters</span></span>  
 <span data-ttu-id="0e885-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="0e885-106">pDebugEventKind</span></span>  
 <span data-ttu-id="0e885-107">Pointeur vers un membre de l’énumération [cordebugdebugeventkind,](cordebugdebugeventkind-enumeration.md) qui indique le type d’événement.</span><span class="sxs-lookup"><span data-stu-id="0e885-107">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e885-108">Notes</span><span class="sxs-lookup"><span data-stu-id="0e885-108">Remarks</span></span>  
 <span data-ttu-id="0e885-109">En fonction de la valeur de `pDebugEventKind`, vous pouvez appeler `QueryInterface` pour obtenir une interface d'événement de débogage plus précise qui fournit des données supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="0e885-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e885-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0e885-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e885-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="0e885-111">Requirements</span></span>  
 <span data-ttu-id="0e885-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e885-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e885-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e885-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e885-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e885-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e885-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e885-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e885-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e885-116">See also</span></span>

- [<span data-ttu-id="0e885-117">ICorDebugDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="0e885-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="0e885-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0e885-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
