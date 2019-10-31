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
ms.openlocfilehash: 36851ac4573d0d65caffaa3f82a1f6fc8440a2d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092750"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="5e54d-102">ICLRRuntimeInfo::SetDefaultStartupFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="5e54d-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="5e54d-103">Définit les indicateurs de démarrage et le fichier de configuration d’hôte qui sera utilisé pour démarrer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="5e54d-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="5e54d-104">Cette méthode remplace l’utilisation du paramètre `startupFlags` dans les fonctions [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) et [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="5e54d-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e54d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e54d-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e54d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e54d-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="5e54d-107">dans Indicateurs de démarrage de l’hôte à définir.</span><span class="sxs-lookup"><span data-stu-id="5e54d-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="5e54d-108">Utilisez les mêmes indicateurs qu’avec les fonctions [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) et [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="5e54d-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="5e54d-109">dans Chemin d’accès du répertoire du fichier de configuration hôte à définir.</span><span class="sxs-lookup"><span data-stu-id="5e54d-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e54d-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5e54d-110">Return Value</span></span>  
 <span data-ttu-id="5e54d-111">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT qui indiquent un échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="5e54d-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5e54d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e54d-112">HRESULT</span></span>|<span data-ttu-id="5e54d-113">Description</span><span class="sxs-lookup"><span data-stu-id="5e54d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e54d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e54d-114">S_OK</span></span>|<span data-ttu-id="5e54d-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="5e54d-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e54d-116">Notes</span><span class="sxs-lookup"><span data-stu-id="5e54d-116">Remarks</span></span>  
 <span data-ttu-id="5e54d-117">Un hôte multithread doit synchroniser les appels à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="5e54d-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="5e54d-118">Sinon, le thread A peut appeler la méthode `SetStartupFlags` une fois que le thread B a terminé un appel à `SetStartupFlags` et avant que le thread B démarre le Runtime.</span><span class="sxs-lookup"><span data-stu-id="5e54d-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e54d-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="5e54d-119">Requirements</span></span>  
 <span data-ttu-id="5e54d-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e54d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e54d-121">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="5e54d-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5e54d-122">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5e54d-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e54d-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e54d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e54d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e54d-124">See also</span></span>

- [<span data-ttu-id="5e54d-125">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="5e54d-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="5e54d-126">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="5e54d-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="5e54d-127">Hébergement</span><span class="sxs-lookup"><span data-stu-id="5e54d-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
