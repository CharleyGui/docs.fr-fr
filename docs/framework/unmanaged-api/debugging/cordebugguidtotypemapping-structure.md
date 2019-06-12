---
title: CorDebugGuidToTypeMapping, structure
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38e1b19d6340f559e6f8b7e0f7bc042a10df16c3
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025989"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="a1b64-102">CorDebugGuidToTypeMapping, structure</span><span class="sxs-lookup"><span data-stu-id="a1b64-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="a1b64-103">Mappe un GUID d’exécution de Windows à son objet ICorDebugType correspondant.</span><span class="sxs-lookup"><span data-stu-id="a1b64-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b64-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="a1b64-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a1b64-105">Members</span></span>  
  
|<span data-ttu-id="a1b64-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a1b64-106">Member</span></span>|<span data-ttu-id="a1b64-107">Description</span><span class="sxs-lookup"><span data-stu-id="a1b64-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="a1b64-108">Le GUID du type Windows Runtime mis en cache.</span><span class="sxs-lookup"><span data-stu-id="a1b64-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="a1b64-109">Pointeur vers un objet ICorDebugType qui fournit des informations sur le type mis en cache.</span><span class="sxs-lookup"><span data-stu-id="a1b64-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1b64-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1b64-110">Requirements</span></span>  
 <span data-ttu-id="a1b64-111">**Plateformes :** Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="a1b64-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="a1b64-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1b64-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1b64-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1b64-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1b64-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1b64-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b64-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1b64-115">See also</span></span>

- [<span data-ttu-id="a1b64-116">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="a1b64-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="a1b64-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="a1b64-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
