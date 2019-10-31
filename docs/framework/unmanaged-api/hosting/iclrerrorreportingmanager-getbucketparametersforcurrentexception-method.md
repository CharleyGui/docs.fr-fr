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
ms.openlocfilehash: b24f8ed4f5e2c6e0022f5599f2ab8c44a30a561a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129277"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="763e0-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="763e0-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>
<span data-ttu-id="763e0-103">Obtient le compartiment Watson pour l’exception actuelle sur le thread appelant.</span><span class="sxs-lookup"><span data-stu-id="763e0-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="763e0-104">Un *compartiment* est une collection de données d’erreur qui est liée à la même erreur de code.</span><span class="sxs-lookup"><span data-stu-id="763e0-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="763e0-105">*Watson* fait référence à un ensemble de technologies permettant de collecter et d’analyser les données associées à une exception.</span><span class="sxs-lookup"><span data-stu-id="763e0-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="763e0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="763e0-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="763e0-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="763e0-107">Parameters</span></span>  
 `pParams`  
 <span data-ttu-id="763e0-108">à Pointeur vers une structure [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) qui contient les données d’erreur pour l’exception.</span><span class="sxs-lookup"><span data-stu-id="763e0-108">[out] A pointer to a [BucketParameters](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="763e0-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="763e0-109">Requirements</span></span>  
 <span data-ttu-id="763e0-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="763e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="763e0-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="763e0-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="763e0-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="763e0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="763e0-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="763e0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="763e0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="763e0-114">See also</span></span>

- [<span data-ttu-id="763e0-115">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="763e0-115">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
