---
title: ICLRErrorReportingManager::GetBucketParametersForCurrentException, méthode
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type:
- apiref
ms.openlocfilehash: 969d74933e908674225684a2e77d5c4804b86122
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615642"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="61411-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="61411-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="61411-103">Obtient le compartiment Watson pour l’exception actuelle sur le thread appelant.</span><span class="sxs-lookup"><span data-stu-id="61411-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="61411-104">Un *compartiment* est une collection de données d’erreur qui est liée à la même erreur de code.</span><span class="sxs-lookup"><span data-stu-id="61411-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="61411-105">*Watson* fait référence à un ensemble de technologies permettant de collecter et d’analyser les données associées à une exception.</span><span class="sxs-lookup"><span data-stu-id="61411-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61411-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61411-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61411-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="61411-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="61411-108">à Pointeur vers une structure [BucketParameters](bucketparameters-structure.md) qui contient les données d’erreur pour l’exception.</span><span class="sxs-lookup"><span data-stu-id="61411-108">[out] A pointer to a [BucketParameters](bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61411-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="61411-109">Requirements</span></span>  
 <span data-ttu-id="61411-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61411-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61411-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="61411-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61411-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="61411-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61411-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61411-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61411-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61411-114">See also</span></span>

- [<span data-ttu-id="61411-115">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="61411-115">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
