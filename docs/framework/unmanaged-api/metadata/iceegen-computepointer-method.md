---
title: ICeeGen::ComputePointer, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
ms.openlocfilehash: 41a3b9c77fc766b2fa39b406dedbb3203cc97ad9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715470"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="5b9de-102">ICeeGen::ComputePointer, méthode</span><span class="sxs-lookup"><span data-stu-id="5b9de-102">ICeeGen::ComputePointer Method</span></span>

<span data-ttu-id="5b9de-103">Détermine la mémoire tampon pour la section de code spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5b9de-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="5b9de-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="5b9de-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b9de-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b9de-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b9de-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5b9de-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="5b9de-107">dans Section de code pour laquelle retourner une mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="5b9de-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="5b9de-108">dans Adresse virtuelle relative de la méthode pour laquelle obtenir un pointeur.</span><span class="sxs-lookup"><span data-stu-id="5b9de-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="5b9de-109">à Pointeur vers la mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="5b9de-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b9de-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5b9de-110">Requirements</span></span>  

 <span data-ttu-id="5b9de-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b9de-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b9de-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5b9de-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b9de-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b9de-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5b9de-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b9de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b9de-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b9de-115">See also</span></span>

- [<span data-ttu-id="5b9de-116">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="5b9de-116">ICeeGen Interface</span></span>](iceegen-interface.md)
