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
ms.openlocfilehash: 3149318a1dc20c96bccc9b81347192bfa2e4bfdf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554825"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="d871b-102">ICorDebugILFrame4::EnumerateLocalVariablesEx, méthode</span><span class="sxs-lookup"><span data-stu-id="d871b-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="d871b-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="d871b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d871b-104">Obtient un énumérateur pour la variable locale dans le frame, et peut inclure des variables ajoutées dans l'instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="d871b-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d871b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d871b-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d871b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d871b-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="d871b-107">dans Membre de l’énumération [ILCodeKind](ilcodekind-enumeration.md) qui spécifie si les variables ajoutées dans l’instrumentation ReJIT du profileur sont incluses dans le frame.</span><span class="sxs-lookup"><span data-stu-id="d871b-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="d871b-108">à Pointeur vers l’adresse d’un objet « ICorDebugValueEnum » qui est l’énumérateur pour les variables locales dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="d871b-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d871b-109">Notes</span><span class="sxs-lookup"><span data-stu-id="d871b-109">Remarks</span></span>  
 <span data-ttu-id="d871b-110">Cette méthode est similaire à la méthode [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) , à ceci près qu’elle accède éventuellement aux variables ajoutées dans l’instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="d871b-110">This method is similar to the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="d871b-111">Affecter `flags` à `ILCODE_ORIGINAL_IL` équivaut à appeler [ICorDebugILFrame :: EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="d871b-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="d871b-112">La définition de `flags` à `ILCODE_REJIT_IL` autorise le débogueur à accéder aux variables locales ajoutées dans l'instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="d871b-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="d871b-113">Si le langage intermédiaire n'est pas instrumenté, l'énumération est vide et la méthode retourne `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="d871b-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="d871b-114">L'énumérateur peut ne pas inclure toutes les variables locales dans la méthode en cours d'exécution, car il est possible que certaines d'entre elles ne soient pas actives.</span><span class="sxs-lookup"><span data-stu-id="d871b-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d871b-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d871b-115">Requirements</span></span>  
 <span data-ttu-id="d871b-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d871b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d871b-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d871b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d871b-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d871b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d871b-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d871b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d871b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d871b-120">See also</span></span>

- [<span data-ttu-id="d871b-121">ICorDebugILFrame4, interface</span><span class="sxs-lookup"><span data-stu-id="d871b-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="d871b-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d871b-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d871b-123">ReJIT : Guide pratique</span><span class="sxs-lookup"><span data-stu-id="d871b-123">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
