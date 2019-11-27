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
ms.openlocfilehash: 06b81615565a04db7d6cfef4da9b5372a85afd68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450346"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="149ad-102">IMetaDataAssemblyImport::EnumAssemblyRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="149ad-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="149ad-103">Énumère les instances de `mdAssemblyRef` définies dans le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="149ad-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="149ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="149ad-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="149ad-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="149ad-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="149ad-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="149ad-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="149ad-107">Il doit s’agir d’une valeur NULL lorsque la méthode `EnumAssemblyRefs` est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="149ad-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="149ad-108">à Énumération des jetons de métadonnées de `mdAssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="149ad-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="149ad-109">dans Nombre maximal de jetons qui peuvent être placés dans le tableau de `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="149ad-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="149ad-110">à Nombre de jetons réellement placés dans `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="149ad-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="149ad-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="149ad-111">Return Value</span></span>  
  
|<span data-ttu-id="149ad-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="149ad-112">HRESULT</span></span>|<span data-ttu-id="149ad-113">Description</span><span class="sxs-lookup"><span data-stu-id="149ad-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="149ad-114">`EnumAssemblyRefs` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="149ad-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="149ad-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="149ad-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="149ad-116">Dans ce cas, `pcTokens` a la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="149ad-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="149ad-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="149ad-117">Requirements</span></span>  
 <span data-ttu-id="149ad-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="149ad-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="149ad-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="149ad-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="149ad-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="149ad-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="149ad-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="149ad-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="149ad-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="149ad-122">See also</span></span>

- [<span data-ttu-id="149ad-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="149ad-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
