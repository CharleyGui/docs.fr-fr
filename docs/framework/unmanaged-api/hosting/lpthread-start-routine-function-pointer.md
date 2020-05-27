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
ms.openlocfilehash: 84cdb42b11ad70f54f21ae36ca2734dc794d06d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008467"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="c4d69-102">LPTHREAD_START_ROUTINE (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="c4d69-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="c4d69-103">Pointe vers une fonction qui avertit l’hôte qu’un thread a commencé à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="c4d69-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="c4d69-104">Ce pointeur de fonction est déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c4d69-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d69-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4d69-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4d69-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4d69-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="c4d69-107">dans Pointeur vers le code dont l’exécution a commencé.</span><span class="sxs-lookup"><span data-stu-id="c4d69-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4d69-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="c4d69-108">Remarks</span></span>  
 <span data-ttu-id="c4d69-109">La fonction vers laquelle `LPTHREAD_START_ROUTINE` pointe est une fonction de rappel et doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="c4d69-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4d69-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c4d69-110">Requirements</span></span>  
 <span data-ttu-id="c4d69-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4d69-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4d69-112">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c4d69-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4d69-113">**Bibliothèque :** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="c4d69-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="c4d69-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4d69-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d69-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4d69-115">See also</span></span>

- [<span data-ttu-id="c4d69-116">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="c4d69-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
