---
title: ICorRuntimeHost::GetConfiguration, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
ms.openlocfilehash: 87549118742da797ef0dd1b08ae9e72c466f7841
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139568"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="77cee-102">ICorRuntimeHost::GetConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="77cee-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="77cee-103">Obtient un objet qui permet à l’hôte de spécifier la configuration de rappel du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="77cee-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77cee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77cee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77cee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="77cee-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="77cee-106">à Pointeur vers l’adresse d’un objet [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) qui peut être utilisé pour configurer le CLR.</span><span class="sxs-lookup"><span data-stu-id="77cee-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77cee-107">Notes</span><span class="sxs-lookup"><span data-stu-id="77cee-107">Remarks</span></span>  
 <span data-ttu-id="77cee-108">Le CLR doit être configuré avant son initialisation ; Sinon, la méthode `GetConfiguration` retourne un HRESULT indiquant une erreur.</span><span class="sxs-lookup"><span data-stu-id="77cee-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77cee-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="77cee-109">Requirements</span></span>  
 <span data-ttu-id="77cee-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77cee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77cee-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="77cee-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77cee-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="77cee-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77cee-113">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="77cee-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77cee-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77cee-114">See also</span></span>

- [<span data-ttu-id="77cee-115">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="77cee-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
