---
title: ICorDebugAppDomain::EnumerateSteppers, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
ms.openlocfilehash: a46d1b4ebf84514a77e62a4108f6aa34cd2dd94e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895264"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="6fbf0-102">ICorDebugAppDomain::EnumerateSteppers, méthode</span><span class="sxs-lookup"><span data-stu-id="6fbf0-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="6fbf0-103">Obtient un énumérateur pour toutes les exécutions pas à pas actives dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6fbf0-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fbf0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fbf0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fbf0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6fbf0-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="6fbf0-106">à Pointeur vers l’adresse d’un objet ICorDebugStepperEnum qui est l’énumérateur pour toutes les exécutions pas à pas actives dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="6fbf0-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fbf0-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6fbf0-107">Requirements</span></span>  
 <span data-ttu-id="6fbf0-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fbf0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fbf0-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fbf0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fbf0-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fbf0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fbf0-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fbf0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
