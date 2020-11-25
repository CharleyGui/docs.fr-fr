---
title: CorDebugCreateProcessFlags, énumération
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
ms.openlocfilehash: f6f589656a3063fc89bd276b32d0ed751fd8d2d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733397"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="d0591-102">CorDebugCreateProcessFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="d0591-102">CorDebugCreateProcessFlags Enumeration</span></span>

<span data-ttu-id="d0591-103">Fournit des options de débogage supplémentaires qui peuvent être utilisées dans un appel à la méthode [ICorDebug :: CreateProcess](icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d0591-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0591-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0591-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d0591-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d0591-105">Members</span></span>  
  
|<span data-ttu-id="d0591-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d0591-106">Member</span></span>|<span data-ttu-id="d0591-107">Description</span><span class="sxs-lookup"><span data-stu-id="d0591-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="d0591-108">Aucune option spéciale n’est définie.</span><span class="sxs-lookup"><span data-stu-id="d0591-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0591-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d0591-109">Requirements</span></span>  

 <span data-ttu-id="d0591-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0591-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0591-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0591-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0591-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0591-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0591-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0591-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0591-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0591-114">See also</span></span>

- [<span data-ttu-id="d0591-115">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="d0591-115">Debugging Enumerations</span></span>](debugging-enumerations.md)
