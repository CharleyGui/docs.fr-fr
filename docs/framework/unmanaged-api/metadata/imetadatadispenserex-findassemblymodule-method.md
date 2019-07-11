---
title: IMetaDataDispenserEx::FindAssemblyModule, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0f6b38cefa1c9b36a660559c1d97fc88f7dbddc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777756"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="e84bb-102">IMetaDataDispenserEx::FindAssemblyModule, méthode</span><span class="sxs-lookup"><span data-stu-id="e84bb-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="e84bb-103">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="e84bb-103">This method is not implemented.</span></span> <span data-ttu-id="e84bb-104">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="e84bb-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e84bb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e84bb-105">Syntax</span></span>  
  
```cpp  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e84bb-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e84bb-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="e84bb-107">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="e84bb-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="e84bb-108">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="e84bb-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="e84bb-109">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="e84bb-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="e84bb-110">[in] Le nom du module.</span><span class="sxs-lookup"><span data-stu-id="e84bb-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="e84bb-111">[in] L’assembly à rechercher.</span><span class="sxs-lookup"><span data-stu-id="e84bb-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="e84bb-112">[out] Le nom simple de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e84bb-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e84bb-113">[in] La taille, en octets, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="e84bb-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="e84bb-114">[out] Le nombre de caractères réellement retournés dans `szName`.</span><span class="sxs-lookup"><span data-stu-id="e84bb-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e84bb-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e84bb-115">Requirements</span></span>  
 <span data-ttu-id="e84bb-116">**Plateforme :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e84bb-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e84bb-117">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e84bb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e84bb-118">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e84bb-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e84bb-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e84bb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e84bb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e84bb-120">See also</span></span>

- [<span data-ttu-id="e84bb-121">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="e84bb-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="e84bb-122">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="e84bb-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
