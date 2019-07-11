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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c7b512de76b5ada882b1d81c2968b4ead5c8c20
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775935"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="db335-102">IMetaDataAssemblyImport::EnumAssemblyRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="db335-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="db335-103">Énumère les `mdAssemblyRef` instances qui sont définis dans le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="db335-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db335-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db335-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db335-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="db335-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="db335-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="db335-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="db335-107">Cela doit être une valeur null valeur lorsque le `EnumAssemblyRefs` méthode est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="db335-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="db335-108">[out] L’énumération des `mdAssemblyRef` des jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="db335-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="db335-109">[in] Le nombre maximal de jetons qui peuvent être placés dans le `rAssemblyRefs` tableau.</span><span class="sxs-lookup"><span data-stu-id="db335-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="db335-110">[out] Le nombre de jetons placés dans `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="db335-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db335-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="db335-111">Return Value</span></span>  
  
|<span data-ttu-id="db335-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db335-112">HRESULT</span></span>|<span data-ttu-id="db335-113">Description</span><span class="sxs-lookup"><span data-stu-id="db335-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="db335-114">`EnumAssemblyRefs` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="db335-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="db335-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="db335-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="db335-116">Dans ce cas, `pcTokens` est défini à zéro.</span><span class="sxs-lookup"><span data-stu-id="db335-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db335-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="db335-117">Requirements</span></span>  
 <span data-ttu-id="db335-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db335-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db335-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db335-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db335-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db335-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db335-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db335-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db335-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db335-122">See also</span></span>

- [<span data-ttu-id="db335-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="db335-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
