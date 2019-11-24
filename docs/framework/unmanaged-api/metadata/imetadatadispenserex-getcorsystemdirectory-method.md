---
title: IMetaDataDispenserEx::GetCORSystemDirectory, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
ms.openlocfilehash: da9a13a3dea34f6681f47e95c5b352a710d7458b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431211"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="05d79-102">IMetaDataDispenserEx::GetCORSystemDirectory, méthode</span><span class="sxs-lookup"><span data-stu-id="05d79-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="05d79-103">Gets the directory that holds the current common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="05d79-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="05d79-104">This method is supported only for use by out-of-process debuggers.</span><span class="sxs-lookup"><span data-stu-id="05d79-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="05d79-105">If called from another component, it will return E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="05d79-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05d79-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05d79-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05d79-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05d79-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="05d79-108">[out] The buffer to receive the directory name.</span><span class="sxs-lookup"><span data-stu-id="05d79-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="05d79-109">[in] The size, in bytes, of `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="05d79-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="05d79-110">[out] The number of bytes actually returned in `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="05d79-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05d79-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="05d79-111">Requirements</span></span>  
 <span data-ttu-id="05d79-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05d79-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05d79-113">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="05d79-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05d79-114">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05d79-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05d79-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05d79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d79-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05d79-116">See also</span></span>

- [<span data-ttu-id="05d79-117">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="05d79-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="05d79-118">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="05d79-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
