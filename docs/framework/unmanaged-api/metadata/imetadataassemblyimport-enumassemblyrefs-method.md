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
ms.openlocfilehash: 1b9700455da82fc7f4a39d4c208ac0b18ef79722
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009117"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="e9869-102">IMetaDataAssemblyImport::EnumAssemblyRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="e9869-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="e9869-103">Énumère les `mdAssemblyRef` instances définies dans le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e9869-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9869-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9869-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9869-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e9869-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e9869-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="e9869-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e9869-107">Il doit s’agir d’une valeur NULL lorsque la `EnumAssemblyRefs` méthode est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="e9869-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="e9869-108">à Énumération des `mdAssemblyRef` jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e9869-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e9869-109">dans Nombre maximal de jetons qui peuvent être placés dans le `rAssemblyRefs` tableau.</span><span class="sxs-lookup"><span data-stu-id="e9869-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e9869-110">à Nombre de jetons réellement placés dans `rAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="e9869-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9869-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e9869-111">Return Value</span></span>  
  
|<span data-ttu-id="e9869-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9869-112">HRESULT</span></span>|<span data-ttu-id="e9869-113">Description</span><span class="sxs-lookup"><span data-stu-id="e9869-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e9869-114">`EnumAssemblyRefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e9869-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e9869-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="e9869-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e9869-116">Dans ce cas, `pcTokens` a la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="e9869-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e9869-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e9869-117">Requirements</span></span>  
 <span data-ttu-id="e9869-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9869-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9869-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e9869-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9869-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e9869-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e9869-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9869-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9869-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9869-122">See also</span></span>

- [<span data-ttu-id="e9869-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="e9869-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
