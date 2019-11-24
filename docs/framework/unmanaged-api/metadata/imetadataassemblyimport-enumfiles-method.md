---
title: IMetaDataAssemblyImport::EnumFiles, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: e4549789ea1af584c0850a535d9f6bb54f844ce0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443544"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="4f655-102">IMetaDataAssemblyImport::EnumFiles, méthode</span><span class="sxs-lookup"><span data-stu-id="4f655-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="4f655-103">Enumerates the files referenced in the current assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="4f655-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f655-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f655-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f655-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f655-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4f655-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="4f655-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4f655-107">This must be a null value for the first call of this method.</span><span class="sxs-lookup"><span data-stu-id="4f655-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="4f655-108">[out] The array used to store the `mdFile` metadata tokens.</span><span class="sxs-lookup"><span data-stu-id="4f655-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4f655-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="4f655-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4f655-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="4f655-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f655-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4f655-111">Return Value</span></span>  
  
|<span data-ttu-id="4f655-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f655-112">HRESULT</span></span>|<span data-ttu-id="4f655-113">Description</span><span class="sxs-lookup"><span data-stu-id="4f655-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4f655-114">`EnumFiles` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="4f655-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4f655-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="4f655-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="4f655-116">In this case, `pcTokens` is set to zero.</span><span class="sxs-lookup"><span data-stu-id="4f655-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f655-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="4f655-117">Requirements</span></span>  
 <span data-ttu-id="4f655-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f655-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f655-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4f655-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f655-120">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f655-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f655-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f655-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f655-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f655-122">See also</span></span>

- [<span data-ttu-id="4f655-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="4f655-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
