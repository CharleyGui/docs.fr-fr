---
title: Méthode ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 616675f839e562227558ece440bdfdf497747572
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784558"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="9ecc4-102">Méthode ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="9ecc4-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="9ecc4-103">Obtient un énumérateur pour les assemblys contenus dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ecc4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ecc4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ecc4-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="9ecc4-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="9ecc4-106">[out] Pointeur vers l'adresse d'un objet d'interface ICorDebugAssemblyEnum qui est l'énumérateur.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ecc4-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9ecc4-107">Return Value</span></span>  
 <span data-ttu-id="9ecc4-108">`S_OK` si cet objet `ICorDebugAssembly3` est un conteneur ; sinon, `S_FALSE`, et l'énumération est vide.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ecc4-109">Notes</span><span class="sxs-lookup"><span data-stu-id="9ecc4-109">Remarks</span></span>  
 <span data-ttu-id="9ecc4-110">Des symboles doivent être utilisés pour énumérer les assemblys contenus dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="9ecc4-111">S'ils ne sont pas présents, la méthode retourne `S_FALSE`, et aucun énumérateur valide n'est fourni.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ecc4-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ecc4-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="9ecc4-113">Requirements</span></span>  
 <span data-ttu-id="9ecc4-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ecc4-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ecc4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ecc4-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ecc4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ecc4-117">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ecc4-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ecc4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ecc4-118">See also</span></span>

- [<span data-ttu-id="9ecc4-119">ICorDebugAssembly3, interface</span><span class="sxs-lookup"><span data-stu-id="9ecc4-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="9ecc4-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9ecc4-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
