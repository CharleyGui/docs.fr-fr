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
ms.openlocfilehash: cd1d9e768698115bee22e35699b044e0c3526d2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136325"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="b456b-102">GetRequestedRuntimeInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="b456b-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="b456b-103">Obtient les informations de version et de répertoire relatives au common language runtime (CLR) demandé par une application.</span><span class="sxs-lookup"><span data-stu-id="b456b-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="b456b-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b456b-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b456b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b456b-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b456b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b456b-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="b456b-107">dans Nom de l’application.</span><span class="sxs-lookup"><span data-stu-id="b456b-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="b456b-108">dans Chaîne spécifiant le numéro de version du Runtime.</span><span class="sxs-lookup"><span data-stu-id="b456b-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="b456b-109">dans Nom du fichier de configuration associé à `pExe`.</span><span class="sxs-lookup"><span data-stu-id="b456b-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="b456b-110">dans Une ou plusieurs des valeurs de l’énumération [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b456b-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="b456b-111">dans Une ou plusieurs des valeurs d’énumération [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b456b-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="b456b-112">à Mémoire tampon qui contient le chemin d’accès au répertoire du runtime une fois l’opération terminée.</span><span class="sxs-lookup"><span data-stu-id="b456b-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="b456b-113">dans Longueur de la mémoire tampon de répertoire.</span><span class="sxs-lookup"><span data-stu-id="b456b-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="b456b-114">à Pointeur vers la longueur de la chaîne du chemin d’accès du répertoire.</span><span class="sxs-lookup"><span data-stu-id="b456b-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="b456b-115">à Mémoire tampon qui contient le numéro de version du runtime en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="b456b-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="b456b-116">dans Longueur de la mémoire tampon de la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="b456b-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="b456b-117">à Pointeur vers la longueur de la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="b456b-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b456b-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b456b-118">Return Value</span></span>  
 <span data-ttu-id="b456b-119">Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="b456b-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="b456b-120">Code de retour</span><span class="sxs-lookup"><span data-stu-id="b456b-120">Return code</span></span>|<span data-ttu-id="b456b-121">Description</span><span class="sxs-lookup"><span data-stu-id="b456b-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b456b-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="b456b-122">S_OK</span></span>|<span data-ttu-id="b456b-123">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="b456b-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="b456b-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b456b-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="b456b-125">La mémoire tampon du répertoire n’est pas assez grande pour stocker le chemin d’accès au répertoire.</span><span class="sxs-lookup"><span data-stu-id="b456b-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="b456b-126">ou</span><span class="sxs-lookup"><span data-stu-id="b456b-126">- or -</span></span><br /><br /> <span data-ttu-id="b456b-127">La mémoire tampon de version n’est pas assez grande pour stocker la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="b456b-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b456b-128">Notes</span><span class="sxs-lookup"><span data-stu-id="b456b-128">Remarks</span></span>  
 <span data-ttu-id="b456b-129">La méthode `GetRequestedRuntimeInfo` retourne des informations d’exécution sur la version chargée dans le processus, qui n’est pas nécessairement la version la plus récente installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b456b-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="b456b-130">Dans la version 2,0 de .NET Framework, vous pouvez obtenir des informations sur la dernière version installée à l’aide de la méthode `GetRequestedRuntimeInfo` comme suit :</span><span class="sxs-lookup"><span data-stu-id="b456b-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="b456b-131">Spécifiez les paramètres `pExe`, `pwszVersion`et `pConfigurationFile` comme null.</span><span class="sxs-lookup"><span data-stu-id="b456b-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="b456b-132">Spécifiez l’indicateur RUNTIME_INFO_UPGRADE_VERSION dans les énumérations `RUNTIME_INFO_FLAGS` pour le paramètre `runtimeInfoFlags`.</span><span class="sxs-lookup"><span data-stu-id="b456b-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="b456b-133">La méthode `GetRequestedRuntimeInfo` ne retourne pas la dernière version du CLR dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="b456b-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="b456b-134">Un fichier de configuration d’application qui spécifie le chargement d’une version particulière du CLR existe.</span><span class="sxs-lookup"><span data-stu-id="b456b-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="b456b-135">Notez que le .NET Framework utilisera le fichier de configuration, même si vous spécifiez NULL pour le paramètre `pConfigurationFile`.</span><span class="sxs-lookup"><span data-stu-id="b456b-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="b456b-136">La méthode [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) était appelée en spécifiant une version antérieure du CLR.</span><span class="sxs-lookup"><span data-stu-id="b456b-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="b456b-137">Une application qui a été compilée pour une version antérieure du CLR est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b456b-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="b456b-138">Pour le paramètre `runtimeInfoFlags`, vous ne pouvez spécifier qu’une seule des constantes d’architecture de l’énumération `RUNTIME_INFO_FLAGS` à la fois :</span><span class="sxs-lookup"><span data-stu-id="b456b-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="b456b-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="b456b-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="b456b-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="b456b-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="b456b-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="b456b-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b456b-142">spécifications</span><span class="sxs-lookup"><span data-stu-id="b456b-142">Requirements</span></span>  
 <span data-ttu-id="b456b-143">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b456b-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b456b-144">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b456b-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b456b-145">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b456b-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b456b-146">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b456b-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b456b-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b456b-147">See also</span></span>

- [<span data-ttu-id="b456b-148">GetRequestedRuntimeVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="b456b-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="b456b-149">GetVersionFromProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="b456b-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="b456b-150">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="b456b-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
