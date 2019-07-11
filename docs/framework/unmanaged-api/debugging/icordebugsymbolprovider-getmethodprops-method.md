---
title: ICorDebugSymbolProvider::GetMethodProps, méthode
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f6971c7991f5e54973d96d9b3f662b54be564d9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771332"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="14553-102">ICorDebugSymbolProvider::GetMethodProps, méthode</span><span class="sxs-lookup"><span data-stu-id="14553-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="14553-103">Retourne des informations sur les propriétés de la méthode, telles que le jeton de métadonnées de la méthode et des informations sur ses paramètres génériques, en fonction d'une adresse virtuelle relative (RVA) dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="14553-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14553-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14553-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="14553-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="14553-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="14553-106">[in] Adresse virtuelle relative dans la méthode sur les informations à récupérer.</span><span class="sxs-lookup"><span data-stu-id="14553-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="14553-107">[out] Pointeur vers le jeton de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="14553-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="14553-108">[out] Pointeur vers le nombre de paramètres génériques associés à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="14553-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="14553-109">[in] Taille du tableau `signature`.</span><span class="sxs-lookup"><span data-stu-id="14553-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="14553-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="14553-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="14553-111">[out] Pointeur vers la taille du tableau `signature` retourné.</span><span class="sxs-lookup"><span data-stu-id="14553-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="14553-112">[out] Mémoire tampon qui conserve les signatures typespec de tous les paramètres génériques.</span><span class="sxs-lookup"><span data-stu-id="14553-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14553-113">Notes</span><span class="sxs-lookup"><span data-stu-id="14553-113">Remarks</span></span>  
 <span data-ttu-id="14553-114">Pour obtenir la taille requise de la méthode `signature` de tableau, définissez la `cbSignature` argument à 0 et `signature` à **null**.</span><span class="sxs-lookup"><span data-stu-id="14553-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="14553-115">Suite au retour de la méthode, `pcbSignature` contient le nombre d'octets requis pour le tableau `signature`.</span><span class="sxs-lookup"><span data-stu-id="14553-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14553-116">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="14553-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14553-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="14553-117">Requirements</span></span>  
 <span data-ttu-id="14553-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14553-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14553-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14553-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14553-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14553-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14553-121">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14553-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14553-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14553-122">See also</span></span>

- [<span data-ttu-id="14553-123">GetTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="14553-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="14553-124">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="14553-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="14553-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="14553-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
