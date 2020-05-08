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
ms.openlocfilehash: 3df35d52a4e5209b282ccef653b065bdcf1f8fe4
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976536"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="e73f9-102">ICorDebugDataTarget::GetPlatform, méthode</span><span class="sxs-lookup"><span data-stu-id="e73f9-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="e73f9-103">Fournit des informations sur la plateforme, y compris l’architecture du processeur et le système d’exploitation, sur lesquelles le processus cible est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e73f9-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e73f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e73f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e73f9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e73f9-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="e73f9-106">à Pointeur vers une énumération [CorDebugPlatformEnum](cordebugplatform-enumeration.md) qui décrit la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="e73f9-106">[out] A pointer to a [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e73f9-107">Notes </span><span class="sxs-lookup"><span data-stu-id="e73f9-107">Remarks</span></span>  
 <span data-ttu-id="e73f9-108">La `CorDebugPlatformEnum` valeur de retour de l’énumération est utilisée par l’interface [ICorDebug](icordebug-interface.md) pour déterminer les détails du processus cible, tels que sa taille de pointeur, sa disposition d’espace d’adressage, son ensemble de registres, son format d’instruction, sa disposition de contexte et ses conventions d’appel.</span><span class="sxs-lookup"><span data-stu-id="e73f9-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="e73f9-109">La `pTargetPlatform` valeur peut faire référence à une plateforme qui est émulée pour la cible au lieu de spécifier le matériel réel en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="e73f9-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="e73f9-110">Par exemple, un processus qui s’exécute dans l’environnement Windows on Windows (WOW) sur une édition 64 bits du système d’exploitation Windows doit utiliser la `CORDB_PLATFORM_WINDOWS_X86` valeur de l’énumération [CorDebugPlatformEnum](cordebugplatform-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="e73f9-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="e73f9-111">Cette méthode doit être correctement exécutée.</span><span class="sxs-lookup"><span data-stu-id="e73f9-111">This method must succeed.</span></span> <span data-ttu-id="e73f9-112">En cas d’échec, la plateforme cible est inutilisable.</span><span class="sxs-lookup"><span data-stu-id="e73f9-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="e73f9-113">La méthode peut échouer pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="e73f9-113">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="e73f9-114">La plateforme émulée pour la cible est inutilisable.</span><span class="sxs-lookup"><span data-stu-id="e73f9-114">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="e73f9-115">Le matériel réel sur la plateforme cible est inutilisable.</span><span class="sxs-lookup"><span data-stu-id="e73f9-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e73f9-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e73f9-116">Requirements</span></span>  
 <span data-ttu-id="e73f9-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e73f9-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e73f9-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e73f9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e73f9-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e73f9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e73f9-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e73f9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e73f9-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e73f9-121">See also</span></span>

- [<span data-ttu-id="e73f9-122">ICorDebugDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="e73f9-122">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="e73f9-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e73f9-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e73f9-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="e73f9-124">Debugging</span></span>](index.md)
