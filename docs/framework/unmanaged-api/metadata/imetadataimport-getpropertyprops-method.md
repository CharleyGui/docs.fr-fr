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
ms.openlocfilehash: 247a2793bf3806f5ee38585d50b4535820dfcb69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437060"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="401a1-102">IMetaDataImport::GetPropertyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="401a1-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="401a1-103">Gets the metadata for the property represented by the specified token.</span><span class="sxs-lookup"><span data-stu-id="401a1-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="401a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="401a1-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="401a1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="401a1-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="401a1-106">[in] A token that represents the property to return metadata for.</span><span class="sxs-lookup"><span data-stu-id="401a1-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="401a1-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span><span class="sxs-lookup"><span data-stu-id="401a1-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="401a1-108">[out] A buffer to hold the property name.</span><span class="sxs-lookup"><span data-stu-id="401a1-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="401a1-109">[in] The size in wide characters of `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="401a1-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="401a1-110">[out] The number of wide characters returned in `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="401a1-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="401a1-111">[out] A pointer to any attribute flags applied to the property.</span><span class="sxs-lookup"><span data-stu-id="401a1-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="401a1-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span><span class="sxs-lookup"><span data-stu-id="401a1-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="401a1-113">[out] A pointer to the metadata signature of the property.</span><span class="sxs-lookup"><span data-stu-id="401a1-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="401a1-114">[out] The number of bytes returned in `ppvSig`.</span><span class="sxs-lookup"><span data-stu-id="401a1-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="401a1-115">[out] A flag specifying the type of the constant that is the default value of the property.</span><span class="sxs-lookup"><span data-stu-id="401a1-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="401a1-116">This value is from the CorElementType enumeration.</span><span class="sxs-lookup"><span data-stu-id="401a1-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="401a1-117">[out] A pointer to the bytes that store the default value for this property.</span><span class="sxs-lookup"><span data-stu-id="401a1-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="401a1-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span><span class="sxs-lookup"><span data-stu-id="401a1-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="401a1-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span><span class="sxs-lookup"><span data-stu-id="401a1-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="401a1-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span><span class="sxs-lookup"><span data-stu-id="401a1-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="401a1-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span><span class="sxs-lookup"><span data-stu-id="401a1-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="401a1-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span><span class="sxs-lookup"><span data-stu-id="401a1-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="401a1-123">[in] Taille maximale du tableau `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="401a1-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="401a1-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span><span class="sxs-lookup"><span data-stu-id="401a1-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="401a1-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="401a1-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="401a1-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="401a1-126">Requirements</span></span>  
 <span data-ttu-id="401a1-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="401a1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="401a1-128">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="401a1-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="401a1-129">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="401a1-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="401a1-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="401a1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401a1-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="401a1-131">See also</span></span>

- [<span data-ttu-id="401a1-132">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="401a1-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="401a1-133">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="401a1-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
