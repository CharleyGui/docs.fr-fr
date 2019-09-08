---
title: ASM_CMP_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- ASM_CMP_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CMP_FLAGS
helpviewer_keywords:
- ASM_CMP_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 4d1e6700-d4be-4fbd-8796-bfb4c07abbc8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a56785d84a07122080efda22d41ec43721474789
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795267"
---
# <a name="asm_cmp_flags-enumeration"></a><span data-ttu-id="f691e-102">ASM_CMP_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="f691e-102">ASM_CMP_FLAGS Enumeration</span></span>
<span data-ttu-id="f691e-103">Indique la version, la build, la culture, la signature, etc. de deux assemblys à comparer par la méthode [IAssemblyName :: IsEqual](iassemblyname-isequal-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f691e-103">Indicates the version, build, culture, signature, and so on, of two assemblies to be compared by the [IAssemblyName::IsEqual](iassemblyname-isequal-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f691e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f691e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_CMPF_NAME                   = 0x1,  
    ASM_CMPF_MAJOR_VERSION          = 0x2,  
    ASM_CMPF_MINOR_VERSION          = 0x4,  
    ASM_CMPF_BUILD_NUMBER           = 0x8,  
    ASM_CMPF_REVISION_NUMBER        = 0x10,  
  
    ASM_CMPF_VERSION                =   
                 ASM_CMPF_MAJOR_VERSION |   
                 ASM_CMPF_MINOR_VERSION |   
                 ASM_CMPF_BUILD_NUMBER  |   
                 ASM_CMPF_REVISION_NUMBER,  
  
    ASM_CMPF_PUBLIC_KEY_TOKEN       = 0x20,  
    ASM_CMPF_CULTURE                = 0x40,  
    ASM_CMPF_CUSTOM                 = 0x80,  
    ASM_CMPF_DEFAULT                = 0x100,  
    ASM_CMPF_RETARGET               = 0x200,  
    ASM_CMPF_ARCHITECTURE           = 0x400,  
    ASM_CMPF_CONFIG_MASK            = 0x800,  
    ASM_CMPF_MVID                   = 0x1000,  
    ASM_CMPF_SIGNATURE              = 0x2000,  
  
    ASM_CMPF_IL_ALL                 =   
                 ASM_CMPF_NAME             |   
                 ASM_CMPF_VERSION          |   
                 ASM_CMPF_PUBLIC_KEY_TOKEN |   
                 ASM_CMPF_CULTURE,  
  
    ASM_CMPF_IL_NO_VERSION          =   
                 ASM_CMPF_NAME             |   
                 ASM_CMPF_PUBLIC_KEY_TOKEN |   
                 ASM_CMPF_CULTURE  
  
} ASM_CMP_FLAGS;  
```  
  
## <a name="requirements"></a><span data-ttu-id="f691e-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f691e-105">Requirements</span></span>  
 <span data-ttu-id="f691e-106">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f691e-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f691e-107">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f691e-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f691e-108">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f691e-108">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f691e-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f691e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f691e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f691e-110">See also</span></span>

- [<span data-ttu-id="f691e-111">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="f691e-111">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="f691e-112">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="f691e-112">Fusion Enumerations</span></span>](fusion-enumerations.md)
