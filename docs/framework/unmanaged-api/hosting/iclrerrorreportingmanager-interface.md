---
title: ICLRErrorReportingManager, interface
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
ms.openlocfilehash: d3816c8a3b6204b053505aa888eb28d696f8990b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677839"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="2505a-102">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="2505a-102">ICLRErrorReportingManager Interface</span></span>

<span data-ttu-id="2505a-103">Fournit des méthodes qui permettent à l’hôte de configurer des vidages de pile personnalisés pour le rapport d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="2505a-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2505a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2505a-104">Methods</span></span>  
  
|<span data-ttu-id="2505a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2505a-105">Method</span></span>|<span data-ttu-id="2505a-106">Description</span><span class="sxs-lookup"><span data-stu-id="2505a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2505a-107">BeginCustomDump, méthode</span><span class="sxs-lookup"><span data-stu-id="2505a-107">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="2505a-108">Spécifie la configuration des vidages de pile personnalisés pour le rapport d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="2505a-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="2505a-109">EndCustomDump, méthode</span><span class="sxs-lookup"><span data-stu-id="2505a-109">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="2505a-110">Efface la configuration de vidage de pile personnalisée qui a été définie par un appel antérieur à `BeginCustomDump` .</span><span class="sxs-lookup"><span data-stu-id="2505a-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="2505a-111">GetBucketParametersForCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="2505a-111">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="2505a-112">Obtient le compartiment Watson pour l’exception actuelle sur le thread appelant.</span><span class="sxs-lookup"><span data-stu-id="2505a-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2505a-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="2505a-113">Remarks</span></span>  

 <span data-ttu-id="2505a-114">La `BeginCustomDump` méthode définit une configuration de vidage de pile personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2505a-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="2505a-115">La `EndCustomDump` méthode efface la configuration de vidage de pile personnalisée et libère tous les États associés.</span><span class="sxs-lookup"><span data-stu-id="2505a-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="2505a-116">Elle doit être appelée une fois que le vidage personnalisé est terminé.</span><span class="sxs-lookup"><span data-stu-id="2505a-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2505a-117">L’échec de l’appel `EndCustomDump` entraîne une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="2505a-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2505a-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2505a-118">Requirements</span></span>  

 <span data-ttu-id="2505a-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2505a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2505a-120">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2505a-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2505a-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2505a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2505a-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2505a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2505a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2505a-123">See also</span></span>

- [<span data-ttu-id="2505a-124">ECustomDumpItemKind, énumération</span><span class="sxs-lookup"><span data-stu-id="2505a-124">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="2505a-125">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="2505a-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
