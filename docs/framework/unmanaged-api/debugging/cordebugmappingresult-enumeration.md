---
title: CorDebugMappingResult, énumération
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
ms.openlocfilehash: 317dc2fe8403ae25949410423f1a28ad365caf6a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789306"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="ab2d0-102">CorDebugMappingResult, énumération</span><span class="sxs-lookup"><span data-stu-id="ab2d0-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="ab2d0-103">Fournit les détails sur la façon dont la valeur du pointeur d'instruction a été obtenue.</span><span class="sxs-lookup"><span data-stu-id="ab2d0-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab2d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab2d0-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="ab2d0-105">Members</span><span class="sxs-lookup"><span data-stu-id="ab2d0-105">Members</span></span>  
  
|<span data-ttu-id="ab2d0-106">Member</span><span class="sxs-lookup"><span data-stu-id="ab2d0-106">Member</span></span>|<span data-ttu-id="ab2d0-107">Description</span><span class="sxs-lookup"><span data-stu-id="ab2d0-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="ab2d0-108">Le code natif est dans le prologue, donc la valeur de l’adresse IP est 0.</span><span class="sxs-lookup"><span data-stu-id="ab2d0-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="ab2d0-109">Le code natif se trouve dans un épilogue, donc la valeur de l’adresse IP est l’adresse de la dernière instruction de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ab2d0-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="ab2d0-110">Aucune information de mappage n’étant disponible pour la méthode, la valeur de l’adresse IP est 0.</span><span class="sxs-lookup"><span data-stu-id="ab2d0-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="ab2d0-111">Bien qu’il existe des informations de mappage pour la méthode, l’adresse actuelle ne peut pas être mappée au code MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="ab2d0-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="ab2d0-112">La valeur de l’adresse IP est 0.</span><span class="sxs-lookup"><span data-stu-id="ab2d0-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="ab2d0-113">Soit la méthode est mappée exactement au code MSIL, soit le frame a été interprété, donc la valeur de l’adresse IP est exacte.</span><span class="sxs-lookup"><span data-stu-id="ab2d0-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="ab2d0-114">La méthode a été correctement mappée, mais la valeur de l’adresse IP peut être approximative.</span><span class="sxs-lookup"><span data-stu-id="ab2d0-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab2d0-115">Notes</span><span class="sxs-lookup"><span data-stu-id="ab2d0-115">Remarks</span></span>  
 <span data-ttu-id="ab2d0-116">Vous pouvez utiliser la méthode [ICorDebugILFrame :: GetIP](icordebugilframe-getip-method.md) pour obtenir la valeur du pointeur d’instruction.</span><span class="sxs-lookup"><span data-stu-id="ab2d0-116">You can use the [ICorDebugILFrame::GetIP](icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab2d0-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ab2d0-117">Requirements</span></span>  
 <span data-ttu-id="ab2d0-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab2d0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab2d0-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab2d0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab2d0-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab2d0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab2d0-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab2d0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab2d0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab2d0-122">See also</span></span>

- [<span data-ttu-id="ab2d0-123">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="ab2d0-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
