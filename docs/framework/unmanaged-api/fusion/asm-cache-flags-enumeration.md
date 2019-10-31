---
title: ASM_CACHE_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
ms.openlocfilehash: 85ac976daec8fd76ee21012a30611235609f4b34
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109493"
---
# <a name="asm_cache_flags-enumeration"></a><span data-ttu-id="55803-102">ASM_CACHE_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="55803-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="55803-103">Indique la source d’un assembly qui est représenté par [IAssemblyCacheItem](iassemblycacheitem-interface.md) dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="55803-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55803-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55803-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="55803-105">Membres</span><span class="sxs-lookup"><span data-stu-id="55803-105">Members</span></span>  
  
|<span data-ttu-id="55803-106">Membre</span><span class="sxs-lookup"><span data-stu-id="55803-106">Member</span></span>|<span data-ttu-id="55803-107">Description</span><span class="sxs-lookup"><span data-stu-id="55803-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="55803-108">Énumère le cache des assemblys précompilés à l’aide de Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="55803-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="55803-109">Énumère les Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="55803-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="55803-110">Énumère les assemblys qui ont été téléchargés à la demande ou qui ont été copiés par des clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="55803-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="55803-111">Indique que la fonction [GetCachePath](getcachepath-function.md) doit retourner le chemin d’accès au global assembly cache pour la Common Language Runtime (CLR) version 2,0.</span><span class="sxs-lookup"><span data-stu-id="55803-111">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="55803-112">Significatif uniquement dans le contexte d’un appel à [GetCachePath](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="55803-112">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="55803-113">Indique que la fonction [GetCachePath](getcachepath-function.md) doit retourner le chemin d’accès au global assembly cache de CLR version 4.</span><span class="sxs-lookup"><span data-stu-id="55803-113">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="55803-114">Significatif uniquement dans le contexte d’un appel à [GetCachePath](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="55803-114">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55803-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="55803-115">Requirements</span></span>  
 <span data-ttu-id="55803-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55803-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55803-117">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="55803-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="55803-118">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="55803-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55803-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55803-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55803-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55803-120">See also</span></span>

- [<span data-ttu-id="55803-121">GetCachePath, fonction</span><span class="sxs-lookup"><span data-stu-id="55803-121">GetCachePath Function</span></span>](getcachepath-function.md)
- [<span data-ttu-id="55803-122">IAssemblyCacheItem, interface</span><span class="sxs-lookup"><span data-stu-id="55803-122">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
- [<span data-ttu-id="55803-123">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="55803-123">Fusion Enumerations</span></span>](fusion-enumerations.md)
