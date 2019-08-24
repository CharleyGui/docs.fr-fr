---
title: ICorDebugAssembly3::GetContainerAssembly, méthode
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4cda67145a0e624f87e93cf02ebdb6bc77c34d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69987599"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="5100e-102">ICorDebugAssembly3::GetContainerAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="5100e-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="5100e-103">Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="5100e-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5100e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5100e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5100e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5100e-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="5100e-106">Pointeur vers l’adresse d’un objet ICorDebugAssembly qui représente l’assembly de conteneur, ou **null** si l’appel de méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="5100e-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5100e-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5100e-107">Return Value</span></span>  
 <span data-ttu-id="5100e-108">`S_OK`Si l’appel de la méthode a échoué; Sinon, `S_FALSE`et `ppAssembly` a la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="5100e-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5100e-109">Notes</span><span class="sxs-lookup"><span data-stu-id="5100e-109">Remarks</span></span>  
 <span data-ttu-id="5100e-110">Si cet assembly a été fusionné avec d’autres assemblys dans un seul assembly conteneur, cette méthode retourne l’assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="5100e-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="5100e-111">Pour plus d’informations et de terminologie, consultez la rubrique [ICorDebugProcess6:: enablevirtualmodulesplitting,](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5100e-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5100e-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5100e-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5100e-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5100e-113">Requirements</span></span>  
 <span data-ttu-id="5100e-114">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5100e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5100e-115">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5100e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5100e-116">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5100e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5100e-117">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5100e-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5100e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5100e-118">See also</span></span>

- [<span data-ttu-id="5100e-119">ICorDebugAssembly3, interface</span><span class="sxs-lookup"><span data-stu-id="5100e-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="5100e-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5100e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
