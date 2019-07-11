---
title: FExecuteInAppDomainCallback (pointeur fonction)
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8edd2a42ed1b826e1b6ea09e92165bc9fa967a8b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760251"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="4cdf6-102">FExecuteInAppDomainCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="4cdf6-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="4cdf6-103">Pointe vers une fonction qui est appelée par le common language runtime (CLR) pour exécuter le code managé.</span><span class="sxs-lookup"><span data-stu-id="4cdf6-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="4cdf6-104">Ce pointeur de fonction a été déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4cdf6-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cdf6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cdf6-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cdf6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4cdf6-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="4cdf6-107">[in] Un pointeur vers la mémoire allouée par l’appelant opaque qui contient le code managé doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="4cdf6-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="4cdf6-108">L’allocation et la durée de vie de cette mémoire sont contrôlées par l’appelant (autrement dit, le CLR).</span><span class="sxs-lookup"><span data-stu-id="4cdf6-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="4cdf6-109">Cela n’est pas mémoire de tas managé CLR.</span><span class="sxs-lookup"><span data-stu-id="4cdf6-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cdf6-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4cdf6-110">Requirements</span></span>  
 <span data-ttu-id="4cdf6-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cdf6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cdf6-112">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4cdf6-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cdf6-113">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="4cdf6-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="4cdf6-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cdf6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cdf6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cdf6-115">See also</span></span>

- [<span data-ttu-id="4cdf6-116">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="4cdf6-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
