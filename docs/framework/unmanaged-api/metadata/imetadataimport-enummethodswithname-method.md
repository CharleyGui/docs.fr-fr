---
title: IMetaDataImport::EnumMethodsWithName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: b0817288040550b5f4c3c4ec063f6a7fdb004137
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450060"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="d554a-102">IMetaDataImport::EnumMethodsWithName, méthode</span><span class="sxs-lookup"><span data-stu-id="d554a-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="d554a-103">Énumère les méthodes portant le nom spécifié et définies par le type référencé par le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="d554a-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d554a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d554a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d554a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d554a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d554a-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="d554a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d554a-107">This must be NULL for the first call of this method.</span><span class="sxs-lookup"><span data-stu-id="d554a-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="d554a-108">[in] A TypeDef token representing the type whose methods to enumerate.</span><span class="sxs-lookup"><span data-stu-id="d554a-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="d554a-109">[in] The name that limits the scope of the enumeration.</span><span class="sxs-lookup"><span data-stu-id="d554a-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="d554a-110">[out] The array used to store the MethodDef tokens.</span><span class="sxs-lookup"><span data-stu-id="d554a-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d554a-111">[in] Taille maximale du tableau `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="d554a-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d554a-112">[out] The number of MethodDef tokens returned in `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="d554a-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d554a-113">Notes</span><span class="sxs-lookup"><span data-stu-id="d554a-113">Remarks</span></span>  
 <span data-ttu-id="d554a-114">This method enumerates fields and methods, but not properties or events.</span><span class="sxs-lookup"><span data-stu-id="d554a-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="d554a-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span><span class="sxs-lookup"><span data-stu-id="d554a-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d554a-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d554a-116">Return Value</span></span>  
  
|<span data-ttu-id="d554a-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d554a-117">HRESULT</span></span>|<span data-ttu-id="d554a-118">Description</span><span class="sxs-lookup"><span data-stu-id="d554a-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d554a-119">`EnumMethodsWithName` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="d554a-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d554a-120">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="d554a-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="d554a-121">In that case, `pcTokens` is zero.</span><span class="sxs-lookup"><span data-stu-id="d554a-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d554a-122">spécifications</span><span class="sxs-lookup"><span data-stu-id="d554a-122">Requirements</span></span>  
 <span data-ttu-id="d554a-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d554a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d554a-124">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d554a-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d554a-125">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d554a-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d554a-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d554a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d554a-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d554a-127">See also</span></span>

- [<span data-ttu-id="d554a-128">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="d554a-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d554a-129">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="d554a-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
