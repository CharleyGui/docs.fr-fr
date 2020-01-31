---
title: ICorDebugProcess5::EnableNGENPolicy, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: 9497bea9b7cc5eb98876c923858dbcbc6adf9d07
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792451"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="dde2e-102">ICorDebugProcess5::EnableNGENPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="dde2e-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="dde2e-103">Définit une valeur qui détermine la façon dont une application charge les images natives lors de l’exécution sous un débogueur managé.</span><span class="sxs-lookup"><span data-stu-id="dde2e-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dde2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dde2e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dde2e-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="dde2e-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="dde2e-106">dans Constante [cordebugngenpolicy,](cordebugngenpolicy-enumeration.md) qui détermine la façon dont une application charge des images natives lors de l’exécution sous un débogueur managé.</span><span class="sxs-lookup"><span data-stu-id="dde2e-106">[in] A [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dde2e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="dde2e-107">Remarks</span></span>  
 <span data-ttu-id="dde2e-108">Si la stratégie est définie avec succès, la méthode retourne `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="dde2e-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="dde2e-109">Si `ePolicy` est en dehors de la plage des valeurs énumérées définies par [cordebugngenpolicy,](cordebugngenpolicy-enumeration.md), la méthode retourne `E_INVALIDARG` et l’appel de la méthode n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="dde2e-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="dde2e-110">Si la stratégie du générateur d’images natives (Ngen. exe) ne peut pas être mise à jour, la méthode retourne `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="dde2e-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="dde2e-111">La méthode `ICorDebugProcess5::EnableNGenPolicy` peut être appelée à tout moment pendant la durée de vie du processus.</span><span class="sxs-lookup"><span data-stu-id="dde2e-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="dde2e-112">La stratégie est appliquée pour tous les modules qui sont chargés après la définition de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="dde2e-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dde2e-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="dde2e-113">Requirements</span></span>  
 <span data-ttu-id="dde2e-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dde2e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dde2e-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dde2e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dde2e-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dde2e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dde2e-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dde2e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde2e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dde2e-118">See also</span></span>

- [<span data-ttu-id="dde2e-119">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="dde2e-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="dde2e-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="dde2e-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="dde2e-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="dde2e-121">Debugging</span></span>](index.md)
