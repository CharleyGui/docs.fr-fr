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
ms.openlocfilehash: 1d58c8c0413346536c3e61e67ca0077c08c2b387
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436491"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="a364c-102">CorParamAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="a364c-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="a364c-103">Contient des valeurs qui décrivent les métadonnées d'un paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="a364c-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a364c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a364c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a364c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a364c-105">Members</span></span>  
  
|<span data-ttu-id="a364c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a364c-106">Member</span></span>|<span data-ttu-id="a364c-107">Description</span><span class="sxs-lookup"><span data-stu-id="a364c-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="a364c-108">Specifies that the parameter is passed into the method call.</span><span class="sxs-lookup"><span data-stu-id="a364c-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="a364c-109">Specifies that the parameter is passed from the method return.</span><span class="sxs-lookup"><span data-stu-id="a364c-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="a364c-110">Specifies that the parameter is optional.</span><span class="sxs-lookup"><span data-stu-id="a364c-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="a364c-111">Reserved for internal use by the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="a364c-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="a364c-112">Specifies that the parameter has a default value.</span><span class="sxs-lookup"><span data-stu-id="a364c-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="a364c-113">Specifies that the parameter has marshaling information.</span><span class="sxs-lookup"><span data-stu-id="a364c-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="a364c-114">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="a364c-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a364c-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="a364c-115">Requirements</span></span>  
 <span data-ttu-id="a364c-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a364c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a364c-117">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a364c-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a364c-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a364c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a364c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a364c-119">See also</span></span>

- [<span data-ttu-id="a364c-120">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="a364c-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
