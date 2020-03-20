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
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179190"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="919f0-102">DacpModuleData, structure</span><span class="sxs-lookup"><span data-stu-id="919f0-102">DacpModuleData Structure</span></span>

<span data-ttu-id="919f0-103">Définit un tampon de transport pour les informations d’exécution d’un module.</span><span class="sxs-lookup"><span data-stu-id="919f0-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="919f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="919f0-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="919f0-105">Membres</span><span class="sxs-lookup"><span data-stu-id="919f0-105">Members</span></span>

| <span data-ttu-id="919f0-106">Membre</span><span class="sxs-lookup"><span data-stu-id="919f0-106">Member</span></span>    | <span data-ttu-id="919f0-107">Description</span><span class="sxs-lookup"><span data-stu-id="919f0-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="919f0-108">Adresse de l’objet du module.</span><span class="sxs-lookup"><span data-stu-id="919f0-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="919f0-109">Un pointeur sur le fichier portable exécutable (PE).</span><span class="sxs-lookup"><span data-stu-id="919f0-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="919f0-110">L’adresse de la base de l’image chargée.</span><span class="sxs-lookup"><span data-stu-id="919f0-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="919f0-111">Un tampon de charge utile pour les informations supplémentaires du module utilisées par l’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="919f0-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="919f0-112">Notes </span><span class="sxs-lookup"><span data-stu-id="919f0-112">Remarks</span></span>

<span data-ttu-id="919f0-113">Cette structure vit à l’intérieur du temps d’exécution et n’est pas exposée à travers des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="919f0-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="919f0-114">Pour l’utiliser, définissez la structure comme spécifié ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="919f0-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="919f0-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="919f0-115">Requirements</span></span>
<span data-ttu-id="919f0-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="919f0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="919f0-117">**En-tête:** Aucun</span><span class="sxs-lookup"><span data-stu-id="919f0-117">**Header:** None</span></span>  
<span data-ttu-id="919f0-118">**Bibliothèque:** Aucun</span><span class="sxs-lookup"><span data-stu-id="919f0-118">**Library:** None</span></span>  
<span data-ttu-id="919f0-119">**.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="919f0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="919f0-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="919f0-120">See also</span></span>

- [<span data-ttu-id="919f0-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="919f0-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="919f0-122">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="919f0-122">Debugging Structures</span></span>](debugging-structures.md)
