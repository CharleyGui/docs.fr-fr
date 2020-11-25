---
title: Méthode ICorDebugVariableSymbol::SetValue
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: 3ef9b9b9a095d6d6026ffc38873661355d660488
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707839"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="b02f4-102">Méthode ICorDebugVariableSymbol::SetValue</span><span class="sxs-lookup"><span data-stu-id="b02f4-102">ICorDebugVariableSymbol::SetValue Method</span></span>

<span data-ttu-id="b02f4-103">Affecte la valeur d'un tableau d'octets à une variable.</span><span class="sxs-lookup"><span data-stu-id="b02f4-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b02f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b02f4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b02f4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b02f4-105">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="b02f4-106">[in] Offset de démarrage dans la variable au niveau duquel définir la valeur.</span><span class="sxs-lookup"><span data-stu-id="b02f4-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="b02f4-107">Ce paramètre est utilisé lors de l'écriture dans des champs membres d'un objet.</span><span class="sxs-lookup"><span data-stu-id="b02f4-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="b02f4-108">[in] Identificateur du thread dont le contexte doit être mis à jour pour refléter la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="b02f4-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="b02f4-109">[in] Taille en octets du contexte de thread.</span><span class="sxs-lookup"><span data-stu-id="b02f4-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="b02f4-110">[in] Contexte de thread utilisé pour écrire la valeur.</span><span class="sxs-lookup"><span data-stu-id="b02f4-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="b02f4-111">[in] Taille en octets de la mémoire tampon `pValue`.</span><span class="sxs-lookup"><span data-stu-id="b02f4-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="b02f4-112">[in] Mémoire tampon contenant la valeur à définir.</span><span class="sxs-lookup"><span data-stu-id="b02f4-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b02f4-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="b02f4-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b02f4-114">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b02f4-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b02f4-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b02f4-115">Requirements</span></span>  

 <span data-ttu-id="b02f4-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b02f4-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b02f4-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b02f4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b02f4-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b02f4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b02f4-119">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b02f4-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b02f4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b02f4-120">See also</span></span>

- [<span data-ttu-id="b02f4-121">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="b02f4-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="b02f4-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b02f4-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
