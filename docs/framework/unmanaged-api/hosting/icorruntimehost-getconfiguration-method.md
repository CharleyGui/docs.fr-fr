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
ms.openlocfilehash: 2a50814a67be5a01a7413050683a915355665f3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720644"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="934a7-102">ICorRuntimeHost::GetConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="934a7-102">ICorRuntimeHost::GetConfiguration Method</span></span>

<span data-ttu-id="934a7-103">Obtient un objet qui permet à l’hôte de spécifier la configuration de rappel du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="934a7-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="934a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="934a7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="934a7-105">Parameters</span></span>  

 `pConfiguration`  
 <span data-ttu-id="934a7-106">à Pointeur vers l’adresse d’un objet [ICorConfiguration](icorconfiguration-interface.md) qui peut être utilisé pour configurer le CLR.</span><span class="sxs-lookup"><span data-stu-id="934a7-106">[out] A pointer to the address of an [ICorConfiguration](icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="934a7-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="934a7-107">Remarks</span></span>  

 <span data-ttu-id="934a7-108">Le CLR doit être configuré avant son initialisation ; Sinon, la `GetConfiguration` méthode retourne un HRESULT indiquant une erreur.</span><span class="sxs-lookup"><span data-stu-id="934a7-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934a7-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="934a7-109">Requirements</span></span>  

 <span data-ttu-id="934a7-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="934a7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="934a7-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="934a7-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="934a7-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="934a7-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="934a7-113">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="934a7-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934a7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="934a7-114">See also</span></span>

- [<span data-ttu-id="934a7-115">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="934a7-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
