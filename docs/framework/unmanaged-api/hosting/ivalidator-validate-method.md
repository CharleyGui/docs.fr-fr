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
ms.openlocfilehash: 688abd210cca193bf03c40f000b74ecb66eb8ede
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008545"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="46d5b-102">IValidator::Validate, méthode</span><span class="sxs-lookup"><span data-stu-id="46d5b-102">IValidator::Validate Method</span></span>
<span data-ttu-id="46d5b-103">Valide le fichier exécutable portable (PE) ou le fichier MSIL (Microsoft Intermediate Language) spécifié.</span><span class="sxs-lookup"><span data-stu-id="46d5b-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46d5b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46d5b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="46d5b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46d5b-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="46d5b-106">dans Pointeur vers une `IVEHandler` instance qui gère les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="46d5b-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="46d5b-107">dans Pointeur vers le domaine d’application dans lequel le fichier est chargé.</span><span class="sxs-lookup"><span data-stu-id="46d5b-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="46d5b-108">dans Combinaison d’opérations de bits de valeurs [ValidatorFlags,](validatorflags-enumeration.md) , indiquant les validations qui doivent être effectuées.</span><span class="sxs-lookup"><span data-stu-id="46d5b-108">[in] A bitwise combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="46d5b-109">dans Nombre maximal d’erreurs à autoriser avant de quitter la validation.</span><span class="sxs-lookup"><span data-stu-id="46d5b-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="46d5b-110">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="46d5b-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="46d5b-111">dans Chaîne qui spécifie le nom du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="46d5b-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="46d5b-112">dans Pointeur vers la mémoire tampon dans laquelle le fichier est stocké.</span><span class="sxs-lookup"><span data-stu-id="46d5b-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="46d5b-113">dans Taille, en octets, du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="46d5b-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46d5b-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="46d5b-114">Requirements</span></span>  
 <span data-ttu-id="46d5b-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46d5b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46d5b-116">**En-tête :** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="46d5b-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="46d5b-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="46d5b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46d5b-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46d5b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
