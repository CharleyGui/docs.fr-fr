---
title: CorDebugHandleType, énumération
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
ms.openlocfilehash: 2d296c1778e00c4c72e860e0705994518d1481e8
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795879"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="b49b3-102">CorDebugHandleType, énumération</span><span class="sxs-lookup"><span data-stu-id="b49b3-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="b49b3-103">Indique le type de handle.</span><span class="sxs-lookup"><span data-stu-id="b49b3-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b49b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b49b3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="b49b3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b49b3-105">Members</span></span>  
  
|<span data-ttu-id="b49b3-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b49b3-106">Member</span></span>|<span data-ttu-id="b49b3-107">Description</span><span class="sxs-lookup"><span data-stu-id="b49b3-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="b49b3-108">Le handle est fort, ce qui empêche la récupération d’un objet par garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b49b3-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="b49b3-109">Le descripteur est faible, ce qui n’empêche pas un objet d’être récupéré par garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b49b3-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="b49b3-110">Le descripteur devient non valide lors de la collecte de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b49b3-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b49b3-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b49b3-111">Requirements</span></span>  
 <span data-ttu-id="b49b3-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b49b3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b49b3-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b49b3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b49b3-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b49b3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b49b3-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b49b3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b49b3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b49b3-116">See also</span></span>

- [<span data-ttu-id="b49b3-117">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="b49b3-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
