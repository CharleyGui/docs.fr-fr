---
title: ICeeGen::AddSectionReloc, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: e5940f229e86b46bb8c5d5b2f9920a8261359f65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436409"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="1411a-102">ICeeGen::AddSectionReloc, méthode</span><span class="sxs-lookup"><span data-stu-id="1411a-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="1411a-103">Adds a .reloc instruction to the code base.</span><span class="sxs-lookup"><span data-stu-id="1411a-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="1411a-104">This method is obsolete and should not be used.</span><span class="sxs-lookup"><span data-stu-id="1411a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1411a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1411a-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1411a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1411a-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="1411a-107">[in] The section of in-memory code to which to add a .reloc instruction.</span><span class="sxs-lookup"><span data-stu-id="1411a-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="1411a-108">[in] The offset of the section.</span><span class="sxs-lookup"><span data-stu-id="1411a-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="1411a-109">[in] The section to which `offset` refers.</span><span class="sxs-lookup"><span data-stu-id="1411a-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="1411a-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span><span class="sxs-lookup"><span data-stu-id="1411a-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1411a-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="1411a-111">Requirements</span></span>  
 <span data-ttu-id="1411a-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1411a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1411a-113">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1411a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1411a-114">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1411a-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1411a-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1411a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1411a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1411a-116">See also</span></span>

- [<span data-ttu-id="1411a-117">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="1411a-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
