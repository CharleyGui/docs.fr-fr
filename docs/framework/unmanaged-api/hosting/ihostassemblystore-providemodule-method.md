---
title: IHostAssemblyStore::ProvideModule, méthode
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
ms.openlocfilehash: 35805d277774e1de03bb7dee1740a2e1305a97c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732994"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="8e9f5-102">IHostAssemblyStore::ProvideModule, méthode</span><span class="sxs-lookup"><span data-stu-id="8e9f5-102">IHostAssemblyStore::ProvideModule Method</span></span>

<span data-ttu-id="8e9f5-103">Résout un module dans un assembly ou un fichier de ressources lié (mais pas incorporé).</span><span class="sxs-lookup"><span data-stu-id="8e9f5-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e9f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e9f5-104">Syntax</span></span>  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e9f5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8e9f5-105">Parameters</span></span>  

 `pBindInfo`  
 <span data-ttu-id="8e9f5-106">dans Pointeur vers une instance [ModuleBindInfo](modulebindinfo-structure.md) qui décrit le nom du module, de l' <xref:System.AppDomain> assembly et du nom du module demandés.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-106">[in] A pointer to a [ModuleBindInfo](modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="8e9f5-107">à Pointeur vers un identificateur unique pour le `IStream` contenant le module chargé.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="8e9f5-108">à Pointeur vers l’adresse d’un `IStream` objet, qui contient l’image PE (Portable Executable) à charger, ou null si le module est introuvable.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="8e9f5-109">à Pointeur vers l’adresse d’un `IStream` objet, qui contient les informations de débogage de programme pour le module demandé, ou null si le fichier. pdb est introuvable.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e9f5-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8e9f5-110">Return Value</span></span>  
  
|<span data-ttu-id="8e9f5-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e9f5-111">HRESULT</span></span>|<span data-ttu-id="8e9f5-112">Description</span><span class="sxs-lookup"><span data-stu-id="8e9f5-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e9f5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e9f5-113">S_OK</span></span>|<span data-ttu-id="8e9f5-114">`ProvideModule` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="8e9f5-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8e9f5-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8e9f5-116">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8e9f5-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8e9f5-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8e9f5-118">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-118">The call timed out.</span></span>|  
|<span data-ttu-id="8e9f5-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8e9f5-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8e9f5-120">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8e9f5-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8e9f5-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8e9f5-122">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8e9f5-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8e9f5-123">E_FAIL</span></span>|<span data-ttu-id="8e9f5-124">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8e9f5-125">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8e9f5-126">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8e9f5-127">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="8e9f5-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="8e9f5-128">L’assembly ou la ressource liée demandé est introuvable.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="8e9f5-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8e9f5-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8e9f5-130">`pdwModuleId` n’est pas assez grand pour contenir l’identificateur que l’hôte souhaite retourner.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e9f5-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="8e9f5-131">Remarks</span></span>  

 <span data-ttu-id="8e9f5-132">La valeur d’identité retournée pour `pdwModuleId` est spécifiée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="8e9f5-133">Les identificateurs doivent être uniques dans la durée de vie d’un processus.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="8e9f5-134">Le CLR utilise cette valeur comme identificateur unique pour le flux associé.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="8e9f5-135">Il vérifie chaque valeur par rapport aux valeurs `pAssemblyId` retournées par les appels à [ProvideAssembly](ihostassemblystore-provideassembly-method.md) et aux valeurs `pdwModuleId` retournées par d’autres appels à `ProvideModule` .</span><span class="sxs-lookup"><span data-stu-id="8e9f5-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="8e9f5-136">Si l’hôte retourne la même valeur d’identificateur pour un autre `IStream` , le CLR vérifie si le contenu de ce flux a déjà été mappé.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="8e9f5-137">Si c’est le cas, le CLR charge la copie existante de l’image au lieu d’en mapper une nouvelle.</span><span class="sxs-lookup"><span data-stu-id="8e9f5-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="8e9f5-138">Par conséquent, l’identificateur ne doit pas non plus chevaucher les identificateurs d’assembly retournés par `ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="8e9f5-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e9f5-139">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8e9f5-139">Requirements</span></span>  

 <span data-ttu-id="8e9f5-140">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e9f5-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e9f5-141">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8e9f5-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e9f5-142">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8e9f5-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e9f5-143">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e9f5-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e9f5-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e9f5-144">See also</span></span>

- [<span data-ttu-id="8e9f5-145">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="8e9f5-145">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8e9f5-146">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="8e9f5-146">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="8e9f5-147">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="8e9f5-147">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
