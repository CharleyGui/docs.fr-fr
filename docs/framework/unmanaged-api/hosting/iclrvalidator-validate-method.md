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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5fbf83690f616556774e8f279e1077fccdb8baf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779913"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="0eada-102">ICLRValidator::Validate, méthode</span><span class="sxs-lookup"><span data-stu-id="0eada-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="0eada-103">Valide le fichier exécutable portable (PE) ou Microsoft intermediate language (MSIL) dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="0eada-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eada-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0eada-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0eada-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0eada-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="0eada-106">[in] Un pointeur vers un `IVEHandler` instance qui gère les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="0eada-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="0eada-107">[in] L’identificateur actuel <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0eada-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="0eada-108">[in] Une combinaison de [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) valeurs indiquant le genre de validation doit être effectuée.</span><span class="sxs-lookup"><span data-stu-id="0eada-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="0eada-109">[in] Le nombre maximal d’erreurs autorisées avant de quitter la validation.</span><span class="sxs-lookup"><span data-stu-id="0eada-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="0eada-110">[in] Inutilisé.</span><span class="sxs-lookup"><span data-stu-id="0eada-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="0eada-111">[in] Le nom du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="0eada-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="0eada-112">[in] Pointeur vers la mémoire tampon de fichier.</span><span class="sxs-lookup"><span data-stu-id="0eada-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="0eada-113">[in] La taille, en octets, du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="0eada-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0eada-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0eada-114">Return Value</span></span>  
  
|<span data-ttu-id="0eada-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0eada-115">HRESULT</span></span>|<span data-ttu-id="0eada-116">Description</span><span class="sxs-lookup"><span data-stu-id="0eada-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0eada-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="0eada-117">S_OK</span></span>|<span data-ttu-id="0eada-118">`Validate` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0eada-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="0eada-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0eada-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0eada-120">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="0eada-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0eada-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0eada-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0eada-122">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="0eada-122">The call timed out.</span></span>|  
|<span data-ttu-id="0eada-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0eada-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0eada-124">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="0eada-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0eada-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0eada-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0eada-126">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="0eada-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0eada-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0eada-127">E_FAIL</span></span>|<span data-ttu-id="0eada-128">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0eada-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0eada-129">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="0eada-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0eada-130">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0eada-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0eada-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0eada-131">Requirements</span></span>  
 <span data-ttu-id="0eada-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0eada-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eada-133">**En-tête :** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="0eada-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="0eada-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0eada-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0eada-135">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eada-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eada-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0eada-136">See also</span></span>

- [<span data-ttu-id="0eada-137">ICLRValidator, interface</span><span class="sxs-lookup"><span data-stu-id="0eada-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
