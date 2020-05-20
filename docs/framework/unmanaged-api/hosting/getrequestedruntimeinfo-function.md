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
ms.openlocfilehash: 0efda458d51677fcd16140cd0f0a835b76c20173
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617176"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="e9570-102">GetRequestedRuntimeInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="e9570-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="e9570-103">Obtient les informations de version et de répertoire relatives au common language runtime (CLR) demandé par une application.</span><span class="sxs-lookup"><span data-stu-id="e9570-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="e9570-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e9570-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9570-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9570-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e9570-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e9570-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="e9570-107">dans Nom de l’application.</span><span class="sxs-lookup"><span data-stu-id="e9570-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="e9570-108">dans Chaîne spécifiant le numéro de version du Runtime.</span><span class="sxs-lookup"><span data-stu-id="e9570-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="e9570-109">dans Nom du fichier de configuration associé à `pExe` .</span><span class="sxs-lookup"><span data-stu-id="e9570-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="e9570-110">dans Une ou plusieurs des [STARTUP_FLAGS](startup-flags-enumeration.md) valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="e9570-110">[in] One or more of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="e9570-111">dans Une ou plusieurs des [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="e9570-111">[in] One or more of the [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="e9570-112">à Mémoire tampon qui contient le chemin d’accès au répertoire du runtime une fois l’opération terminée.</span><span class="sxs-lookup"><span data-stu-id="e9570-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="e9570-113">dans Longueur de la mémoire tampon de répertoire.</span><span class="sxs-lookup"><span data-stu-id="e9570-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="e9570-114">à Pointeur vers la longueur de la chaîne du chemin d’accès du répertoire.</span><span class="sxs-lookup"><span data-stu-id="e9570-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="e9570-115">à Mémoire tampon qui contient le numéro de version du runtime en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="e9570-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="e9570-116">dans Longueur de la mémoire tampon de la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="e9570-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="e9570-117">à Pointeur vers la longueur de la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="e9570-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9570-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e9570-118">Return Value</span></span>  
 <span data-ttu-id="e9570-119">Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="e9570-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="e9570-120">Code de retour</span><span class="sxs-lookup"><span data-stu-id="e9570-120">Return code</span></span>|<span data-ttu-id="e9570-121">Description</span><span class="sxs-lookup"><span data-stu-id="e9570-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e9570-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9570-122">S_OK</span></span>|<span data-ttu-id="e9570-123">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="e9570-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="e9570-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e9570-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e9570-125">La mémoire tampon du répertoire n’est pas assez grande pour stocker le chemin d’accès au répertoire.</span><span class="sxs-lookup"><span data-stu-id="e9570-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="e9570-126">- ou -</span><span class="sxs-lookup"><span data-stu-id="e9570-126">- or -</span></span><br /><br /> <span data-ttu-id="e9570-127">La mémoire tampon de version n’est pas assez grande pour stocker la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="e9570-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9570-128">Notes</span><span class="sxs-lookup"><span data-stu-id="e9570-128">Remarks</span></span>  
 <span data-ttu-id="e9570-129">La `GetRequestedRuntimeInfo` méthode retourne des informations d’exécution sur la version chargée dans le processus, qui n’est pas nécessairement la version la plus récente installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e9570-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="e9570-130">Dans la version 2,0 de .NET Framework, vous pouvez obtenir des informations sur la dernière version installée à l’aide de la `GetRequestedRuntimeInfo` méthode comme suit :</span><span class="sxs-lookup"><span data-stu-id="e9570-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="e9570-131">Spécifiez `pExe` les `pwszVersion` paramètres, et `pConfigurationFile` comme null.</span><span class="sxs-lookup"><span data-stu-id="e9570-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="e9570-132">Spécifiez l’indicateur RUNTIME_INFO_UPGRADE_VERSION dans les `RUNTIME_INFO_FLAGS` énumérations du `runtimeInfoFlags` paramètre.</span><span class="sxs-lookup"><span data-stu-id="e9570-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="e9570-133">La `GetRequestedRuntimeInfo` méthode ne retourne pas la dernière version du CLR dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="e9570-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="e9570-134">Un fichier de configuration d’application qui spécifie le chargement d’une version particulière du CLR existe.</span><span class="sxs-lookup"><span data-stu-id="e9570-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="e9570-135">Notez que le .NET Framework utilisera le fichier de configuration, même si vous spécifiez NULL pour le `pConfigurationFile` paramètre.</span><span class="sxs-lookup"><span data-stu-id="e9570-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="e9570-136">La méthode [CorBindToRuntimeEx](corbindtoruntimeex-function.md) était appelée en spécifiant une version antérieure du CLR.</span><span class="sxs-lookup"><span data-stu-id="e9570-136">The [CorBindToRuntimeEx](corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="e9570-137">Une application qui a été compilée pour une version antérieure du CLR est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e9570-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="e9570-138">Pour le `runtimeInfoFlags` paramètre, vous ne pouvez spécifier qu’une seule des constantes d’architecture de l' `RUNTIME_INFO_FLAGS` énumération à la fois :</span><span class="sxs-lookup"><span data-stu-id="e9570-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="e9570-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="e9570-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="e9570-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="e9570-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="e9570-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="e9570-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9570-142">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="e9570-142">Requirements</span></span>  
 <span data-ttu-id="e9570-143">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9570-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9570-144">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e9570-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9570-145">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e9570-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9570-146">**Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9570-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9570-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9570-147">See also</span></span>

- [<span data-ttu-id="e9570-148">GetRequestedRuntimeVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="e9570-148">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="e9570-149">GetVersionFromProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="e9570-149">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="e9570-150">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="e9570-150">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
