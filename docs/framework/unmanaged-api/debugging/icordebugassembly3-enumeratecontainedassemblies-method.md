---
title: ICorDebugAssembly3::EnumerateContainedAssemblies, méthode
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 1e040453d5eb7a312f2e665974486492b99de16d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719682"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="fece3-102">ICorDebugAssembly3::EnumerateContainedAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="fece3-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>

<span data-ttu-id="fece3-103">Obtient un énumérateur pour les assemblys contenus dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="fece3-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fece3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fece3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fece3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fece3-105">Parameters</span></span>  

 `ppAssemblies`  
 <span data-ttu-id="fece3-106">[out] Pointeur vers l'adresse d'un objet d'interface ICorDebugAssemblyEnum qui est l'énumérateur.</span><span class="sxs-lookup"><span data-stu-id="fece3-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fece3-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="fece3-107">Return Value</span></span>  

 <span data-ttu-id="fece3-108">`S_OK` si cet objet `ICorDebugAssembly3` est un conteneur ; sinon, `S_FALSE`, et l'énumération est vide.</span><span class="sxs-lookup"><span data-stu-id="fece3-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fece3-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="fece3-109">Remarks</span></span>  

 <span data-ttu-id="fece3-110">Des symboles doivent être utilisés pour énumérer les assemblys contenus dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="fece3-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="fece3-111">S'ils ne sont pas présents, la méthode retourne `S_FALSE`, et aucun énumérateur valide n'est fourni.</span><span class="sxs-lookup"><span data-stu-id="fece3-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fece3-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fece3-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fece3-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fece3-113">Requirements</span></span>  

 <span data-ttu-id="fece3-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fece3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fece3-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fece3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fece3-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fece3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fece3-117">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fece3-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fece3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fece3-118">See also</span></span>

- [<span data-ttu-id="fece3-119">ICorDebugAssembly3, interface</span><span class="sxs-lookup"><span data-stu-id="fece3-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="fece3-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="fece3-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
