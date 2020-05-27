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
ms.openlocfilehash: 206dcd3a0a82da9b6211c8c2045e4e9d3d991973
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008870"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="700ce-102">ICeeGen::ComputePointer, méthode</span><span class="sxs-lookup"><span data-stu-id="700ce-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="700ce-103">Détermine la mémoire tampon pour la section de code spécifiée.</span><span class="sxs-lookup"><span data-stu-id="700ce-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="700ce-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="700ce-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="700ce-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="700ce-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="700ce-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="700ce-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="700ce-107">dans Section de code pour laquelle retourner une mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="700ce-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="700ce-108">dans Adresse virtuelle relative de la méthode pour laquelle obtenir un pointeur.</span><span class="sxs-lookup"><span data-stu-id="700ce-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="700ce-109">à Pointeur vers la mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="700ce-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="700ce-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="700ce-110">Requirements</span></span>  
 <span data-ttu-id="700ce-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="700ce-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="700ce-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="700ce-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="700ce-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="700ce-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="700ce-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="700ce-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="700ce-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="700ce-115">See also</span></span>

- [<span data-ttu-id="700ce-116">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="700ce-116">ICeeGen Interface</span></span>](iceegen-interface.md)
