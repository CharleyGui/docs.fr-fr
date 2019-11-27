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
ms.openlocfilehash: 34636f1ca8e42c452aa41f6145d439a26f01b0a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436393"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="e8a34-102">ICeeGen::AllocateMethodBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="e8a34-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="e8a34-103">Crée une mémoire tampon de la taille spécifiée pour une méthode et obtient l’adresse virtuelle relative de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e8a34-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="e8a34-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="e8a34-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8a34-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8a34-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8a34-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8a34-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="e8a34-107">dans Longueur de la mémoire tampon à créer.</span><span class="sxs-lookup"><span data-stu-id="e8a34-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="e8a34-108">à Mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="e8a34-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="e8a34-109">à Adresse virtuelle relative de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e8a34-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8a34-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e8a34-110">Requirements</span></span>  
 <span data-ttu-id="e8a34-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8a34-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8a34-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e8a34-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8a34-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e8a34-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8a34-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8a34-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a34-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8a34-115">See also</span></span>

- [<span data-ttu-id="e8a34-116">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="e8a34-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
