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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fcf32c4b27324ccc54eabbb248e8c9906cf693b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782360"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="e3399-102">IMetaDataImport::GetMemberProps, méthode</span><span class="sxs-lookup"><span data-stu-id="e3399-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="e3399-103">Obtient les informations stockées dans les métadonnées pour une définition de membre spécifié, y compris le nom, le signature binaire et l’adresse virtuelle relative, de la <xref:System.Type> membre référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="e3399-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="e3399-104">Il s’agit d’une méthode d’assistance simple : si *Mo* est un MethodDef, puis **GetMethodProps** est appelé ; si *Mo* est FieldDef, puis **GetFieldProps** est appelée.</span><span class="sxs-lookup"><span data-stu-id="e3399-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="e3399-105">Consultez ces autres méthodes pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="e3399-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="e3399-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3399-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e3399-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e3399-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="e3399-108">[in] Le jeton qui référence le membre pour obtenir les métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="e3399-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="e3399-109">[out] Pointeur vers le jeton de métadonnées qui représente la classe du membre.</span><span class="sxs-lookup"><span data-stu-id="e3399-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="e3399-110">[out] Le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="e3399-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="e3399-111">[in] La taille en caractères larges de la `szMember` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="e3399-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="e3399-112">[out] La taille en caractères larges du nom retourné.</span><span class="sxs-lookup"><span data-stu-id="e3399-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="e3399-113">[out] Les valeurs d’indicateur appliqués au membre.</span><span class="sxs-lookup"><span data-stu-id="e3399-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="e3399-114">[out] Pointeur vers la signature de métadonnées binaires du membre.</span><span class="sxs-lookup"><span data-stu-id="e3399-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="e3399-115">[out] La taille en octets de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="e3399-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="e3399-116">[out] Pointeur vers l’adresse virtuelle relative du membre.</span><span class="sxs-lookup"><span data-stu-id="e3399-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="e3399-117">[out] Les indicateurs d’implémentation méthode associés au membre.</span><span class="sxs-lookup"><span data-stu-id="e3399-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="e3399-118">[out] Un indicateur qui marque un <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="e3399-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="e3399-119">C’est un de le `ELEMENT_TYPE_*` valeurs.</span><span class="sxs-lookup"><span data-stu-id="e3399-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="e3399-120">[out] Une valeur de chaîne constante retournée par ce membre.</span><span class="sxs-lookup"><span data-stu-id="e3399-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="e3399-121">[out] La taille en caractères de `ppValue`, ou zéro si `ppValue` ne contient pas de chaîne.</span><span class="sxs-lookup"><span data-stu-id="e3399-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3399-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e3399-122">Requirements</span></span>  
 <span data-ttu-id="e3399-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3399-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3399-124">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e3399-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3399-125">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3399-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e3399-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3399-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3399-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3399-127">See also</span></span>

- [<span data-ttu-id="e3399-128">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="e3399-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e3399-129">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="e3399-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
