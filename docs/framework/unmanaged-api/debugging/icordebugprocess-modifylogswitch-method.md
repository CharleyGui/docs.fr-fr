---
title: ICorDebugProcess::ModifyLogSwitch, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
ms.openlocfilehash: 3ac1b3606131f534195df9b6b59bf72b1bff27fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724531"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="0e2ae-102">ICorDebugProcess::ModifyLogSwitch, méthode</span><span class="sxs-lookup"><span data-stu-id="0e2ae-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>

<span data-ttu-id="0e2ae-103">Définit le niveau de gravité du commutateur de journalisation spécifié.</span><span class="sxs-lookup"><span data-stu-id="0e2ae-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e2ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e2ae-104">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e2ae-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e2ae-105">Parameters</span></span>  

 `pLogSwitchName`  
 <span data-ttu-id="0e2ae-106">dans Pointeur vers une chaîne qui spécifie le nom du commutateur de journal.</span><span class="sxs-lookup"><span data-stu-id="0e2ae-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="0e2ae-107">dans Niveau de gravité à définir pour le commutateur de journalisation spécifié.</span><span class="sxs-lookup"><span data-stu-id="0e2ae-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e2ae-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="0e2ae-108">Remarks</span></span>  

 <span data-ttu-id="0e2ae-109">Cette méthode est valide uniquement après que le rappel [ICorDebugManagedCallback :: CreateProcess](icordebugmanagedcallback-createprocess-method.md) s’est produit.</span><span class="sxs-lookup"><span data-stu-id="0e2ae-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e2ae-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0e2ae-110">Requirements</span></span>  

 <span data-ttu-id="0e2ae-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e2ae-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e2ae-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e2ae-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e2ae-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e2ae-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e2ae-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e2ae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
