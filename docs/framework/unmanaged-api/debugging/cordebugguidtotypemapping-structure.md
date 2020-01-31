---
title: Structure CorDebugGuidToTypeMapping
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
ms.openlocfilehash: b855a53c9e4303138d7605bdf108d37bb345b917
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789327"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="ebfef-102">Structure CorDebugGuidToTypeMapping</span><span class="sxs-lookup"><span data-stu-id="ebfef-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="ebfef-103">Mappe un GUID Windows Runtime à son objet ICorDebugType correspondant.</span><span class="sxs-lookup"><span data-stu-id="ebfef-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebfef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebfef-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="ebfef-105">Members</span><span class="sxs-lookup"><span data-stu-id="ebfef-105">Members</span></span>  
  
|<span data-ttu-id="ebfef-106">Member</span><span class="sxs-lookup"><span data-stu-id="ebfef-106">Member</span></span>|<span data-ttu-id="ebfef-107">Description</span><span class="sxs-lookup"><span data-stu-id="ebfef-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="ebfef-108">GUID du type de Windows Runtime mis en cache.</span><span class="sxs-lookup"><span data-stu-id="ebfef-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="ebfef-109">Pointeur vers un objet ICorDebugType qui fournit des informations sur le type mis en cache.</span><span class="sxs-lookup"><span data-stu-id="ebfef-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ebfef-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ebfef-110">Requirements</span></span>  
 <span data-ttu-id="ebfef-111">**Plateformes :** Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="ebfef-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="ebfef-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebfef-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebfef-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebfef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebfef-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebfef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebfef-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebfef-115">See also</span></span>

- [<span data-ttu-id="ebfef-116">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="ebfef-116">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ebfef-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="ebfef-117">Debugging</span></span>](index.md)
