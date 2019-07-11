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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6db1990df2ed6b29d548c147ed40b5bc98254d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745692"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="2d760-102">ICorDebugChain::GetStackRange, méthode</span><span class="sxs-lookup"><span data-stu-id="2d760-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="2d760-103">Obtient la plage d’adresses du segment de pile pour cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="2d760-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d760-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d760-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d760-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d760-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="2d760-106">[out] Un pointeur vers un `CORDB_ADDRESS` valeur qui est l’adresse de départ du segment de pile.</span><span class="sxs-lookup"><span data-stu-id="2d760-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="2d760-107">[out] Un pointeur vers un `CORDB_ADDRESS` valeur qui est l’adresse de fin du segment de pile.</span><span class="sxs-lookup"><span data-stu-id="2d760-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d760-108">Notes</span><span class="sxs-lookup"><span data-stu-id="2d760-108">Remarks</span></span>  
 <span data-ttu-id="2d760-109">La plage numérique est significative uniquement pour la comparaison des emplacements de frame de pile.</span><span class="sxs-lookup"><span data-stu-id="2d760-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="2d760-110">Vous ne pouvez pas faire d’hypothèses concernant ce qui est réellement stocké sur la pile.</span><span class="sxs-lookup"><span data-stu-id="2d760-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d760-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2d760-111">Requirements</span></span>  
 <span data-ttu-id="2d760-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d760-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d760-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d760-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d760-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d760-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d760-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d760-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
