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
ms.openlocfilehash: 50aebb09924b93a622e5b7d84e65e41ee91f6018
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006192"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="38d76-102">IMetaDataDispenserEx::FindAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="38d76-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="38d76-103">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="38d76-103">This method is not implemented.</span></span> <span data-ttu-id="38d76-104">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="38d76-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38d76-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38d76-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="38d76-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="38d76-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="38d76-107">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="38d76-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="38d76-108">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="38d76-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="38d76-109">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="38d76-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="38d76-110">dans Assembly à trouver.</span><span class="sxs-lookup"><span data-stu-id="38d76-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="38d76-111">à Nom simple de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="38d76-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="38d76-112">dans Taille, en octets, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="38d76-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="38d76-113">à Nombre de caractères réellement retournés dans `szName` .</span><span class="sxs-lookup"><span data-stu-id="38d76-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38d76-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="38d76-114">Requirements</span></span>  
 <span data-ttu-id="38d76-115">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38d76-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38d76-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="38d76-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38d76-117">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38d76-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38d76-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38d76-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d76-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38d76-119">See also</span></span>

- [<span data-ttu-id="38d76-120">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="38d76-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="38d76-121">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="38d76-121">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
