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
ms.openlocfilehash: aded23e190de18d76bb2b9e2ffbae51cf2325419
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729224"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="1707e-102">IMetaDataImport::GetPropertyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="1707e-102">IMetaDataImport::GetPropertyProps Method</span></span>

<span data-ttu-id="1707e-103">Obtient les métadonnées de la propriété représentée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="1707e-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1707e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1707e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1707e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1707e-105">Parameters</span></span>  

 `prop`  
 <span data-ttu-id="1707e-106">dans Jeton qui représente la propriété dont les métadonnées doivent être retournées.</span><span class="sxs-lookup"><span data-stu-id="1707e-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="1707e-107">à Pointeur vers le jeton TypeDef qui représente le type qui implémente la propriété.</span><span class="sxs-lookup"><span data-stu-id="1707e-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="1707e-108">à Mémoire tampon destinée à contenir le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="1707e-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="1707e-109">dans Taille en caractères larges de `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="1707e-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="1707e-110">à Nombre de caractères larges retournés dans `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="1707e-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="1707e-111">à Pointeur vers tous les indicateurs d’attribut appliqués à la propriété.</span><span class="sxs-lookup"><span data-stu-id="1707e-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="1707e-112">Cette valeur est un masque de masque de l’énumération [CorPropertyAttr,](corpropertyattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="1707e-112">This value is a bitmask from the [CorPropertyAttr](corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="1707e-113">à Pointeur vers la signature de métadonnées de la propriété.</span><span class="sxs-lookup"><span data-stu-id="1707e-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="1707e-114">à Nombre d’octets retournés dans `ppvSig` .</span><span class="sxs-lookup"><span data-stu-id="1707e-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="1707e-115">à Indicateur spécifiant le type de la constante qui est la valeur par défaut de la propriété.</span><span class="sxs-lookup"><span data-stu-id="1707e-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="1707e-116">Cette valeur provient de l’énumération CorElementType.</span><span class="sxs-lookup"><span data-stu-id="1707e-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="1707e-117">à Pointeur vers les octets qui stockent la valeur par défaut de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="1707e-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="1707e-118">à Taille en caractères larges de `ppDefaultValue` , si `pdwCPlusTypeFlag` est ELEMENT_TYPE_STRING ; sinon, cette valeur n’est pas pertinente.</span><span class="sxs-lookup"><span data-stu-id="1707e-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="1707e-119">Dans ce cas, la longueur de `ppDefaultValue` est déduite du type spécifié par `pdwCPlusTypeFlag` .</span><span class="sxs-lookup"><span data-stu-id="1707e-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="1707e-120">à Pointeur vers le jeton MethodDef qui représente la méthode d’accesseur Set pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="1707e-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="1707e-121">à Pointeur vers le jeton MethodDef qui représente la méthode d’accesseur get pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="1707e-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="1707e-122">à Tableau de jetons MethodDef qui représentent d’autres méthodes associées à la propriété.</span><span class="sxs-lookup"><span data-stu-id="1707e-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1707e-123">[in] Taille maximale du tableau `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="1707e-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="1707e-124">Si vous ne fournissez pas un tableau suffisamment grand pour contenir toutes les méthodes, elles sont ignorées sans avertissement.</span><span class="sxs-lookup"><span data-stu-id="1707e-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="1707e-125">à Nombre de jetons MethodDef retournés dans `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="1707e-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1707e-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1707e-126">Requirements</span></span>  

 <span data-ttu-id="1707e-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1707e-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1707e-128">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1707e-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1707e-129">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1707e-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1707e-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1707e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1707e-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1707e-131">See also</span></span>

- [<span data-ttu-id="1707e-132">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="1707e-132">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1707e-133">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="1707e-133">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
