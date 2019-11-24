---
title: IMetaDataAssemblyEmit::DefineAssembly, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 20628e708261076c6e172ff30c366a0d69c2e0f2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432120"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="8f9d6-102">IMetaDataAssemblyEmit::DefineAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="8f9d6-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="8f9d6-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span><span class="sxs-lookup"><span data-stu-id="8f9d6-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f9d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f9d6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f9d6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8f9d6-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="8f9d6-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span><span class="sxs-lookup"><span data-stu-id="8f9d6-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="8f9d6-107">[in] The size in bytes of `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="8f9d6-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="8f9d6-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span><span class="sxs-lookup"><span data-stu-id="8f9d6-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="8f9d6-109">[in] The human-readable text name of the assembly.</span><span class="sxs-lookup"><span data-stu-id="8f9d6-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="8f9d6-110">This value must not exceed 1024 characters.</span><span class="sxs-lookup"><span data-stu-id="8f9d6-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="8f9d6-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span><span class="sxs-lookup"><span data-stu-id="8f9d6-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="8f9d6-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span><span class="sxs-lookup"><span data-stu-id="8f9d6-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="8f9d6-113">[out] A pointer to the metadata token.</span><span class="sxs-lookup"><span data-stu-id="8f9d6-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f9d6-114">Notes</span><span class="sxs-lookup"><span data-stu-id="8f9d6-114">Remarks</span></span>  
 <span data-ttu-id="8f9d6-115">Only one `Assembly` metadata structure can be defined within a manifest.</span><span class="sxs-lookup"><span data-stu-id="8f9d6-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f9d6-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="8f9d6-116">Requirements</span></span>  
 <span data-ttu-id="8f9d6-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f9d6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f9d6-118">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8f9d6-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f9d6-119">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f9d6-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f9d6-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f9d6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f9d6-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f9d6-121">See also</span></span>

- [<span data-ttu-id="8f9d6-122">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="8f9d6-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
