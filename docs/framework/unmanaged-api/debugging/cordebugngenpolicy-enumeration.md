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
ms.openlocfilehash: de0e07429187f1ec484942d522cdf57f819d553a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789294"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="56ba7-102">CorDebugNGenPolicy, énumération</span><span class="sxs-lookup"><span data-stu-id="56ba7-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="56ba7-103">Fournit une valeur qui détermine si un débogueur charge les images natives (NGen) depuis le cache d'images natives.</span><span class="sxs-lookup"><span data-stu-id="56ba7-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ba7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56ba7-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="56ba7-105">Members</span><span class="sxs-lookup"><span data-stu-id="56ba7-105">Members</span></span>  
  
|<span data-ttu-id="56ba7-106">Nom du membre</span><span class="sxs-lookup"><span data-stu-id="56ba7-106">Member name</span></span>|<span data-ttu-id="56ba7-107">Description</span><span class="sxs-lookup"><span data-stu-id="56ba7-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="56ba7-108">Dans une application Windows 8. x Store, l’utilisation d’images du cache d’images natives locales est désactivée.</span><span class="sxs-lookup"><span data-stu-id="56ba7-108">In a Windows 8.x Store app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="56ba7-109">Dans une application de bureau, ce paramètre n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="56ba7-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56ba7-110">Notes</span><span class="sxs-lookup"><span data-stu-id="56ba7-110">Remarks</span></span>  
 <span data-ttu-id="56ba7-111">L’énumération `CorDebugNGENPolicy` est utilisée par la méthode [ICorDebugProcess5 :: enablengenpolicy,](icordebugprocess5-enablengenpolicy-method.md) .</span><span class="sxs-lookup"><span data-stu-id="56ba7-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="56ba7-112">La désactivation de l’utilisation d’images à partir du cache d’images natives local offre une expérience de débogage cohérente en garantissant que le débogueur charge des images déboguées et compilées juste-à-temps au lieu d’images natives optimisées.</span><span class="sxs-lookup"><span data-stu-id="56ba7-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56ba7-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="56ba7-113">Requirements</span></span>  
 <span data-ttu-id="56ba7-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56ba7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56ba7-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56ba7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56ba7-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56ba7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56ba7-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56ba7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ba7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56ba7-118">See also</span></span>

- [<span data-ttu-id="56ba7-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="56ba7-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
