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
ms.openlocfilehash: d623fe862eaf5902fd89d0e512dd07f73a03246f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860817"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="f38f2-102">DacpMethodDescData, structure</span><span class="sxs-lookup"><span data-stu-id="f38f2-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="f38f2-103">Définit une mémoire tampon de transport pour les informations d’exécution d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="f38f2-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f38f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f38f2-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="f38f2-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f38f2-105">Members</span></span>

| <span data-ttu-id="f38f2-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f38f2-106">Member</span></span>                       | <span data-ttu-id="f38f2-107">Description</span><span class="sxs-lookup"><span data-stu-id="f38f2-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="f38f2-108">Indique si le runtime a du code natif disponible pour l’instanciation donnée de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f38f2-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="f38f2-109">Indique si la méthode est générée dynamiquement via la génération de code léger.</span><span class="sxs-lookup"><span data-stu-id="f38f2-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="f38f2-110">Numéro d’emplacement de la méthode dans la table de méthodes.</span><span class="sxs-lookup"><span data-stu-id="f38f2-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="f38f2-111">Adresse Native initiale de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f38f2-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="f38f2-112">Pointeur vers une mémoire tampon utilisée en interne par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="f38f2-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="f38f2-113">Pointeur vers le `MethodDesc` dans le Runtime.</span><span class="sxs-lookup"><span data-stu-id="f38f2-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="f38f2-114">Pointeur vers une mémoire tampon utilisée en interne par le runtime pour suivre les méthodes.</span><span class="sxs-lookup"><span data-stu-id="f38f2-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="f38f2-115">Pointeur vers une mémoire tampon utilisée en interne par le runtime pour les informations de module.</span><span class="sxs-lookup"><span data-stu-id="f38f2-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="f38f2-116">Jeton associé à la méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="f38f2-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="f38f2-117">Pointeur vers une mémoire tampon de garbage collection utilisée en interne par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="f38f2-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="f38f2-118">Pointeur vers une mémoire tampon de garbage collection utilisée en interne par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="f38f2-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="f38f2-119">Si la méthode est dynamique, le runtime utilise cette mémoire tampon en interne pour le suivi des informations.</span><span class="sxs-lookup"><span data-stu-id="f38f2-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="f38f2-120">Utilisé pour remplir la structure par demande lorsqu’une adresse de code natif est fournie.</span><span class="sxs-lookup"><span data-stu-id="f38f2-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="f38f2-121">Informations sur la dernière version instrumentée de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f38f2-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="f38f2-122">Informations de ReJIT pour l’adresse Native demandée.</span><span class="sxs-lookup"><span data-stu-id="f38f2-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="f38f2-123">Nombre de fois que la méthode a été rejitted par l’instrumentation.</span><span class="sxs-lookup"><span data-stu-id="f38f2-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="f38f2-124">Notes </span><span class="sxs-lookup"><span data-stu-id="f38f2-124">Remarks</span></span>

<span data-ttu-id="f38f2-125">Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="f38f2-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="f38f2-126">Pour l’utiliser, définissez la structure comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="f38f2-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="f38f2-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f38f2-127">Requirements</span></span>
<span data-ttu-id="f38f2-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f38f2-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f38f2-129">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="f38f2-129">**Header:** None</span></span>  
<span data-ttu-id="f38f2-130">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="f38f2-130">**Library:** None</span></span>  
<span data-ttu-id="f38f2-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f38f2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f38f2-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f38f2-132">See also</span></span>

- [<span data-ttu-id="f38f2-133">Débogage</span><span class="sxs-lookup"><span data-stu-id="f38f2-133">Debugging</span></span>](index.md)
- [<span data-ttu-id="f38f2-134">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="f38f2-134">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="f38f2-135">Types de données courants</span><span class="sxs-lookup"><span data-stu-id="f38f2-135">Common Data Types</span></span>](../common-data-types-unmanaged-api-reference.md)
