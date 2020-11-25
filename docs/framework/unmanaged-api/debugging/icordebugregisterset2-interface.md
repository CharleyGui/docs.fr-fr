---
title: ICorDebugRegisterSet2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: c04bb3a7584fcb783af929e87713dbec67ad705f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712317"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="3bf4e-102">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="3bf4e-102">ICorDebugRegisterSet2 Interface</span></span>

<span data-ttu-id="3bf4e-103">Étend les fonctionnalités de l’interface [ICorDebugRegisterSet](icordebugregisterset-interface.md) pour les plateformes matérielles qui ont plus de 64 registres.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-103">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3bf4e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3bf4e-104">Methods</span></span>  
  
|<span data-ttu-id="3bf4e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="3bf4e-105">Method</span></span>|<span data-ttu-id="3bf4e-106">Description</span><span class="sxs-lookup"><span data-stu-id="3bf4e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3bf4e-107">GetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="3bf4e-107">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="3bf4e-108">Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) spécifié par le masque de bits.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="3bf4e-109">GetRegistersAvailable, méthode</span><span class="sxs-lookup"><span data-stu-id="3bf4e-109">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="3bf4e-110">Obtient un tableau d’octets qui fournit une bitmap des registres disponibles.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="3bf4e-111">SetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="3bf4e-111">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="3bf4e-112">Non implémenté dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bf4e-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="3bf4e-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bf4e-114">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="3bf4e-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bf4e-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3bf4e-115">Requirements</span></span>  

 <span data-ttu-id="3bf4e-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bf4e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bf4e-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bf4e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bf4e-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bf4e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bf4e-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bf4e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf4e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bf4e-120">See also</span></span>

- [<span data-ttu-id="3bf4e-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3bf4e-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3bf4e-122">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="3bf4e-122">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
