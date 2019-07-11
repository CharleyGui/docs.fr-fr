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
ms.openlocfilehash: 65af5303468904ee40da4d567381782af70bfb38
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776498"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="15c4e-102">WAITORTIMERCALLBACK (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="15c4e-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="15c4e-103">Pointe vers une fonction qui avertit l’hôte qu’un handle d’attente (<xref:System.Threading.WaitHandle>) a été signalé ou a expiré.</span><span class="sxs-lookup"><span data-stu-id="15c4e-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="15c4e-104">Ce pointeur de fonction a été déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="15c4e-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c4e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15c4e-105">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15c4e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="15c4e-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="15c4e-107">[in] Pointeur vers un objet qui contient les informations définies par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="15c4e-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="15c4e-108">[in] `true` si le handle d’attente a expiré, ou `false` si elle a été signalée.</span><span class="sxs-lookup"><span data-stu-id="15c4e-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15c4e-109">Notes</span><span class="sxs-lookup"><span data-stu-id="15c4e-109">Remarks</span></span>  
 <span data-ttu-id="15c4e-110">La fonction à laquelle `WAITORTIMERCALLBACK` points est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="15c4e-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15c4e-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="15c4e-111">Requirements</span></span>  
 <span data-ttu-id="15c4e-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15c4e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15c4e-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="15c4e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15c4e-114">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="15c4e-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="15c4e-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15c4e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c4e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15c4e-116">See also</span></span>

- [<span data-ttu-id="15c4e-117">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="15c4e-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
