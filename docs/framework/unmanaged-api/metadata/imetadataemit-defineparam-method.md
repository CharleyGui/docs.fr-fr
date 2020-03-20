---
title: IMetaDataEmit::DefineParam, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177694"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="04270-102">IMetaDataEmit::DefineParam, méthode</span><span class="sxs-lookup"><span data-stu-id="04270-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="04270-103">Crée une définition de paramètre avec la signature spécifiée pour la méthode référencée par le jeton spécifié, et obtient un jeton pour cette définition de paramètre.</span><span class="sxs-lookup"><span data-stu-id="04270-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04270-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04270-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04270-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="04270-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="04270-106">[dans] Le jeton de la méthode dont le paramètre est défini.</span><span class="sxs-lookup"><span data-stu-id="04270-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="04270-107">[dans] Le numéro de séquence de paramètres.</span><span class="sxs-lookup"><span data-stu-id="04270-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="04270-108">[dans] Le nom du paramètre dans Unicode.</span><span class="sxs-lookup"><span data-stu-id="04270-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="04270-109">[dans] Drapeaux pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="04270-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="04270-110">C’est un peu `CorParamAttr` de valeur.</span><span class="sxs-lookup"><span data-stu-id="04270-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="04270-111">[dans] `ELEMENT_TYPE_` pour la valeur *\** constante.</span><span class="sxs-lookup"><span data-stu-id="04270-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="04270-112">[dans] La valeur constante du paramètre.</span><span class="sxs-lookup"><span data-stu-id="04270-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="04270-113">[dans] La taille, dans les `pValue`caractères Unicode, de .</span><span class="sxs-lookup"><span data-stu-id="04270-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="04270-114">[out] Le `mdParamDef` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="04270-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04270-115">Notes </span><span class="sxs-lookup"><span data-stu-id="04270-115">Remarks</span></span>  
 <span data-ttu-id="04270-116">Les valeurs `ulParamSeq` de séquence commencent par 1 pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="04270-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="04270-117">Une valeur de retour a un nombre de séquences de 0.</span><span class="sxs-lookup"><span data-stu-id="04270-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04270-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="04270-118">Requirements</span></span>  
 <span data-ttu-id="04270-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04270-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04270-120">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="04270-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04270-121">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04270-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04270-122">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04270-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04270-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04270-123">See also</span></span>

- [<span data-ttu-id="04270-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="04270-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="04270-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="04270-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
