---
title: ICorDebugProcess3::SetEnableCustomNotification, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
ms.openlocfilehash: ec60274648315c4fa38f3832d8d39c1a269956b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129705"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="a2f55-102">ICorDebugProcess3::SetEnableCustomNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="a2f55-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="a2f55-103">Active et désactive les notifications personnalisées du débogueur du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="a2f55-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2f55-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2f55-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a2f55-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="a2f55-106">dans Type qui spécifie les notifications personnalisées du débogueur.</span><span class="sxs-lookup"><span data-stu-id="a2f55-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="a2f55-107">[in] `true` pour activer les notifications personnalisées du débogueur ; `false` de désactiver les notifications.</span><span class="sxs-lookup"><span data-stu-id="a2f55-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="a2f55-108">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="a2f55-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2f55-109">Notes</span><span class="sxs-lookup"><span data-stu-id="a2f55-109">Remarks</span></span>  
 <span data-ttu-id="a2f55-110">Lorsque `fEnable` a la valeur `true`, les appels à la méthode <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> déclenchent un rappel [ICorDebugManagedCallback3 :: CustomNotification,](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a2f55-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="a2f55-111">Les notifications sont désactivées par défaut ; par conséquent, le débogueur doit spécifier les types de notification qu’il connaît et souhaite gérer.</span><span class="sxs-lookup"><span data-stu-id="a2f55-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="a2f55-112">Étant donné que la classe [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) est limitée par le domaine d’application, le débogueur doit appeler `SetEnableCustomNotification` pour chaque domaine d’application dans le processus s’il souhaite recevoir la notification dans tout le processus.</span><span class="sxs-lookup"><span data-stu-id="a2f55-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="a2f55-113">À partir du .NET Framework 4, la seule notification prise en charge est une notification de dépendance inter-threads.</span><span class="sxs-lookup"><span data-stu-id="a2f55-113">Starting with the .NET Framework 4, the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2f55-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="a2f55-114">Requirements</span></span>  
 <span data-ttu-id="a2f55-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2f55-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2f55-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2f55-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2f55-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2f55-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2f55-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2f55-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2f55-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2f55-119">See also</span></span>

- [<span data-ttu-id="a2f55-120">ICorDebugProcess3, interface</span><span class="sxs-lookup"><span data-stu-id="a2f55-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [<span data-ttu-id="a2f55-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a2f55-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a2f55-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="a2f55-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
