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
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431686"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="e780b-102">IMetaDataEmit::DefineParam, méthode</span><span class="sxs-lookup"><span data-stu-id="e780b-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="e780b-103">Crée une définition de paramètre avec la signature spécifiée pour la méthode référencée par le jeton spécifié et obtient un jeton pour cette définition de paramètre.</span><span class="sxs-lookup"><span data-stu-id="e780b-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e780b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e780b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e780b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e780b-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="e780b-106">dans Jeton pour la méthode dont le paramètre est défini.</span><span class="sxs-lookup"><span data-stu-id="e780b-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="e780b-107">dans Numéro de séquence du paramètre.</span><span class="sxs-lookup"><span data-stu-id="e780b-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="e780b-108">dans Nom du paramètre en Unicode.</span><span class="sxs-lookup"><span data-stu-id="e780b-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e780b-109">dans Indicateurs pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="e780b-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="e780b-110">Il s’agit d’un masque de ré`CorParamAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="e780b-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="e780b-111">[in] `ELEMENT_TYPE_` *\** pour la valeur constante.</span><span class="sxs-lookup"><span data-stu-id="e780b-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e780b-112">dans Valeur de constante pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="e780b-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="e780b-113">dans Taille, en caractères Unicode, de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="e780b-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="e780b-114">à Jeton `mdParamDef` assigné.</span><span class="sxs-lookup"><span data-stu-id="e780b-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e780b-115">Notes</span><span class="sxs-lookup"><span data-stu-id="e780b-115">Remarks</span></span>  
 <span data-ttu-id="e780b-116">Les valeurs de séquence dans `ulParamSeq` commencent par 1 pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="e780b-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="e780b-117">Une valeur de retour a un numéro de séquence égal à 0.</span><span class="sxs-lookup"><span data-stu-id="e780b-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e780b-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e780b-118">Requirements</span></span>  
 <span data-ttu-id="e780b-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e780b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e780b-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e780b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e780b-121">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e780b-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e780b-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e780b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e780b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e780b-123">See also</span></span>

- [<span data-ttu-id="e780b-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="e780b-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e780b-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="e780b-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
