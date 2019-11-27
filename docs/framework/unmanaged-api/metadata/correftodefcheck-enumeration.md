---
title: CorRefToDefCheck, énumération
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: e6c3c9b842bd823e8975661964480fd801779b2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450124"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="429fc-102">CorRefToDefCheck, énumération</span><span class="sxs-lookup"><span data-stu-id="429fc-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="429fc-103">Spécifie des indicateurs pour contrôler les éléments référencés qui sont convertis en définitions afin d'optimiser le code.</span><span class="sxs-lookup"><span data-stu-id="429fc-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="429fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="429fc-104">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="429fc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="429fc-105">Members</span></span>  
  
|<span data-ttu-id="429fc-106">Membre</span><span class="sxs-lookup"><span data-stu-id="429fc-106">Member</span></span>|<span data-ttu-id="429fc-107">Description</span><span class="sxs-lookup"><span data-stu-id="429fc-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="429fc-108">Spécifie que les références de type et les références de membre doivent être converties en définitions.</span><span class="sxs-lookup"><span data-stu-id="429fc-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="429fc-109">Il s’agit de la valeur par &#124; défaut (`MDTypeRefToDef` `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="429fc-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="429fc-110">Spécifie que tous les éléments référencés doivent être convertis en définitions.</span><span class="sxs-lookup"><span data-stu-id="429fc-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="429fc-111">Spécifie qu’aucun élément référencé ne doit être converti en définitions.</span><span class="sxs-lookup"><span data-stu-id="429fc-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="429fc-112">Spécifie que seules les références de type doivent être converties en définitions de type.</span><span class="sxs-lookup"><span data-stu-id="429fc-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="429fc-113">Spécifie que seules les références de membre doivent être converties en définitions.</span><span class="sxs-lookup"><span data-stu-id="429fc-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="429fc-114">Autrement dit, les références de membre doivent être converties en définitions de méthode ou définitions de champ.</span><span class="sxs-lookup"><span data-stu-id="429fc-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="429fc-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="429fc-115">Requirements</span></span>  
 <span data-ttu-id="429fc-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="429fc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="429fc-117">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="429fc-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="429fc-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="429fc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="429fc-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="429fc-119">See also</span></span>

- [<span data-ttu-id="429fc-120">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="429fc-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
