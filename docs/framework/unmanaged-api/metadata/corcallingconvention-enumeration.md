---
title: CorCallingConvention, énumération
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: 310319e8fefe80017c58706e2beaee5eb1e78422
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007902"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="e5c83-102">CorCallingConvention, énumération</span><span class="sxs-lookup"><span data-stu-id="e5c83-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="e5c83-103">Contient des valeurs qui décrivent les types de conventions d’appel effectuées dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="e5c83-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5c83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5c83-104">Syntax</span></span>  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="e5c83-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e5c83-105">Members</span></span>  
  
|<span data-ttu-id="e5c83-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e5c83-106">Member</span></span>|<span data-ttu-id="e5c83-107">Description</span><span class="sxs-lookup"><span data-stu-id="e5c83-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="e5c83-108">Indique une convention d’appel par défaut.</span><span class="sxs-lookup"><span data-stu-id="e5c83-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="e5c83-109">Indique que la méthode accepte un nombre variable de paramètres.</span><span class="sxs-lookup"><span data-stu-id="e5c83-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="e5c83-110">Indique que l’appel concerne un champ.</span><span class="sxs-lookup"><span data-stu-id="e5c83-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="e5c83-111">Indique que l’appel est à une méthode locale.</span><span class="sxs-lookup"><span data-stu-id="e5c83-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="e5c83-112">Indique que l’appel est à une propriété.</span><span class="sxs-lookup"><span data-stu-id="e5c83-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="e5c83-113">Indique que l’appel n’est pas géré.</span><span class="sxs-lookup"><span data-stu-id="e5c83-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="e5c83-114">Indique une instanciation de méthode générique.</span><span class="sxs-lookup"><span data-stu-id="e5c83-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="e5c83-115">Indique un appel PInvoke 64 bits à une méthode qui accepte un nombre variable de paramètres.</span><span class="sxs-lookup"><span data-stu-id="e5c83-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="e5c83-116">Décrit une valeur 4 bits non valide.</span><span class="sxs-lookup"><span data-stu-id="e5c83-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="e5c83-117">Indique que la Convention d’appel est décrite par les quatre bits inférieurs.</span><span class="sxs-lookup"><span data-stu-id="e5c83-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="e5c83-118">Indique que le bit supérieur décrit un `this` paramètre.</span><span class="sxs-lookup"><span data-stu-id="e5c83-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="e5c83-119">Indique qu’un `this` paramètre est décrit explicitement dans la signature.</span><span class="sxs-lookup"><span data-stu-id="e5c83-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="e5c83-120">Indique une signature de méthode générique avec un nombre explicite d’arguments de type.</span><span class="sxs-lookup"><span data-stu-id="e5c83-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="e5c83-121">Cela précède un nombre de paramètres ordinaires.</span><span class="sxs-lookup"><span data-stu-id="e5c83-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5c83-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e5c83-122">Requirements</span></span>  
 <span data-ttu-id="e5c83-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5c83-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5c83-124">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e5c83-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e5c83-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5c83-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c83-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5c83-126">See also</span></span>

- [<span data-ttu-id="e5c83-127">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="e5c83-127">Metadata Enumerations</span></span>](metadata-enumerations.md)
