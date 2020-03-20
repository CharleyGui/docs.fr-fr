---
title: IMetaDataAssemblyImport::EnumFiles, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: 70f76318f51047cb81262f744a6fbed5fe401692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177814"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="5bf9b-102">IMetaDataAssemblyImport::EnumFiles, méthode</span><span class="sxs-lookup"><span data-stu-id="5bf9b-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="5bf9b-103">Énumère les fichiers mentionnés dans le manifeste actuel de l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="5bf9b-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bf9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bf9b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bf9b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5bf9b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5bf9b-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="5bf9b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5bf9b-107">Cela doit être une valeur nulle pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="5bf9b-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="5bf9b-108">[out] Le tableau utilisé `mdFile` pour stocker les jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="5bf9b-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5bf9b-109">[dans] Le nombre `mdFile` maximum de jetons qui `rFiles`peuvent être placés en .</span><span class="sxs-lookup"><span data-stu-id="5bf9b-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5bf9b-110">[out] Le nombre `mdFile` de jetons `rFiles`effectivement placés en .</span><span class="sxs-lookup"><span data-stu-id="5bf9b-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bf9b-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5bf9b-111">Return Value</span></span>  
  
|<span data-ttu-id="5bf9b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5bf9b-112">HRESULT</span></span>|<span data-ttu-id="5bf9b-113">Description</span><span class="sxs-lookup"><span data-stu-id="5bf9b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5bf9b-114">`EnumFiles`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="5bf9b-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5bf9b-115">Il n’y a pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="5bf9b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="5bf9b-116">Dans ce `pcTokens` cas, est réglé à zéro.</span><span class="sxs-lookup"><span data-stu-id="5bf9b-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5bf9b-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5bf9b-117">Requirements</span></span>  
 <span data-ttu-id="5bf9b-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bf9b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bf9b-119">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="5bf9b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5bf9b-120">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5bf9b-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5bf9b-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bf9b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf9b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bf9b-122">See also</span></span>

- [<span data-ttu-id="5bf9b-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="5bf9b-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
