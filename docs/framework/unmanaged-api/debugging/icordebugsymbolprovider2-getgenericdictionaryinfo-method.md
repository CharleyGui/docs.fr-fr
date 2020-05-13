---
title: Méthode ICorDebugSymbolProvider2::GetGenericDictionaryInfo
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: a6c32b72c5924399aeb13d56ddf9242fe7990f35
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379319"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="2fc23-102">Méthode ICorDebugSymbolProvider2::GetGenericDictionaryInfo</span><span class="sxs-lookup"><span data-stu-id="2fc23-102">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="2fc23-103">Récupère un mappage de dictionnaire générique.</span><span class="sxs-lookup"><span data-stu-id="2fc23-103">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="2fc23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fc23-104">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="2fc23-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2fc23-105">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="2fc23-106">à Pointeur vers l’adresse d’un objet [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) contenant le mappage de dictionnaire générique.</span><span class="sxs-lookup"><span data-stu-id="2fc23-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="2fc23-107">Pour plus d'informations, consultez la section Remarques.</span><span class="sxs-lookup"><span data-stu-id="2fc23-107">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fc23-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="2fc23-108">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="2fc23-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2fc23-109">This method is available with .NET Native only.</span></span>

<span data-ttu-id="2fc23-110">Le mappage se compose de deux sections de niveau supérieur :</span><span class="sxs-lookup"><span data-stu-id="2fc23-110">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="2fc23-111">[Répertoire](#Directory) contenant les adresses virtuelles relatives (RVA) de tous les dictionnaires inclus dans ce mappage.</span><span class="sxs-lookup"><span data-stu-id="2fc23-111">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="2fc23-112">[Segment](#Heap) aligné sur les octets qui contient les informations d’instanciation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2fc23-112">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="2fc23-113">Il commence immédiatement après la dernière entrée du répertoire.</span><span class="sxs-lookup"><span data-stu-id="2fc23-113">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="2fc23-114">Répertoire</span><span class="sxs-lookup"><span data-stu-id="2fc23-114">The Directory</span></span>

<span data-ttu-id="2fc23-115">Chaque entrée du répertoire fait référence à un offset dans le tas, c'est-à-dire un offset par rapport au début du tas.</span><span class="sxs-lookup"><span data-stu-id="2fc23-115">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="2fc23-116">La valeur d'entrées individuelles n'est pas nécessairement unique : il est possible que plusieurs entrées de répertoire pointent vers le même offset dans le tas.</span><span class="sxs-lookup"><span data-stu-id="2fc23-116">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="2fc23-117">La structure de la partie répertoire du mappage de dictionnaire générique est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2fc23-117">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="2fc23-118">Les 4 premiers octets contiennent le nombre d'entrées de dictionnaire (c'est-à-dire le nombre d'adresses virtuelles relatives dans le dictionnaire).</span><span class="sxs-lookup"><span data-stu-id="2fc23-118">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="2fc23-119">Nous faisons référence à cette valeur en tant que *N*. Si le bit élevé est défini, les entrées sont triées par adresse virtuelle relative dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="2fc23-119">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="2fc23-120">Les *entrées* d’annuaire sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="2fc23-120">The *N* directory entries follow.</span></span> <span data-ttu-id="2fc23-121">Chaque entrée se compose de 8 octets dans deux segments de 4 octets :</span><span class="sxs-lookup"><span data-stu-id="2fc23-121">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="2fc23-122">Octets 0-3 : adresse RVA (adresse virtuelle relative du dictionnaire)</span><span class="sxs-lookup"><span data-stu-id="2fc23-122">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="2fc23-123">Octets 4-7 : offset (offset par rapport au début du tas)</span><span class="sxs-lookup"><span data-stu-id="2fc23-123">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="2fc23-124">Tas</span><span class="sxs-lookup"><span data-stu-id="2fc23-124">The Heap</span></span>

<span data-ttu-id="2fc23-125">La taille du tas peut être calculée par un lecteur de flux en soustrayant la longueur du flux de la taille du répertoire + 4.</span><span class="sxs-lookup"><span data-stu-id="2fc23-125">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="2fc23-126">En d’autres termes :</span><span class="sxs-lookup"><span data-stu-id="2fc23-126">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="2fc23-127">où la taille du répertoire est `N * 8`.</span><span class="sxs-lookup"><span data-stu-id="2fc23-127">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="2fc23-128">Le format de chaque élément d'informations d'instanciation sur le tas est le suivant :</span><span class="sxs-lookup"><span data-stu-id="2fc23-128">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="2fc23-129">La longueur de cet élément d'informations d'instanciation en octets au format de métadonnées ECMA compressé.</span><span class="sxs-lookup"><span data-stu-id="2fc23-129">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="2fc23-130">La valeur exclut ces informations de longueur.</span><span class="sxs-lookup"><span data-stu-id="2fc23-130">The value excludes this length information.</span></span>

- <span data-ttu-id="2fc23-131">Nombre de types d’instanciation générique, ou *T*, au format de métadonnées ECMA compressé.</span><span class="sxs-lookup"><span data-stu-id="2fc23-131">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="2fc23-132">Types *T* , chacun représenté dans le format de signature de type ECMA.</span><span class="sxs-lookup"><span data-stu-id="2fc23-132">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="2fc23-133">L'inclusion de la longueur de chaque élément de tas permet d'effectuer un tri simple de la section répertoire sans affecter le tas.</span><span class="sxs-lookup"><span data-stu-id="2fc23-133">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="2fc23-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2fc23-134">Requirements</span></span>

<span data-ttu-id="2fc23-135">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fc23-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2fc23-136">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fc23-136">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="2fc23-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fc23-137">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2fc23-138">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fc23-138">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2fc23-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fc23-139">See also</span></span>

- [<span data-ttu-id="2fc23-140">ICorDebugSymbolProvider2, interface</span><span class="sxs-lookup"><span data-stu-id="2fc23-140">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="2fc23-141">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2fc23-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
