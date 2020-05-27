---
title: LockClrVersion, fonction
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
ms.openlocfilehash: 09bcebfdcfea3d5728d404cdb6b5fb170a5432c3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008493"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="41e99-102">LockClrVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="41e99-102">LockClrVersion Function</span></span>
<span data-ttu-id="41e99-103">Permet à l’hôte de déterminer la version du common language runtime (CLR) qui sera utilisée dans le processus avant d’initialiser explicitement le CLR.</span><span class="sxs-lookup"><span data-stu-id="41e99-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="41e99-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="41e99-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e99-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41e99-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41e99-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41e99-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="41e99-107">dans Fonction à appeler par le CLR lors de l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="41e99-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="41e99-108">dans Fonction à appeler par l’hôte pour informer le CLR que l’initialisation démarre.</span><span class="sxs-lookup"><span data-stu-id="41e99-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="41e99-109">dans Fonction à appeler par l’hôte pour informer le CLR que l’initialisation est terminée.</span><span class="sxs-lookup"><span data-stu-id="41e99-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41e99-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="41e99-110">Return Value</span></span>  
 <span data-ttu-id="41e99-111">Cette méthode retourne des codes d’erreur COM standard, tels que définis dans WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="41e99-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="41e99-112">Code de retour</span><span class="sxs-lookup"><span data-stu-id="41e99-112">Return code</span></span>|<span data-ttu-id="41e99-113">Description</span><span class="sxs-lookup"><span data-stu-id="41e99-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="41e99-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="41e99-114">S_OK</span></span>|<span data-ttu-id="41e99-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="41e99-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="41e99-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="41e99-116">E_INVALIDARG</span></span>|<span data-ttu-id="41e99-117">Un ou plusieurs arguments ont la valeur null.</span><span class="sxs-lookup"><span data-stu-id="41e99-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41e99-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="41e99-118">Remarks</span></span>  
 <span data-ttu-id="41e99-119">L’hôte appelle `LockClrVersion` avant d’initialiser le CLR.</span><span class="sxs-lookup"><span data-stu-id="41e99-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="41e99-120">`LockClrVersion`prend trois paramètres, qui sont tous des rappels de type [FLockClrVersionCallback (](flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="41e99-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="41e99-121">Ce type est défini comme suit.</span><span class="sxs-lookup"><span data-stu-id="41e99-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="41e99-122">Les étapes suivantes se produisent lors de l’initialisation du Runtime :</span><span class="sxs-lookup"><span data-stu-id="41e99-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="41e99-123">L’hôte appelle [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ou l’une des autres fonctions d’initialisation du Runtime.</span><span class="sxs-lookup"><span data-stu-id="41e99-123">The host calls [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="41e99-124">L’hôte peut également initialiser le runtime à l’aide de l’activation d’objet COM.</span><span class="sxs-lookup"><span data-stu-id="41e99-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="41e99-125">Le runtime appelle la fonction spécifiée par le `hostCallback` paramètre.</span><span class="sxs-lookup"><span data-stu-id="41e99-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="41e99-126">La fonction spécifiée par `hostCallback` effectue ensuite la séquence d’appels suivante :</span><span class="sxs-lookup"><span data-stu-id="41e99-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="41e99-127">Fonction spécifiée par le `pBeginHostSetup` paramètre.</span><span class="sxs-lookup"><span data-stu-id="41e99-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="41e99-128">`CorBindToRuntimeEx`(ou une autre fonction d’initialisation du Runtime).</span><span class="sxs-lookup"><span data-stu-id="41e99-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="41e99-129">[ICLRRuntimeHost :: SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="41e99-129">[ICLRRuntimeHost::SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="41e99-130">[ICLRRuntimeHost :: Start](iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="41e99-130">[ICLRRuntimeHost::Start](iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="41e99-131">Fonction spécifiée par le `pEndHostSetup` paramètre.</span><span class="sxs-lookup"><span data-stu-id="41e99-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="41e99-132">Tous les appels de `pBeginHostSetup` à `pEndHostSetup` doivent se produire sur un thread ou une fibre unique, avec la même pile logique.</span><span class="sxs-lookup"><span data-stu-id="41e99-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="41e99-133">Ce thread peut être différent du thread sur lequel `hostCallback` est appelé.</span><span class="sxs-lookup"><span data-stu-id="41e99-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e99-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="41e99-134">Requirements</span></span>  
 <span data-ttu-id="41e99-135">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41e99-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e99-136">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41e99-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41e99-137">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="41e99-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41e99-138">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41e99-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e99-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41e99-139">See also</span></span>

- [<span data-ttu-id="41e99-140">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="41e99-140">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
