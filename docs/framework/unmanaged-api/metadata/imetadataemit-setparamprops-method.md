---
title: IMetaDataEmit::SetParamProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: 13220dcfdd260688494d5aebc50f94abf8a82215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177503"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="26743-102">IMetaDataEmit::SetParamProps, méthode</span><span class="sxs-lookup"><span data-stu-id="26743-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="26743-103">Définit ou modifie les caractéristiques d’un paramètre de méthode qui a été défini par un appel antérieur à [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="26743-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26743-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26743-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26743-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="26743-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="26743-106">[dans] Le jeton pour le paramètre cible.</span><span class="sxs-lookup"><span data-stu-id="26743-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="26743-107">[dans] Le nom du paramètre dans Unicode.</span><span class="sxs-lookup"><span data-stu-id="26743-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="26743-108">[dans] Les drapeaux pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="26743-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="26743-109">[dans] Le ELEMENT_TYPE_ pour la valeur constante.</span><span class="sxs-lookup"><span data-stu-id="26743-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="26743-110">[dans] La valeur constante du paramètre.</span><span class="sxs-lookup"><span data-stu-id="26743-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="26743-111">[dans] La taille dans (Unicode) caractères de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="26743-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26743-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="26743-112">Requirements</span></span>  
 <span data-ttu-id="26743-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26743-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26743-114">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="26743-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26743-115">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26743-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26743-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26743-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26743-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26743-117">See also</span></span>

- [<span data-ttu-id="26743-118">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="26743-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="26743-119">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="26743-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
