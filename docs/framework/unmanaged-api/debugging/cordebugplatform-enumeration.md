---
title: CorDebugPlatform, énumération
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
ms.openlocfilehash: 5435f78b28975a5426fcb2fce94904efc1051c5b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696399"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="909b3-102">CorDebugPlatform, énumération</span><span class="sxs-lookup"><span data-stu-id="909b3-102">CorDebugPlatform Enumeration</span></span>

<span data-ttu-id="909b3-103">Fournit les valeurs de plateforme cible utilisées par la méthode [ICorDebugDataTarget :: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="909b3-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="909b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="909b3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a><span data-ttu-id="909b3-105">Membres</span><span class="sxs-lookup"><span data-stu-id="909b3-105">Members</span></span>  
  
|<span data-ttu-id="909b3-106">Membre</span><span class="sxs-lookup"><span data-stu-id="909b3-106">Member</span></span>|<span data-ttu-id="909b3-107">Description</span><span class="sxs-lookup"><span data-stu-id="909b3-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="909b3-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="909b3-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="909b3-109">La plateforme cible est Windows s'exécutant sur du matériel Intel x86.</span><span class="sxs-lookup"><span data-stu-id="909b3-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="909b3-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="909b3-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="909b3-111">La plateforme cible est Windows 64 bits s'exécutant sur du matériel AMD64 ou Intel EM64T.</span><span class="sxs-lookup"><span data-stu-id="909b3-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="909b3-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="909b3-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="909b3-113">La plateforme cible est Windows 32 bits s'exécutant sur du matériel IA-64.</span><span class="sxs-lookup"><span data-stu-id="909b3-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="909b3-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="909b3-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="909b3-115">La plateforme cible est le système d’exploitation Macintosh s’exécutant sur un matériel PowerPC.</span><span class="sxs-lookup"><span data-stu-id="909b3-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="909b3-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="909b3-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="909b3-117">La plateforme cible est le système d’exploitation Macintosh s’exécutant sur du matériel Intel x86.</span><span class="sxs-lookup"><span data-stu-id="909b3-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="909b3-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="909b3-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="909b3-119">La plateforme cible est le système d’exploitation Macintosh s’exécutant sur le matériel ARM Windows.</span><span class="sxs-lookup"><span data-stu-id="909b3-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="909b3-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="909b3-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="909b3-121">La plateforme cible est le système d’exploitation Macintosh s’exécutant sur du matériel AMD64.</span><span class="sxs-lookup"><span data-stu-id="909b3-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="909b3-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="909b3-122">Requirements</span></span>  

 <span data-ttu-id="909b3-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="909b3-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="909b3-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="909b3-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="909b3-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="909b3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="909b3-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="909b3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="909b3-127">Les membres `CORDB_PLATFORM_WINDOWS_ARM` et `CORDB_PLATFORM_MAC_AMD64` sont disponibles dans .NET Framework 4.5.2 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="909b3-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="909b3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="909b3-128">See also</span></span>

- [<span data-ttu-id="909b3-129">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="909b3-129">Debugging Enumerations</span></span>](debugging-enumerations.md)
