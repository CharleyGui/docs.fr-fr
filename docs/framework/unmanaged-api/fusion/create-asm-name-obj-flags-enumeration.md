---
title: CREATE_ASM_NAME_OBJ_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9897e396424b9076da8f30c61b5a14cfa9539690
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795423"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="e3868-102">CREATE_ASM_NAME_OBJ_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="e3868-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="e3868-103">Spécifie les attributs d’un objet d' [interface IAssemblyName](iassemblyname-interface.md) lorsqu’il est construit par la fonction [CreateAssemblyNameObject,](createassemblynameobject-function.md) .</span><span class="sxs-lookup"><span data-stu-id="e3868-103">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3868-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3868-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e3868-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e3868-105">Members</span></span>  
  
|<span data-ttu-id="e3868-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e3868-106">Member</span></span>|<span data-ttu-id="e3868-107">Description</span><span class="sxs-lookup"><span data-stu-id="e3868-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="e3868-108">Indique que le paramètre passé est une identité textuelle.</span><span class="sxs-lookup"><span data-stu-id="e3868-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="e3868-109">Définit quelques valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="e3868-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="e3868-110">Vérifie la règle d’assembly friend (nom et clé publique uniquement).</span><span class="sxs-lookup"><span data-stu-id="e3868-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="e3868-111">Ce membre est destiné à un usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="e3868-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="e3868-112">Combinaison des `CANOF_PARSE_DISPLAY_NAME` indicateurs et `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` .</span><span class="sxs-lookup"><span data-stu-id="e3868-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="e3868-113">Ce membre est destiné à un usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="e3868-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3868-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e3868-114">Requirements</span></span>  
 <span data-ttu-id="e3868-115">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3868-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3868-116">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e3868-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e3868-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3868-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3868-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3868-118">See also</span></span>

- [<span data-ttu-id="e3868-119">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="e3868-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="e3868-120">CreateAssemblyNameObject, fonction</span><span class="sxs-lookup"><span data-stu-id="e3868-120">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="e3868-121">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="e3868-121">Fusion Enumerations</span></span>](fusion-enumerations.md)
