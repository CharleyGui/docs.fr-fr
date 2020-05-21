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
ms.openlocfilehash: ccf48b6aea25bd602b55727c2e5958811702f6bf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762576"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="d4588-102">ICLRRuntimeInfo::GetVersionString, méthode</span><span class="sxs-lookup"><span data-stu-id="d4588-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="d4588-103">Obtient les informations de version de common language runtime (CLR) associées à une interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) donnée.</span><span class="sxs-lookup"><span data-stu-id="d4588-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="d4588-104">Cette méthode remplace les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d4588-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="d4588-105">GetRequestedRuntimeInfo,</span><span class="sxs-lookup"><span data-stu-id="d4588-105">GetRequestedRuntimeInfo</span></span>](getrequestedruntimeinfo-function.md)  
  
- [<span data-ttu-id="d4588-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="d4588-106">GetRequestedRuntimeVersion</span></span>](getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="d4588-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4588-107">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4588-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4588-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="d4588-109">à Version de compilation .NET Framework au format «v*A*. *B*[.\* X\*]».</span><span class="sxs-lookup"><span data-stu-id="d4588-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="d4588-110">*A*, *B*et *X* sont des nombres décimaux qui correspondent à la version principale, à la version mineure et au numéro de Build.</span><span class="sxs-lookup"><span data-stu-id="d4588-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="d4588-111">*X* est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d4588-111">*X* is optional.</span></span> <span data-ttu-id="d4588-112">Si *X* n’est pas présent, il n’y a aucun point final.</span><span class="sxs-lookup"><span data-stu-id="d4588-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4588-113">Ce paramètre doit correspondre au nom de répertoire de la version .NET Framework, tel qu’il apparaît sous C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="d4588-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="d4588-114">Les exemples de valeurs sont « v 1.0.3705 », « v 1.1.4322 », « v 2.0.50727 » et « v 4.0 ». *x*», où *x* dépend du numéro de Build installé.</span><span class="sxs-lookup"><span data-stu-id="d4588-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="d4588-115">Notez que le préfixe « v » est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d4588-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="d4588-116">[in, out] Spécifie la taille de `pwzBuffer` pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="d4588-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="d4588-117">Si `pwzBuffer` a `null` la valeur, `pchBuffer` retourne la taille requise de `pwzBuffer` pour autoriser la préallocation.</span><span class="sxs-lookup"><span data-stu-id="d4588-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4588-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d4588-118">Return Value</span></span>  
 <span data-ttu-id="d4588-119">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d4588-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d4588-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4588-120">HRESULT</span></span>|<span data-ttu-id="d4588-121">Description</span><span class="sxs-lookup"><span data-stu-id="d4588-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4588-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4588-122">S_OK</span></span>|<span data-ttu-id="d4588-123">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="d4588-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="d4588-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d4588-124">E_POINTER</span></span>|<span data-ttu-id="d4588-125">`pwzBuffer` ou `pchBuffer` est null.</span><span class="sxs-lookup"><span data-stu-id="d4588-125">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4588-126">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="d4588-126">Requirements</span></span>  
 <span data-ttu-id="d4588-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4588-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4588-128">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="d4588-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d4588-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d4588-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4588-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4588-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4588-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4588-131">See also</span></span>

- [<span data-ttu-id="d4588-132">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="d4588-132">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="d4588-133">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="d4588-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="d4588-134">Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="d4588-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="d4588-135">Hébergement</span><span class="sxs-lookup"><span data-stu-id="d4588-135">Hosting</span></span>](index.md)
