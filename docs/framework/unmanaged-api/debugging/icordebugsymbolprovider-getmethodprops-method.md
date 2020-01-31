---
title: ICorDebugSymbolProvider::GetMethodProps, méthode
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 58642d0a9b1cfe1fd969f39fa7e5ab22a8dbfa05
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791581"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="9c218-102">ICorDebugSymbolProvider::GetMethodProps, méthode</span><span class="sxs-lookup"><span data-stu-id="9c218-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="9c218-103">Retourne des informations sur les propriétés de la méthode, telles que le jeton de métadonnées de la méthode et des informations sur ses paramètres génériques, en fonction d'une adresse virtuelle relative (RVA) dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="9c218-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c218-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c218-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9c218-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="9c218-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="9c218-106">[in] Adresse virtuelle relative dans la méthode sur les informations à récupérer.</span><span class="sxs-lookup"><span data-stu-id="9c218-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="9c218-107">[out] Pointeur vers le jeton de métadonnées de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9c218-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="9c218-108">[out] Pointeur vers le nombre de paramètres génériques associés à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="9c218-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="9c218-109">[in] Taille du tableau `signature`.</span><span class="sxs-lookup"><span data-stu-id="9c218-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="9c218-110">Consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="9c218-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="9c218-111">[out] Pointeur vers la taille du tableau `signature` retourné.</span><span class="sxs-lookup"><span data-stu-id="9c218-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="9c218-112">[out] Mémoire tampon qui conserve les signatures typespec de tous les paramètres génériques.</span><span class="sxs-lookup"><span data-stu-id="9c218-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c218-113">Notes</span><span class="sxs-lookup"><span data-stu-id="9c218-113">Remarks</span></span>  
 <span data-ttu-id="9c218-114">Pour récupérer la taille requise du tableau `signature` de la méthode, affectez la valeur 0 à l’argument `cbSignature` et `signature` la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="9c218-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="9c218-115">Suite au retour de la méthode, `pcbSignature` contient le nombre d'octets requis pour le tableau `signature`.</span><span class="sxs-lookup"><span data-stu-id="9c218-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c218-116">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9c218-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c218-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="9c218-117">Requirements</span></span>  
 <span data-ttu-id="9c218-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c218-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c218-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c218-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c218-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c218-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c218-121">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c218-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c218-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c218-122">See also</span></span>

- [<span data-ttu-id="9c218-123">GetTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="9c218-123">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="9c218-124">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="9c218-124">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="9c218-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9c218-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
