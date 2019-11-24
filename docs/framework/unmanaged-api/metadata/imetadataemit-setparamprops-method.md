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
ms.openlocfilehash: 813460aa027b259866b168d426fd28502b5c4465
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432496"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="ce3c8-102">IMetaDataEmit::SetParamProps, méthode</span><span class="sxs-lookup"><span data-stu-id="ce3c8-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="ce3c8-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="ce3c8-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce3c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce3c8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ce3c8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce3c8-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="ce3c8-106">[in] The token for the target parameter.</span><span class="sxs-lookup"><span data-stu-id="ce3c8-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="ce3c8-107">[in] The name of the parameter in Unicode.</span><span class="sxs-lookup"><span data-stu-id="ce3c8-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="ce3c8-108">[in] The flags for the parameter.</span><span class="sxs-lookup"><span data-stu-id="ce3c8-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="ce3c8-109">[in] The ELEMENT_TYPE_\* for the constant value.</span><span class="sxs-lookup"><span data-stu-id="ce3c8-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="ce3c8-110">[in] The constant value for the parameter.</span><span class="sxs-lookup"><span data-stu-id="ce3c8-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="ce3c8-111">[in] The size in (Unicode) characters of `pValue`.</span><span class="sxs-lookup"><span data-stu-id="ce3c8-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce3c8-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="ce3c8-112">Requirements</span></span>  
 <span data-ttu-id="ce3c8-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce3c8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce3c8-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ce3c8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce3c8-115">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce3c8-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce3c8-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce3c8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce3c8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce3c8-117">See also</span></span>

- [<span data-ttu-id="ce3c8-118">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ce3c8-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ce3c8-119">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ce3c8-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
