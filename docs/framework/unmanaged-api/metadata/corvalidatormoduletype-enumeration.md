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
ms.openlocfilehash: 2fb7f11677870f7d53439f1867f167fabe70b22a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723842"
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="2eedb-102">CorValidatorModuleType, énumération</span><span class="sxs-lookup"><span data-stu-id="2eedb-102">CorValidatorModuleType Enumeration</span></span>

<span data-ttu-id="2eedb-103">Spécifie le type d’un module.</span><span class="sxs-lookup"><span data-stu-id="2eedb-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eedb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2eedb-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2eedb-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2eedb-105">Members</span></span>  
  
|<span data-ttu-id="2eedb-106">Membre</span><span class="sxs-lookup"><span data-stu-id="2eedb-106">Member</span></span>|<span data-ttu-id="2eedb-107">Description</span><span class="sxs-lookup"><span data-stu-id="2eedb-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="2eedb-108">Le type du module n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="2eedb-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="2eedb-109">Valeur minimale de l' `CorValidatorModuleType` énumération.</span><span class="sxs-lookup"><span data-stu-id="2eedb-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="2eedb-110">Le module est un fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="2eedb-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="2eedb-111">Le module est un fichier. obj.</span><span class="sxs-lookup"><span data-stu-id="2eedb-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="2eedb-112">Le module est une session de débogueur modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="2eedb-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="2eedb-113">Le module est un module qui a été généré de manière incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="2eedb-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="2eedb-114">Valeur maximale de l' `CorValidatorModuleType` énumération.</span><span class="sxs-lookup"><span data-stu-id="2eedb-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2eedb-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2eedb-115">Requirements</span></span>  

 <span data-ttu-id="2eedb-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eedb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eedb-117">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2eedb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2eedb-118">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2eedb-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2eedb-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eedb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eedb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2eedb-120">See also</span></span>

- [<span data-ttu-id="2eedb-121">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="2eedb-121">Metadata Enumerations</span></span>](metadata-enumerations.md)
