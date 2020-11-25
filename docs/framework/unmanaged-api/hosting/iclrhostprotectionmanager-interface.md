---
title: ICLRHostProtectionManager, interface
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: e8ead998907d55b0bfbf82e5f6f4e7c504f657ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714157"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="19991-102">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="19991-102">ICLRHostProtectionManager Interface</span></span>

<span data-ttu-id="19991-103">Permet à l’hôte de bloquer des classes, des méthodes, des propriétés et des champs managés spécifiques de s’exécuter dans du code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="19991-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19991-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="19991-104">Methods</span></span>  
  
|<span data-ttu-id="19991-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="19991-105">Method</span></span>|<span data-ttu-id="19991-106">Description</span><span class="sxs-lookup"><span data-stu-id="19991-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19991-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="19991-107">SetEagerSerializeGrantSets</span></span>](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="19991-108">Fournit une garantie que certaines conditions de concurrence rares qui peuvent provoquer des erreurs d’common language runtime fatales (CLR) ne se produiront jamais.</span><span class="sxs-lookup"><span data-stu-id="19991-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="19991-109">SetProtectedCategories, méthode</span><span class="sxs-lookup"><span data-stu-id="19991-109">SetProtectedCategories Method</span></span>](iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="19991-110">Spécifie les catégories de types et de membres managés dont l’exécution doit être bloquée dans du code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="19991-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19991-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="19991-111">Requirements</span></span>  

 <span data-ttu-id="19991-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19991-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19991-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="19991-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19991-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19991-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19991-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19991-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19991-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19991-116">See also</span></span>

- [<span data-ttu-id="19991-117">EApiCategories, énumération</span><span class="sxs-lookup"><span data-stu-id="19991-117">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="19991-118">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="19991-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
