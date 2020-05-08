---
title: ICorDebugChain::GetStackRange, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: 40ecc183c32500ad9e88ceb1bfc0528d717430e8
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894456"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="6e2de-102">ICorDebugChain::GetStackRange, méthode</span><span class="sxs-lookup"><span data-stu-id="6e2de-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="6e2de-103">Obtient la plage d’adresses du segment de pile pour cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="6e2de-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e2de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e2de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e2de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6e2de-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="6e2de-106">à Pointeur vers une `CORDB_ADDRESS` valeur qui est l’adresse de départ du segment de pile.</span><span class="sxs-lookup"><span data-stu-id="6e2de-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="6e2de-107">à Pointeur vers une `CORDB_ADDRESS` valeur qui est l’adresse de fin du segment de pile.</span><span class="sxs-lookup"><span data-stu-id="6e2de-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e2de-108">Notes </span><span class="sxs-lookup"><span data-stu-id="6e2de-108">Remarks</span></span>  
 <span data-ttu-id="6e2de-109">La plage numérique est significative uniquement pour la comparaison des emplacements de frame de pile.</span><span class="sxs-lookup"><span data-stu-id="6e2de-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="6e2de-110">Vous ne pouvez pas faire d’hypothèses sur ce qui est réellement stocké sur la pile.</span><span class="sxs-lookup"><span data-stu-id="6e2de-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e2de-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6e2de-111">Requirements</span></span>  
 <span data-ttu-id="6e2de-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e2de-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e2de-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e2de-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e2de-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e2de-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e2de-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e2de-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
