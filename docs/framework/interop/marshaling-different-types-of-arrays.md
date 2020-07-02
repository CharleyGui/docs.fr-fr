---
title: Marshaling de différents types de tableaux
description: Marshaler différents types de tableaux, comme des entiers par valeur ou référence, des entiers à deux dimensions par valeur, des chaînes par valeur et des structures avec des entiers ou des chaînes.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: f1473c7917189f0b36c96b2adcf20005c5fd6b48
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621494"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="59b9a-103">Marshaling de différents types de tableaux</span><span class="sxs-lookup"><span data-stu-id="59b9a-103">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="59b9a-104">Un tableau est un type référence compris dans du code managé qui contient un ou plusieurs éléments du même type.</span><span class="sxs-lookup"><span data-stu-id="59b9a-104">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="59b9a-105">Même si les tableaux sont des types référence, ils sont passés comme des paramètres In aux fonctions non managées.</span><span class="sxs-lookup"><span data-stu-id="59b9a-105">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="59b9a-106">Ce comportement est incohérent avec la manière dont les tableaux managés sont passés aux objets managés, c'est-à-dire en tant que paramètres In/Out.</span><span class="sxs-lookup"><span data-stu-id="59b9a-106">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="59b9a-107">Pour plus d'informations, voir [Copie et épinglage](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="59b9a-107">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="59b9a-108">Le tableau suivant répertorie les options de marshaling des tableaux et décrit leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="59b9a-108">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="59b9a-109">Array</span><span class="sxs-lookup"><span data-stu-id="59b9a-109">Array</span></span>|<span data-ttu-id="59b9a-110">Description</span><span class="sxs-lookup"><span data-stu-id="59b9a-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="59b9a-111">D'entiers par valeur.</span><span class="sxs-lookup"><span data-stu-id="59b9a-111">Of integers by value.</span></span>|<span data-ttu-id="59b9a-112">Passe un tableau d'entiers en tant que paramètre In.</span><span class="sxs-lookup"><span data-stu-id="59b9a-112">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="59b9a-113">D'entiers par référence.</span><span class="sxs-lookup"><span data-stu-id="59b9a-113">Of integers by reference.</span></span>|<span data-ttu-id="59b9a-114">Passe un tableau d'entiers en tant que paramètre In/Out.</span><span class="sxs-lookup"><span data-stu-id="59b9a-114">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="59b9a-115">D'entiers par valeur (à deux dimensions).</span><span class="sxs-lookup"><span data-stu-id="59b9a-115">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="59b9a-116">Passe une matrice d'entiers en tant que paramètre In.</span><span class="sxs-lookup"><span data-stu-id="59b9a-116">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="59b9a-117">De chaînes par valeur.</span><span class="sxs-lookup"><span data-stu-id="59b9a-117">Of strings by value.</span></span>|<span data-ttu-id="59b9a-118">Passe un tableau de chaînes en tant que paramètre In.</span><span class="sxs-lookup"><span data-stu-id="59b9a-118">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="59b9a-119">De structures avec des entiers.</span><span class="sxs-lookup"><span data-stu-id="59b9a-119">Of structures with integers.</span></span>|<span data-ttu-id="59b9a-120">Passe un tableau de structures contenant uniquement des entiers en tant que paramètre In.</span><span class="sxs-lookup"><span data-stu-id="59b9a-120">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="59b9a-121">De structures avec des chaînes.</span><span class="sxs-lookup"><span data-stu-id="59b9a-121">Of structures with strings.</span></span>|<span data-ttu-id="59b9a-122">Passe un tableau de structures contenant uniquement des chaînes en tant que paramètre In/Out.</span><span class="sxs-lookup"><span data-stu-id="59b9a-122">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="59b9a-123">Les membres du tableau peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="59b9a-123">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="59b9a-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="59b9a-124">Example</span></span>  
 <span data-ttu-id="59b9a-125">Cet exemple montre comment passer les types de tableaux suivants :</span><span class="sxs-lookup"><span data-stu-id="59b9a-125">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="59b9a-126">Tableau d'entiers par valeur.</span><span class="sxs-lookup"><span data-stu-id="59b9a-126">Array of integers by value.</span></span>  
  
