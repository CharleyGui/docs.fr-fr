---
title: DacpModuleData, structure
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 2e27082ba4c35bc10eb65139b2af6c81c10d79a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739123"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="2cc1d-102">DacpModuleData, structure</span><span class="sxs-lookup"><span data-stu-id="2cc1d-102">DacpModuleData Structure</span></span>

<span data-ttu-id="2cc1d-103">Définit une mémoire tampon de transport pour les informations d’exécution d’un module.</span><span class="sxs-lookup"><span data-stu-id="2cc1d-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2cc1d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cc1d-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File; 
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="2cc1d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2cc1d-105">Members</span></span>

| <span data-ttu-id="2cc1d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="2cc1d-106">Member</span></span>    | <span data-ttu-id="2cc1d-107">Description</span><span class="sxs-lookup"><span data-stu-id="2cc1d-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="2cc1d-108">Adresse de l’objet de module.</span><span class="sxs-lookup"><span data-stu-id="2cc1d-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="2cc1d-109">Pointeur vers le fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="2cc1d-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="2cc1d-110">L’adresse de l’image chargée de base.</span><span class="sxs-lookup"><span data-stu-id="2cc1d-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="2cc1d-111">Un tampon de la charge utile pour les informations de module supplémentaire utilisées par le runtime.</span><span class="sxs-lookup"><span data-stu-id="2cc1d-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2cc1d-112">Notes</span><span class="sxs-lookup"><span data-stu-id="2cc1d-112">Remarks</span></span>

<span data-ttu-id="2cc1d-113">Cette structure se trouve au sein du runtime et n’est pas exposée par le biais d’en-têtes ou les fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="2cc1d-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="2cc1d-114">Pour l’utiliser, définir la structure comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="2cc1d-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="2cc1d-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2cc1d-115">Requirements</span></span>
<span data-ttu-id="2cc1d-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cc1d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2cc1d-117">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="2cc1d-117">**Header:** None</span></span>  
<span data-ttu-id="2cc1d-118">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="2cc1d-118">**Library:** None</span></span>  
<span data-ttu-id="2cc1d-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2cc1d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2cc1d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cc1d-120">See also</span></span>

- [<span data-ttu-id="2cc1d-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="2cc1d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="2cc1d-122">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="2cc1d-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
