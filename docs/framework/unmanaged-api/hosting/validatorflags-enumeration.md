---
title: ValidatorFlags, énumération
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5f38231eb6a5911527c21ee3304fc77cfcf8e90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776518"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="ab380-102">ValidatorFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="ab380-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="ab380-103">Contient des valeurs qui indiquent le type de validation doit être effectuée dans un appel à la [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="ab380-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab380-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab380-104">Syntax</span></span>  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="ab380-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ab380-105">Members</span></span>  
  
|<span data-ttu-id="ab380-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ab380-106">Member</span></span>|<span data-ttu-id="ab380-107">Description</span><span class="sxs-lookup"><span data-stu-id="ab380-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="ab380-108">Spécifie que seuls le Microsoft intermediate language (MSIL) dans le fichier exécutable doit être validé.</span><span class="sxs-lookup"><span data-stu-id="ab380-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="ab380-109">Spécifie que seul le format du fichier exécutable doit être validé.</span><span class="sxs-lookup"><span data-stu-id="ab380-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="ab380-110">Spécifie que tous les types de validation doivent être effectuées et signalés sur.</span><span class="sxs-lookup"><span data-stu-id="ab380-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="ab380-111">Spécifie que le format du fichier exécutable ne doit pas être validé.</span><span class="sxs-lookup"><span data-stu-id="ab380-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="ab380-112">Spécifie que les messages d’erreur de validation doivent inclure les lignes de code source qui déclenchent des erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="ab380-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="ab380-113">Valeur de ce champ n’est pas valide dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="ab380-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab380-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ab380-114">Requirements</span></span>  
 <span data-ttu-id="ab380-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab380-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab380-116">**En-tête :** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="ab380-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="ab380-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab380-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab380-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab380-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab380-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab380-119">See also</span></span>

- [<span data-ttu-id="ab380-120">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="ab380-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="ab380-121">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="ab380-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
