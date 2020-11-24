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
ms.openlocfilehash: 76b231f00651186518d3bccfafa5780f258c4f75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688183"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="fc4b3-102">ICorDebugThread::EnumerateChains, méthode</span><span class="sxs-lookup"><span data-stu-id="fc4b3-102">ICorDebugThread::EnumerateChains Method</span></span>

<span data-ttu-id="fc4b3-103">Obtient un pointeur d’interface vers un énumérateur ICorDebugChainEnum qui contient toutes les chaînes de pile de cet objet ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="fc4b3-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc4b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc4b3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc4b3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc4b3-105">Parameters</span></span>  

 `ppChains`  
 <span data-ttu-id="fc4b3-106">à Pointeur vers l’adresse d’un `ICorDebugChainEnum` objet qui autorise l’énumération de toutes les chaînes de pile dans ce thread, en commençant à la chaîne active (autrement dit, la plus récente).</span><span class="sxs-lookup"><span data-stu-id="fc4b3-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc4b3-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="fc4b3-107">Remarks</span></span>  

 <span data-ttu-id="fc4b3-108">La chaîne de pile représente la pile d’appels physique du thread.</span><span class="sxs-lookup"><span data-stu-id="fc4b3-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="fc4b3-109">Les circonstances suivantes créent une limite de chaîne de pile :</span><span class="sxs-lookup"><span data-stu-id="fc4b3-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="fc4b3-110">Transition managée vers non managée ou non managée vers managée.</span><span class="sxs-lookup"><span data-stu-id="fc4b3-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="fc4b3-111">Commutateur de contexte.</span><span class="sxs-lookup"><span data-stu-id="fc4b3-111">A context switch.</span></span>  
  
- <span data-ttu-id="fc4b3-112">Détournement d’un thread utilisateur par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="fc4b3-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="fc4b3-113">Dans le cas simple d’un thread qui exécute du code purement managé dans un contexte unique, une correspondance un-à-un existe entre les threads et les chaînes de pile.</span><span class="sxs-lookup"><span data-stu-id="fc4b3-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="fc4b3-114">Un débogueur peut réorganiser les piles des appels physiques de tous les threads en piles d’appels logiques.</span><span class="sxs-lookup"><span data-stu-id="fc4b3-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="fc4b3-115">Cela implique de trier toutes les chaînes des threads en fonction de leurs relations appelant/appelé, puis de les regrouper.</span><span class="sxs-lookup"><span data-stu-id="fc4b3-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc4b3-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fc4b3-116">Requirements</span></span>  

 <span data-ttu-id="fc4b3-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc4b3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc4b3-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc4b3-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc4b3-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc4b3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc4b3-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc4b3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
