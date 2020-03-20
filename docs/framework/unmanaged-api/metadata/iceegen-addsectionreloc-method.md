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
ms.openlocfilehash: 129750644962cee3206b9e38cbeaa77d38dddd71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176108"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="ff9ea-102">ICeeGen::AddSectionReloc, méthode</span><span class="sxs-lookup"><span data-stu-id="ff9ea-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="ff9ea-103">Ajoute une instruction .reloc à la base de code.</span><span class="sxs-lookup"><span data-stu-id="ff9ea-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="ff9ea-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="ff9ea-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff9ea-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff9ea-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff9ea-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ff9ea-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="ff9ea-107">[dans] La section du code de mémoire à laquelle ajouter une instruction .reloc.</span><span class="sxs-lookup"><span data-stu-id="ff9ea-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="ff9ea-108">[dans] Le décalage de la section.</span><span class="sxs-lookup"><span data-stu-id="ff9ea-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="ff9ea-109">[dans] La section `offset` à laquelle se réfère.</span><span class="sxs-lookup"><span data-stu-id="ff9ea-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="ff9ea-110">[dans] L’une des valeurs [CeeSectionRelocType,](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) indiquant le genre d’instruction .reloc à ajouter.</span><span class="sxs-lookup"><span data-stu-id="ff9ea-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff9ea-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ff9ea-111">Requirements</span></span>  
 <span data-ttu-id="ff9ea-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff9ea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff9ea-113">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="ff9ea-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff9ea-114">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff9ea-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff9ea-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff9ea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff9ea-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff9ea-116">See also</span></span>

- [<span data-ttu-id="ff9ea-117">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="ff9ea-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
