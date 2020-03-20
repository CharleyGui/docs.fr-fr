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
ms.openlocfilehash: 9587bbe8f087fd9a51bba67492af1d5acb53ae4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176095"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="4df71-102">ICeeGen::ComputePointer, méthode</span><span class="sxs-lookup"><span data-stu-id="4df71-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="4df71-103">Détermine le tampon pour la section de code spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4df71-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="4df71-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="4df71-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df71-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4df71-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4df71-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4df71-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="4df71-107">[dans] La section de code pour laquelle retourner un tampon.</span><span class="sxs-lookup"><span data-stu-id="4df71-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="4df71-108">[dans] L’adresse virtuelle relative de la méthode pour laquelle obtenir un pointeur.</span><span class="sxs-lookup"><span data-stu-id="4df71-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="4df71-109">[out] Un pointeur vers le tampon retourné.</span><span class="sxs-lookup"><span data-stu-id="4df71-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4df71-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4df71-110">Requirements</span></span>  
 <span data-ttu-id="4df71-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4df71-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4df71-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="4df71-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4df71-113">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4df71-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4df71-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4df71-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df71-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4df71-115">See also</span></span>

- [<span data-ttu-id="4df71-116">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="4df71-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
