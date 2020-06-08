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
ms.openlocfilehash: aa02d42511a863434fef236f90afae2c5417a78d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504015"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="47fdc-102">ICLRRuntimeInfo::SetDefaultStartupFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="47fdc-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="47fdc-103">Définit les indicateurs de démarrage et le fichier de configuration d’hôte qui sera utilisé pour démarrer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="47fdc-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="47fdc-104">Cette méthode remplace l’utilisation du `startupFlags` paramètre dans les fonctions [CorBindToRuntimeEx](corbindtoruntimeex-function.md) et [CorBindToRuntimeHost](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="47fdc-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47fdc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47fdc-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47fdc-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="47fdc-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="47fdc-107">dans Indicateurs de démarrage de l’hôte à définir.</span><span class="sxs-lookup"><span data-stu-id="47fdc-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="47fdc-108">Utilisez les mêmes indicateurs qu’avec les fonctions [CorBindToRuntimeEx](corbindtoruntimeex-function.md) et [CorBindToRuntimeHost](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="47fdc-108">Use the same flags as with the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="47fdc-109">dans Chemin d’accès du répertoire du fichier de configuration hôte à définir.</span><span class="sxs-lookup"><span data-stu-id="47fdc-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47fdc-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="47fdc-110">Return Value</span></span>  
 <span data-ttu-id="47fdc-111">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT qui indiquent un échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="47fdc-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="47fdc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47fdc-112">HRESULT</span></span>|<span data-ttu-id="47fdc-113">Description</span><span class="sxs-lookup"><span data-stu-id="47fdc-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47fdc-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="47fdc-114">S_OK</span></span>|<span data-ttu-id="47fdc-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="47fdc-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47fdc-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="47fdc-116">Remarks</span></span>  
 <span data-ttu-id="47fdc-117">Un hôte multithread doit synchroniser les appels à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="47fdc-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="47fdc-118">Sinon, le thread A peut appeler la `SetStartupFlags` méthode une fois que le thread b a terminé un appel à `SetStartupFlags` et avant que le thread b démarre le Runtime.</span><span class="sxs-lookup"><span data-stu-id="47fdc-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47fdc-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="47fdc-119">Requirements</span></span>  
 <span data-ttu-id="47fdc-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47fdc-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47fdc-121">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="47fdc-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="47fdc-122">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="47fdc-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47fdc-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47fdc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47fdc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47fdc-124">See also</span></span>

- [<span data-ttu-id="47fdc-125">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="47fdc-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="47fdc-126">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="47fdc-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="47fdc-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="47fdc-127">Hosting</span></span>](index.md)
