---
title: ICeeGen::AllocateMethodBuffer, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: 38b9ea2ffab439f55f0a6d34d7f42c7669629168
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177922"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="5e709-102">ICeeGen::AllocateMethodBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="5e709-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="5e709-103">Crée un tampon de la taille spécifiée pour une méthode, et obtient l’adresse virtuelle relative de la méthode.</span><span class="sxs-lookup"><span data-stu-id="5e709-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="5e709-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="5e709-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e709-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e709-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e709-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e709-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="5e709-107">[dans] La longueur du tampon à créer.</span><span class="sxs-lookup"><span data-stu-id="5e709-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="5e709-108">[out] Le tampon retourné.</span><span class="sxs-lookup"><span data-stu-id="5e709-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="5e709-109">[out] L’adresse virtuelle relative de la méthode.</span><span class="sxs-lookup"><span data-stu-id="5e709-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e709-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5e709-110">Requirements</span></span>  
 <span data-ttu-id="5e709-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e709-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e709-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="5e709-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e709-113">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e709-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e709-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e709-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e709-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e709-115">See also</span></span>

- [<span data-ttu-id="5e709-116">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="5e709-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
