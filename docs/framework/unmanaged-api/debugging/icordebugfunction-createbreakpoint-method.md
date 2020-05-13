---
title: ICorDebugFunction::CreateBreakpoint, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type:
- apiref
ms.openlocfilehash: 5d7e83c6aa494f2363698d0220bbfe724b54e612
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209433"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="652db-102">ICorDebugFunction::CreateBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="652db-102">ICorDebugFunction::CreateBreakpoint Method</span></span>
<span data-ttu-id="652db-103">Crée un point d’arrêt au début de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="652db-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="652db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="652db-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="652db-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="652db-105">Parameters</span></span>  
 `ppBreakpoint`  
 <span data-ttu-id="652db-106">à Pointeur vers l’adresse d’un objet ICorDebugFunctionBreakpoint qui représente le nouveau point d’arrêt pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="652db-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="652db-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="652db-107">Requirements</span></span>  
 <span data-ttu-id="652db-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="652db-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="652db-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="652db-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="652db-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="652db-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="652db-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="652db-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
