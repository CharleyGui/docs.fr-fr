---
title: Icordebugsymbolprovider::gettypeprops, méthode
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 435a814d20e039c794f4f9eeb024d5afbfcd6dbd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771193"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="26f4e-102">Icordebugsymbolprovider::gettypeprops, méthode</span><span class="sxs-lookup"><span data-stu-id="26f4e-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="26f4e-103">Retourne des informations sur les propriétés d'un type, comme le nombre de signature de ses paramètres génériques, en fonction d'une adresse virtuelle relative (RVA) dans une vtable.</span><span class="sxs-lookup"><span data-stu-id="26f4e-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26f4e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26f4e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="26f4e-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="26f4e-106">[in] Adresse virtuelle relative (RVA) dans une vtable.</span><span class="sxs-lookup"><span data-stu-id="26f4e-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="26f4e-107">[in] Taille du tableau `signature`.</span><span class="sxs-lookup"><span data-stu-id="26f4e-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="26f4e-108">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="26f4e-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="26f4e-109">[out] Pointeur vers la taille du tableau `signature` retourné.</span><span class="sxs-lookup"><span data-stu-id="26f4e-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="26f4e-110">[out] Mémoire tampon qui conserve les signatures typespec de tous les paramètres génériques.</span><span class="sxs-lookup"><span data-stu-id="26f4e-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26f4e-111">Notes</span><span class="sxs-lookup"><span data-stu-id="26f4e-111">Remarks</span></span>  
 <span data-ttu-id="26f4e-112">Pour obtenir la taille requise du type `signature` de tableau, définissez la `cbSignature` argument à 0 et `signature` à **null**.</span><span class="sxs-lookup"><span data-stu-id="26f4e-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="26f4e-113">Suite au retour de la méthode, `pcbSignature` contient le nombre d'octets requis pour le tableau `signature`.</span><span class="sxs-lookup"><span data-stu-id="26f4e-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26f4e-114">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="26f4e-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26f4e-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="26f4e-115">Requirements</span></span>  
 <span data-ttu-id="26f4e-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26f4e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26f4e-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26f4e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26f4e-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26f4e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26f4e-119">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26f4e-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f4e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26f4e-120">See also</span></span>

- [<span data-ttu-id="26f4e-121">GetMethodProps, méthode</span><span class="sxs-lookup"><span data-stu-id="26f4e-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="26f4e-122">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="26f4e-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="26f4e-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="26f4e-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
