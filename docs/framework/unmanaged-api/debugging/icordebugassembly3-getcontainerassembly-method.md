---
title: Méthode ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 969cca6d5613670fc4b26fc973785b4874c3684c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778072"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="5c9d2-102">Méthode ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="5c9d2-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="5c9d2-103">Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="5c9d2-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c9d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c9d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c9d2-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="5c9d2-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="5c9d2-106">Pointeur vers l’adresse d’un objet ICorDebugAssembly qui représente l’assembly de conteneur, ou **null** si l’appel de méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="5c9d2-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c9d2-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5c9d2-107">Return Value</span></span>  
 <span data-ttu-id="5c9d2-108">`S_OK` si l’appel de la méthode a échoué ; Sinon, `S_FALSE`et `ppAssembly` a la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="5c9d2-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c9d2-109">Notes</span><span class="sxs-lookup"><span data-stu-id="5c9d2-109">Remarks</span></span>  
 <span data-ttu-id="5c9d2-110">Si cet assembly a été fusionné avec d’autres assemblys dans un seul assembly conteneur, cette méthode retourne l’assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="5c9d2-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="5c9d2-111">Pour plus d’informations et de terminologie, consultez la rubrique [ICorDebugProcess6 :: enablevirtualmodulesplitting,](icordebugprocess6-enablevirtualmodulesplitting-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5c9d2-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c9d2-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5c9d2-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c9d2-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="5c9d2-113">Requirements</span></span>  
 <span data-ttu-id="5c9d2-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c9d2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c9d2-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c9d2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c9d2-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c9d2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c9d2-117">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c9d2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9d2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c9d2-118">See also</span></span>

- [<span data-ttu-id="5c9d2-119">ICorDebugAssembly3, interface</span><span class="sxs-lookup"><span data-stu-id="5c9d2-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="5c9d2-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5c9d2-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
