---
title: CorpubPublish (coclasse)
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: c73eab14bf6f9f9599bed79f4c5f85ed035c0518
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722347"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="45187-102">CorpubPublish (coclasse)</span><span class="sxs-lookup"><span data-stu-id="45187-102">CorpubPublish Coclass</span></span>

<span data-ttu-id="45187-103">Fournit les interfaces pour la publication d'informations sur les domaines d'application et les processus.</span><span class="sxs-lookup"><span data-stu-id="45187-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45187-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="45187-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="45187-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="45187-105">Interfaces</span></span>  
  
|<span data-ttu-id="45187-106">Interface</span><span class="sxs-lookup"><span data-stu-id="45187-106">Interface</span></span>|<span data-ttu-id="45187-107">Description</span><span class="sxs-lookup"><span data-stu-id="45187-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="45187-108">ICorPublish, interface</span><span class="sxs-lookup"><span data-stu-id="45187-108">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="45187-109">Fournit des méthodes pour la publication d’informations sur les processus et les domaines d’application dans ces processus.</span><span class="sxs-lookup"><span data-stu-id="45187-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="45187-110">ICorPublishAppDomain, interface</span><span class="sxs-lookup"><span data-stu-id="45187-110">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="45187-111">Représente et fournit des informations sur, un domaine d’application dans un processus.</span><span class="sxs-lookup"><span data-stu-id="45187-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="45187-112">ICorPublishAppDomainEnum, interface</span><span class="sxs-lookup"><span data-stu-id="45187-112">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="45187-113">Fournit des méthodes qui parcourent une collection de domaines d’application qui existent actuellement dans un processus.</span><span class="sxs-lookup"><span data-stu-id="45187-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="45187-114">ICorPublishProcess, interface</span><span class="sxs-lookup"><span data-stu-id="45187-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="45187-115">Représente un processus qui s’exécute sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="45187-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="45187-116">ICorPublishProcessEnum, interface</span><span class="sxs-lookup"><span data-stu-id="45187-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="45187-117">Fournit des méthodes qui parcourent une collection de processus en cours d’exécution sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="45187-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45187-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="45187-118">Remarks</span></span>  

 <span data-ttu-id="45187-119">Un scénario de publication classique implique un développeur qui souhaite déboguer du code managé qui s’exécute sur un ordinateur au sein d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="45187-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="45187-120">L’environnement d’hébergement peut exécuter plusieurs domaines d’application au sein d’un processus.</span><span class="sxs-lookup"><span data-stu-id="45187-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="45187-121">Le développeur souhaite utiliser une interface graphique utilisateur ou d’autres moyens pour répertorier tous les processus en cours d’exécution sur l’ordinateur et choisir un processus spécifique.</span><span class="sxs-lookup"><span data-stu-id="45187-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="45187-122">La liste doit inclure tous les domaines d’application dans les processus qui exécutent du code managé.</span><span class="sxs-lookup"><span data-stu-id="45187-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="45187-123">Le développeur peut ensuite identifier le domaine d’application spécifique et attacher un débogueur à ce domaine.</span><span class="sxs-lookup"><span data-stu-id="45187-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45187-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="45187-124">Requirements</span></span>  

 <span data-ttu-id="45187-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45187-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45187-126">**En-tête :** CorPub. idl</span><span class="sxs-lookup"><span data-stu-id="45187-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="45187-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45187-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45187-128">**Versions de .NET Framework :**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45187-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45187-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45187-129">See also</span></span>

- [<span data-ttu-id="45187-130">Débogage</span><span class="sxs-lookup"><span data-stu-id="45187-130">Debugging</span></span>](index.md)
