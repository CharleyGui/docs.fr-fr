---
title: IMetaDataImport::GetMemberProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177231"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="63e4d-102">IMetaDataImport::GetMemberProps, méthode</span><span class="sxs-lookup"><span data-stu-id="63e4d-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="63e4d-103">Obtient les informations stockées dans les métadonnées pour une définition spécifiée du <xref:System.Type> membre, y compris le nom, la signature binaire et l’adresse virtuelle relative, du membre référencé par le jeton spécifié des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="63e4d-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="63e4d-104">Il s’agit d’une méthode d’aide simple: si *mb* est un MethodDef, puis **GetMethodProps** est appelé; si *mb* est un FieldDef, alors **GetFieldProps** est appelé.</span><span class="sxs-lookup"><span data-stu-id="63e4d-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="63e4d-105">Voir ces autres méthodes pour plus de détails.</span><span class="sxs-lookup"><span data-stu-id="63e4d-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="63e4d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63e4d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63e4d-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="63e4d-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="63e4d-108">[dans] Le jeton qui fait référence au membre pour obtenir les métadonnées associées pour.</span><span class="sxs-lookup"><span data-stu-id="63e4d-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="63e4d-109">[out] Un pointeur vers le jeton des métadonnées qui représente la classe du membre.</span><span class="sxs-lookup"><span data-stu-id="63e4d-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="63e4d-110">[out] Le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="63e4d-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="63e4d-111">[dans] La taille en caractères larges du `szMember` tampon.</span><span class="sxs-lookup"><span data-stu-id="63e4d-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="63e4d-112">[out] La taille dans les caractères larges du nom retourné.</span><span class="sxs-lookup"><span data-stu-id="63e4d-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="63e4d-113">[out] Toutes les valeurs du drapeau s’appliquaient au membre.</span><span class="sxs-lookup"><span data-stu-id="63e4d-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="63e4d-114">[out] Un pointeur à la signature binaire métadonnées du membre.</span><span class="sxs-lookup"><span data-stu-id="63e4d-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="63e4d-115">[out] La taille dans `ppvSigBlob`les octets de .</span><span class="sxs-lookup"><span data-stu-id="63e4d-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="63e4d-116">[out] Un pointeur à l’adresse virtuelle relative du membre.</span><span class="sxs-lookup"><span data-stu-id="63e4d-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="63e4d-117">[out] Tous les indicateurs de mise en œuvre de méthode associés au membre.</span><span class="sxs-lookup"><span data-stu-id="63e4d-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="63e4d-118">[out] Un drapeau qui <xref:System.ValueType>marque un .</span><span class="sxs-lookup"><span data-stu-id="63e4d-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="63e4d-119">C’est l’une des `ELEMENT_TYPE_*` valeurs.</span><span class="sxs-lookup"><span data-stu-id="63e4d-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="63e4d-120">[out] Une valeur de chaîne constante retournée par ce membre.</span><span class="sxs-lookup"><span data-stu-id="63e4d-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="63e4d-121">[out] La taille dans `ppValue`les caractères de , ou zéro si `ppValue` ne tient pas une chaîne.</span><span class="sxs-lookup"><span data-stu-id="63e4d-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63e4d-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="63e4d-122">Requirements</span></span>  
 <span data-ttu-id="63e4d-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63e4d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63e4d-124">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="63e4d-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63e4d-125">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63e4d-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63e4d-126">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63e4d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e4d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63e4d-127">See also</span></span>

- [<span data-ttu-id="63e4d-128">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="63e4d-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="63e4d-129">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="63e4d-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
