---
title: ICeeGen::TruncateSection, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
ms.openlocfilehash: 3005db62bba4089c669a00f62e3c1e62f9e1dae9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685694"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="a8894-102">ICeeGen::TruncateSection, méthode</span><span class="sxs-lookup"><span data-stu-id="a8894-102">ICeeGen::TruncateSection Method</span></span>

<span data-ttu-id="a8894-103">Tronque la section de code spécifiée selon la longueur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a8894-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="a8894-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="a8894-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8894-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8894-105">Syntax</span></span>  
  
```cpp  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8894-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a8894-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="a8894-107">dans Section à tronquer.</span><span class="sxs-lookup"><span data-stu-id="a8894-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="a8894-108">dans Longueur, en octets, à laquelle la section doit être tronquée.</span><span class="sxs-lookup"><span data-stu-id="a8894-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8894-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="a8894-109">Remarks</span></span>  

 <span data-ttu-id="a8894-110">Appelez `TruncateSection` uniquement si vous avez des exigences de section spéciales qui ne sont pas gérées par d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="a8894-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8894-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a8894-111">Requirements</span></span>  

 <span data-ttu-id="a8894-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8894-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8894-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a8894-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8894-114">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8894-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8894-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8894-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8894-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8894-116">See also</span></span>

- [<span data-ttu-id="a8894-117">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="a8894-117">ICeeGen Interface</span></span>](iceegen-interface.md)
