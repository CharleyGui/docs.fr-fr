---
title: CeeSectionAttr, énumération
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61fc71c2ab0a9107f5e9fbb354fe0f8c2fb0dace
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776337"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="407c1-102">CeeSectionAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="407c1-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="407c1-103">Fournit des valeurs qui spécifient les attributs d’une section pour une utilisation par le [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="407c1-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="407c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="407c1-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="407c1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="407c1-105">Members</span></span>  
  
|<span data-ttu-id="407c1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="407c1-106">Member</span></span>|<span data-ttu-id="407c1-107">Description</span><span class="sxs-lookup"><span data-stu-id="407c1-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="407c1-108">Section a pas d’attributs.</span><span class="sxs-lookup"><span data-stu-id="407c1-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="407c1-109">Section contient des données initialisées qui peuvent être uniquement lues, ne pas mis à jour.</span><span class="sxs-lookup"><span data-stu-id="407c1-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="407c1-110">Section contient des données initialisées qui peuvent être lues ou mis à jour.</span><span class="sxs-lookup"><span data-stu-id="407c1-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="407c1-111">Section contient le code exécutable qui est autorisé à être lu et exécuté.</span><span class="sxs-lookup"><span data-stu-id="407c1-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="407c1-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="407c1-112">Requirements</span></span>  
 <span data-ttu-id="407c1-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="407c1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="407c1-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="407c1-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="407c1-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="407c1-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="407c1-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="407c1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="407c1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="407c1-117">See also</span></span>

- [<span data-ttu-id="407c1-118">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="407c1-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
