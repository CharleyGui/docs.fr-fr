---
title: ICLRRuntimeInfo::GetVersionString, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c80b85171ac9dab270a267cf2dd33a9f1c23d60
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650308"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="90067-102">ICLRRuntimeInfo::GetVersionString, méthode</span><span class="sxs-lookup"><span data-stu-id="90067-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="90067-103">Obtient les informations de version du common language runtime (CLR) associées à une donnée [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="90067-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="90067-104">Cette méthode remplace les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="90067-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="90067-105">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="90067-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
- [<span data-ttu-id="90067-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="90067-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="90067-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90067-107">Syntax</span></span>  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90067-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="90067-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="90067-109">[out] La version de compilation .NET Framework dans le format « v*A*. *B*[. *X*] ».</span><span class="sxs-lookup"><span data-stu-id="90067-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="90067-110">*Un*, *B*, et *X* sont des nombres décimaux qui correspondent à la version principale, la version secondaire et le numéro de build.</span><span class="sxs-lookup"><span data-stu-id="90067-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="90067-111">*X* est facultatif.</span><span class="sxs-lookup"><span data-stu-id="90067-111">*X* is optional.</span></span> <span data-ttu-id="90067-112">Si *X* est absent, il n’est pas de point final.</span><span class="sxs-lookup"><span data-stu-id="90067-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90067-113">Ce paramètre doit correspondre au nom de répertoire pour la version de .NET Framework, tel qu’il apparaît sous C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="90067-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="90067-114">Exemples de valeurs : « v1.0.3705 », « v1.1.4322 », « v2.0.50727 » et « v4.0. *x*», où *x* varie selon le numéro de build installé.</span><span class="sxs-lookup"><span data-stu-id="90067-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="90067-115">Notez que le préfixe « v » est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="90067-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="90067-116">[in, out] Spécifie la taille du `pwzBuffer` pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="90067-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="90067-117">Si `pwzBuffer` est `null`, `pchBuffer` retourne la taille requise de `pwzBuffer` pour autoriser la pré-allocation.</span><span class="sxs-lookup"><span data-stu-id="90067-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90067-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="90067-118">Return Value</span></span>  
 <span data-ttu-id="90067-119">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="90067-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="90067-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90067-120">HRESULT</span></span>|<span data-ttu-id="90067-121">Description</span><span class="sxs-lookup"><span data-stu-id="90067-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90067-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="90067-122">S_OK</span></span>|<span data-ttu-id="90067-123">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="90067-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="90067-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="90067-124">E_POINTER</span></span>|<span data-ttu-id="90067-125">`pwzBuffer` ou `pchBuffer` est null.</span><span class="sxs-lookup"><span data-stu-id="90067-125">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90067-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="90067-126">Requirements</span></span>  
 <span data-ttu-id="90067-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90067-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90067-128">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="90067-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="90067-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90067-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90067-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90067-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90067-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90067-131">See also</span></span>

- [<span data-ttu-id="90067-132">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="90067-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="90067-133">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="90067-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="90067-134">Interfaces d’hébergement CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="90067-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="90067-135">Hébergement</span><span class="sxs-lookup"><span data-stu-id="90067-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
