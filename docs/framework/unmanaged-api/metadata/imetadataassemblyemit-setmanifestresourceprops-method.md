---
title: IMetaDataAssemblyEmit::SetManifestResourceProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
ms.openlocfilehash: f6b5e12df60663b75e10b04eaa008a75d720d753
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434429"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="cf3d8-102">IMetaDataAssemblyEmit::SetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="cf3d8-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="cf3d8-103">Modifie la structure de métadonnées `ManifestResource` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cf3d8-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf3d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf3d8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf3d8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf3d8-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="cf3d8-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span><span class="sxs-lookup"><span data-stu-id="cf3d8-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="cf3d8-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span><span class="sxs-lookup"><span data-stu-id="cf3d8-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="cf3d8-108">[in] The offset to the beginning of the resource within the file.</span><span class="sxs-lookup"><span data-stu-id="cf3d8-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="cf3d8-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span><span class="sxs-lookup"><span data-stu-id="cf3d8-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf3d8-110">Notes</span><span class="sxs-lookup"><span data-stu-id="cf3d8-110">Remarks</span></span>  
 <span data-ttu-id="cf3d8-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="cf3d8-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf3d8-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="cf3d8-112">Requirements</span></span>  
 <span data-ttu-id="cf3d8-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf3d8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf3d8-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf3d8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf3d8-115">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf3d8-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf3d8-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf3d8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf3d8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf3d8-117">See also</span></span>

- [<span data-ttu-id="cf3d8-118">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="cf3d8-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
