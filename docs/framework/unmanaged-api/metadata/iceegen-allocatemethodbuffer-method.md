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
ms.openlocfilehash: 8dc7f439cac56c2d55916ff8631ec3095c67680d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008883"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="006f2-102">ICeeGen::AllocateMethodBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="006f2-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="006f2-103">Crée une mémoire tampon de la taille spécifiée pour une méthode et obtient l’adresse virtuelle relative de la méthode.</span><span class="sxs-lookup"><span data-stu-id="006f2-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="006f2-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="006f2-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="006f2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="006f2-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="006f2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="006f2-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="006f2-107">dans Longueur de la mémoire tampon à créer.</span><span class="sxs-lookup"><span data-stu-id="006f2-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="006f2-108">à Mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="006f2-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="006f2-109">à Adresse virtuelle relative de la méthode.</span><span class="sxs-lookup"><span data-stu-id="006f2-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="006f2-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="006f2-110">Requirements</span></span>  
 <span data-ttu-id="006f2-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="006f2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="006f2-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="006f2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="006f2-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="006f2-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="006f2-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="006f2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="006f2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="006f2-115">See also</span></span>

- [<span data-ttu-id="006f2-116">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="006f2-116">ICeeGen Interface</span></span>](iceegen-interface.md)