- <span data-ttu-id="59b9a-127">Tableau d'entiers par référence, qui peut être redimensionné.</span><span class="sxs-lookup"><span data-stu-id="59b9a-127">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="59b9a-128">Tableau multidimensionnel (matrice) d'entiers par valeur.</span><span class="sxs-lookup"><span data-stu-id="59b9a-128">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="59b9a-129">Tableau de chaînes par valeur.</span><span class="sxs-lookup"><span data-stu-id="59b9a-129">Array of strings by value.</span></span>  
  
- <span data-ttu-id="59b9a-130">Tableau de structures avec des entiers.</span><span class="sxs-lookup"><span data-stu-id="59b9a-130">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="59b9a-131">Tableau de structures avec des chaînes.</span><span class="sxs-lookup"><span data-stu-id="59b9a-131">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="59b9a-132">À moins qu'un tableau ne soit explicitement marshalé par référence, le comportement par défaut marshale le tableau en tant que paramètre In.</span><span class="sxs-lookup"><span data-stu-id="59b9a-132">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="59b9a-133">Vous pouvez modifier ce comportement en appliquant explicitement les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="59b9a-133">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="59b9a-134">L'exemple Tableaux utilise les fonctions non managées ci-dessous, accompagnées de leur déclaration de fonction d'origine :</span><span class="sxs-lookup"><span data-stu-id="59b9a-134">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="59b9a-135">**TestArrayOfInts** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59b9a-135">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="59b9a-136">**TestRefArrayOfInts** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59b9a-136">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="59b9a-137">**TestMatrixOfInts** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59b9a-137">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="59b9a-138">**TestArrayOfStrings** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59b9a-138">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="59b9a-139">**TestArrayOfStructs** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59b9a-139">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="59b9a-140">**TestArrayOfStructs2** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="59b9a-140">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="59b9a-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) est une bibliothèque non managée personnalisée qui contient des implémentations pour les fonctions précédemment répertoriées, ainsi que les deux variables de structure **MYPOINT** et **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="59b9a-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="59b9a-142">Ces structures contiennent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="59b9a-142">The structures contain the following elements:</span></span>  
  
```cpp
typedef struct _MYPOINT  
{  
   int x;
   int y;
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;
   char* last;
} MYPERSON;  
```  
  
 <span data-ttu-id="59b9a-143">Dans cet exemple, les structures `MyPoint` et `MyPerson` contiennent des types incorporés.</span><span class="sxs-lookup"><span data-stu-id="59b9a-143">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="59b9a-144">L'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est défini pour s'assurer que les membres soient disposés en mémoire de manière séquentielle, dans l'ordre dans lequel ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="59b9a-144">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="59b9a-145">La classe `NativeMethods` contient un ensemble de méthodes appelé par la classe `App` .</span><span class="sxs-lookup"><span data-stu-id="59b9a-145">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="59b9a-146">Pour obtenir des détails spécifiques sur le passage de tableaux, voir les commentaires de l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="59b9a-146">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="59b9a-147">Un tableau, qui est un type référence, est passé en tant que paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="59b9a-147">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="59b9a-148">Pour que l'appelant reçoive les résultats, **InAttribute** et **OutAttribute** doivent être appliqués explicitement à l'argument contenant le tableau.</span><span class="sxs-lookup"><span data-stu-id="59b9a-148">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="59b9a-149">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="59b9a-149">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="59b9a-150">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="59b9a-150">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="59b9a-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59b9a-151">See also</span></span>

- [<span data-ttu-id="59b9a-152">Types de données d'appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="59b9a-152">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="59b9a-153">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="59b9a-153">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
