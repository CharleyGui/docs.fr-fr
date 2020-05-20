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
ms.openlocfilehash: dbe4129cf4160a1a9b31bc6f418095ea4b392d57
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616994"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="3ad69-102">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="3ad69-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="3ad69-103">Fournit des méthodes qui permettent à l’hôte de configurer des vidages de pile personnalisés pour le rapport d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="3ad69-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ad69-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3ad69-104">Methods</span></span>  
  
|<span data-ttu-id="3ad69-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="3ad69-105">Method</span></span>|<span data-ttu-id="3ad69-106">Description</span><span class="sxs-lookup"><span data-stu-id="3ad69-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ad69-107">BeginCustomDump, méthode</span><span class="sxs-lookup"><span data-stu-id="3ad69-107">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="3ad69-108">Spécifie la configuration des vidages de pile personnalisés pour le rapport d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="3ad69-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="3ad69-109">EndCustomDump, méthode</span><span class="sxs-lookup"><span data-stu-id="3ad69-109">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="3ad69-110">Efface la configuration de vidage de pile personnalisée qui a été définie par un appel antérieur à `BeginCustomDump` .</span><span class="sxs-lookup"><span data-stu-id="3ad69-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="3ad69-111">GetBucketParametersForCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="3ad69-111">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="3ad69-112">Obtient le compartiment Watson pour l’exception actuelle sur le thread appelant.</span><span class="sxs-lookup"><span data-stu-id="3ad69-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ad69-113">Notes</span><span class="sxs-lookup"><span data-stu-id="3ad69-113">Remarks</span></span>  
 <span data-ttu-id="3ad69-114">La `BeginCustomDump` méthode définit une configuration de vidage de pile personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3ad69-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="3ad69-115">La `EndCustomDump` méthode efface la configuration de vidage de pile personnalisée et libère tous les États associés.</span><span class="sxs-lookup"><span data-stu-id="3ad69-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="3ad69-116">Elle doit être appelée une fois que le vidage personnalisé est terminé.</span><span class="sxs-lookup"><span data-stu-id="3ad69-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3ad69-117">L’échec de l’appel `EndCustomDump` entraîne une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="3ad69-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ad69-118">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="3ad69-118">Requirements</span></span>  
 <span data-ttu-id="3ad69-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ad69-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ad69-120">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3ad69-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ad69-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3ad69-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ad69-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ad69-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad69-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ad69-123">See also</span></span>

- [<span data-ttu-id="3ad69-124">ECustomDumpItemKind, énumération</span><span class="sxs-lookup"><span data-stu-id="3ad69-124">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="3ad69-125">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="3ad69-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
