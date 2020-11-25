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
ms.openlocfilehash: d5f61aa9b4a65a5f33e64aa4441370c3f7ca5b03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732721"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="1f702-102">CeeSectionRelocExtra, union</span><span class="sxs-lookup"><span data-stu-id="1f702-102">CeeSectionRelocExtra Union</span></span>

<span data-ttu-id="1f702-103">Représente un décalage d’adresse utilisé par l’interface [ICeeGen](iceegen-interface.md) pour déplacer une section.</span><span class="sxs-lookup"><span data-stu-id="1f702-103">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f702-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f702-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="1f702-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1f702-105">Members</span></span>  
  
|<span data-ttu-id="1f702-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1f702-106">Member</span></span>|<span data-ttu-id="1f702-107">Description</span><span class="sxs-lookup"><span data-stu-id="1f702-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="1f702-108">Ajustement d’adresse supérieure pour la section.</span><span class="sxs-lookup"><span data-stu-id="1f702-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f702-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1f702-109">Requirements</span></span>  

 <span data-ttu-id="1f702-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f702-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f702-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1f702-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1f702-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f702-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1f702-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f702-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f702-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f702-114">See also</span></span>

- [<span data-ttu-id="1f702-115">Unions de métadonnées</span><span class="sxs-lookup"><span data-stu-id="1f702-115">Metadata Unions</span></span>](metadata-unions.md)
