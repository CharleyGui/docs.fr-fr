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
ms.openlocfilehash: bc5bbba2fa4a95955e52a2e083a2097178b5d96a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437522"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="51e15-102">IMetaDataImport::GetMemberProps, méthode</span><span class="sxs-lookup"><span data-stu-id="51e15-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="51e15-103">Obtient les informations stockées dans les métadonnées pour une définition de membre spécifiée, y compris le nom, la signature binaire et l’adresse virtuelle relative, du membre <xref:System.Type> référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="51e15-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="51e15-104">Il s’agit d’une méthode d’assistance simple : si *Mo* est un MethodDef, **GetMethodProps,** est appelé ; Si *Mo* est un FieldDef, **GetFieldProps,** est appelé.</span><span class="sxs-lookup"><span data-stu-id="51e15-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="51e15-105">Pour plus d’informations, consultez ces autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="51e15-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="51e15-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51e15-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="51e15-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51e15-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="51e15-108">dans Jeton qui référence le membre pour lequel obtenir les métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="51e15-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="51e15-109">à Pointeur vers le jeton de métadonnées qui représente la classe du membre.</span><span class="sxs-lookup"><span data-stu-id="51e15-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="51e15-110">à Nom du membre.</span><span class="sxs-lookup"><span data-stu-id="51e15-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="51e15-111">dans Taille en caractères larges de la mémoire tampon de `szMember`.</span><span class="sxs-lookup"><span data-stu-id="51e15-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="51e15-112">à Taille en caractères larges du nom retourné.</span><span class="sxs-lookup"><span data-stu-id="51e15-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="51e15-113">à Toutes les valeurs d’indicateur appliquées au membre.</span><span class="sxs-lookup"><span data-stu-id="51e15-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="51e15-114">à Pointeur vers la signature de métadonnées binaires du membre.</span><span class="sxs-lookup"><span data-stu-id="51e15-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="51e15-115">à Taille en octets de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="51e15-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="51e15-116">à Pointeur vers l’adresse virtuelle relative du membre.</span><span class="sxs-lookup"><span data-stu-id="51e15-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="51e15-117">à Indicateurs d’implémentation de méthode associés au membre.</span><span class="sxs-lookup"><span data-stu-id="51e15-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="51e15-118">à Indicateur qui marque un <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="51e15-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="51e15-119">Il s’agit de l’une des valeurs `ELEMENT_TYPE_*`.</span><span class="sxs-lookup"><span data-stu-id="51e15-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="51e15-120">à Valeur de chaîne constante retournée par ce membre.</span><span class="sxs-lookup"><span data-stu-id="51e15-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="51e15-121">à Taille en caractères de `ppValue`, ou zéro si `ppValue` ne contient pas de chaîne.</span><span class="sxs-lookup"><span data-stu-id="51e15-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51e15-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="51e15-122">Requirements</span></span>  
 <span data-ttu-id="51e15-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51e15-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51e15-124">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="51e15-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51e15-125">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="51e15-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51e15-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51e15-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51e15-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51e15-127">See also</span></span>

- [<span data-ttu-id="51e15-128">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="51e15-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="51e15-129">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="51e15-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
