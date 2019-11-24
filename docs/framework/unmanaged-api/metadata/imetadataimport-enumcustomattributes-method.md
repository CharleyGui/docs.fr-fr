---
title: IMetaDataImport::EnumCustomAttributes, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: a43c1883038e41cac1b58c78bc26f20d436ebbd1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440238"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="f944d-102">IMetaDataImport::EnumCustomAttributes, méthode</span><span class="sxs-lookup"><span data-stu-id="f944d-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="f944d-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span><span class="sxs-lookup"><span data-stu-id="f944d-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f944d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f944d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f944d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f944d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f944d-106">[in, out] A pointer to the returned enumerator.</span><span class="sxs-lookup"><span data-stu-id="f944d-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="f944d-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span><span class="sxs-lookup"><span data-stu-id="f944d-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="f944d-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span><span class="sxs-lookup"><span data-stu-id="f944d-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="f944d-109">[out] An array of custom attribute tokens.</span><span class="sxs-lookup"><span data-stu-id="f944d-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f944d-110">[in] Taille maximale du tableau `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="f944d-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="f944d-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="f944d-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f944d-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f944d-112">Return Value</span></span>  
  
|<span data-ttu-id="f944d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f944d-113">HRESULT</span></span>|<span data-ttu-id="f944d-114">Description</span><span class="sxs-lookup"><span data-stu-id="f944d-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f944d-115">`EnumCustomAttributes` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="f944d-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f944d-116">There are no custom attributes to enumerate.</span><span class="sxs-lookup"><span data-stu-id="f944d-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="f944d-117">In that case, `pcCustomAttributes` is zero.</span><span class="sxs-lookup"><span data-stu-id="f944d-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f944d-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="f944d-118">Requirements</span></span>  
 <span data-ttu-id="f944d-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f944d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f944d-120">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f944d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f944d-121">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f944d-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f944d-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f944d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f944d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f944d-123">See also</span></span>

- [<span data-ttu-id="f944d-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="f944d-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f944d-125">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="f944d-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
