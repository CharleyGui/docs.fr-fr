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
ms.openlocfilehash: 80623bdec939b0ae5fc13008c1c4001c613ac435
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195957"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="f9e19-102">BucketParameters, structure</span><span class="sxs-lookup"><span data-stu-id="f9e19-102">BucketParameters Structure</span></span>
<span data-ttu-id="f9e19-103">Stocke le nom de type d’un événement et les paramètres de l’exception actuelle qui est associée à l’événement.</span><span class="sxs-lookup"><span data-stu-id="f9e19-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9e19-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="f9e19-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f9e19-105">Members</span></span>  
  
|<span data-ttu-id="f9e19-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f9e19-106">Member</span></span>|<span data-ttu-id="f9e19-107">Description</span><span class="sxs-lookup"><span data-stu-id="f9e19-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="f9e19-108">`true`, si le reste de cette structure est valide ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="f9e19-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="f9e19-109">Nom du type d’événement.</span><span class="sxs-lookup"><span data-stu-id="f9e19-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="f9e19-110">Tableau de chaînes, chacune spécifiant un paramètre pour l’exception actuelle associée à l’événement.</span><span class="sxs-lookup"><span data-stu-id="f9e19-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9e19-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="f9e19-111">Requirements</span></span>  
 <span data-ttu-id="f9e19-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9e19-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9e19-113">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="f9e19-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="f9e19-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9e19-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e19-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9e19-115">See also</span></span>

- [<span data-ttu-id="f9e19-116">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="f9e19-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
