---
title: FLockClrVersionCallback (pointeur fonction)
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
ms.openlocfilehash: d18702a1bb15d2cc6c7b8577b91ed011e9bd0c05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733670"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="265cd-102">FLockClrVersionCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="265cd-102">FLockClrVersionCallback Function Pointer</span></span>

<span data-ttu-id="265cd-103">Pointe vers une fonction que le common language runtime (CLR) appelle pour indiquer que l’initialisation a démarré ou est terminée.</span><span class="sxs-lookup"><span data-stu-id="265cd-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="265cd-104">Ce pointeur de fonction est déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="265cd-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="265cd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="265cd-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="265cd-106">Notes</span><span class="sxs-lookup"><span data-stu-id="265cd-106">Remarks</span></span>  

 <span data-ttu-id="265cd-107">Cette fonction est implémentée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="265cd-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="265cd-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="265cd-108">Requirements</span></span>  

 <span data-ttu-id="265cd-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="265cd-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="265cd-110">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="265cd-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="265cd-111">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="265cd-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="265cd-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="265cd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="265cd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="265cd-113">See also</span></span>

- [<span data-ttu-id="265cd-114">LockClrVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="265cd-114">LockClrVersion Function</span></span>](lockclrversion-function.md)
- [<span data-ttu-id="265cd-115">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="265cd-115">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
