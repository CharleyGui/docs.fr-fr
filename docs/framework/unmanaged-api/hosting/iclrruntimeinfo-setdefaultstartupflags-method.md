---
title: ICLRRuntimeInfo::SetDefaultStartupFlags, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2996acd9678557b08fcfa543ecc7648ed639b143
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748344"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="68737-102">ICLRRuntimeInfo::SetDefaultStartupFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="68737-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="68737-103">Définit les indicateurs de démarrage et le fichier de configuration d’hôte qui sera utilisé pour démarrer le runtime.</span><span class="sxs-lookup"><span data-stu-id="68737-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="68737-104">Cette méthode remplace l’utilisation de la `startupFlags` paramètre dans le [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) et [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) fonctions.</span><span class="sxs-lookup"><span data-stu-id="68737-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68737-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68737-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68737-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68737-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="68737-107">[in] Les indicateurs de démarrage hôte à définir.</span><span class="sxs-lookup"><span data-stu-id="68737-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="68737-108">Utilisez les mêmes indicateurs comme avec la [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) et [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) fonctions.</span><span class="sxs-lookup"><span data-stu-id="68737-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="68737-109">[in] Le chemin du répertoire du fichier de configuration d’hôte à définir.</span><span class="sxs-lookup"><span data-stu-id="68737-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68737-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="68737-110">Return Value</span></span>  
 <span data-ttu-id="68737-111">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l’échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="68737-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="68737-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68737-112">HRESULT</span></span>|<span data-ttu-id="68737-113">Description</span><span class="sxs-lookup"><span data-stu-id="68737-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68737-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="68737-114">S_OK</span></span>|<span data-ttu-id="68737-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="68737-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68737-116">Notes</span><span class="sxs-lookup"><span data-stu-id="68737-116">Remarks</span></span>  
 <span data-ttu-id="68737-117">Un hôte multithread doit synchroniser des appels à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="68737-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="68737-118">Sinon, le thread A peut appeler le `SetStartupFlags` méthode une fois que le thread B a terminé un appel à `SetStartupFlags` et avant que thread B démarre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="68737-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68737-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="68737-119">Requirements</span></span>  
 <span data-ttu-id="68737-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68737-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68737-121">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="68737-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="68737-122">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68737-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68737-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68737-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68737-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68737-124">See also</span></span>

- [<span data-ttu-id="68737-125">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="68737-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="68737-126">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="68737-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="68737-127">Hébergement</span><span class="sxs-lookup"><span data-stu-id="68737-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
