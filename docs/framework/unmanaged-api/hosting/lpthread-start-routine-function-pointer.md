---
title: LPTHREAD_START_ROUTINE (pointeur fonction)
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 577526536e07172070a1e8a65e73fd15646681fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768351"
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="219cb-102">LPTHREAD_START_ROUTINE (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="219cb-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="219cb-103">Pointe vers une fonction qui avertit l’hôte qu’un thread a commencé à exécuter.</span><span class="sxs-lookup"><span data-stu-id="219cb-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="219cb-104">Ce pointeur de fonction a été déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="219cb-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="219cb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="219cb-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="219cb-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="219cb-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="219cb-107">[in] Pointeur vers le code qui a démarré l’exécution.</span><span class="sxs-lookup"><span data-stu-id="219cb-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="219cb-108">Notes</span><span class="sxs-lookup"><span data-stu-id="219cb-108">Remarks</span></span>  
 <span data-ttu-id="219cb-109">La fonction à laquelle `LPTHREAD_START_ROUTINE` points est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="219cb-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="219cb-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="219cb-110">Requirements</span></span>  
 <span data-ttu-id="219cb-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="219cb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="219cb-112">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="219cb-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="219cb-113">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="219cb-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="219cb-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="219cb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="219cb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="219cb-115">See also</span></span>

- [<span data-ttu-id="219cb-116">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="219cb-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
