---
title: 'Méthode icordebugvariablesymbol :: GetValue, méthode'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: 5ef7e67efb2bafd9b9f52203246fd7d1590e6107
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120968"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="f5782-102">Méthode icordebugvariablesymbol :: GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="f5782-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="f5782-103">Obtient la valeur d'une variable sous forme d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="f5782-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5782-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5782-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f5782-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f5782-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="f5782-106">[in] Offset de démarrage dans la variable au niveau duquel lire la valeur.</span><span class="sxs-lookup"><span data-stu-id="f5782-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="f5782-107">Ce paramètre est utilisé lors de la lecture de champs membres d'un objet.</span><span class="sxs-lookup"><span data-stu-id="f5782-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="f5782-108">[in] Taille en octets de l'argument `context`.</span><span class="sxs-lookup"><span data-stu-id="f5782-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="f5782-109">[in] Contexte de thread utilisé pour lire la valeur.</span><span class="sxs-lookup"><span data-stu-id="f5782-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="f5782-110">[in] Taille en octets de la mémoire tampon `pValue`.</span><span class="sxs-lookup"><span data-stu-id="f5782-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="f5782-111">[out] Nombre d'octets réellement écrits dans la mémoire tampon `pValue`.</span><span class="sxs-lookup"><span data-stu-id="f5782-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f5782-112">[out] Tableau d'octets contenant la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="f5782-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5782-113">Notes</span><span class="sxs-lookup"><span data-stu-id="f5782-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5782-114">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f5782-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5782-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="f5782-115">Requirements</span></span>  
 <span data-ttu-id="f5782-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5782-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5782-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5782-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5782-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5782-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5782-119">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5782-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5782-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5782-120">See also</span></span>

- [<span data-ttu-id="f5782-121">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="f5782-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="f5782-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f5782-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
