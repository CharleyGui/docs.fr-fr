---
title: IMetaDataEmit2::GetDeltaSaveSize, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 219d3196e3b2125033a23623b7e77e31c6f1ff03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440481"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="ca2b2-102">IMetaDataEmit2::GetDeltaSaveSize, méthode</span><span class="sxs-lookup"><span data-stu-id="ca2b2-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="ca2b2-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span><span class="sxs-lookup"><span data-stu-id="ca2b2-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca2b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca2b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca2b2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca2b2-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="ca2b2-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span><span class="sxs-lookup"><span data-stu-id="ca2b2-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="ca2b2-107">For the .NET Framework version 2.0, this parameter is ignored.</span><span class="sxs-lookup"><span data-stu-id="ca2b2-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="ca2b2-108">[out] The change in the size of the metadata.</span><span class="sxs-lookup"><span data-stu-id="ca2b2-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca2b2-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="ca2b2-109">Requirements</span></span>  
 <span data-ttu-id="ca2b2-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca2b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca2b2-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ca2b2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca2b2-112">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca2b2-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ca2b2-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca2b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca2b2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca2b2-114">See also</span></span>

- [<span data-ttu-id="ca2b2-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ca2b2-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="ca2b2-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ca2b2-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
