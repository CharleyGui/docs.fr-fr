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
ms.openlocfilehash: 8b54cb30ec96ad0fb7851af6f2d465fe771886ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677851"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="34fe9-102">BucketParameters, structure</span><span class="sxs-lookup"><span data-stu-id="34fe9-102">BucketParameters Structure</span></span>

<span data-ttu-id="34fe9-103">Stocke le nom de type d’un événement et les paramètres de l’exception actuelle qui est associée à l’événement.</span><span class="sxs-lookup"><span data-stu-id="34fe9-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34fe9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34fe9-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="34fe9-105">Membres</span><span class="sxs-lookup"><span data-stu-id="34fe9-105">Members</span></span>  
  
|<span data-ttu-id="34fe9-106">Membre</span><span class="sxs-lookup"><span data-stu-id="34fe9-106">Member</span></span>|<span data-ttu-id="34fe9-107">Description</span><span class="sxs-lookup"><span data-stu-id="34fe9-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="34fe9-108">`true`Si le reste de cette structure est valide ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="34fe9-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="34fe9-109">Nom du type d’événement.</span><span class="sxs-lookup"><span data-stu-id="34fe9-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="34fe9-110">Tableau de chaînes, chacune spécifiant un paramètre pour l’exception actuelle associée à l’événement.</span><span class="sxs-lookup"><span data-stu-id="34fe9-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34fe9-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="34fe9-111">Requirements</span></span>  

 <span data-ttu-id="34fe9-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34fe9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34fe9-113">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="34fe9-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="34fe9-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34fe9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34fe9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34fe9-115">See also</span></span>

- [<span data-ttu-id="34fe9-116">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="34fe9-116">Hosting Structures</span></span>](hosting-structures.md)
