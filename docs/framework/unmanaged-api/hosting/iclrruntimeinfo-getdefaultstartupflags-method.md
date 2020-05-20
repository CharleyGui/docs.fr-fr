---
title: ICLRRuntimeInfo::GetDefaultStartupFlags, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
ms.openlocfilehash: 8513787f48ae89632816face386bbcda20555dac
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703888"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="9dc7b-102">ICLRRuntimeInfo::GetDefaultStartupFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="9dc7b-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="9dc7b-103">Obtient les indicateurs de démarrage et le fichier de configuration d’hôte qui sera utilisé pour démarrer le Runtime.</span><span class="sxs-lookup"><span data-stu-id="9dc7b-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dc7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dc7b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9dc7b-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="9dc7b-106">à Pointeur vers les indicateurs de démarrage de l’hôte qui sont actuellement définis.</span><span class="sxs-lookup"><span data-stu-id="9dc7b-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="9dc7b-107">à Pointeur vers le chemin d’accès du répertoire du fichier de configuration hôte actuel.</span><span class="sxs-lookup"><span data-stu-id="9dc7b-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="9dc7b-108">[in, out] En entrée, taille de `pwzHostConfigFile` , pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="9dc7b-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="9dc7b-109">Si `pwzHostConfigFile` a la valeur null, la méthode retourne la taille requise de `pwzHostConfigFile` pour la pré-allocation.</span><span class="sxs-lookup"><span data-stu-id="9dc7b-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9dc7b-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9dc7b-110">Return Value</span></span>  
 <span data-ttu-id="9dc7b-111">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT qui indiquent un échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9dc7b-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9dc7b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9dc7b-112">HRESULT</span></span>|<span data-ttu-id="9dc7b-113">Description</span><span class="sxs-lookup"><span data-stu-id="9dc7b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9dc7b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9dc7b-114">S_OK</span></span>|<span data-ttu-id="9dc7b-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="9dc7b-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dc7b-116">Notes</span><span class="sxs-lookup"><span data-stu-id="9dc7b-116">Remarks</span></span>  
 <span data-ttu-id="9dc7b-117">Cette méthode retourne les valeurs d’indicateur par défaut ( `STARTUP_CONCURRENT_GC` et `NULL` ), ou les valeurs fournies par un appel précédent à la [méthode ICLRRuntimeInfo :: SetDefaultStartupFlags,](iclrruntimeinfo-setdefaultstartupflags-method.md), ou les valeurs définies par l’une des `CorBind*` méthodes si elles sont liées à ce Runtime.</span><span class="sxs-lookup"><span data-stu-id="9dc7b-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dc7b-118">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="9dc7b-118">Requirements</span></span>  
 <span data-ttu-id="9dc7b-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dc7b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dc7b-120">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="9dc7b-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9dc7b-121">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9dc7b-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9dc7b-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dc7b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc7b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dc7b-123">See also</span></span>

- [<span data-ttu-id="9dc7b-124">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="9dc7b-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="9dc7b-125">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="9dc7b-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="9dc7b-126">Hébergement</span><span class="sxs-lookup"><span data-stu-id="9dc7b-126">Hosting</span></span>](index.md)
