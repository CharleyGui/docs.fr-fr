---
title: COR_VERSION, structure
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1f0a36d186c6d9788d43b075bf9d67c36ed1acb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740569"
---
# <a name="corversion-structure"></a><span data-ttu-id="4e9ac-102">COR_VERSION, structure</span><span class="sxs-lookup"><span data-stu-id="4e9ac-102">COR_VERSION Structure</span></span>
<span data-ttu-id="4e9ac-103">Stocke le numéro de version en quatre parties du CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="4e9ac-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e9ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e9ac-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="4e9ac-105">Membres</span><span class="sxs-lookup"><span data-stu-id="4e9ac-105">Members</span></span>  
  
|<span data-ttu-id="4e9ac-106">Membre</span><span class="sxs-lookup"><span data-stu-id="4e9ac-106">Member</span></span>|<span data-ttu-id="4e9ac-107">Description</span><span class="sxs-lookup"><span data-stu-id="4e9ac-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="4e9ac-108">Numéro de version principale.</span><span class="sxs-lookup"><span data-stu-id="4e9ac-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="4e9ac-109">Numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="4e9ac-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="4e9ac-110">Le numéro de build.</span><span class="sxs-lookup"><span data-stu-id="4e9ac-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="4e9ac-111">Le numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="4e9ac-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e9ac-112">Notes</span><span class="sxs-lookup"><span data-stu-id="4e9ac-112">Remarks</span></span>  
 <span data-ttu-id="4e9ac-113">Si le numéro de version est 1.0.3705.288, 1 est le numéro de version majeure, 0 est le numéro de version secondaire, 3705 est le numéro de build et 288 est le numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="4e9ac-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e9ac-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4e9ac-114">Requirements</span></span>  
 <span data-ttu-id="4e9ac-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e9ac-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e9ac-116">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="4e9ac-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="4e9ac-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e9ac-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e9ac-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e9ac-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e9ac-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e9ac-119">See also</span></span>

- [<span data-ttu-id="4e9ac-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="4e9ac-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="4e9ac-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="4e9ac-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
