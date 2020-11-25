---
title: WAITORTIMERCALLBACK (pointeur fonction)
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
ms.openlocfilehash: 74256f35804ff59f04952a1ac20ac7866e8f5683
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732812"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="2284c-102">WAITORTIMERCALLBACK (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="2284c-102">WAITORTIMERCALLBACK Function Pointer</span></span>

<span data-ttu-id="2284c-103">Pointe vers une fonction qui avertit l’hôte qu’un handle d’attente ( <xref:System.Threading.WaitHandle> ) a été signalé ou a expiré.</span><span class="sxs-lookup"><span data-stu-id="2284c-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="2284c-104">Ce pointeur de fonction est déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2284c-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2284c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2284c-105">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2284c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2284c-106">Parameters</span></span>  

 `lpParameter`  
 <span data-ttu-id="2284c-107">dans Pointeur vers un objet qui contient les informations définies par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="2284c-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="2284c-108">[in] `true` Si le handle d’attente a expiré ou `false` s’il a été signalé.</span><span class="sxs-lookup"><span data-stu-id="2284c-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2284c-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="2284c-109">Remarks</span></span>  

 <span data-ttu-id="2284c-110">La fonction vers laquelle `WAITORTIMERCALLBACK` pointe est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="2284c-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2284c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2284c-111">Requirements</span></span>  

 <span data-ttu-id="2284c-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2284c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2284c-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2284c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2284c-114">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="2284c-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="2284c-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2284c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2284c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2284c-116">See also</span></span>

- [<span data-ttu-id="2284c-117">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="2284c-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
