---
title: IMetaDataImport::GetPropertyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175328"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="9f5fa-102">IMetaDataImport::GetPropertyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="9f5fa-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="9f5fa-103">Obtient les métadonnées pour la propriété représentée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f5fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f5fa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,
   [out] LPCWSTR           szProperty,
   [in]  ULONG             cchProperty,
   [out] ULONG             *pchProperty,
   [out] DWORD             *pdwPropFlags,
   [out] PCCOR_SIGNATURE   *ppvSig,
   [out] ULONG             *pbSig,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,
   [out] mdMethodDef       *pmdGetter,
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,
   [out] ULONG             *pcOtherMethod
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f5fa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9f5fa-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="9f5fa-106">[dans] Un jeton qui représente la propriété pour retourner les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="9f5fa-107">[out] Un pointeur sur le jeton TypeDef qui représente le type qui implémente la propriété.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="9f5fa-108">[out] Un tampon pour tenir le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="9f5fa-109">[dans] La taille en `szProperty`caractères larges de .</span><span class="sxs-lookup"><span data-stu-id="9f5fa-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="9f5fa-110">[out] Le nombre de personnages `szProperty`larges retournés dans .</span><span class="sxs-lookup"><span data-stu-id="9f5fa-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="9f5fa-111">[out] Un pointeur à tous les drapeaux d’attribut appliqués à la propriété.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="9f5fa-112">Cette valeur est un peumask de l’énumération [CorPropertyAttr.](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="9f5fa-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="9f5fa-113">[out] Un pointeur à la signature des métadonnées de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="9f5fa-114">[out] Le nombre d’octets retournés dans `ppvSig`.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="9f5fa-115">[out] Un drapeau spécifiant le type de la constante qui est la valeur par défaut de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="9f5fa-116">Cette valeur provient de l’énumération De CorElementType.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="9f5fa-117">[out] Un pointeur aux octets qui stockent la valeur par défaut pour cette propriété.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="9f5fa-118">[out] La taille en `ppDefaultValue`caractères `pdwCPlusTypeFlag` larges de , si est ELEMENT_TYPE_STRING; autrement, cette valeur n’est pas pertinente.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="9f5fa-119">Dans ce cas, `ppDefaultValue` la durée de la durée est `pdwCPlusTypeFlag`déduite du type spécifié par .</span><span class="sxs-lookup"><span data-stu-id="9f5fa-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="9f5fa-120">[out] Un pointeur pour le jeton MethodDef qui représente la méthode d’accesseur défini pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="9f5fa-121">[out] Un pointeur pour le jeton MethodDef qui représente la méthode d’accès pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="9f5fa-122">[out] Un tableau de jetons MethodDef qui représentent d’autres méthodes associées à la propriété.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9f5fa-123">[in] Taille maximale du tableau `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="9f5fa-124">Si vous ne fournissez pas un tableau assez grand pour contenir toutes les méthodes, ils sont ignorés sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="9f5fa-125">[out] Le nombre de jetons MethodDef retournés dans `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="9f5fa-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f5fa-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9f5fa-126">Requirements</span></span>  
 <span data-ttu-id="9f5fa-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f5fa-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f5fa-128">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="9f5fa-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f5fa-129">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9f5fa-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f5fa-130">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f5fa-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f5fa-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f5fa-131">See also</span></span>

- [<span data-ttu-id="9f5fa-132">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="9f5fa-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9f5fa-133">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="9f5fa-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
