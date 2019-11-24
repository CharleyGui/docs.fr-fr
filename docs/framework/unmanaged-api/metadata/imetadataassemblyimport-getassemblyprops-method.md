---
title: IMetaDataAssemblyImport::GetAssemblyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: c3c57074ae53e2e1d8d41aa04cb6eb6089db58b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449432"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="6853f-102">IMetaDataAssemblyImport::GetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="6853f-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="6853f-103">Gets the set of properties for the assembly with the specified metadata signature.</span><span class="sxs-lookup"><span data-stu-id="6853f-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6853f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6853f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6853f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6853f-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="6853f-106">[in].</span><span class="sxs-lookup"><span data-stu-id="6853f-106">[in].</span></span> <span data-ttu-id="6853f-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span><span class="sxs-lookup"><span data-stu-id="6853f-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="6853f-108">[out] A pointer to the public key or the metadata token.</span><span class="sxs-lookup"><span data-stu-id="6853f-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="6853f-109">[out] The number of bytes in the returned public key.</span><span class="sxs-lookup"><span data-stu-id="6853f-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="6853f-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span><span class="sxs-lookup"><span data-stu-id="6853f-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="6853f-111">[out] The simple name of the assembly.</span><span class="sxs-lookup"><span data-stu-id="6853f-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6853f-112">[in] The size, in wide chars, of `szName`.</span><span class="sxs-lookup"><span data-stu-id="6853f-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="6853f-113">[out] The number of wide chars actually returned in `szName`.</span><span class="sxs-lookup"><span data-stu-id="6853f-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="6853f-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span><span class="sxs-lookup"><span data-stu-id="6853f-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="6853f-115">[out] Flags that describe the metadata applied to an assembly.</span><span class="sxs-lookup"><span data-stu-id="6853f-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="6853f-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span><span class="sxs-lookup"><span data-stu-id="6853f-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6853f-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="6853f-117">Requirements</span></span>  
 <span data-ttu-id="6853f-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6853f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6853f-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6853f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6853f-120">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6853f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6853f-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6853f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6853f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6853f-122">See also</span></span>

- [<span data-ttu-id="6853f-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="6853f-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
