---
title: Coclasse CLRRuntimeHost
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
ms.openlocfilehash: 7c77cb2e89cb8fd87bf219780b9460649de19c9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731757"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="d0880-102">Coclasse CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="d0880-102">CLRRuntimeHost Coclass</span></span>

<span data-ttu-id="d0880-103">Fournit des interfaces pour la gestion de l’exécution du code par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="d0880-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0880-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0880-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="d0880-105">Interfaces</span><span class="sxs-lookup"><span data-stu-id="d0880-105">Interfaces</span></span>  
  
|<span data-ttu-id="d0880-106">Interface</span><span class="sxs-lookup"><span data-stu-id="d0880-106">Interface</span></span>|<span data-ttu-id="d0880-107">Description</span><span class="sxs-lookup"><span data-stu-id="d0880-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="d0880-108">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="d0880-108">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)|<span data-ttu-id="d0880-109">Fournit des méthodes pour contrôler l’exécution d’applications par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="d0880-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="d0880-110">ICLRValidator, interface</span><span class="sxs-lookup"><span data-stu-id="d0880-110">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)|<span data-ttu-id="d0880-111">Fournit des méthodes pour la validation des images exécutables portables et pour la création de rapports détaillés des erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="d0880-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0880-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d0880-112">Requirements</span></span>  

 <span data-ttu-id="d0880-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0880-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0880-114">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="d0880-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d0880-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0880-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0880-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0880-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0880-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0880-117">See also</span></span>

- [<span data-ttu-id="d0880-118">Hébergement des coclasses</span><span class="sxs-lookup"><span data-stu-id="d0880-118">Hosting Coclasses</span></span>](hosting-coclasses.md)
