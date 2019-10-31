---
title: 'ICorDebugSymbolProvider :: GetMethodProps,, méthode'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 811106216e1e454ddf342af1578f74c80ba2acc9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138830"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="8602e-102">ICorDebugSymbolProvider :: GetMethodProps,, méthode</span><span class="sxs-lookup"><span data-stu-id="8602e-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="8602e-103">Retourne des informations sur les propriétés de la méthode, telles que le jeton de métadonnées de la méthode et des informations sur ses paramètres génériques, en fonction d'une adresse virtuelle relative (RVA) dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8602e-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8602e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8602e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8602e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8602e-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="8602e-106">[in] Adresse virtuelle relative dans la méthode sur les informations à récupérer.</span><span class="sxs-lookup"><span data-stu-id="8602e-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="8602e-107">[out] Pointeur vers le jeton de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8602e-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="8602e-108">[out] Pointeur vers le nombre de paramètres génériques associés à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8602e-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="8602e-109">[in] Taille du tableau `signature`.</span><span class="sxs-lookup"><span data-stu-id="8602e-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="8602e-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="8602e-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="8602e-111">[out] Pointeur vers la taille du tableau `signature` retourné.</span><span class="sxs-lookup"><span data-stu-id="8602e-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="8602e-112">[out] Mémoire tampon qui conserve les signatures typespec de tous les paramètres génériques.</span><span class="sxs-lookup"><span data-stu-id="8602e-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8602e-113">Notes</span><span class="sxs-lookup"><span data-stu-id="8602e-113">Remarks</span></span>  
 <span data-ttu-id="8602e-114">Pour récupérer la taille requise du tableau `signature` de la méthode, affectez la valeur 0 à l’argument `cbSignature` et `signature` la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="8602e-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="8602e-115">Suite au retour de la méthode, `pcbSignature` contient le nombre d'octets requis pour le tableau `signature`.</span><span class="sxs-lookup"><span data-stu-id="8602e-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8602e-116">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8602e-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8602e-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="8602e-117">Requirements</span></span>  
 <span data-ttu-id="8602e-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8602e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8602e-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8602e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8602e-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8602e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8602e-121">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8602e-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8602e-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8602e-122">See also</span></span>

- [<span data-ttu-id="8602e-123">GetTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8602e-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="8602e-124">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="8602e-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8602e-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8602e-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
