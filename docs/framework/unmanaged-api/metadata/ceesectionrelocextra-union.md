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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2e73caa3c69090bca30c8d4a907ddb619bd0ed4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776324"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="c6df4-102">CeeSectionRelocExtra, union</span><span class="sxs-lookup"><span data-stu-id="c6df4-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="c6df4-103">Représente un offset d’adresse qui est utilisé par le [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface pour déplacer une section.</span><span class="sxs-lookup"><span data-stu-id="c6df4-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6df4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6df4-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="c6df4-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c6df4-105">Members</span></span>  
  
|<span data-ttu-id="c6df4-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c6df4-106">Member</span></span>|<span data-ttu-id="c6df4-107">Description</span><span class="sxs-lookup"><span data-stu-id="c6df4-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="c6df4-108">L’ajustement de la limite supérieure de la section.</span><span class="sxs-lookup"><span data-stu-id="c6df4-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6df4-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c6df4-109">Requirements</span></span>  
 <span data-ttu-id="c6df4-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6df4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6df4-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c6df4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6df4-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6df4-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6df4-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6df4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6df4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6df4-114">See also</span></span>

- [<span data-ttu-id="c6df4-115">Unions de métadonnées</span><span class="sxs-lookup"><span data-stu-id="c6df4-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
