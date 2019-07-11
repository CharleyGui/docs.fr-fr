---
title: CorValidatorModuleType, énumération
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04bed418d96658e29328cf2ce6bba445639b437f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750757"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="87958-102">CorValidatorModuleType, énumération</span><span class="sxs-lookup"><span data-stu-id="87958-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="87958-103">Spécifie le type d’un module.</span><span class="sxs-lookup"><span data-stu-id="87958-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87958-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87958-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="87958-105">Membres</span><span class="sxs-lookup"><span data-stu-id="87958-105">Members</span></span>  
  
|<span data-ttu-id="87958-106">Membre</span><span class="sxs-lookup"><span data-stu-id="87958-106">Member</span></span>|<span data-ttu-id="87958-107">Description</span><span class="sxs-lookup"><span data-stu-id="87958-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="87958-108">Le module est un type non valide.</span><span class="sxs-lookup"><span data-stu-id="87958-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="87958-109">La valeur minimale de la `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="87958-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="87958-110">Le module est un fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="87958-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="87958-111">Le module est un fichier .obj.</span><span class="sxs-lookup"><span data-stu-id="87958-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="87958-112">Le module est une session de débogueur modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="87958-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="87958-113">Le module est un qui a été générée de façon incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="87958-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="87958-114">La valeur maximale de la `CorValidatorModuleType` enum.</span><span class="sxs-lookup"><span data-stu-id="87958-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87958-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="87958-115">Requirements</span></span>  
 <span data-ttu-id="87958-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87958-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87958-117">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="87958-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87958-118">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="87958-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87958-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87958-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87958-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87958-120">See also</span></span>

- [<span data-ttu-id="87958-121">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="87958-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
