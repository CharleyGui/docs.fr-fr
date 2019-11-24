---
title: ICeeGen::GetMethodBuffer, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
ms.openlocfilehash: 8c8ecab9d957e72bb6c0817af07c863fcff97cde
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436331"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="dc99c-102">ICeeGen::GetMethodBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="dc99c-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="dc99c-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span><span class="sxs-lookup"><span data-stu-id="dc99c-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="dc99c-104">This method is obsolete and should not be used.</span><span class="sxs-lookup"><span data-stu-id="dc99c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc99c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc99c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc99c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dc99c-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="dc99c-107">[in] The relative virtual address of the method for which to return a buffer.</span><span class="sxs-lookup"><span data-stu-id="dc99c-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="dc99c-108">[out] A pointer to the returned buffer.</span><span class="sxs-lookup"><span data-stu-id="dc99c-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc99c-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="dc99c-109">Requirements</span></span>  
 <span data-ttu-id="dc99c-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc99c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc99c-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc99c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc99c-112">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc99c-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc99c-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc99c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc99c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc99c-114">See also</span></span>

- [<span data-ttu-id="dc99c-115">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="dc99c-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
