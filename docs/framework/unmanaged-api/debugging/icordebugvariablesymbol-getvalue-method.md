---
title: Méthode ICorDebugVariableSymbol::GetValue
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed88c8ff78006c14bdee51ba6f95aaaedd66cf41
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774829"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="38c0e-102">Méthode ICorDebugVariableSymbol::GetValue</span><span class="sxs-lookup"><span data-stu-id="38c0e-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="38c0e-103">Obtient la valeur d'une variable sous forme d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="38c0e-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38c0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38c0e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38c0e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="38c0e-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="38c0e-106">[in] Offset de démarrage dans la variable au niveau duquel lire la valeur.</span><span class="sxs-lookup"><span data-stu-id="38c0e-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="38c0e-107">Ce paramètre est utilisé lors de la lecture de champs membres d'un objet.</span><span class="sxs-lookup"><span data-stu-id="38c0e-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="38c0e-108">[in] Taille en octets de l'argument `context`.</span><span class="sxs-lookup"><span data-stu-id="38c0e-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="38c0e-109">[in] Contexte de thread utilisé pour lire la valeur.</span><span class="sxs-lookup"><span data-stu-id="38c0e-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="38c0e-110">[in] Taille en octets de la mémoire tampon `pValue`.</span><span class="sxs-lookup"><span data-stu-id="38c0e-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="38c0e-111">[out] Nombre d'octets réellement écrits dans la mémoire tampon `pValue`.</span><span class="sxs-lookup"><span data-stu-id="38c0e-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="38c0e-112">[out] Tableau d'octets contenant la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="38c0e-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38c0e-113">Notes</span><span class="sxs-lookup"><span data-stu-id="38c0e-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38c0e-114">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="38c0e-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38c0e-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="38c0e-115">Requirements</span></span>  
 <span data-ttu-id="38c0e-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38c0e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38c0e-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38c0e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38c0e-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38c0e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38c0e-119">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38c0e-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38c0e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38c0e-120">See also</span></span>

- [<span data-ttu-id="38c0e-121">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="38c0e-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="38c0e-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="38c0e-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
