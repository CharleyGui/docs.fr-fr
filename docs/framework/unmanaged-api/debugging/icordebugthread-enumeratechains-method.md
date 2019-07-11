---
title: ICorDebugThread::EnumerateChains, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f0ed843f72d3f1e1575da15776a94a9097fd02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771101"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="e64c4-102">ICorDebugThread::EnumerateChains, méthode</span><span class="sxs-lookup"><span data-stu-id="e64c4-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="e64c4-103">Obtient un pointeur d’interface vers un énumérateur ICorDebugChainEnum qui contient toutes les chaînes de pile dans cet objet ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="e64c4-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e64c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e64c4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e64c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e64c4-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="e64c4-106">[out] Un pointeur vers l’adresse d’un `ICorDebugChainEnum` objet qui permet l’énumération de la pile de toutes les chaînes dans ce thread, en commençant par la chaîne active (autrement dit, la plus récente).</span><span class="sxs-lookup"><span data-stu-id="e64c4-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e64c4-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e64c4-107">Remarks</span></span>  
 <span data-ttu-id="e64c4-108">La chaîne de pile représente la pile des appels physique pour le thread.</span><span class="sxs-lookup"><span data-stu-id="e64c4-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="e64c4-109">Les circonstances suivantes créer une limite de chaîne de pile :</span><span class="sxs-lookup"><span data-stu-id="e64c4-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="e64c4-110">Une transition managé à managé ou non managé à managé.</span><span class="sxs-lookup"><span data-stu-id="e64c4-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="e64c4-111">Un changement de contexte.</span><span class="sxs-lookup"><span data-stu-id="e64c4-111">A context switch.</span></span>  
  
- <span data-ttu-id="e64c4-112">Un blocage d’un thread de l’utilisateur du débogueur.</span><span class="sxs-lookup"><span data-stu-id="e64c4-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="e64c4-113">Dans le cas simple pour un thread qui est en cours d’exécution du code purement managé dans un contexte unique, une correspondance exacte existe entre les threads et les chaînes de pile.</span><span class="sxs-lookup"><span data-stu-id="e64c4-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="e64c4-114">Un débogueur peut être amené à réorganiser les piles des appels physique de tous les threads dans les piles des appels logiques.</span><span class="sxs-lookup"><span data-stu-id="e64c4-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="e64c4-115">Il serait nécessaire de trier des chaînes de tous les threads en fonction de leurs relations appelant/appelé et le regroupement.</span><span class="sxs-lookup"><span data-stu-id="e64c4-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e64c4-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e64c4-116">Requirements</span></span>  
 <span data-ttu-id="e64c4-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e64c4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e64c4-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e64c4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e64c4-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e64c4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e64c4-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e64c4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
