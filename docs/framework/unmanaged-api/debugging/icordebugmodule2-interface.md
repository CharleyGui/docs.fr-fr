---
title: ICorDebugModule2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
ms.openlocfilehash: 2b8e6048dd6b8df71ac3dddcc4397f6d512127c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695879"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="38ae8-102">ICorDebugModule2, interface</span><span class="sxs-lookup"><span data-stu-id="38ae8-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="38ae8-103">Sert d’extension logique à l’interface ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="38ae8-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38ae8-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="38ae8-104">Methods</span></span>  
  
|<span data-ttu-id="38ae8-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="38ae8-105">Method</span></span>|<span data-ttu-id="38ae8-106">Description</span><span class="sxs-lookup"><span data-stu-id="38ae8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38ae8-107">ApplyChanges, méthode</span><span class="sxs-lookup"><span data-stu-id="38ae8-107">ApplyChanges Method</span></span>](icordebugmodule2-applychanges-method.md)|<span data-ttu-id="38ae8-108">Applique les modifications apportées aux métadonnées et les modifications apportées au code MSIL (Microsoft Intermediate Language) au processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="38ae8-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="38ae8-109">GetJITCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="38ae8-109">GetJITCompilerFlags Method</span></span>](icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="38ae8-110">Obtient les indicateurs qui contrôlent la compilation juste-à-temps (JIT, Just-in-Time) pour ce `ICorDebugModule2` .</span><span class="sxs-lookup"><span data-stu-id="38ae8-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="38ae8-111">ResolveAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="38ae8-111">ResolveAssembly Method</span></span>](icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="38ae8-112">Résout l’assembly référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="38ae8-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="38ae8-113">SetJITCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="38ae8-113">SetJITCompilerFlags Method</span></span>](icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="38ae8-114">Définit les indicateurs qui contrôlent la compilation JIT pour ce `ICorDebugModule2` .</span><span class="sxs-lookup"><span data-stu-id="38ae8-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="38ae8-115">SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="38ae8-115">SetJMCStatus Method</span></span>](icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="38ae8-116">Affecte la valeur spécifiée à l’état Uniquement mon code (uniquement mon code) de toutes les méthodes de toutes les classes de ce, à l' `ICorDebugModule2` exception de celles du `pTokens` tableau, qu’il définit sur la valeur opposée.</span><span class="sxs-lookup"><span data-stu-id="38ae8-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38ae8-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="38ae8-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38ae8-118">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="38ae8-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38ae8-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="38ae8-119">Requirements</span></span>  

 <span data-ttu-id="38ae8-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38ae8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38ae8-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38ae8-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38ae8-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38ae8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38ae8-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38ae8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ae8-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38ae8-124">See also</span></span>

- [<span data-ttu-id="38ae8-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="38ae8-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
