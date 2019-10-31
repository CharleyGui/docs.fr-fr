---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
ms.openlocfilehash: 69a7501d9b887b9504067409356bf302c47466e7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090251"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="f7e4a-102">ICorDebugILFrame4::EnumerateLocalVariablesEx, méthode</span><span class="sxs-lookup"><span data-stu-id="f7e4a-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="f7e4a-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="f7e4a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f7e4a-104">Obtient un énumérateur pour la variable locale dans le frame, et peut inclure des variables ajoutées dans l'instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="f7e4a-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e4a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7e4a-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7e4a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7e4a-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="f7e4a-107">dans Membre de l’énumération [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) qui spécifie si les variables ajoutées dans l’instrumentation ReJIT du profileur sont incluses dans le frame.</span><span class="sxs-lookup"><span data-stu-id="f7e4a-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="f7e4a-108">à Pointeur vers l’adresse d’un objet « ICorDebugValueEnum » qui est l’énumérateur pour les variables locales dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="f7e4a-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7e4a-109">Notes</span><span class="sxs-lookup"><span data-stu-id="f7e4a-109">Remarks</span></span>  
 <span data-ttu-id="f7e4a-110">Cette méthode est similaire à la méthode [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) , à ceci près qu’elle accède éventuellement aux variables ajoutées dans l’instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="f7e4a-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="f7e4a-111">La définition de `flags` sur `ILCODE_ORIGINAL_IL` revient à appeler [ICorDebugILFrame :: EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="f7e4a-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="f7e4a-112">La définition de `flags` à `ILCODE_REJIT_IL` autorise le débogueur à accéder aux variables locales ajoutées dans l'instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="f7e4a-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="f7e4a-113">Si le langage intermédiaire n'est pas instrumenté, l'énumération est vide et la méthode retourne `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="f7e4a-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="f7e4a-114">L'énumérateur peut ne pas inclure toutes les variables locales dans la méthode en cours d'exécution, car il est possible que certaines d'entre elles ne soient pas actives.</span><span class="sxs-lookup"><span data-stu-id="f7e4a-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7e4a-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="f7e4a-115">Requirements</span></span>  
 <span data-ttu-id="f7e4a-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7e4a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7e4a-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7e4a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7e4a-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7e4a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7e4a-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7e4a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e4a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7e4a-120">See also</span></span>

- [<span data-ttu-id="f7e4a-121">ICorDebugILFrame4, interface</span><span class="sxs-lookup"><span data-stu-id="f7e4a-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="f7e4a-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f7e4a-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f7e4a-123">ReJIT : Guide pratique</span><span class="sxs-lookup"><span data-stu-id="f7e4a-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
