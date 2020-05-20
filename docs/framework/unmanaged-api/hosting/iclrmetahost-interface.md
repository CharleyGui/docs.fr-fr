---
title: ICLRMetaHost, interface
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
ms.openlocfilehash: 391adc6f9fe55ad7ca527ea416956ab013a27b15
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703721"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="3106f-102">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="3106f-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="3106f-103">Fournit des méthodes qui retournent une version spécifique du common language runtime (CLR) en fonction de son numéro de version, de la liste de tous les CLR installés, de la liste de tous les runtimes chargés dans un processus spécifié, de la découverte de la version CLR utilisée pour compiler un assembly, de la sortie d’un processus avec arrêt du runtime propre et de la liaison d’API héritée</span><span class="sxs-lookup"><span data-stu-id="3106f-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3106f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3106f-104">Methods</span></span>  
  
|<span data-ttu-id="3106f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="3106f-105">Method</span></span>|<span data-ttu-id="3106f-106">Description</span><span class="sxs-lookup"><span data-stu-id="3106f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3106f-107">EnumerateInstalledRuntimes, méthode</span><span class="sxs-lookup"><span data-stu-id="3106f-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="3106f-108">Retourne une énumération qui contient un pointeur d’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) valide pour chaque version du CLR installée sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3106f-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="3106f-109">EnumerateLoadedRuntimes, méthode</span><span class="sxs-lookup"><span data-stu-id="3106f-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="3106f-110">Retourne une énumération qui contient un pointeur d’interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) valide pour chaque CLR qui est chargé dans un processus donné.</span><span class="sxs-lookup"><span data-stu-id="3106f-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="3106f-111">Cette méthode remplace [GetVersionFromProcess](getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="3106f-111">This method supersedes [GetVersionFromProcess](getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="3106f-112">ExitProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="3106f-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="3106f-113">Tente d’arrêter correctement tous les runtimes chargés, puis termine le processus.</span><span class="sxs-lookup"><span data-stu-id="3106f-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="3106f-114">Remplace la fonction [CorExitProcess,](corexitprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="3106f-114">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="3106f-115">GetRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="3106f-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="3106f-116">Obtient l’interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) qui correspond à une version particulière du CLR.</span><span class="sxs-lookup"><span data-stu-id="3106f-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="3106f-117">Cette méthode remplace la fonction [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) utilisée avec l’indicateur [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="3106f-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="3106f-118">GetVersionFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="3106f-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="3106f-119">Obtient la version de compilation .NET Framework d’origine de l’assembly (stockée dans les métadonnées), en fonction de son chemin d’accès au fichier.</span><span class="sxs-lookup"><span data-stu-id="3106f-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="3106f-120">Cette méthode remplace [GetFileVersion,](getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="3106f-120">This method supersedes [GetFileVersion](getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="3106f-121">QueryLegacyV2RuntimeBinding, méthode</span><span class="sxs-lookup"><span data-stu-id="3106f-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="3106f-122">Retourne une interface qui représente un runtime auquel une stratégie d’activation héritée a été liée, par exemple en utilisant l' `useLegacyV2RuntimeActivationPolicy` attribut sur l’entrée du fichier de configuration de l' [ \< élément de démarrage>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , en utilisant directement les API d’activation héritées ou en appelant la méthode [ICLRRuntimeInfo :: BindAsLegacyV2Runtime,](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3106f-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="3106f-123">RequestRuntimeLoadedNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="3106f-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="3106f-124">Garantit un rappel au pointeur de fonction spécifié quand une version CLR est chargée pour la première fois, mais pas encore démarrée.</span><span class="sxs-lookup"><span data-stu-id="3106f-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="3106f-125">Cette méthode remplace [LockClrVersion](lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="3106f-125">This method supersedes [LockClrVersion](lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3106f-126">Notes</span><span class="sxs-lookup"><span data-stu-id="3106f-126">Remarks</span></span>  
 <span data-ttu-id="3106f-127">La seule façon d’accéder à une instance de cette interface est d’appeler la fonction [CLRCreateInstance](clrcreateinstance-function.md) comme suit :</span><span class="sxs-lookup"><span data-stu-id="3106f-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3106f-128">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="3106f-128">Requirements</span></span>  
 <span data-ttu-id="3106f-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3106f-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3106f-130">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="3106f-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3106f-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3106f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3106f-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3106f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3106f-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3106f-133">See also</span></span>

- [<span data-ttu-id="3106f-134">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="3106f-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="3106f-135">Hébergement</span><span class="sxs-lookup"><span data-stu-id="3106f-135">Hosting</span></span>](index.md)
