---
title: CeeSectionRelocExtra, union
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
ms.openlocfilehash: 7becace679b62a635d8231c3d42213f247f44190
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444167"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="ab81e-102">CeeSectionRelocExtra, union</span><span class="sxs-lookup"><span data-stu-id="ab81e-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="ab81e-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span><span class="sxs-lookup"><span data-stu-id="ab81e-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab81e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab81e-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="ab81e-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ab81e-105">Members</span></span>  
  
|<span data-ttu-id="ab81e-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ab81e-106">Member</span></span>|<span data-ttu-id="ab81e-107">Description</span><span class="sxs-lookup"><span data-stu-id="ab81e-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="ab81e-108">The upper address adjustment for the section.</span><span class="sxs-lookup"><span data-stu-id="ab81e-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab81e-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="ab81e-109">Requirements</span></span>  
 <span data-ttu-id="ab81e-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab81e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab81e-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab81e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab81e-112">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab81e-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab81e-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab81e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab81e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab81e-114">See also</span></span>

- [<span data-ttu-id="ab81e-115">Unions de métadonnées</span><span class="sxs-lookup"><span data-stu-id="ab81e-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
