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
ms.openlocfilehash: 1b40ed8e107d30c22b4ade25d29376b1b74583d1
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842411"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="b0ccf-102">IManagedObject::GetObjectIdentity, méthode</span><span class="sxs-lookup"><span data-stu-id="b0ccf-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="b0ccf-103">Obtient l’identité de cet objet managé.</span><span class="sxs-lookup"><span data-stu-id="b0ccf-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ccf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0ccf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0ccf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b0ccf-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="b0ccf-106">à Pointeur vers le GUID du processus dans lequel l’objet réside.</span><span class="sxs-lookup"><span data-stu-id="b0ccf-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="b0ccf-107">à Pointeur vers l’ID du domaine d’application de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b0ccf-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="b0ccf-108">à Pointeur vers l’index de l’objet dans la table v classique COM.</span><span class="sxs-lookup"><span data-stu-id="b0ccf-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0ccf-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="b0ccf-109">Remarks</span></span>  
 <span data-ttu-id="b0ccf-110">L’identité d’un objet géré comprend le GUID du processus, l’ID de domaine d’application et l’index de l’objet dans la table v Classic COM.</span><span class="sxs-lookup"><span data-stu-id="b0ccf-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ccf-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b0ccf-111">Requirements</span></span>  
 <span data-ttu-id="b0ccf-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0ccf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0ccf-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b0ccf-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0ccf-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b0ccf-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0ccf-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0ccf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ccf-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0ccf-116">See also</span></span>

- [<span data-ttu-id="b0ccf-117">IManagedObject, interface</span><span class="sxs-lookup"><span data-stu-id="b0ccf-117">IManagedObject Interface</span></span>](imanagedobject-interface.md)
