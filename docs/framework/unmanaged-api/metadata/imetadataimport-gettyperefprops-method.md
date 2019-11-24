---
title: IMetaDataImport::GetTypeRefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 6ea7605e062eb77e0488b3a9561c4d83be16fa7d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436712"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="41ba7-102">IMetaDataImport::GetTypeRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="41ba7-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="41ba7-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span><span class="sxs-lookup"><span data-stu-id="41ba7-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41ba7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41ba7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41ba7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41ba7-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="41ba7-106">[in] The TypeRef token that represents the type to return metadata for.</span><span class="sxs-lookup"><span data-stu-id="41ba7-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="41ba7-107">[out] A pointer to the scope in which the reference is made.</span><span class="sxs-lookup"><span data-stu-id="41ba7-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="41ba7-108">This value is an AssemblyRef or ModuleRef token.</span><span class="sxs-lookup"><span data-stu-id="41ba7-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="41ba7-109">[out] A buffer containing the type name.</span><span class="sxs-lookup"><span data-stu-id="41ba7-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="41ba7-110">[in] The requested size in wide characters of `szName`.</span><span class="sxs-lookup"><span data-stu-id="41ba7-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="41ba7-111">[out] The returned size in wide characters of `szName`.</span><span class="sxs-lookup"><span data-stu-id="41ba7-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41ba7-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="41ba7-112">Requirements</span></span>  
 <span data-ttu-id="41ba7-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41ba7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41ba7-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="41ba7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41ba7-115">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41ba7-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="41ba7-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41ba7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ba7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41ba7-117">See also</span></span>

- [<span data-ttu-id="41ba7-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="41ba7-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="41ba7-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="41ba7-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
