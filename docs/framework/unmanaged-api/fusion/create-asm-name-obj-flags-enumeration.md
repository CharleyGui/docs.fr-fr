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
ms.openlocfilehash: f6abb59c3aaec40a4e7b228b8c69147a2d454431
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108883"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="fc53a-102">CREATE_ASM_NAME_OBJ_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="fc53a-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="fc53a-103">Spécifie les attributs d’un objet d' [interface IAssemblyName](iassemblyname-interface.md) lorsqu’il est construit par la fonction [CreateAssemblyNameObject,](createassemblynameobject-function.md) .</span><span class="sxs-lookup"><span data-stu-id="fc53a-103">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc53a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc53a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="fc53a-105">Membres</span><span class="sxs-lookup"><span data-stu-id="fc53a-105">Members</span></span>  
  
|<span data-ttu-id="fc53a-106">Membre</span><span class="sxs-lookup"><span data-stu-id="fc53a-106">Member</span></span>|<span data-ttu-id="fc53a-107">Description</span><span class="sxs-lookup"><span data-stu-id="fc53a-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="fc53a-108">Indique que le paramètre passé est une identité textuelle.</span><span class="sxs-lookup"><span data-stu-id="fc53a-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="fc53a-109">Définit quelques valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="fc53a-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="fc53a-110">Vérifie la règle d’assembly friend (nom et clé publique uniquement).</span><span class="sxs-lookup"><span data-stu-id="fc53a-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="fc53a-111">Ce membre est destiné à un usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="fc53a-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="fc53a-112">Combinaison des indicateurs `CANOF_PARSE_DISPLAY_NAME` et `CANOF_VERIFY_FRIEND_ASSEMBLYNAME`.</span><span class="sxs-lookup"><span data-stu-id="fc53a-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="fc53a-113">Ce membre est destiné à un usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="fc53a-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc53a-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="fc53a-114">Requirements</span></span>  
 <span data-ttu-id="fc53a-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc53a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc53a-116">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="fc53a-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fc53a-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc53a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc53a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc53a-118">See also</span></span>

- [<span data-ttu-id="fc53a-119">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="fc53a-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="fc53a-120">CreateAssemblyNameObject, fonction</span><span class="sxs-lookup"><span data-stu-id="fc53a-120">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="fc53a-121">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="fc53a-121">Fusion Enumerations</span></span>](fusion-enumerations.md)
