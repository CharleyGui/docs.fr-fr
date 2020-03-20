---
title: ICLRValidator::Validate, méthode
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178060"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="e55d9-102">ICLRValidator::Validate, méthode</span><span class="sxs-lookup"><span data-stu-id="e55d9-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="e55d9-103">Valide la langue intermédiaire portable exécutable (PE) ou Microsoft (MSIL) dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="e55d9-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e55d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e55d9-104">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="e55d9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e55d9-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="e55d9-106">[dans] Un pointeur `IVEHandler` à une instance qui gère les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="e55d9-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="e55d9-107">[dans] L’identifiant pour <xref:System.AppDomain>le courant .</span><span class="sxs-lookup"><span data-stu-id="e55d9-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="e55d9-108">[dans] Une combinaison de valeurs [ValidatorFlags,](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) indiquant le type de validation qui doit être effectuée.</span><span class="sxs-lookup"><span data-stu-id="e55d9-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="e55d9-109">[dans] Le nombre maximum d’erreurs à autoriser avant de sortir de la validation.</span><span class="sxs-lookup"><span data-stu-id="e55d9-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="e55d9-110">[in] Inutilisé.</span><span class="sxs-lookup"><span data-stu-id="e55d9-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="e55d9-111">[dans] Le nom du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="e55d9-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="e55d9-112">[dans] Un pointeur vers le tampon de fichier.</span><span class="sxs-lookup"><span data-stu-id="e55d9-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="e55d9-113">[dans] La taille, dans les octets, du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="e55d9-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e55d9-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e55d9-114">Return Value</span></span>  
  
|<span data-ttu-id="e55d9-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e55d9-115">HRESULT</span></span>|<span data-ttu-id="e55d9-116">Description</span><span class="sxs-lookup"><span data-stu-id="e55d9-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e55d9-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="e55d9-117">S_OK</span></span>|<span data-ttu-id="e55d9-118">`Validate`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e55d9-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="e55d9-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e55d9-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e55d9-120">L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="e55d9-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e55d9-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e55d9-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e55d9-122">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="e55d9-122">The call timed out.</span></span>|  
|<span data-ttu-id="e55d9-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e55d9-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e55d9-124">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="e55d9-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e55d9-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e55d9-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e55d9-126">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="e55d9-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e55d9-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e55d9-127">E_FAIL</span></span>|<span data-ttu-id="e55d9-128">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e55d9-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e55d9-129">Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e55d9-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e55d9-130">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e55d9-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e55d9-131">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e55d9-131">Requirements</span></span>  
 <span data-ttu-id="e55d9-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e55d9-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e55d9-133">**En-tête:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="e55d9-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="e55d9-134">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e55d9-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e55d9-135">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e55d9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e55d9-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e55d9-136">See also</span></span>

- [<span data-ttu-id="e55d9-137">ICLRValidator, interface</span><span class="sxs-lookup"><span data-stu-id="e55d9-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
