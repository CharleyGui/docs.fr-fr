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
ms.openlocfilehash: 6fd7a19d9fc77b43bbceb1b5e5399a455429e700
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616149"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="ca447-102">FExecuteInAppDomainCallback (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="ca447-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="ca447-103">Pointe vers une fonction qui est appelée par le common language runtime (CLR) pour exécuter du code managé.</span><span class="sxs-lookup"><span data-stu-id="ca447-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="ca447-104">Ce pointeur de fonction est déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ca447-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca447-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca447-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca447-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca447-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="ca447-107">dans Pointeur vers la mémoire allouée par l’appelant opaque qui contient le code managé à exécuter.</span><span class="sxs-lookup"><span data-stu-id="ca447-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="ca447-108">L’allocation et la durée de vie de cette mémoire sont contrôlées par l’appelant (autrement dit, le CLR).</span><span class="sxs-lookup"><span data-stu-id="ca447-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="ca447-109">Il ne s’agit pas de la mémoire du tas managé CLR.</span><span class="sxs-lookup"><span data-stu-id="ca447-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca447-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="ca447-110">Requirements</span></span>  
 <span data-ttu-id="ca447-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca447-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca447-112">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ca447-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca447-113">**Bibliothèque :** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="ca447-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="ca447-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca447-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca447-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca447-115">See also</span></span>

- [<span data-ttu-id="ca447-116">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="ca447-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
