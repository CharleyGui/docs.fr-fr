---
title: IValidator::Validate, méthode
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 840a3779ca5692787c2c352db60a29d6a4d4ba4f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768589"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="2dce2-102">IValidator::Validate, méthode</span><span class="sxs-lookup"><span data-stu-id="2dce2-102">IValidator::Validate Method</span></span>
<span data-ttu-id="2dce2-103">Valide le spécifié exécutable portable (PE) ou un fichier Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="2dce2-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dce2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2dce2-104">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2dce2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2dce2-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="2dce2-106">[in] Un pointeur vers un `IVEHandler` instance qui gère les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="2dce2-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="2dce2-107">[in] Pointeur vers le domaine d’application dans lequel le fichier est chargé.</span><span class="sxs-lookup"><span data-stu-id="2dce2-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="2dce2-108">[in] Une combinaison au niveau du bit de [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) valeurs indiquant les validations qui doivent être effectuées.</span><span class="sxs-lookup"><span data-stu-id="2dce2-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="2dce2-109">[in] Le nombre maximal d’erreurs autorisées avant de quitter la validation.</span><span class="sxs-lookup"><span data-stu-id="2dce2-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="2dce2-110">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="2dce2-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="2dce2-111">[in] Chaîne qui spécifie le nom du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="2dce2-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="2dce2-112">[in] Pointeur vers la mémoire tampon dans lequel le fichier est stocké.</span><span class="sxs-lookup"><span data-stu-id="2dce2-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="2dce2-113">[in] La taille, en octets, du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="2dce2-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dce2-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2dce2-114">Requirements</span></span>  
 <span data-ttu-id="2dce2-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dce2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dce2-116">**En-tête :** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="2dce2-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="2dce2-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2dce2-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2dce2-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dce2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
