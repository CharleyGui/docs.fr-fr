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
ms.openlocfilehash: 4ce50f7706583f291d2e6a141d40ab6dd3e4b3e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674383"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="a705b-102">ICLRValidator::Validate, méthode</span><span class="sxs-lookup"><span data-stu-id="a705b-102">ICLRValidator::Validate Method</span></span>

<span data-ttu-id="a705b-103">Valide l’exécutable portable (PE) ou le langage MSIL (Microsoft Intermediate Language) dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="a705b-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a705b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a705b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a705b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a705b-105">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="a705b-106">dans Pointeur vers une `IVEHandler` instance qui gère les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="a705b-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="a705b-107">dans Identificateur du actuel <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="a705b-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="a705b-108">dans Combinaison de valeurs [ValidatorFlags,](validatorflags-enumeration.md) indiquant le type de validation à effectuer.</span><span class="sxs-lookup"><span data-stu-id="a705b-108">[in] A combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="a705b-109">dans Nombre maximal d’erreurs à autoriser avant de quitter la validation.</span><span class="sxs-lookup"><span data-stu-id="a705b-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="a705b-110">[in] Inutilisé.</span><span class="sxs-lookup"><span data-stu-id="a705b-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="a705b-111">dans Nom du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="a705b-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="a705b-112">dans Pointeur vers la mémoire tampon de fichier.</span><span class="sxs-lookup"><span data-stu-id="a705b-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="a705b-113">dans Taille, en octets, du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="a705b-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a705b-114">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a705b-114">Return Value</span></span>  
  
|<span data-ttu-id="a705b-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a705b-115">HRESULT</span></span>|<span data-ttu-id="a705b-116">Description</span><span class="sxs-lookup"><span data-stu-id="a705b-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a705b-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="a705b-117">S_OK</span></span>|<span data-ttu-id="a705b-118">`Validate` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a705b-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="a705b-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a705b-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a705b-120">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="a705b-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a705b-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a705b-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a705b-122">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="a705b-122">The call timed out.</span></span>|  
|<span data-ttu-id="a705b-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a705b-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a705b-124">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="a705b-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a705b-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a705b-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a705b-126">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="a705b-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a705b-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a705b-127">E_FAIL</span></span>|<span data-ttu-id="a705b-128">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a705b-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a705b-129">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a705b-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a705b-130">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a705b-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a705b-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a705b-131">Requirements</span></span>  

 <span data-ttu-id="a705b-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a705b-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a705b-133">**En-tête :** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="a705b-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="a705b-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a705b-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a705b-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a705b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a705b-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a705b-136">See also</span></span>

- [<span data-ttu-id="a705b-137">ICLRValidator, interface</span><span class="sxs-lookup"><span data-stu-id="a705b-137">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
