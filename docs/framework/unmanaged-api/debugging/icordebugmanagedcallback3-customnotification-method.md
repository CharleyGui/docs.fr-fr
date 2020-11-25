---
title: ICorDebugManagedCallback3::CustomNotification, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
ms.openlocfilehash: f30c9b6746d0e1594994870a96e94eb8105e4c94
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700832"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="b4d86-102">ICorDebugManagedCallback3::CustomNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="b4d86-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>

<span data-ttu-id="b4d86-103">Indique qu’une notification du débogueur personnalisé a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="b4d86-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4d86-104">Syntax</span></span>  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4d86-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b4d86-105">Parameters</span></span>  

 `pThread`  
 <span data-ttu-id="b4d86-106">dans Pointeur vers le thread qui a déclenché la notification.</span><span class="sxs-lookup"><span data-stu-id="b4d86-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="b4d86-107">dans Pointeur vers le domaine d’application qui contient le thread qui a déclenché la notification.</span><span class="sxs-lookup"><span data-stu-id="b4d86-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4d86-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b4d86-108">Return Value</span></span>  

 <span data-ttu-id="b4d86-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b4d86-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b4d86-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4d86-110">HRESULT</span></span>|<span data-ttu-id="b4d86-111">Description</span><span class="sxs-lookup"><span data-stu-id="b4d86-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4d86-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4d86-112">S_OK</span></span>|<span data-ttu-id="b4d86-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="b4d86-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b4d86-114">Exceptions</span><span class="sxs-lookup"><span data-stu-id="b4d86-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4d86-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="b4d86-115">Remarks</span></span>  

 <span data-ttu-id="b4d86-116">Un appel ultérieur à la méthode [ICorDebugThread4 :: GetCurrentCustomDebuggerNotification,](icordebugthread4-getcurrentcustomdebuggernotification-method.md) récupère l’objet thread qui a été passé à la <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="b4d86-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b4d86-117">Le type de l’objet thread doit avoir été préalablement activé en appelant la méthode [ICorDebugProcess3 :: SetEnableCustomNotification,](icordebugprocess3-setenablecustomnotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b4d86-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="b4d86-118">Le débogueur peut lire des paramètres spécifiques au type à partir des champs de l’objet thread et peut stocker les réponses dans des champs.</span><span class="sxs-lookup"><span data-stu-id="b4d86-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="b4d86-119">L’interface [ICorDebug](icordebug-interface.md) n’impose aucune stratégie sur les types de notifications ou leur contenu, et la sémantique des notifications est strictement un contrat entre les débogueurs, les applications et le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4d86-119">The [ICorDebug](icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d86-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b4d86-120">Requirements</span></span>  

 <span data-ttu-id="b4d86-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4d86-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d86-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4d86-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4d86-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4d86-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4d86-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4d86-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d86-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4d86-125">See also</span></span>

- [<span data-ttu-id="b4d86-126">ICorDebugManagedCallback3, interface</span><span class="sxs-lookup"><span data-stu-id="b4d86-126">ICorDebugManagedCallback3 Interface</span></span>](icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="b4d86-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b4d86-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b4d86-128">Débogage</span><span class="sxs-lookup"><span data-stu-id="b4d86-128">Debugging</span></span>](index.md)
