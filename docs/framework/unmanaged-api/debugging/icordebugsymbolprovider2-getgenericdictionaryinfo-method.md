---
title: Méthode ICorDebugSymbolProvider2::GetGenericDictionaryInfo
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65407fca73971546725d9457d25bf1270d2001e2
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662536"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="ae6f4-102">Méthode ICorDebugSymbolProvider2::GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="ae6f4-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="ae6f4-103">Récupère un mappage de dictionnaire générique.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-103">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae6f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae6f4-104">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="ae6f4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ae6f4-105">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="ae6f4-106">[out] Un pointeur vers l’adresse d’un [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objet contenant le mappage de dictionnaire générique.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="ae6f4-107">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-107">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae6f4-108">Notes</span><span class="sxs-lookup"><span data-stu-id="ae6f4-108">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="ae6f4-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-109">This method is available with .NET Native only.</span></span>

<span data-ttu-id="ae6f4-110">Le mappage se compose de deux sections de niveau supérieur :</span><span class="sxs-lookup"><span data-stu-id="ae6f4-110">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="ae6f4-111">Un [directory](#Directory) contenant les adresses virtuelles relatives (RVA) de tous les dictionnaires inclus dans ce mappage.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="ae6f4-112">Aligné sur un octet [tas](#Heap) qui contient des informations d’instanciation d’objet.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="ae6f4-113">Il commence immédiatement après la dernière entrée du répertoire.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-113">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="ae6f4-114">Répertoire</span><span class="sxs-lookup"><span data-stu-id="ae6f4-114">The Directory</span></span>

<span data-ttu-id="ae6f4-115">Chaque entrée du répertoire fait référence à un offset dans le tas, c'est-à-dire un offset par rapport au début du tas.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="ae6f4-116">La valeur d'entrées individuelles n'est pas nécessairement unique : il est possible que plusieurs entrées de répertoire pointent vers le même offset dans le tas.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="ae6f4-117">La structure de la partie répertoire du mappage de dictionnaire générique est la suivante :</span><span class="sxs-lookup"><span data-stu-id="ae6f4-117">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="ae6f4-118">Les 4 premiers octets contiennent le nombre d'entrées de dictionnaire (c'est-à-dire le nombre d'adresses virtuelles relatives dans le dictionnaire).</span><span class="sxs-lookup"><span data-stu-id="ae6f4-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="ae6f4-119">Nous faisons référence à cette valeur en tant que *N*. Si le bit de poids fort est défini, les entrées sont triées par ordre croissant des adresses virtuelles relatives.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="ae6f4-120">Le *N* suivent des entrées de répertoire.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-120">The *N* directory entries follow.</span></span> <span data-ttu-id="ae6f4-121">Chaque entrée se compose de 8 octets dans deux segments de 4 octets :</span><span class="sxs-lookup"><span data-stu-id="ae6f4-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="ae6f4-122">Octets 0-3 : ADRESSE RVA ; adresse virtuelle relative du dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="ae6f4-123">Octets 4-7 : Offset ; un décalage par rapport au début du segment de mémoire.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="ae6f4-124">Tas</span><span class="sxs-lookup"><span data-stu-id="ae6f4-124">The Heap</span></span>

<span data-ttu-id="ae6f4-125">La taille du tas peut être calculée par un lecteur de flux en soustrayant la longueur du flux de la taille du répertoire + 4.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="ae6f4-126">En d'autres termes :</span><span class="sxs-lookup"><span data-stu-id="ae6f4-126">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="ae6f4-127">où la taille du répertoire est `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-127">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="ae6f4-128">Le format de chaque élément d'informations d'instanciation sur le tas est le suivant :</span><span class="sxs-lookup"><span data-stu-id="ae6f4-128">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="ae6f4-129">La longueur de cet élément d'informations d'instanciation en octets au format de métadonnées ECMA compressé.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="ae6f4-130">La valeur exclut ces informations de longueur.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-130">The value excludes this length information.</span></span>

- <span data-ttu-id="ae6f4-131">Le nombre de types d’instanciation générique, ou *T*, au format de métadonnées ECMA compressé.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="ae6f4-132">*T* types, chacun représenté au format de signature de type ECMA.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-132">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="ae6f4-133">L'inclusion de la longueur de chaque élément de tas permet d'effectuer un tri simple de la section répertoire sans affecter le tas.</span><span class="sxs-lookup"><span data-stu-id="ae6f4-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="ae6f4-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ae6f4-134">Requirements</span></span>

<span data-ttu-id="ae6f4-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae6f4-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ae6f4-136">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae6f4-136">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="ae6f4-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae6f4-137">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ae6f4-138">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae6f4-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ae6f4-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae6f4-139">See also</span></span>

- [<span data-ttu-id="ae6f4-140">ICorDebugSymbolProvider2, interface</span><span class="sxs-lookup"><span data-stu-id="ae6f4-140">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="ae6f4-141">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ae6f4-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
