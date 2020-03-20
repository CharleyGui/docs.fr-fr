---
title: IMetaDataEmit::SetFieldProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: b921118f7c43edef3c07cbb34cbbd9119d36ce51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177555"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="34c55-102">IMetaDataEmit::SetFieldProps, méthode</span><span class="sxs-lookup"><span data-stu-id="34c55-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="34c55-103">Définit ou met à jour la valeur par défaut pour le champ référencé par le jeton de champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="34c55-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34c55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34c55-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34c55-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="34c55-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="34c55-106">[dans] Le jeton pour le champ cible.</span><span class="sxs-lookup"><span data-stu-id="34c55-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="34c55-107">[dans] Attributs de champ.</span><span class="sxs-lookup"><span data-stu-id="34c55-107">[in] Field attributes.</span></span> <span data-ttu-id="34c55-108">C’est un peu `CorFieldAttr` de valeur.</span><span class="sxs-lookup"><span data-stu-id="34c55-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="34c55-109">[dans] Le `ELEMENT_TYPE_` *\** pour la valeur constante.</span><span class="sxs-lookup"><span data-stu-id="34c55-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="34c55-110">C’est `CorElementType` une valeur.</span><span class="sxs-lookup"><span data-stu-id="34c55-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="34c55-111">Si une constante n’est pas `ELEMENT_TYPE_END`définie, définissez cette valeur à .</span><span class="sxs-lookup"><span data-stu-id="34c55-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="34c55-112">[dans] La valeur constante pour le domaine.</span><span class="sxs-lookup"><span data-stu-id="34c55-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="34c55-113">[dans] La taille, dans les `pValue`caractères Unicode, de .</span><span class="sxs-lookup"><span data-stu-id="34c55-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34c55-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="34c55-114">Requirements</span></span>  
 <span data-ttu-id="34c55-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34c55-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34c55-116">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="34c55-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="34c55-117">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34c55-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34c55-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34c55-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34c55-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34c55-119">See also</span></span>

- [<span data-ttu-id="34c55-120">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="34c55-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="34c55-121">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="34c55-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
