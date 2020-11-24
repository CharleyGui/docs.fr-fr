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
ms.openlocfilehash: 52d5ad3a18c102422e90621c7d1e23b2692c0000
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683228"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="f2d07-102">CREATE_ASM_NAME_OBJ_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="f2d07-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>

<span data-ttu-id="f2d07-103">Spécifie les attributs d’un objet d' [interface IAssemblyName](iassemblyname-interface.md) lorsqu’il est construit par la fonction [CreateAssemblyNameObject,](createassemblynameobject-function.md) .</span><span class="sxs-lookup"><span data-stu-id="f2d07-103">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2d07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2d07-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="f2d07-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f2d07-105">Members</span></span>  
  
|<span data-ttu-id="f2d07-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f2d07-106">Member</span></span>|<span data-ttu-id="f2d07-107">Description</span><span class="sxs-lookup"><span data-stu-id="f2d07-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="f2d07-108">Indique que le paramètre passé est une identité textuelle.</span><span class="sxs-lookup"><span data-stu-id="f2d07-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="f2d07-109">Définit quelques valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="f2d07-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="f2d07-110">Vérifie la règle d’assembly friend (nom et clé publique uniquement).</span><span class="sxs-lookup"><span data-stu-id="f2d07-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="f2d07-111">Ce membre est destiné à un usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="f2d07-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="f2d07-112">Combinaison des `CANOF_PARSE_DISPLAY_NAME` `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` indicateurs et.</span><span class="sxs-lookup"><span data-stu-id="f2d07-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="f2d07-113">Ce membre est destiné à un usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="f2d07-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2d07-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f2d07-114">Requirements</span></span>  

 <span data-ttu-id="f2d07-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2d07-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2d07-116">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f2d07-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f2d07-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2d07-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d07-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2d07-118">See also</span></span>

- [<span data-ttu-id="f2d07-119">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="f2d07-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="f2d07-120">CreateAssemblyNameObject, fonction</span><span class="sxs-lookup"><span data-stu-id="f2d07-120">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="f2d07-121">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="f2d07-121">Fusion Enumerations</span></span>](fusion-enumerations.md)
