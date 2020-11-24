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
ms.openlocfilehash: 33927cc0e3a3cdaad70d437f9dd5ca5dfdcdc46b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673555"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="92397-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="92397-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>

<span data-ttu-id="92397-103">Obtient le compartiment Watson pour l’exception actuelle sur le thread appelant.</span><span class="sxs-lookup"><span data-stu-id="92397-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="92397-104">Un *compartiment* est une collection de données d’erreur qui est liée à la même erreur de code.</span><span class="sxs-lookup"><span data-stu-id="92397-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="92397-105">*Watson* fait référence à un ensemble de technologies permettant de collecter et d’analyser les données associées à une exception.</span><span class="sxs-lookup"><span data-stu-id="92397-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92397-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92397-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92397-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="92397-107">Parameters</span></span>  

 `pParams`  
 <span data-ttu-id="92397-108">à Pointeur vers une structure [BucketParameters](bucketparameters-structure.md) qui contient les données d’erreur pour l’exception.</span><span class="sxs-lookup"><span data-stu-id="92397-108">[out] A pointer to a [BucketParameters](bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92397-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="92397-109">Requirements</span></span>  

 <span data-ttu-id="92397-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92397-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92397-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="92397-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92397-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92397-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92397-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92397-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92397-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92397-114">See also</span></span>

- [<span data-ttu-id="92397-115">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="92397-115">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
