---
title: IMetaDataImport::GetInterfaceImplProps, méthode
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: e5eb735acac73d694a0719c206bd22711a8c0333
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437538"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="f4386-102">IMetaDataImport::GetInterfaceImplProps, méthode</span><span class="sxs-lookup"><span data-stu-id="f4386-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="f4386-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span><span class="sxs-lookup"><span data-stu-id="f4386-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="f4386-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4386-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4386-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f4386-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="f4386-106">[in] The metadata token representing the method to return the class and interface tokens for.</span><span class="sxs-lookup"><span data-stu-id="f4386-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="f4386-107">[out] The metadata token representing the class that implements the method.</span><span class="sxs-lookup"><span data-stu-id="f4386-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="f4386-108">[out] The metadata token representing the interface that defines the implemented method.</span><span class="sxs-lookup"><span data-stu-id="f4386-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="f4386-109">Notes</span><span class="sxs-lookup"><span data-stu-id="f4386-109">Remarks</span></span>

 <span data-ttu-id="f4386-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="f4386-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="f4386-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span><span class="sxs-lookup"><span data-stu-id="f4386-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="f4386-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="f4386-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="f4386-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="f4386-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="f4386-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="f4386-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="f4386-115">Conceptually, this information is stored into an interface implementation table as:</span><span class="sxs-lookup"><span data-stu-id="f4386-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="f4386-116">Row number</span><span class="sxs-lookup"><span data-stu-id="f4386-116">Row number</span></span> | <span data-ttu-id="f4386-117">Class token</span><span class="sxs-lookup"><span data-stu-id="f4386-117">Class token</span></span> | <span data-ttu-id="f4386-118">Interface token</span><span class="sxs-lookup"><span data-stu-id="f4386-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="f4386-119">4</span><span class="sxs-lookup"><span data-stu-id="f4386-119">4</span></span>          |             |                 |
| <span data-ttu-id="f4386-120">5</span><span class="sxs-lookup"><span data-stu-id="f4386-120">5</span></span>          | <span data-ttu-id="f4386-121">02000007</span><span class="sxs-lookup"><span data-stu-id="f4386-121">02000007</span></span>    | <span data-ttu-id="f4386-122">02000003</span><span class="sxs-lookup"><span data-stu-id="f4386-122">02000003</span></span>        |
| <span data-ttu-id="f4386-123">6</span><span class="sxs-lookup"><span data-stu-id="f4386-123">6</span></span>          | <span data-ttu-id="f4386-124">02000007</span><span class="sxs-lookup"><span data-stu-id="f4386-124">02000007</span></span>    | <span data-ttu-id="f4386-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="f4386-125">0100000A</span></span>        |
| <span data-ttu-id="f4386-126">7</span><span class="sxs-lookup"><span data-stu-id="f4386-126">7</span></span>          |             |                 |
| <span data-ttu-id="f4386-127">8</span><span class="sxs-lookup"><span data-stu-id="f4386-127">8</span></span>          | <span data-ttu-id="f4386-128">02000007</span><span class="sxs-lookup"><span data-stu-id="f4386-128">02000007</span></span>    | <span data-ttu-id="f4386-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="f4386-129">0200001C</span></span>        |

<span data-ttu-id="f4386-130">Recall, the token is a 4-byte value:</span><span class="sxs-lookup"><span data-stu-id="f4386-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="f4386-131">The lower 3 bytes hold the row number, or RID.</span><span class="sxs-lookup"><span data-stu-id="f4386-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="f4386-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="f4386-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="f4386-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span><span class="sxs-lookup"><span data-stu-id="f4386-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="f4386-134">spécifications</span><span class="sxs-lookup"><span data-stu-id="f4386-134">Requirements</span></span>  
 <span data-ttu-id="f4386-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4386-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4386-136">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f4386-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4386-137">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f4386-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4386-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4386-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4386-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4386-139">See also</span></span>

- [<span data-ttu-id="f4386-140">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="f4386-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f4386-141">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="f4386-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
