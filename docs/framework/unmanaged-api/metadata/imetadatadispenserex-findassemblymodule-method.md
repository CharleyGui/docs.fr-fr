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
ms.openlocfilehash: 64f1e2a8f05616c7ca84bc130428629b1176e985
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006179"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="d6045-102">IMetaDataDispenserEx::FindAssemblyModule, méthode</span><span class="sxs-lookup"><span data-stu-id="d6045-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="d6045-103">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="d6045-103">This method is not implemented.</span></span> <span data-ttu-id="d6045-104">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="d6045-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6045-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6045-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d6045-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d6045-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="d6045-107">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="d6045-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="d6045-108">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="d6045-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="d6045-109">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="d6045-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="d6045-110">dans Nom du module.</span><span class="sxs-lookup"><span data-stu-id="d6045-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="d6045-111">dans Assembly à trouver.</span><span class="sxs-lookup"><span data-stu-id="d6045-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="d6045-112">à Nom simple de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d6045-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d6045-113">dans Taille, en octets, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="d6045-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="d6045-114">à Nombre de caractères réellement retournés dans `szName` .</span><span class="sxs-lookup"><span data-stu-id="d6045-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6045-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d6045-115">Requirements</span></span>  
 <span data-ttu-id="d6045-116">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6045-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6045-117">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d6045-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6045-118">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d6045-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6045-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6045-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6045-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6045-120">See also</span></span>

- [<span data-ttu-id="d6045-121">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="d6045-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="d6045-122">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="d6045-122">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
