---
title: IMetaDataImport::GetParamProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: bb73ccdd9eee4b5a655a56b5d6757e0c6003fbc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437124"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="4b20c-102">IMetaDataImport::GetParamProps, méthode</span><span class="sxs-lookup"><span data-stu-id="4b20c-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="4b20c-103">Obtient les valeurs de métadonnées pour le paramètre référencé par le jeton ParamDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="4b20c-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b20c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b20c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b20c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4b20c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="4b20c-106">[in] A ParamDef token that represents the parameter to return metadata for.</span><span class="sxs-lookup"><span data-stu-id="4b20c-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="4b20c-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span><span class="sxs-lookup"><span data-stu-id="4b20c-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="4b20c-108">[out] The ordinal position of the parameter in the method argument list.</span><span class="sxs-lookup"><span data-stu-id="4b20c-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="4b20c-109">[out] A buffer to hold the name of the parameter.</span><span class="sxs-lookup"><span data-stu-id="4b20c-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4b20c-110">[in] The requested size in wide characters of `szName`.</span><span class="sxs-lookup"><span data-stu-id="4b20c-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="4b20c-111">[out] The returned size in wide characters of `szName`.</span><span class="sxs-lookup"><span data-stu-id="4b20c-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="4b20c-112">[out] A pointer to any attribute flags associated with the parameter.</span><span class="sxs-lookup"><span data-stu-id="4b20c-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="4b20c-113">This is a bitmask of `CorParamAttr` values.</span><span class="sxs-lookup"><span data-stu-id="4b20c-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="4b20c-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="4b20c-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="4b20c-115">[out] A pointer to a constant string returned by the parameter.</span><span class="sxs-lookup"><span data-stu-id="4b20c-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="4b20c-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span><span class="sxs-lookup"><span data-stu-id="4b20c-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b20c-117">Notes</span><span class="sxs-lookup"><span data-stu-id="4b20c-117">Remarks</span></span>

<span data-ttu-id="4b20c-118">The sequence values in `pulSequence` begin with 1 for parameters.</span><span class="sxs-lookup"><span data-stu-id="4b20c-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="4b20c-119">A return value has a sequence number of 0.</span><span class="sxs-lookup"><span data-stu-id="4b20c-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b20c-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="4b20c-120">Requirements</span></span>  
 <span data-ttu-id="4b20c-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b20c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b20c-122">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4b20c-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b20c-123">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b20c-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4b20c-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b20c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b20c-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b20c-125">See also</span></span>

- [<span data-ttu-id="4b20c-126">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="4b20c-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4b20c-127">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="4b20c-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
