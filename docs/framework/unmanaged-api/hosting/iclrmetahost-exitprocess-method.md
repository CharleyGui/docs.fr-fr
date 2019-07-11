---
title: ICLRMetaHost::ExitProcess, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0288c9912125e20cfb9f9aaaac5003ae9e0b51e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779788"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="349c5-102">ICLRMetaHost::ExitProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="349c5-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="349c5-103">Tente d’arrêter correctement les runtimes tous chargés et puis met fin au processus.</span><span class="sxs-lookup"><span data-stu-id="349c5-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="349c5-104">Remplace le [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="349c5-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="349c5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="349c5-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="349c5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="349c5-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="349c5-107">[in] Le code de sortie pour le processus.</span><span class="sxs-lookup"><span data-stu-id="349c5-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="349c5-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="349c5-108">Return Value</span></span>  
 <span data-ttu-id="349c5-109">Cette méthode ne retourne jamais, donc sa valeur de retour n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="349c5-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="349c5-110">Notes</span><span class="sxs-lookup"><span data-stu-id="349c5-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="349c5-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="349c5-111">Requirements</span></span>  
 <span data-ttu-id="349c5-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="349c5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="349c5-113">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="349c5-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="349c5-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="349c5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="349c5-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="349c5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="349c5-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="349c5-116">See also</span></span>

- [<span data-ttu-id="349c5-117">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="349c5-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="349c5-118">Hébergement</span><span class="sxs-lookup"><span data-stu-id="349c5-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
