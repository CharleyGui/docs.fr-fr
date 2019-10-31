---
title: IManagedObject::GetObjectIdentity, méthode
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
ms.openlocfilehash: 8c884569a452fb2985713956f942205cda6ea1ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141244"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="359eb-102">IManagedObject::GetObjectIdentity, méthode</span><span class="sxs-lookup"><span data-stu-id="359eb-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="359eb-103">Obtient l’identité de cet objet managé.</span><span class="sxs-lookup"><span data-stu-id="359eb-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="359eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="359eb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="359eb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="359eb-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="359eb-106">à Pointeur vers le GUID du processus dans lequel l’objet réside.</span><span class="sxs-lookup"><span data-stu-id="359eb-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="359eb-107">à Pointeur vers l’ID du domaine d’application de l’objet.</span><span class="sxs-lookup"><span data-stu-id="359eb-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="359eb-108">à Pointeur vers l’index de l’objet dans la table v classique COM.</span><span class="sxs-lookup"><span data-stu-id="359eb-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="359eb-109">Notes</span><span class="sxs-lookup"><span data-stu-id="359eb-109">Remarks</span></span>  
 <span data-ttu-id="359eb-110">L’identité d’un objet géré comprend le GUID du processus, l’ID de domaine d’application et l’index de l’objet dans la table v Classic COM.</span><span class="sxs-lookup"><span data-stu-id="359eb-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="359eb-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="359eb-111">Requirements</span></span>  
 <span data-ttu-id="359eb-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="359eb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="359eb-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="359eb-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="359eb-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="359eb-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="359eb-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="359eb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="359eb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="359eb-116">See also</span></span>

- [<span data-ttu-id="359eb-117">IManagedObject, interface</span><span class="sxs-lookup"><span data-stu-id="359eb-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
