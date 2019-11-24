---
title: ICeeGen::GetSectionCreate, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
ms.openlocfilehash: 2c3c3a0168216902e5982b7d0193e72acc2bdf47
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448094"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="2176e-102">ICeeGen::GetSectionCreate, méthode</span><span class="sxs-lookup"><span data-stu-id="2176e-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="2176e-103">Generates and gets a code section using the specified name and flag values.</span><span class="sxs-lookup"><span data-stu-id="2176e-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="2176e-104">This method is obsolete and should not be used.</span><span class="sxs-lookup"><span data-stu-id="2176e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2176e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2176e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2176e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2176e-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="2176e-107">[in] A pointer to a string that specifies the name of the section to be created.</span><span class="sxs-lookup"><span data-stu-id="2176e-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="2176e-108">[in] Flags that specify options.</span><span class="sxs-lookup"><span data-stu-id="2176e-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="2176e-109">[out] A pointer to the newly created code section.</span><span class="sxs-lookup"><span data-stu-id="2176e-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2176e-110">Notes</span><span class="sxs-lookup"><span data-stu-id="2176e-110">Remarks</span></span>  
 <span data-ttu-id="2176e-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span><span class="sxs-lookup"><span data-stu-id="2176e-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2176e-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="2176e-112">Requirements</span></span>  
 <span data-ttu-id="2176e-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2176e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2176e-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2176e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2176e-115">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2176e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2176e-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2176e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2176e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2176e-117">See also</span></span>

- [<span data-ttu-id="2176e-118">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="2176e-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
