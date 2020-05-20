---
title: ICLRMetaHost::GetVersionFromFile, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
ms.openlocfilehash: 40efc256dde13d645d43f50bb574d73b5668919c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703736"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="f704a-102">ICLRMetaHost::GetVersionFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="f704a-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="f704a-103">Obtient la version de compilation .NET Framework d’origine d’un assembly (stockée dans les métadonnées), en fonction de son chemin d’accès au fichier.</span><span class="sxs-lookup"><span data-stu-id="f704a-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="f704a-104">Cette méthode remplace la fonction [GetFileVersion,](getfileversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="f704a-104">This method supersedes the [GetFileVersion](getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f704a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f704a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f704a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f704a-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="f704a-107">dans Chemin d’accès complet au fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="f704a-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="f704a-108">à Version de compilation .NET Framework stockée dans les métadonnées, au format «v*A*. *B*[.\* X\*]».</span><span class="sxs-lookup"><span data-stu-id="f704a-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="f704a-109">*A*, *B*et *X* sont des nombres décimaux qui correspondent à la version principale, à la version mineure et au numéro de Build.</span><span class="sxs-lookup"><span data-stu-id="f704a-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="f704a-110">La longueur de cette chaîne est limitée à MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="f704a-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f704a-111">Cette sortie correspond au nom du répertoire de la version .NET Framework, tel qu’il apparaît sous C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="f704a-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="f704a-112">Les exemples de valeurs sont « v 1.0.3705 », « v 1.1.4322 », « v 2.0.50727 » et « v 4.0 ». *X*», où *x* dépend du numéro de Build installé.</span><span class="sxs-lookup"><span data-stu-id="f704a-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="f704a-113">Notez que le préfixe « v » est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f704a-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="f704a-114">[in, out] Taille de `pwzbuffer` pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="f704a-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f704a-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f704a-115">Return Value</span></span>  
 <span data-ttu-id="f704a-116">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f704a-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f704a-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f704a-117">HRESULT</span></span>|<span data-ttu-id="f704a-118">Description</span><span class="sxs-lookup"><span data-stu-id="f704a-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f704a-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="f704a-119">S_OK</span></span>|<span data-ttu-id="f704a-120">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="f704a-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="f704a-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f704a-121">E_POINTER</span></span>|<span data-ttu-id="f704a-122">`pwzbuffer` ou `pcchBuffer` est null.</span><span class="sxs-lookup"><span data-stu-id="f704a-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="f704a-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="f704a-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="f704a-124">La mémoire tampon est insuffisante.</span><span class="sxs-lookup"><span data-stu-id="f704a-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f704a-125">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="f704a-125">Requirements</span></span>  
 <span data-ttu-id="f704a-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f704a-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f704a-127">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="f704a-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f704a-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f704a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f704a-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f704a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f704a-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f704a-130">See also</span></span>

- [<span data-ttu-id="f704a-131">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="f704a-131">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="f704a-132">Hébergement</span><span class="sxs-lookup"><span data-stu-id="f704a-132">Hosting</span></span>](index.md)
