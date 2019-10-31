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
ms.openlocfilehash: 8ae47eac713fbee30ea543538957b12460b8e1fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123275"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="04956-102">IValidator::Validate, méthode</span><span class="sxs-lookup"><span data-stu-id="04956-102">IValidator::Validate Method</span></span>
<span data-ttu-id="04956-103">Valide le fichier exécutable portable (PE) ou le fichier MSIL (Microsoft Intermediate Language) spécifié.</span><span class="sxs-lookup"><span data-stu-id="04956-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04956-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04956-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="04956-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="04956-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="04956-106">dans Pointeur vers une instance de `IVEHandler` qui gère les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="04956-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="04956-107">dans Pointeur vers le domaine d’application dans lequel le fichier est chargé.</span><span class="sxs-lookup"><span data-stu-id="04956-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="04956-108">dans Combinaison d’opérations de bits de valeurs [ValidatorFlags,](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) , indiquant les validations qui doivent être effectuées.</span><span class="sxs-lookup"><span data-stu-id="04956-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="04956-109">dans Nombre maximal d’erreurs à autoriser avant de quitter la validation.</span><span class="sxs-lookup"><span data-stu-id="04956-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="04956-110">dans Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="04956-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="04956-111">dans Chaîne qui spécifie le nom du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="04956-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="04956-112">dans Pointeur vers la mémoire tampon dans laquelle le fichier est stocké.</span><span class="sxs-lookup"><span data-stu-id="04956-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="04956-113">dans Taille, en octets, du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="04956-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04956-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="04956-114">Requirements</span></span>  
 <span data-ttu-id="04956-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04956-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04956-116">**En-tête :** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="04956-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="04956-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="04956-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04956-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04956-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
