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
ms.openlocfilehash: 18cd9dd14e615a7e76bfff30c9ae584305bd1907
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708933"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="54754-102">IMetaDataAssemblyImport::EnumAssemblyRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="54754-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>

<span data-ttu-id="54754-103">Énumère les `mdAssemblyRef` instances définies dans le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="54754-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54754-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54754-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54754-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="54754-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="54754-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="54754-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="54754-107">Il doit s’agir d’une valeur NULL lorsque la `EnumAssemblyRefs` méthode est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="54754-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="54754-108">à Énumération des `mdAssemblyRef` jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="54754-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="54754-109">dans Nombre maximal de jetons qui peuvent être placés dans le `rAssemblyRefs` tableau.</span><span class="sxs-lookup"><span data-stu-id="54754-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="54754-110">à Nombre de jetons réellement placés dans `rAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="54754-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54754-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="54754-111">Return Value</span></span>  
  
|<span data-ttu-id="54754-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54754-112">HRESULT</span></span>|<span data-ttu-id="54754-113">Description</span><span class="sxs-lookup"><span data-stu-id="54754-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="54754-114">`EnumAssemblyRefs` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="54754-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="54754-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="54754-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="54754-116">Dans ce cas, `pcTokens` a la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="54754-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54754-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="54754-117">Requirements</span></span>  

 <span data-ttu-id="54754-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54754-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54754-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="54754-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54754-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54754-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54754-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54754-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54754-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54754-122">See also</span></span>

- [<span data-ttu-id="54754-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="54754-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
