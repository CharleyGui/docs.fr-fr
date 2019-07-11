---
title: CorMethodSemanticsAttr, énumération
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b09ccfdb33c9853ed97005461f2288f1e7e6fd1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781753"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="2d4dc-102">CorMethodSemanticsAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="2d4dc-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="2d4dc-103">Contient des valeurs qui décrivent la relation entre une méthode et une propriété ou un événement associé.</span><span class="sxs-lookup"><span data-stu-id="2d4dc-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d4dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d4dc-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="2d4dc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2d4dc-105">Members</span></span>  
  
|<span data-ttu-id="2d4dc-106">Membre</span><span class="sxs-lookup"><span data-stu-id="2d4dc-106">Member</span></span>|<span data-ttu-id="2d4dc-107">Description</span><span class="sxs-lookup"><span data-stu-id="2d4dc-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="2d4dc-108">Spécifie que la méthode est un `set` accesseur pour une propriété.</span><span class="sxs-lookup"><span data-stu-id="2d4dc-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="2d4dc-109">Spécifie que la méthode est un `get` accesseur pour une propriété.</span><span class="sxs-lookup"><span data-stu-id="2d4dc-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="2d4dc-110">Spécifie que la méthode a une relation à une propriété ou un événement autres que ceux définis ici.</span><span class="sxs-lookup"><span data-stu-id="2d4dc-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="2d4dc-111">Spécifie que la méthode ajoute des méthodes de gestionnaire pour un événement.</span><span class="sxs-lookup"><span data-stu-id="2d4dc-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="2d4dc-112">Spécifie que la méthode supprime des méthodes de gestionnaire pour un événement.</span><span class="sxs-lookup"><span data-stu-id="2d4dc-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="2d4dc-113">Spécifie que la méthode déclenche un événement.</span><span class="sxs-lookup"><span data-stu-id="2d4dc-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d4dc-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2d4dc-114">Requirements</span></span>  
 <span data-ttu-id="2d4dc-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d4dc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d4dc-116">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2d4dc-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2d4dc-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d4dc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d4dc-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d4dc-118">See also</span></span>

- [<span data-ttu-id="2d4dc-119">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="2d4dc-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
