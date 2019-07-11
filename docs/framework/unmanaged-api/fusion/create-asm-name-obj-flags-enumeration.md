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
ms.openlocfilehash: 871ad81cd83c40d7299f39ede404e274b95b2ac0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778459"
---
# <a name="createasmnameobjflags-enumeration"></a><span data-ttu-id="6913f-102">CREATE_ASM_NAME_OBJ_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="6913f-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="6913f-103">Spécifie les attributs d’un [IAssemblyName, Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) de l’objet lorsqu’il est construit par la [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="6913f-103">Specifies the attributes of an [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6913f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6913f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6913f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6913f-105">Members</span></span>  
  
|<span data-ttu-id="6913f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6913f-106">Member</span></span>|<span data-ttu-id="6913f-107">Description</span><span class="sxs-lookup"><span data-stu-id="6913f-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="6913f-108">Indique que le paramètre passé est une identité textuelle.</span><span class="sxs-lookup"><span data-stu-id="6913f-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="6913f-109">Définit le nombre de valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="6913f-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="6913f-110">Vérifie la règle d’assembly friend (uniquement un nom et clé publique).</span><span class="sxs-lookup"><span data-stu-id="6913f-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="6913f-111">Ce membre est à usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="6913f-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="6913f-112">Une combinaison de la `CANOF_PARSE_DISPLAY_NAME` et `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` indicateurs.</span><span class="sxs-lookup"><span data-stu-id="6913f-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="6913f-113">Ce membre est à usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="6913f-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6913f-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6913f-114">Requirements</span></span>  
 <span data-ttu-id="6913f-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6913f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6913f-116">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6913f-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6913f-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6913f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6913f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6913f-118">See also</span></span>

- [<span data-ttu-id="6913f-119">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="6913f-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="6913f-120">CreateAssemblyNameObject, fonction</span><span class="sxs-lookup"><span data-stu-id="6913f-120">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)
- [<span data-ttu-id="6913f-121">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="6913f-121">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
