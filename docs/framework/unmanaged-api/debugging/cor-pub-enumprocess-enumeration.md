---
title: COR_PUB_ENUMPROCESS, énumération
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eab5fc13b74d8af4f0baaa3953c5c73ea255bfe6
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274020"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="dfde1-102">COR_PUB_ENUMPROCESS, énumération</span><span class="sxs-lookup"><span data-stu-id="dfde1-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="dfde1-103">Identifie le type de processus à énumérer.</span><span class="sxs-lookup"><span data-stu-id="dfde1-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfde1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfde1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="dfde1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="dfde1-105">Members</span></span>  
  
|<span data-ttu-id="dfde1-106">Nom de membre</span><span class="sxs-lookup"><span data-stu-id="dfde1-106">Member name</span></span>|<span data-ttu-id="dfde1-107">Description</span><span class="sxs-lookup"><span data-stu-id="dfde1-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="dfde1-108">Processus managé.</span><span class="sxs-lookup"><span data-stu-id="dfde1-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfde1-109">Notes</span><span class="sxs-lookup"><span data-stu-id="dfde1-109">Remarks</span></span>  
 <span data-ttu-id="dfde1-110">La version actuelle de l’API de débogage non managé énumère uniquement les processus managés.</span><span class="sxs-lookup"><span data-stu-id="dfde1-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfde1-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dfde1-111">Requirements</span></span>  
 <span data-ttu-id="dfde1-112">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfde1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfde1-113">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="dfde1-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="dfde1-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfde1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfde1-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfde1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfde1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfde1-116">See also</span></span>

- [<span data-ttu-id="dfde1-117">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="dfde1-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
