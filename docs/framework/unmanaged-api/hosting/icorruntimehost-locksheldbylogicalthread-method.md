---
title: ICorRuntimeHost::LocksHeldByLogicalThread, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
ms.openlocfilehash: 16f34d91861f9fcae51691ab13549bdf1ef333a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671497"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="eb43c-102">ICorRuntimeHost::LocksHeldByLogicalThread, méthode</span><span class="sxs-lookup"><span data-stu-id="eb43c-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>

<span data-ttu-id="eb43c-103">Récupère le nombre de verrous que le thread actuel contient.</span><span class="sxs-lookup"><span data-stu-id="eb43c-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="eb43c-104">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="eb43c-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb43c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb43c-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb43c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eb43c-106">Parameters</span></span>  

 `pCount`  
 <span data-ttu-id="eb43c-107">à Pointeur vers le nombre de verrous que le thread actuel contient.</span><span class="sxs-lookup"><span data-stu-id="eb43c-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb43c-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eb43c-108">Requirements</span></span>  

 <span data-ttu-id="eb43c-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb43c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb43c-110">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eb43c-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb43c-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb43c-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb43c-112">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="eb43c-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb43c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb43c-113">See also</span></span>

- [<span data-ttu-id="eb43c-114">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="eb43c-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
