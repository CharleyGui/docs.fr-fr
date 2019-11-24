---
title: IMetaDataDispenserEx::FindAssembly, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
ms.openlocfilehash: 2d974b7368dd01062d2d310d076dce05e102eb81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442285"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="e962d-102">IMetaDataDispenserEx::FindAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="e962d-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="e962d-103">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="e962d-103">This method is not implemented.</span></span> <span data-ttu-id="e962d-104">If called, it returns E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="e962d-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e962d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e962d-105">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e962d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e962d-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="e962d-107">[in] Not used.</span><span class="sxs-lookup"><span data-stu-id="e962d-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="e962d-108">[in] Not used.</span><span class="sxs-lookup"><span data-stu-id="e962d-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="e962d-109">[in] Not used.</span><span class="sxs-lookup"><span data-stu-id="e962d-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="e962d-110">[in] The assembly to be found.</span><span class="sxs-lookup"><span data-stu-id="e962d-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="e962d-111">[out] The simple name of the assembly.</span><span class="sxs-lookup"><span data-stu-id="e962d-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e962d-112">[in] The size, in bytes, of `szName`.</span><span class="sxs-lookup"><span data-stu-id="e962d-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="e962d-113">[out] The number of characters actually returned in `szName`.</span><span class="sxs-lookup"><span data-stu-id="e962d-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e962d-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="e962d-114">Requirements</span></span>  
 <span data-ttu-id="e962d-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e962d-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e962d-116">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e962d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e962d-117">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e962d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e962d-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e962d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e962d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e962d-119">See also</span></span>

- [<span data-ttu-id="e962d-120">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="e962d-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="e962d-121">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="e962d-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
