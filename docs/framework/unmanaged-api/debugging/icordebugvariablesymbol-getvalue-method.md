---
title: Méthode ICorDebugVariableSymbol::GetValue
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b72b9dbeff6aa06a132dc7ec3ddd9477553c4c2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967997"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="d45d1-102">Méthode ICorDebugVariableSymbol::GetValue</span><span class="sxs-lookup"><span data-stu-id="d45d1-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="d45d1-103">Obtient la valeur d'une variable sous forme d'un tableau d'octets.</span><span class="sxs-lookup"><span data-stu-id="d45d1-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d45d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d45d1-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d45d1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d45d1-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="d45d1-106">[in] Offset de démarrage dans la variable au niveau duquel lire la valeur.</span><span class="sxs-lookup"><span data-stu-id="d45d1-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="d45d1-107">Ce paramètre est utilisé lors de la lecture de champs membres d'un objet.</span><span class="sxs-lookup"><span data-stu-id="d45d1-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="d45d1-108">[in] Taille en octets de l'argument `context`.</span><span class="sxs-lookup"><span data-stu-id="d45d1-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="d45d1-109">[in] Contexte de thread utilisé pour lire la valeur.</span><span class="sxs-lookup"><span data-stu-id="d45d1-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="d45d1-110">[in] Taille en octets de la mémoire tampon `pValue`.</span><span class="sxs-lookup"><span data-stu-id="d45d1-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="d45d1-111">[out] Nombre d'octets réellement écrits dans la mémoire tampon `pValue`.</span><span class="sxs-lookup"><span data-stu-id="d45d1-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d45d1-112">[out] Tableau d'octets contenant la valeur de la variable.</span><span class="sxs-lookup"><span data-stu-id="d45d1-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d45d1-113">Notes</span><span class="sxs-lookup"><span data-stu-id="d45d1-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d45d1-114">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d45d1-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d45d1-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d45d1-115">Requirements</span></span>  
 <span data-ttu-id="d45d1-116">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d45d1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d45d1-117">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d45d1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d45d1-118">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d45d1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d45d1-119">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d45d1-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d45d1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d45d1-120">See also</span></span>

- [<span data-ttu-id="d45d1-121">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="d45d1-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="d45d1-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d45d1-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
