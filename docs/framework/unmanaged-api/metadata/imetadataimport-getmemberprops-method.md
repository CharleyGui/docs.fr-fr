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
ms.openlocfilehash: f01d65a339c77e6af3e768c620f17ef0190c1e58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733216"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="d527c-102">IMetaDataImport::GetMemberProps, méthode</span><span class="sxs-lookup"><span data-stu-id="d527c-102">IMetaDataImport::GetMemberProps Method</span></span>

<span data-ttu-id="d527c-103">Obtient les informations stockées dans les métadonnées pour une définition de membre spécifiée, y compris le nom, la signature binaire et l’adresse virtuelle relative, du <xref:System.Type> membre référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="d527c-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="d527c-104">Il s’agit d’une méthode d’assistance simple : si *Mo* est un MethodDef, **GetMethodProps,** est appelé ; Si *Mo* est un FieldDef, **GetFieldProps,** est appelé.</span><span class="sxs-lookup"><span data-stu-id="d527c-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="d527c-105">Pour plus d’informations, consultez ces autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="d527c-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="d527c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d527c-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d527c-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d527c-107">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="d527c-108">dans Jeton qui référence le membre pour lequel obtenir les métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="d527c-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="d527c-109">à Pointeur vers le jeton de métadonnées qui représente la classe du membre.</span><span class="sxs-lookup"><span data-stu-id="d527c-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="d527c-110">à Nom du membre.</span><span class="sxs-lookup"><span data-stu-id="d527c-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="d527c-111">dans Taille en caractères larges de la `szMember` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="d527c-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="d527c-112">à Taille en caractères larges du nom retourné.</span><span class="sxs-lookup"><span data-stu-id="d527c-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="d527c-113">à Toutes les valeurs d’indicateur appliquées au membre.</span><span class="sxs-lookup"><span data-stu-id="d527c-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="d527c-114">à Pointeur vers la signature de métadonnées binaires du membre.</span><span class="sxs-lookup"><span data-stu-id="d527c-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="d527c-115">à Taille en octets de `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="d527c-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="d527c-116">à Pointeur vers l’adresse virtuelle relative du membre.</span><span class="sxs-lookup"><span data-stu-id="d527c-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="d527c-117">à Indicateurs d’implémentation de méthode associés au membre.</span><span class="sxs-lookup"><span data-stu-id="d527c-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="d527c-118">à Indicateur qui marque un <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="d527c-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="d527c-119">Il s’agit de l’une des `ELEMENT_TYPE_*` valeurs.</span><span class="sxs-lookup"><span data-stu-id="d527c-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="d527c-120">à Valeur de chaîne constante retournée par ce membre.</span><span class="sxs-lookup"><span data-stu-id="d527c-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="d527c-121">à Taille en caractères de `ppValue` , ou zéro si `ppValue` ne contient pas de chaîne.</span><span class="sxs-lookup"><span data-stu-id="d527c-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d527c-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d527c-122">Requirements</span></span>  

 <span data-ttu-id="d527c-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d527c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d527c-124">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d527c-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d527c-125">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d527c-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d527c-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d527c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d527c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d527c-127">See also</span></span>

- [<span data-ttu-id="d527c-128">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="d527c-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d527c-129">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="d527c-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
