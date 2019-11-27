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
ms.openlocfilehash: 01be6c30e16e4abdd6002fc8207b33a9c76a2eef
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448744"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="39267-102">ICeeGen::ComputePointer, méthode</span><span class="sxs-lookup"><span data-stu-id="39267-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="39267-103">Détermine la mémoire tampon pour la section de code spécifiée.</span><span class="sxs-lookup"><span data-stu-id="39267-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="39267-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="39267-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39267-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39267-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39267-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="39267-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="39267-107">dans Section de code pour laquelle retourner une mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="39267-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="39267-108">dans Adresse virtuelle relative de la méthode pour laquelle obtenir un pointeur.</span><span class="sxs-lookup"><span data-stu-id="39267-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="39267-109">à Pointeur vers la mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="39267-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39267-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="39267-110">Requirements</span></span>  
 <span data-ttu-id="39267-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39267-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39267-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="39267-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39267-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="39267-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="39267-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39267-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39267-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39267-115">See also</span></span>

- [<span data-ttu-id="39267-116">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="39267-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
