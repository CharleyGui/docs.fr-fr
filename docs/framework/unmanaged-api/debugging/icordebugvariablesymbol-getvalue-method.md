---
title: Méthode ICorDebugVariableSymbol::GetValue
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: 2dc074384d209d0740a1fb0a9a16d96ff355f02b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790877"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="0a411-102">Méthode ICorDebugVariableSymbol::GetValue</span><span class="sxs-lookup"><span data-stu-id="0a411-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="0a411-103">Obtient la valeur d'une variable sous forme d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="0a411-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a411-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a411-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0a411-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="0a411-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="0a411-106">[in] Offset de démarrage dans la variable au niveau duquel lire la valeur.</span><span class="sxs-lookup"><span data-stu-id="0a411-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="0a411-107">Ce paramètre est utilisé lors de la lecture de champs membres d'un objet.</span><span class="sxs-lookup"><span data-stu-id="0a411-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="0a411-108">[in] Taille en octets de l'argument `context`.</span><span class="sxs-lookup"><span data-stu-id="0a411-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="0a411-109">[in] Contexte de thread utilisé pour lire la valeur.</span><span class="sxs-lookup"><span data-stu-id="0a411-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="0a411-110">[in] Taille en octets de la mémoire tampon `pValue`.</span><span class="sxs-lookup"><span data-stu-id="0a411-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="0a411-111">[out] Nombre d'octets réellement écrits dans la mémoire tampon `pValue`.</span><span class="sxs-lookup"><span data-stu-id="0a411-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="0a411-112">[out] Tableau d'octets contenant la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="0a411-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a411-113">Notes</span><span class="sxs-lookup"><span data-stu-id="0a411-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a411-114">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0a411-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a411-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="0a411-115">Requirements</span></span>  
 <span data-ttu-id="0a411-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a411-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a411-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a411-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a411-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a411-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a411-119">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a411-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a411-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a411-120">See also</span></span>

- [<span data-ttu-id="0a411-121">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="0a411-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="0a411-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0a411-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
