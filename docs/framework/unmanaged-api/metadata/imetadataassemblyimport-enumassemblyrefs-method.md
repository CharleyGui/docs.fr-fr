---
title: IMetaDataAssemblyImport::EnumAssemblyRefs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 6a4489d094974eb872b39824ceb185b0cbe48625
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177825"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="2c03b-102">IMetaDataAssemblyImport::EnumAssemblyRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="2c03b-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="2c03b-103">Énumère les `mdAssemblyRef` instances qui sont définies dans le manifeste de l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="2c03b-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c03b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c03b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c03b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2c03b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2c03b-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="2c03b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2c03b-107">Cela doit être une `EnumAssemblyRefs` valeur nulle lorsque la méthode est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="2c03b-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="2c03b-108">[out] L’énumération `mdAssemblyRef` des jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2c03b-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2c03b-109">[dans] Le nombre maximum de jetons qui `rAssemblyRefs` peuvent être placés dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="2c03b-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2c03b-110">[out] Le nombre de jetons `rAssemblyRefs`effectivement placés en .</span><span class="sxs-lookup"><span data-stu-id="2c03b-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c03b-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2c03b-111">Return Value</span></span>  
  
|<span data-ttu-id="2c03b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c03b-112">HRESULT</span></span>|<span data-ttu-id="2c03b-113">Description</span><span class="sxs-lookup"><span data-stu-id="2c03b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2c03b-114">`EnumAssemblyRefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2c03b-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2c03b-115">Il n’y a pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="2c03b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2c03b-116">Dans ce `pcTokens` cas, est réglé à zéro.</span><span class="sxs-lookup"><span data-stu-id="2c03b-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c03b-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2c03b-117">Requirements</span></span>  
 <span data-ttu-id="2c03b-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c03b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c03b-119">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="2c03b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c03b-120">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c03b-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c03b-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c03b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c03b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c03b-122">See also</span></span>

- [<span data-ttu-id="2c03b-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="2c03b-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
