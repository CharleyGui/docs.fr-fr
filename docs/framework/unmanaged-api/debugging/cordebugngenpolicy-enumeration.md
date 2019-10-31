---
title: CorDebugNGenPolicy, énumération
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: 826dfceb28512e4fd3157c432b7a4d94fba704fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097862"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="328fc-102">CorDebugNGenPolicy, énumération</span><span class="sxs-lookup"><span data-stu-id="328fc-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="328fc-103">Fournit une valeur qui détermine si un débogueur charge les images natives (NGen) depuis le cache d'images natives.</span><span class="sxs-lookup"><span data-stu-id="328fc-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="328fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="328fc-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="328fc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="328fc-105">Members</span></span>  
  
|<span data-ttu-id="328fc-106">Nom de membre</span><span class="sxs-lookup"><span data-stu-id="328fc-106">Member name</span></span>|<span data-ttu-id="328fc-107">Description</span><span class="sxs-lookup"><span data-stu-id="328fc-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="328fc-108">Dans une application [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)], l’utilisation d’images du cache d’images natives locales est désactivée.</span><span class="sxs-lookup"><span data-stu-id="328fc-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="328fc-109">Dans une application de bureau, ce paramètre n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="328fc-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="328fc-110">Notes</span><span class="sxs-lookup"><span data-stu-id="328fc-110">Remarks</span></span>  
 <span data-ttu-id="328fc-111">L’énumération `CorDebugNGENPolicy` est utilisée par la méthode [ICorDebugProcess5 :: enablengenpolicy,](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="328fc-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="328fc-112">La désactivation de l’utilisation d’images à partir du cache d’images natives local offre une expérience de débogage cohérente en garantissant que le débogueur charge des images déboguées et compilées juste-à-temps au lieu d’images natives optimisées.</span><span class="sxs-lookup"><span data-stu-id="328fc-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="328fc-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="328fc-113">Requirements</span></span>  
 <span data-ttu-id="328fc-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="328fc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="328fc-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="328fc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="328fc-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="328fc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="328fc-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="328fc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="328fc-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="328fc-118">See also</span></span>

- [<span data-ttu-id="328fc-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="328fc-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
