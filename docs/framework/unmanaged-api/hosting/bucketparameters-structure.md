---
title: BucketParameters, structure
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: 7037065be138c369b847e7f86de7b46fc5ae601a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616877"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="e6922-102">BucketParameters, structure</span><span class="sxs-lookup"><span data-stu-id="e6922-102">BucketParameters Structure</span></span>
<span data-ttu-id="e6922-103">Stocke le nom de type d’un événement et les paramètres de l’exception actuelle qui est associée à l’événement.</span><span class="sxs-lookup"><span data-stu-id="e6922-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6922-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6922-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="e6922-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e6922-105">Members</span></span>  
  
|<span data-ttu-id="e6922-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e6922-106">Member</span></span>|<span data-ttu-id="e6922-107">Description</span><span class="sxs-lookup"><span data-stu-id="e6922-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="e6922-108">`true`Si le reste de cette structure est valide ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="e6922-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="e6922-109">Nom du type d’événement.</span><span class="sxs-lookup"><span data-stu-id="e6922-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="e6922-110">Tableau de chaînes, chacune spécifiant un paramètre pour l’exception actuelle associée à l’événement.</span><span class="sxs-lookup"><span data-stu-id="e6922-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6922-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="e6922-111">Requirements</span></span>  
 <span data-ttu-id="e6922-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6922-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6922-113">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="e6922-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e6922-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6922-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6922-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6922-115">See also</span></span>

- [<span data-ttu-id="e6922-116">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="e6922-116">Hosting Structures</span></span>](hosting-structures.md)
