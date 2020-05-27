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
ms.openlocfilehash: d11fefe220fdb00457cc48a6cd166673350be049
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006027"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="36232-102">CeeSectionRelocExtra, union</span><span class="sxs-lookup"><span data-stu-id="36232-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="36232-103">Représente un décalage d’adresse utilisé par l’interface [ICeeGen](iceegen-interface.md) pour déplacer une section.</span><span class="sxs-lookup"><span data-stu-id="36232-103">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36232-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36232-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="36232-105">Membres</span><span class="sxs-lookup"><span data-stu-id="36232-105">Members</span></span>  
  
|<span data-ttu-id="36232-106">Membre</span><span class="sxs-lookup"><span data-stu-id="36232-106">Member</span></span>|<span data-ttu-id="36232-107">Description</span><span class="sxs-lookup"><span data-stu-id="36232-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="36232-108">Ajustement d’adresse supérieure pour la section.</span><span class="sxs-lookup"><span data-stu-id="36232-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36232-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="36232-109">Requirements</span></span>  
 <span data-ttu-id="36232-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36232-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36232-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="36232-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36232-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="36232-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36232-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36232-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36232-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36232-114">See also</span></span>

- [<span data-ttu-id="36232-115">Unions de métadonnées</span><span class="sxs-lookup"><span data-stu-id="36232-115">Metadata Unions</span></span>](metadata-unions.md)
