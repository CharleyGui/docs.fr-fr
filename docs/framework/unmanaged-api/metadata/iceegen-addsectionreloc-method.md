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
ms.openlocfilehash: 2f66d34fcfdd8c61dcc92817ec1a928ac5b603fc
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008896"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="54d22-102">ICeeGen::AddSectionReloc, méthode</span><span class="sxs-lookup"><span data-stu-id="54d22-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="54d22-103">Ajoute une instruction. reloc à la base de code.</span><span class="sxs-lookup"><span data-stu-id="54d22-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="54d22-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="54d22-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54d22-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54d22-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54d22-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="54d22-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="54d22-107">dans Section du code en mémoire à laquelle ajouter une instruction. reloc.</span><span class="sxs-lookup"><span data-stu-id="54d22-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="54d22-108">dans Décalage de la section.</span><span class="sxs-lookup"><span data-stu-id="54d22-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="54d22-109">dans Section à laquelle `offset` fait référence.</span><span class="sxs-lookup"><span data-stu-id="54d22-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="54d22-110">dans L’une des valeurs [CeeSectionRelocType,](ceesectionreloctype-enumeration.md) , indiquant le type d’instruction. reloc à ajouter.</span><span class="sxs-lookup"><span data-stu-id="54d22-110">[in] One of the [CeeSectionRelocType](ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54d22-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="54d22-111">Requirements</span></span>  
 <span data-ttu-id="54d22-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54d22-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54d22-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="54d22-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54d22-114">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="54d22-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54d22-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54d22-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d22-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54d22-116">See also</span></span>

- [<span data-ttu-id="54d22-117">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="54d22-117">ICeeGen Interface</span></span>](iceegen-interface.md)
