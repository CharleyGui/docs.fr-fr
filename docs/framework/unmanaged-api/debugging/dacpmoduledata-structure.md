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
ms.openlocfilehash: e10d1792a8dc0b57ddd121ec09854e8e1824cade
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860801"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="c4101-102">DacpModuleData, structure</span><span class="sxs-lookup"><span data-stu-id="c4101-102">DacpModuleData Structure</span></span>

<span data-ttu-id="c4101-103">Définit une mémoire tampon de transport pour les informations d’exécution d’un module.</span><span class="sxs-lookup"><span data-stu-id="c4101-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c4101-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4101-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="c4101-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c4101-105">Members</span></span>

| <span data-ttu-id="c4101-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c4101-106">Member</span></span>    | <span data-ttu-id="c4101-107">Description</span><span class="sxs-lookup"><span data-stu-id="c4101-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="c4101-108">Adresse de l’objet de module.</span><span class="sxs-lookup"><span data-stu-id="c4101-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="c4101-109">Pointeur vers le fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="c4101-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="c4101-110">Adresse de la base de l’image chargée.</span><span class="sxs-lookup"><span data-stu-id="c4101-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="c4101-111">Mémoire tampon de charge utile pour les informations de module supplémentaires utilisées par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="c4101-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c4101-112">Notes </span><span class="sxs-lookup"><span data-stu-id="c4101-112">Remarks</span></span>

<span data-ttu-id="c4101-113">Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="c4101-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="c4101-114">Pour l’utiliser, définissez la structure comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="c4101-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4101-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c4101-115">Requirements</span></span>
<span data-ttu-id="c4101-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4101-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c4101-117">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="c4101-117">**Header:** None</span></span>  
<span data-ttu-id="c4101-118">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="c4101-118">**Library:** None</span></span>  
<span data-ttu-id="c4101-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c4101-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c4101-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4101-120">See also</span></span>

- [<span data-ttu-id="c4101-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="c4101-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="c4101-122">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="c4101-122">Debugging Structures</span></span>](debugging-structures.md)
