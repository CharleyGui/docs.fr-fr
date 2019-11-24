---
title: IMetaDataEmit2::SaveDeltaToStream, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: b5da781f148c23efcc909ad65e198e4f3c6fe5b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447871"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="631cc-102">IMetaDataEmit2::SaveDeltaToStream, méthode</span><span class="sxs-lookup"><span data-stu-id="631cc-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="631cc-103">Saves changes from the current edit-and-continue session to the specified stream.</span><span class="sxs-lookup"><span data-stu-id="631cc-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="631cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="631cc-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="631cc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="631cc-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="631cc-106">[in] An interface pointer to the writable stream to which to save changes.</span><span class="sxs-lookup"><span data-stu-id="631cc-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="631cc-107">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="631cc-107">[in] Reserved.</span></span> <span data-ttu-id="631cc-108">This value must be zero.</span><span class="sxs-lookup"><span data-stu-id="631cc-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="631cc-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="631cc-109">Requirements</span></span>  
 <span data-ttu-id="631cc-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="631cc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="631cc-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="631cc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="631cc-112">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="631cc-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="631cc-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="631cc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="631cc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="631cc-114">See also</span></span>

- [<span data-ttu-id="631cc-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="631cc-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="631cc-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="631cc-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
