---
title: DacpMethodDescData, structure
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 97079b824dbd0e056374af4173e49304babd6c32
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739135"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="0971d-102">DacpMethodDescData, structure</span><span class="sxs-lookup"><span data-stu-id="0971d-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="0971d-103">Définit une mémoire tampon de transport pour les informations d’exécution d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="0971d-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0971d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0971d-104">Syntax</span></span>

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a><span data-ttu-id="0971d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="0971d-105">Members</span></span>

| <span data-ttu-id="0971d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="0971d-106">Member</span></span>                       | <span data-ttu-id="0971d-107">Description</span><span class="sxs-lookup"><span data-stu-id="0971d-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="0971d-108">Indique si le runtime est disponible pour l’instanciation spécifique de la méthode de code natif.</span><span class="sxs-lookup"><span data-stu-id="0971d-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="0971d-109">Indique si la méthode générée dynamiquement via la génération de code léger.</span><span class="sxs-lookup"><span data-stu-id="0971d-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="0971d-110">Numéro d’emplacement de la méthode dans la table de méthodes.</span><span class="sxs-lookup"><span data-stu-id="0971d-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="0971d-111">Adresse native initiale de la méthode.</span><span class="sxs-lookup"><span data-stu-id="0971d-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="0971d-112">Pointeur vers une mémoire tampon utilisée en interne par le runtime.</span><span class="sxs-lookup"><span data-stu-id="0971d-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="0971d-113">Pointeur vers le `MethodDesc` dans le runtime.</span><span class="sxs-lookup"><span data-stu-id="0971d-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="0971d-114">Pointeur vers une mémoire tampon utilisée en interne par le runtime pour effectuer le suivi de méthodes.</span><span class="sxs-lookup"><span data-stu-id="0971d-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="0971d-115">Pointeur vers une mémoire tampon utilisée en interne par le runtime pour des informations sur le module.</span><span class="sxs-lookup"><span data-stu-id="0971d-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="0971d-116">Jeton associé à la méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="0971d-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="0971d-117">Pointeur vers une mémoire tampon de collection de mémoire utilisée en interne par le runtime.</span><span class="sxs-lookup"><span data-stu-id="0971d-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="0971d-118">Pointeur vers une mémoire tampon de collection de mémoire utilisée en interne par le runtime.</span><span class="sxs-lookup"><span data-stu-id="0971d-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="0971d-119">Si la méthode est dynamique, le runtime utilise cette mémoire tampon en interne pour plus d’informations de suivi.</span><span class="sxs-lookup"><span data-stu-id="0971d-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="0971d-120">Utilisé pour remplir la structure par demande en fonction d’une adresse de code natif.</span><span class="sxs-lookup"><span data-stu-id="0971d-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="0971d-121">Informations sur la dernière version de la méthode instrumentée.</span><span class="sxs-lookup"><span data-stu-id="0971d-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="0971d-122">Informations de ReJIT pour l’adresse native demandée.</span><span class="sxs-lookup"><span data-stu-id="0971d-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="0971d-123">Nombre de fois que la méthode a été rejitted via l’instrumentation.</span><span class="sxs-lookup"><span data-stu-id="0971d-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="0971d-124">Notes</span><span class="sxs-lookup"><span data-stu-id="0971d-124">Remarks</span></span>

<span data-ttu-id="0971d-125">Cette structure se trouve au sein du runtime et n’est pas exposée par le biais d’en-têtes ou les fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="0971d-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="0971d-126">Pour l’utiliser, définir la structure comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="0971d-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="0971d-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0971d-127">Requirements</span></span>
<span data-ttu-id="0971d-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0971d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0971d-129">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="0971d-129">**Header:** None</span></span>  
<span data-ttu-id="0971d-130">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="0971d-130">**Library:** None</span></span>  
<span data-ttu-id="0971d-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0971d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0971d-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0971d-132">See also</span></span>

- [<span data-ttu-id="0971d-133">Débogage</span><span class="sxs-lookup"><span data-stu-id="0971d-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="0971d-134">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="0971d-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="0971d-135">Types de données communs</span><span class="sxs-lookup"><span data-stu-id="0971d-135">Common Data Types</span></span>](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
