---
title: CorParamAttr, énumération
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bfa8f1b5df76c7fdfe2f25b637b157bfa4424f7a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781654"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="a4416-102">CorParamAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="a4416-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="a4416-103">Contient des valeurs qui décrivent les métadonnées d'un paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="a4416-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4416-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4416-104">Syntax</span></span>  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="a4416-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a4416-105">Members</span></span>  
  
|<span data-ttu-id="a4416-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a4416-106">Member</span></span>|<span data-ttu-id="a4416-107">Description</span><span class="sxs-lookup"><span data-stu-id="a4416-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="a4416-108">Spécifie que le paramètre est passé dans l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="a4416-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="a4416-109">Spécifie que le paramètre est passé à partir de la méthode de retour.</span><span class="sxs-lookup"><span data-stu-id="a4416-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="a4416-110">Spécifie que le paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="a4416-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="a4416-111">Réservé à un usage interne par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="a4416-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="a4416-112">Spécifie que le paramètre a une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a4416-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="a4416-113">Spécifie que le paramètre a des informations de marshaling.</span><span class="sxs-lookup"><span data-stu-id="a4416-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="a4416-114">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="a4416-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a4416-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a4416-115">Requirements</span></span>  
 <span data-ttu-id="a4416-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4416-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4416-117">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a4416-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a4416-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4416-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4416-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4416-119">See also</span></span>

- [<span data-ttu-id="a4416-120">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="a4416-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
