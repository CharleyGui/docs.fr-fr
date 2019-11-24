---
title: IMetaDataEmit::DefinePermissionSet, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
ms.openlocfilehash: 4e11a52c977de7796043868e80c147d8cfd1f506
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431572"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="587ca-102">IMetaDataEmit::DefinePermissionSet, méthode</span><span class="sxs-lookup"><span data-stu-id="587ca-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="587ca-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span><span class="sxs-lookup"><span data-stu-id="587ca-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="587ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="587ca-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="587ca-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="587ca-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="587ca-106">[in] The object to be decorated.</span><span class="sxs-lookup"><span data-stu-id="587ca-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="587ca-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span><span class="sxs-lookup"><span data-stu-id="587ca-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="587ca-108">[in] The permission BLOB.</span><span class="sxs-lookup"><span data-stu-id="587ca-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="587ca-109">[in] The size, in bytes, of `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="587ca-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="587ca-110">[out] The returned permission token.</span><span class="sxs-lookup"><span data-stu-id="587ca-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="587ca-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="587ca-111">Requirements</span></span>  
 <span data-ttu-id="587ca-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="587ca-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="587ca-113">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="587ca-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="587ca-114">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="587ca-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="587ca-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="587ca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="587ca-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="587ca-116">See also</span></span>

- [<span data-ttu-id="587ca-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="587ca-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="587ca-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="587ca-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
