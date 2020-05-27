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
ms.openlocfilehash: 6da8a111f716906e403d85bc0b1a29eba7238100
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006062"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="319a8-102">CeeSectionAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="319a8-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="319a8-103">Fournit des valeurs qui spécifient des attributs d’une section pour une utilisation par l’interface [ICeeGen](iceegen-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="319a8-103">Provides values that specify attributes of a section for use by the [ICeeGen](iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="319a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="319a8-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="319a8-105">Membres</span><span class="sxs-lookup"><span data-stu-id="319a8-105">Members</span></span>  
  
|<span data-ttu-id="319a8-106">Membre</span><span class="sxs-lookup"><span data-stu-id="319a8-106">Member</span></span>|<span data-ttu-id="319a8-107">Description</span><span class="sxs-lookup"><span data-stu-id="319a8-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="319a8-108">La section n’a pas d’attributs.</span><span class="sxs-lookup"><span data-stu-id="319a8-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="319a8-109">La section contient des données initialisées qui ne peuvent être lues et non mises à jour.</span><span class="sxs-lookup"><span data-stu-id="319a8-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="319a8-110">La section contient des données initialisées qui peuvent être lues ou mises à jour.</span><span class="sxs-lookup"><span data-stu-id="319a8-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="319a8-111">La section contient du code exécutable qui peut être lu et exécuté.</span><span class="sxs-lookup"><span data-stu-id="319a8-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="319a8-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="319a8-112">Requirements</span></span>  
 <span data-ttu-id="319a8-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="319a8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="319a8-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="319a8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="319a8-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="319a8-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="319a8-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="319a8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="319a8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="319a8-117">See also</span></span>

- [<span data-ttu-id="319a8-118">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="319a8-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
