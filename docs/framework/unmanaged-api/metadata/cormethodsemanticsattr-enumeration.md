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
ms.openlocfilehash: bab215a8221696a0e43e228278085fcef52a40e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442825"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="bdc56-102">CorMethodSemanticsAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="bdc56-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="bdc56-103">Contient des valeurs qui décrivent la relation entre une méthode et une propriété ou un événement associé.</span><span class="sxs-lookup"><span data-stu-id="bdc56-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdc56-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="bdc56-105">Membres</span><span class="sxs-lookup"><span data-stu-id="bdc56-105">Members</span></span>  
  
|<span data-ttu-id="bdc56-106">Membre</span><span class="sxs-lookup"><span data-stu-id="bdc56-106">Member</span></span>|<span data-ttu-id="bdc56-107">Description</span><span class="sxs-lookup"><span data-stu-id="bdc56-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="bdc56-108">Spécifie que la méthode est un accesseur `set` pour une propriété.</span><span class="sxs-lookup"><span data-stu-id="bdc56-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="bdc56-109">Spécifie que la méthode est un accesseur `get` pour une propriété.</span><span class="sxs-lookup"><span data-stu-id="bdc56-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="bdc56-110">Spécifie que la méthode a une relation avec une propriété ou un événement autre que ceux définis ici.</span><span class="sxs-lookup"><span data-stu-id="bdc56-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="bdc56-111">Spécifie que la méthode ajoute des méthodes de gestionnaire pour un événement.</span><span class="sxs-lookup"><span data-stu-id="bdc56-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="bdc56-112">Spécifie que la méthode supprime les méthodes de gestionnaire pour un événement.</span><span class="sxs-lookup"><span data-stu-id="bdc56-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="bdc56-113">Spécifie que la méthode déclenche un événement.</span><span class="sxs-lookup"><span data-stu-id="bdc56-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bdc56-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bdc56-114">Requirements</span></span>  
 <span data-ttu-id="bdc56-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdc56-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdc56-116">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="bdc56-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bdc56-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdc56-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdc56-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdc56-118">See also</span></span>

- [<span data-ttu-id="bdc56-119">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="bdc56-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
