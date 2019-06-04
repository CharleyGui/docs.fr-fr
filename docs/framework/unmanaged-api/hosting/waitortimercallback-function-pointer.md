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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f938c7dcf08654eef1e2403426eb5c54d6d2a6b3
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490120"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="865be-102">WAITORTIMERCALLBACK (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="865be-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="865be-103">Pointe vers une fonction qui avertit l’hôte qu’un handle d’attente (<xref:System.Threading.WaitHandle>) a été signalé ou a expiré.</span><span class="sxs-lookup"><span data-stu-id="865be-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="865be-104">Ce pointeur de fonction a été déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="865be-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865be-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="865be-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="865be-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="865be-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="865be-107">[in] Pointeur vers un objet qui contient les informations définies par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="865be-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="865be-108">[in] `true` si le handle d’attente a expiré, ou `false` si elle a été signalée.</span><span class="sxs-lookup"><span data-stu-id="865be-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="865be-109">Notes</span><span class="sxs-lookup"><span data-stu-id="865be-109">Remarks</span></span>  
 <span data-ttu-id="865be-110">La fonction à laquelle `WAITORTIMERCALLBACK` points est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="865be-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="865be-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="865be-111">Requirements</span></span>  
 <span data-ttu-id="865be-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="865be-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="865be-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="865be-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="865be-114">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="865be-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="865be-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="865be-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865be-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="865be-116">See also</span></span>

- [<span data-ttu-id="865be-117">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="865be-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
