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
ms.openlocfilehash: 9d4690cb6adedc77717e577d409cb52b18b1b5ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443835"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="46c1d-102">CorCallingConvention, énumération</span><span class="sxs-lookup"><span data-stu-id="46c1d-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="46c1d-103">Contient des valeurs qui décrivent les types de conventions d’appel effectuées dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="46c1d-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c1d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46c1d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="46c1d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="46c1d-105">Members</span></span>  
  
|<span data-ttu-id="46c1d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="46c1d-106">Member</span></span>|<span data-ttu-id="46c1d-107">Description</span><span class="sxs-lookup"><span data-stu-id="46c1d-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="46c1d-108">Indique une convention d’appel par défaut.</span><span class="sxs-lookup"><span data-stu-id="46c1d-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="46c1d-109">Indique que la méthode accepte un nombre variable de paramètres.</span><span class="sxs-lookup"><span data-stu-id="46c1d-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="46c1d-110">Indique que l’appel concerne un champ.</span><span class="sxs-lookup"><span data-stu-id="46c1d-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="46c1d-111">Indique que l’appel est à une méthode locale.</span><span class="sxs-lookup"><span data-stu-id="46c1d-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="46c1d-112">Indique que l’appel est à une propriété.</span><span class="sxs-lookup"><span data-stu-id="46c1d-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="46c1d-113">Indique que l’appel n’est pas géré.</span><span class="sxs-lookup"><span data-stu-id="46c1d-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="46c1d-114">Indique une instanciation de méthode générique.</span><span class="sxs-lookup"><span data-stu-id="46c1d-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="46c1d-115">Indique un appel PInvoke 64 bits à une méthode qui accepte un nombre variable de paramètres.</span><span class="sxs-lookup"><span data-stu-id="46c1d-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="46c1d-116">Décrit une valeur 4 bits non valide.</span><span class="sxs-lookup"><span data-stu-id="46c1d-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="46c1d-117">Indique que la Convention d’appel est décrite par les quatre bits inférieurs.</span><span class="sxs-lookup"><span data-stu-id="46c1d-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="46c1d-118">Indique que le bit supérieur décrit un paramètre de `this`.</span><span class="sxs-lookup"><span data-stu-id="46c1d-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="46c1d-119">Indique qu’un paramètre `this` est décrit explicitement dans la signature.</span><span class="sxs-lookup"><span data-stu-id="46c1d-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="46c1d-120">Indique une signature de méthode générique avec un nombre explicite d’arguments de type.</span><span class="sxs-lookup"><span data-stu-id="46c1d-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="46c1d-121">Cela précède un nombre de paramètres ordinaires.</span><span class="sxs-lookup"><span data-stu-id="46c1d-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46c1d-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="46c1d-122">Requirements</span></span>  
 <span data-ttu-id="46c1d-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46c1d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46c1d-124">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="46c1d-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="46c1d-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46c1d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c1d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46c1d-126">See also</span></span>

- [<span data-ttu-id="46c1d-127">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="46c1d-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
