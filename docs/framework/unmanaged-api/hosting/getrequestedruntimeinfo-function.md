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
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178151"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="be5e2-102">GetRequestedRuntimeInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="be5e2-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="be5e2-103">Obtient des informations de version et d’annuaire sur l’heure d’exécution de langue commune (CLR) demandées par une application.</span><span class="sxs-lookup"><span data-stu-id="be5e2-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="be5e2-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="be5e2-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be5e2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be5e2-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="be5e2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be5e2-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="be5e2-107">[dans] Le nom de l’application.</span><span class="sxs-lookup"><span data-stu-id="be5e2-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="be5e2-108">[dans] Une chaîne spécifiant le numéro de version de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="be5e2-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="be5e2-109">[dans] Le nom du fichier de `pExe`configuration qui est associé à .</span><span class="sxs-lookup"><span data-stu-id="be5e2-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="be5e2-110">[dans] Une ou plusieurs des valeurs d’énumération [STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="be5e2-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="be5e2-111">[dans] Une ou plusieurs des valeurs d’énumération [RUNTIME_INFO_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="be5e2-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="be5e2-112">[out] Un tampon qui contient le chemin d’annuaire vers le temps d’exécution une fois terminé.</span><span class="sxs-lookup"><span data-stu-id="be5e2-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="be5e2-113">[dans] La longueur du tampon d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="be5e2-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="be5e2-114">[out] Un pointeur sur la longueur de la chaîne de trajectoire d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="be5e2-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="be5e2-115">[out] Un tampon qui contient le numéro de version du temps d’exécution une fois terminé.</span><span class="sxs-lookup"><span data-stu-id="be5e2-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="be5e2-116">[dans] La longueur du tampon de chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="be5e2-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="be5e2-117">[out] Un pointeur sur la longueur de la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="be5e2-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be5e2-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="be5e2-118">Return Value</span></span>  
 <span data-ttu-id="be5e2-119">Cette méthode renvoie les codes d’erreur standard du modèle d’objet composant (COM), tels que définis dans WinError.h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="be5e2-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="be5e2-120">Code de retour</span><span class="sxs-lookup"><span data-stu-id="be5e2-120">Return code</span></span>|<span data-ttu-id="be5e2-121">Description</span><span class="sxs-lookup"><span data-stu-id="be5e2-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="be5e2-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="be5e2-122">S_OK</span></span>|<span data-ttu-id="be5e2-123">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="be5e2-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="be5e2-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="be5e2-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="be5e2-125">Le tampon d’annuaire n’est pas assez grand pour stocker le chemin d’annuaire.</span><span class="sxs-lookup"><span data-stu-id="be5e2-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="be5e2-126">- ou -</span><span class="sxs-lookup"><span data-stu-id="be5e2-126">- or -</span></span><br /><br /> <span data-ttu-id="be5e2-127">Le tampon de version n’est pas assez grand pour stocker la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="be5e2-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be5e2-128">Notes </span><span class="sxs-lookup"><span data-stu-id="be5e2-128">Remarks</span></span>  
 <span data-ttu-id="be5e2-129">La `GetRequestedRuntimeInfo` méthode renvoie les informations en temps d’exécution sur la version chargée dans le processus, qui n’est pas nécessairement la dernière version installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="be5e2-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="be5e2-130">Dans la version cadre .NET 2.0, vous pouvez obtenir `GetRequestedRuntimeInfo` des informations sur la dernière version installée en utilisant la méthode comme suit:</span><span class="sxs-lookup"><span data-stu-id="be5e2-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="be5e2-131">Spécifier le `pExe`, `pwszVersion`, et `pConfigurationFile` les paramètres comme nuls.</span><span class="sxs-lookup"><span data-stu-id="be5e2-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="be5e2-132">Spécifier le drapeau `RUNTIME_INFO_FLAGS` RUNTIME_INFO_UPGRADE_VERSION dans les `runtimeInfoFlags` énumérations pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="be5e2-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="be5e2-133">La `GetRequestedRuntimeInfo` méthode ne renvoie pas la dernière version CLR dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="be5e2-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="be5e2-134">Il existe un fichier de configuration d’application qui spécifie le chargement d’une version CLR particulière.</span><span class="sxs-lookup"><span data-stu-id="be5e2-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="be5e2-135">Notez que le cadre .NET utilisera le fichier `pConfigurationFile` de configuration même si vous spécifiez nul pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="be5e2-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="be5e2-136">La méthode [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a été appelée spécifiant une version CLR antérieure.</span><span class="sxs-lookup"><span data-stu-id="be5e2-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="be5e2-137">Une application qui a été compilée pour une version CLR antérieure est actuellement en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="be5e2-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="be5e2-138">Pour `runtimeInfoFlags` le paramètre, vous ne pouvez spécifier qu’une seule des constantes d’architecture de l’énumération à la `RUNTIME_INFO_FLAGS` fois :</span><span class="sxs-lookup"><span data-stu-id="be5e2-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="be5e2-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="be5e2-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="be5e2-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="be5e2-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="be5e2-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="be5e2-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be5e2-142">Spécifications</span><span class="sxs-lookup"><span data-stu-id="be5e2-142">Requirements</span></span>  
 <span data-ttu-id="be5e2-143">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be5e2-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be5e2-144">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="be5e2-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be5e2-145">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="be5e2-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be5e2-146">**.NET Versions-cadre:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be5e2-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be5e2-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be5e2-147">See also</span></span>

- [<span data-ttu-id="be5e2-148">GetRequestedRuntimeVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="be5e2-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="be5e2-149">GetVersionFromProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="be5e2-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="be5e2-150">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="be5e2-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
