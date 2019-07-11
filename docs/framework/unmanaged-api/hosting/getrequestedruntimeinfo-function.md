---
title: GetRequestedRuntimeInfo, fonction
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62a6f6d6e73ce42c8c86d4e458322e5bd361f412
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778136"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="df42f-102">GetRequestedRuntimeInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="df42f-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="df42f-103">Obtient des informations de version et au répertoire sur le common language runtime (CLR) demandée par une application.</span><span class="sxs-lookup"><span data-stu-id="df42f-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="df42f-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="df42f-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df42f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df42f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df42f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df42f-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="df42f-107">[in] Le nom de l’application.</span><span class="sxs-lookup"><span data-stu-id="df42f-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="df42f-108">[in] Chaîne spécifiant le numéro de version du runtime.</span><span class="sxs-lookup"><span data-stu-id="df42f-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="df42f-109">[in] Le nom du fichier de configuration qui est associé avec `pExe`.</span><span class="sxs-lookup"><span data-stu-id="df42f-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="df42f-110">[in] Une ou plusieurs de la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="df42f-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="df42f-111">[in] Une ou plusieurs de la [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="df42f-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="df42f-112">[out] Une mémoire tampon qui contient le chemin d’accès du répertoire à l’exécution en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="df42f-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="df42f-113">[in] La longueur de la mémoire tampon du répertoire.</span><span class="sxs-lookup"><span data-stu-id="df42f-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="df42f-114">[out] Pointeur vers la longueur de la chaîne de chemin d’accès de répertoire.</span><span class="sxs-lookup"><span data-stu-id="df42f-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="df42f-115">[out] Une mémoire tampon qui contient le numéro de version du runtime en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="df42f-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="df42f-116">[in] La longueur du tampon de chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="df42f-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="df42f-117">[out] Pointeur vers la longueur de la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="df42f-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df42f-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="df42f-118">Return Value</span></span>  
 <span data-ttu-id="df42f-119">Cette méthode retourne des codes d’erreur de composant COM (Object Model) standard, tel que défini dans WinError.h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="df42f-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="df42f-120">Code de retour</span><span class="sxs-lookup"><span data-stu-id="df42f-120">Return code</span></span>|<span data-ttu-id="df42f-121">Description</span><span class="sxs-lookup"><span data-stu-id="df42f-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="df42f-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="df42f-122">S_OK</span></span>|<span data-ttu-id="df42f-123">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="df42f-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="df42f-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="df42f-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="df42f-125">Le tampon de répertoire n’est pas suffisamment grand pour stocker le chemin d’accès de répertoire.</span><span class="sxs-lookup"><span data-stu-id="df42f-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="df42f-126">ou</span><span class="sxs-lookup"><span data-stu-id="df42f-126">- or -</span></span><br /><br /> <span data-ttu-id="df42f-127">Le tampon de version n’est pas suffisamment grand pour stocker la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="df42f-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df42f-128">Notes</span><span class="sxs-lookup"><span data-stu-id="df42f-128">Remarks</span></span>  
 <span data-ttu-id="df42f-129">Le `GetRequestedRuntimeInfo` méthode retourne des informations d’exécution sur la version chargée dans le processus, ce qui n’est pas nécessairement la dernière version installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="df42f-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="df42f-130">Dans le .NET Framework version 2.0, vous pouvez obtenir des informations sur la dernière version installée à l’aide de la `GetRequestedRuntimeInfo` méthode comme suit :</span><span class="sxs-lookup"><span data-stu-id="df42f-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="df42f-131">Spécifiez le `pExe`, `pwszVersion`, et `pConfigurationFile` paramètres comme null.</span><span class="sxs-lookup"><span data-stu-id="df42f-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="df42f-132">Spécifiez l’indicateur RUNTIME_INFO_UPGRADE_VERSION dans le `RUNTIME_INFO_FLAGS` énumérations pour le `runtimeInfoFlags` paramètre.</span><span class="sxs-lookup"><span data-stu-id="df42f-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="df42f-133">Le `GetRequestedRuntimeInfo` méthode ne retourne pas la dernière version CLR dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="df42f-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="df42f-134">Il existe un fichier de configuration qui spécifie le chargement d’une version particulière du CLR.</span><span class="sxs-lookup"><span data-stu-id="df42f-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="df42f-135">Notez que le .NET Framework utilisera le fichier de configuration même si vous spécifiez null pour le `pConfigurationFile` paramètre.</span><span class="sxs-lookup"><span data-stu-id="df42f-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="df42f-136">Le [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) méthode a été appelée en spécifiant une version antérieure du CLR.</span><span class="sxs-lookup"><span data-stu-id="df42f-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="df42f-137">Une application qui a été compilée pour une version antérieure du CLR est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="df42f-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="df42f-138">Pour le `runtimeInfoFlags` paramètre, vous pouvez spécifier uniquement une des constantes d’architecture de la `RUNTIME_INFO_FLAGS` énumération à la fois :</span><span class="sxs-lookup"><span data-stu-id="df42f-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="df42f-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="df42f-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="df42f-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="df42f-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="df42f-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="df42f-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df42f-142">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="df42f-142">Requirements</span></span>  
 <span data-ttu-id="df42f-143">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df42f-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df42f-144">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df42f-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df42f-145">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df42f-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df42f-146">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df42f-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df42f-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df42f-147">See also</span></span>

- [<span data-ttu-id="df42f-148">GetRequestedRuntimeVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="df42f-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="df42f-149">GetVersionFromProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="df42f-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="df42f-150">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="df42f-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
