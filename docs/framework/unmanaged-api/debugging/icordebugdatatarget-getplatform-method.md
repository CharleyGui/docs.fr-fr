---
title: ICorDebugDataTarget::GetPlatform, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: 5715f0634346dd0c6591cfe5687690aa0fba95f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125317"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="7ab46-102">ICorDebugDataTarget::GetPlatform, méthode</span><span class="sxs-lookup"><span data-stu-id="7ab46-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="7ab46-103">Fournit des informations sur la plateforme, y compris l’architecture du processeur et le système d’exploitation, sur lesquelles le processus cible est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7ab46-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ab46-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ab46-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ab46-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="7ab46-106">à Pointeur vers une énumération [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) qui décrit la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="7ab46-106">[out] A pointer to a [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ab46-107">Notes</span><span class="sxs-lookup"><span data-stu-id="7ab46-107">Remarks</span></span>  
 <span data-ttu-id="7ab46-108">La `CorDebugPlatformEnum` valeur de retour de l’énumération est utilisée par l’interface [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) pour déterminer les détails du processus cible, comme sa taille de pointeur, sa disposition d’espace d’adressage, son ensemble de registres, son format d’instruction, sa disposition de contexte et ses conventions d’appel.</span><span class="sxs-lookup"><span data-stu-id="7ab46-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="7ab46-109">La valeur `pTargetPlatform` peut faire référence à une plateforme qui est émulée pour la cible au lieu de spécifier le matériel réel en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="7ab46-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="7ab46-110">Par exemple, un processus qui s’exécute dans l’environnement WOW (Windows on Windows) sur une édition 64 bits du système d’exploitation Windows doit utiliser la valeur `CORDB_PLATFORM_WINDOWS_X86` de l’énumération [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="7ab46-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="7ab46-111">Cette méthode doit être correctement exécutée.</span><span class="sxs-lookup"><span data-stu-id="7ab46-111">This method must succeed.</span></span> <span data-ttu-id="7ab46-112">En cas d’échec, la plateforme cible est inutilisable.</span><span class="sxs-lookup"><span data-stu-id="7ab46-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="7ab46-113">La méthode peut échouer pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="7ab46-113">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="7ab46-114">La plateforme émulée pour la cible est inutilisable.</span><span class="sxs-lookup"><span data-stu-id="7ab46-114">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="7ab46-115">Le matériel réel sur la plateforme cible est inutilisable.</span><span class="sxs-lookup"><span data-stu-id="7ab46-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ab46-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="7ab46-116">Requirements</span></span>  
 <span data-ttu-id="7ab46-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ab46-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ab46-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ab46-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ab46-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ab46-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ab46-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ab46-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab46-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ab46-121">See also</span></span>

- [<span data-ttu-id="7ab46-122">ICorDebugDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="7ab46-122">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="7ab46-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7ab46-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7ab46-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="7ab46-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
