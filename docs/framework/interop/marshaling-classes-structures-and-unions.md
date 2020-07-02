---
title: Marshaling de classes, de structures, et d'unions
description: Examinez comment marshaler des classes, des structures et des unions. Affichez des exemples de classes de marshaling, des structures avec des structures imbriquées, des tableaux de structures et des unions.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
ms.openlocfilehash: 5e616b5bb513939cadd8fe5c72675ba0b6e070a3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621520"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="126e0-104">Marshaling de classes, de structures, et d'unions</span><span class="sxs-lookup"><span data-stu-id="126e0-104">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="126e0-105">Les classes et les structures sont similaires dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="126e0-105">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="126e0-106">Elles peuvent toutes deux posséder des champs, des propriétés et des événements.</span><span class="sxs-lookup"><span data-stu-id="126e0-106">Both can have fields, properties, and events.</span></span> <span data-ttu-id="126e0-107">Elles peuvent également posséder des méthodes statiques et non statiques.</span><span class="sxs-lookup"><span data-stu-id="126e0-107">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="126e0-108">Une différence notable existe toutefois : les structures sont des types valeur et les classes sont des types référence.</span><span class="sxs-lookup"><span data-stu-id="126e0-108">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="126e0-109">Le tableau suivant répertorie les options de marshaling pour les classes, les structures et les unions. Il décrit leur utilisation et fournit un lien vers l'exemple d'appel de code non managé correspondant.</span><span class="sxs-lookup"><span data-stu-id="126e0-109">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="126e0-110">Type</span><span class="sxs-lookup"><span data-stu-id="126e0-110">Type</span></span>|<span data-ttu-id="126e0-111">Description</span><span class="sxs-lookup"><span data-stu-id="126e0-111">Description</span></span>|<span data-ttu-id="126e0-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="126e0-112">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="126e0-113">Classe par valeur.</span><span class="sxs-lookup"><span data-stu-id="126e0-113">Class by value.</span></span>|<span data-ttu-id="126e0-114">Passe une classe avec des membres entiers en tant que paramètre In/Out, comme le cas managé.</span><span class="sxs-lookup"><span data-stu-id="126e0-114">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="126e0-115">SysTime (exemple)</span><span class="sxs-lookup"><span data-stu-id="126e0-115">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="126e0-116">Structure par valeur.</span><span class="sxs-lookup"><span data-stu-id="126e0-116">Structure by value.</span></span>|<span data-ttu-id="126e0-117">Passe des structures en tant que paramètres In.</span><span class="sxs-lookup"><span data-stu-id="126e0-117">Passes structures as In parameters.</span></span>|[<span data-ttu-id="126e0-118">Exemple de structures</span><span class="sxs-lookup"><span data-stu-id="126e0-118">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="126e0-119">Structure par référence.</span><span class="sxs-lookup"><span data-stu-id="126e0-119">Structure by reference.</span></span>|<span data-ttu-id="126e0-120">Passe des structures en tant que paramètres In/Out.</span><span class="sxs-lookup"><span data-stu-id="126e0-120">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="126e0-121">[OSInfo (exemple)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="126e0-121">[OSInfo sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="126e0-122">Structure avec structures imbriquées (aplaties).</span><span class="sxs-lookup"><span data-stu-id="126e0-122">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="126e0-123">Passe une classe représentant une structure avec structures imbriquées dans la fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="126e0-123">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="126e0-124">La structure est aplatie sous la forme d'une même grande structure dans le prototype managé.</span><span class="sxs-lookup"><span data-stu-id="126e0-124">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="126e0-125">FindFile (exemple)</span><span class="sxs-lookup"><span data-stu-id="126e0-125">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="126e0-126">Structure avec un pointeur vers une autre structure.</span><span class="sxs-lookup"><span data-stu-id="126e0-126">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="126e0-127">Passe une structure contenant un pointeur vers une autre structure en tant que membre.</span><span class="sxs-lookup"><span data-stu-id="126e0-127">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="126e0-128">Exemple structures</span><span class="sxs-lookup"><span data-stu-id="126e0-128">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="126e0-129">Tableau de structures avec des entiers par valeur.</span><span class="sxs-lookup"><span data-stu-id="126e0-129">Array of structures with integers by value.</span></span>|<span data-ttu-id="126e0-130">Passe un tableau de structures contenant uniquement des entiers en tant que paramètre In/Out.</span><span class="sxs-lookup"><span data-stu-id="126e0-130">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="126e0-131">Les membres du tableau peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="126e0-131">Members of the array can be changed.</span></span>|[<span data-ttu-id="126e0-132">Arrays, exemple</span><span class="sxs-lookup"><span data-stu-id="126e0-132">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="126e0-133">Tableau de structures avec des entiers et des chaînes par référence.</span><span class="sxs-lookup"><span data-stu-id="126e0-133">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="126e0-134">Passe un tableau de structures contenant des entiers et des chaînes en tant que paramètre Out.</span><span class="sxs-lookup"><span data-stu-id="126e0-134">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="126e0-135">La fonction appelée alloue de la mémoire pour le tableau.</span><span class="sxs-lookup"><span data-stu-id="126e0-135">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="126e0-136">OutArrayOfStructs, exemple</span><span class="sxs-lookup"><span data-stu-id="126e0-136">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="126e0-137">Unions avec types valeur.</span><span class="sxs-lookup"><span data-stu-id="126e0-137">Unions with value types.</span></span>|<span data-ttu-id="126e0-138">Passe des unions avec des types valeur (entier et double).</span><span class="sxs-lookup"><span data-stu-id="126e0-138">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="126e0-139">Unions (exemple)</span><span class="sxs-lookup"><span data-stu-id="126e0-139">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="126e0-140">Unions avec types mixtes.</span><span class="sxs-lookup"><span data-stu-id="126e0-140">Unions with mixed types.</span></span>|<span data-ttu-id="126e0-141">Passe des unions avec des types mixtes (entier et chaîne).</span><span class="sxs-lookup"><span data-stu-id="126e0-141">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="126e0-142">Unions (exemple)</span><span class="sxs-lookup"><span data-stu-id="126e0-142">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="126e0-143">Structure avec une disposition spécifique à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="126e0-143">Struct with platform-specific layout.</span></span>|<span data-ttu-id="126e0-144">Passe un type avec des définitions de compression natives.</span><span class="sxs-lookup"><span data-stu-id="126e0-144">Passes a type with native-packing definitions.</span></span>|[<span data-ttu-id="126e0-145">Exemple de plateforme</span><span class="sxs-lookup"><span data-stu-id="126e0-145">Platform sample</span></span>](#platform-sample)|
|<span data-ttu-id="126e0-146">Valeurs Null dans la structure.</span><span class="sxs-lookup"><span data-stu-id="126e0-146">Null values in structure.</span></span>|<span data-ttu-id="126e0-147">Passe une référence null (**Nothing** en Visual Basic) au lieu d’une référence à un type valeur.</span><span class="sxs-lookup"><span data-stu-id="126e0-147">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="126e0-148">[HandleRef (exemple)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="126e0-148">[HandleRef sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="126e0-149">Exemple de structures</span><span class="sxs-lookup"><span data-stu-id="126e0-149">Structures sample</span></span>

<span data-ttu-id="126e0-150">Cet exemple montre comment passer une structure qui pointe vers une autre structure, comment passer une structure avec structure incorporée et comment passer une structure avec tableau incorporé.</span><span class="sxs-lookup"><span data-stu-id="126e0-150">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="126e0-151">L'exemple Structures utilise les fonctions non managées ci-dessous, accompagnées de leur déclaration de fonction d'origine :</span><span class="sxs-lookup"><span data-stu-id="126e0-151">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="126e0-152">**TestStructInStruct** exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="126e0-152">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="126e0-153">**TestStructInStruct3** exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="126e0-153">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="126e0-154">**TestArrayInStruct** exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="126e0-154">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="126e0-155">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) est une bibliothèque non managée personnalisée qui contient des implémentations des fonctions précédemment répertoriées, ainsi que quatre structures : **MYPERSON**, **MYPERSON2**, **MYPERSON3** et **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="126e0-155">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="126e0-156">Ces structures contiennent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="126e0-156">These structures contain the following elements:</span></span>

```cpp
typedef struct _MYPERSON
{
   char* first;
   char* last;
} MYPERSON, *LP_MYPERSON;

typedef struct _MYPERSON2
{
   MYPERSON* person;
   int age;
} MYPERSON2, *LP_MYPERSON2;

typedef struct _MYPERSON3
{
   MYPERSON person;
   int age;
} MYPERSON3;

typedef struct _MYARRAYSTRUCT
{
   bool flag;
   int vals[ 3 ];
} MYARRAYSTRUCT;
```

<span data-ttu-id="126e0-157">Les structures managées `MyPerson`,`MyPerson2`, `MyPerson3` et `MyArrayStruct` ont les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="126e0-157">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="126e0-158">`MyPerson` contient uniquement des membres de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="126e0-158">`MyPerson` contains only string members.</span></span> <span data-ttu-id="126e0-159">Le champ [CharSet](specifying-a-character-set.md) affecte le format ANSI aux chaînes quand elles sont passées à la fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="126e0-159">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="126e0-160">`MyPerson2`contient un **IntPtr** à la `MyPerson` structure.</span><span class="sxs-lookup"><span data-stu-id="126e0-160">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="126e0-161">Le type **IntPtr** remplace le pointeur d’origine vers la structure non managée, car les applications .NET Framework n’utilisent pas de pointeurs, sauf si le code est marqué comme étant **unsafe**.</span><span class="sxs-lookup"><span data-stu-id="126e0-161">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="126e0-162">`MyPerson3` contient `MyPerson` comme structure incorporée.</span><span class="sxs-lookup"><span data-stu-id="126e0-162">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="126e0-163">Une structure incorporée dans une autre structure peut être aplatie en plaçant les éléments de la structure incorporée directement dans la structure principale. Elle peut également être conservée comme une structure incorporée, comme dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="126e0-163">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="126e0-164">`MyArrayStruct` contient un tableau d'entiers.</span><span class="sxs-lookup"><span data-stu-id="126e0-164">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="126e0-165">L’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> définit la valeur d’énumération <xref:System.Runtime.InteropServices.UnmanagedType> sur **ByValArray**, qui est utilisée pour indiquer le nombre d’éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="126e0-165">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="126e0-166">Pour toutes les structures de cet exemple, l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est appliqué pour garantir que les membres soient classés de manière séquentielle dans la mémoire, dans l'ordre dans lequel ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="126e0-166">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="126e0-167">La classe `NativeMethods` contient des prototypes managés pour les méthodes `TestStructInStruct`, `TestStructInStruct3` et `TestArrayInStruct` appelées par la classe `App`.</span><span class="sxs-lookup"><span data-stu-id="126e0-167">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="126e0-168">Chaque prototype déclare un seul paramètre de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="126e0-168">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="126e0-169">`TestStructInStruct` déclare une référence au type `MyPerson2` comme son paramètre.</span><span class="sxs-lookup"><span data-stu-id="126e0-169">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="126e0-170">`TestStructInStruct3` déclare le type `MyPerson3` en tant que paramètre et passe le paramètre par valeur.</span><span class="sxs-lookup"><span data-stu-id="126e0-170">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="126e0-171">`TestArrayInStruct` déclare une référence au type `MyArrayStruct` comme son paramètre.</span><span class="sxs-lookup"><span data-stu-id="126e0-171">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="126e0-172">Les structures en tant qu’arguments de méthodes sont passées par valeur, sauf si le paramètre contient le mot clé **ref** (**ByRef** dans Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="126e0-172">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="126e0-173">Par exemple, la méthode `TestStructInStruct` passe une référence (la valeur d'une adresse) à un objet de type `MyPerson2` au code non managé.</span><span class="sxs-lookup"><span data-stu-id="126e0-173">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="126e0-174">Pour manipuler la structure vers laquelle pointe `MyPerson2`, l'exemple crée une mémoire tampon d'une taille spécifiée et retourne son adresse en combinant les méthodes <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> et <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="126e0-174">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="126e0-175">Ensuite, l'exemple copie le contenu de la structure managée vers la mémoire tampon non managée.</span><span class="sxs-lookup"><span data-stu-id="126e0-175">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="126e0-176">Enfin, l'exemple utilise la méthode <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> pour marshaler des données à partir de la mémoire tampon non managée vers un objet managé, ainsi que la méthode <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> pour libérer le bloc de mémoire non managé.</span><span class="sxs-lookup"><span data-stu-id="126e0-176">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="126e0-177">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="126e0-177">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="126e0-178">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="126e0-178">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="126e0-179">FindFile (exemple)</span><span class="sxs-lookup"><span data-stu-id="126e0-179">FindFile sample</span></span>

<span data-ttu-id="126e0-180">Cet exemple montre comment passer une structure qui contient une autre structure incorporée à une fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="126e0-180">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="126e0-181">Il montre également comment utiliser l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> pour déclarer un tableau de longueur fixe au sein de la structure.</span><span class="sxs-lookup"><span data-stu-id="126e0-181">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="126e0-182">Dans cet exemple, les éléments de la structure incorporée sont ajoutés à la structure parent.</span><span class="sxs-lookup"><span data-stu-id="126e0-182">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="126e0-183">Pour obtenir un exemple de structure incorporée non aplatie, consultez [Exemples de structures](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="126e0-183">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="126e0-184">L'exemple FindFile utilise la fonction non managée ci-dessous, accompagnée de sa déclaration de fonction d'origine :</span><span class="sxs-lookup"><span data-stu-id="126e0-184">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="126e0-185">**FindFirstFile** exportée depuis Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="126e0-185">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="126e0-186">La structure d'origine passée à la fonction contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="126e0-186">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _WIN32_FIND_DATA
{
  DWORD    dwFileAttributes;
  FILETIME ftCreationTime;
  FILETIME ftLastAccessTime;
  FILETIME ftLastWriteTime;
  DWORD    nFileSizeHigh;
  DWORD    nFileSizeLow;
  DWORD    dwReserved0;
  DWORD    dwReserved1;
  TCHAR    cFileName[ MAX_PATH ];
  TCHAR    cAlternateFileName[ 14 ];
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;
```

<span data-ttu-id="126e0-187">Dans cet exemple, la classe `FindData` contient un membre de données correspondant pour chaque élément de la structure d'origine et de la structure incorporée.</span><span class="sxs-lookup"><span data-stu-id="126e0-187">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="126e0-188">À la place des deux tampons caractère d'origine, la classe substitue des chaînes.</span><span class="sxs-lookup"><span data-stu-id="126e0-188">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="126e0-189">**MarshalAsAttribute** définit l’énumération <xref:System.Runtime.InteropServices.UnmanagedType> sur **ByValTStr**, qui est utilisé pour identifier les tableaux de caractères de longueur fixe inline qui apparaissent au sein des structures non managées.</span><span class="sxs-lookup"><span data-stu-id="126e0-189">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="126e0-190">La classe `NativeMethods` contient un prototype managé de la méthode `FindFirstFile`, qui passe la classe `FindData` en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="126e0-190">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="126e0-191">Le paramètre doit être déclaré avec les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute>, car les classes, qui sont des types référence, sont passées en tant que paramètres In par défaut.</span><span class="sxs-lookup"><span data-stu-id="126e0-191">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="126e0-192">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="126e0-192">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="126e0-193">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="126e0-193">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="126e0-194">Unions (exemple)</span><span class="sxs-lookup"><span data-stu-id="126e0-194">Unions sample</span></span>

<span data-ttu-id="126e0-195">Cet exemple montre comment passer des structures contenant uniquement des types valeur, ainsi que des structures contenant un type valeur et une chaîne en tant que paramètres, à une fonction non managée nécessitant une union.</span><span class="sxs-lookup"><span data-stu-id="126e0-195">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="126e0-196">Une union représente un emplacement de mémoire qui peut être partagé par plusieurs variables.</span><span class="sxs-lookup"><span data-stu-id="126e0-196">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="126e0-197">L'exemple Unions utilise la fonction non managée ci-dessous, accompagnée de sa déclaration de fonction d'origine :</span><span class="sxs-lookup"><span data-stu-id="126e0-197">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="126e0-198">**TestUnion** exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="126e0-198">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="126e0-199">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) est une bibliothèque non managée personnalisée qui contient une implémentation de la fonction précédemment répertoriée, ainsi que deux unions, **MYUNION** et **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="126e0-199">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="126e0-200">Les unions peuvent contenir les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="126e0-200">The unions contain the following elements:</span></span>

```cpp
union MYUNION
{
    int number;
    double d;
}

union MYUNION2
{
    int i;
    char str[128];
};
```

<span data-ttu-id="126e0-201">Dans du code managé, les unions sont définies en tant que structures.</span><span class="sxs-lookup"><span data-stu-id="126e0-201">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="126e0-202">La structure `MyUnion` contient deux types valeur comme ses membres : un entier et un double.</span><span class="sxs-lookup"><span data-stu-id="126e0-202">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="126e0-203">L'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est défini pour contrôler la position précise de chaque membre de données.</span><span class="sxs-lookup"><span data-stu-id="126e0-203">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="126e0-204">L'attribut <xref:System.Runtime.InteropServices.FieldOffsetAttribute> fournit la position physique des champs dans la représentation non managée d'une union.</span><span class="sxs-lookup"><span data-stu-id="126e0-204">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="126e0-205">Notez que les deux membres possèdent les mêmes valeurs de décalage. Ils peuvent donc définir la même zone de mémoire.</span><span class="sxs-lookup"><span data-stu-id="126e0-205">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="126e0-206">`MyUnion2_1` et `MyUnion2_2` contiennent respectivement un type valeur (entier) et une chaîne.</span><span class="sxs-lookup"><span data-stu-id="126e0-206">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="126e0-207">Dans du code managé, les types valeur et les types référence ne sont pas autorisés à se chevaucher.</span><span class="sxs-lookup"><span data-stu-id="126e0-207">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="126e0-208">Cet exemple utilise la surcharge de méthode pour permettre à l'appelant d'utiliser les deux types quand il appelle la même fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="126e0-208">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="126e0-209">La disposition de `MyUnion2_1` est explicite et possède une valeur de décalage précise.</span><span class="sxs-lookup"><span data-stu-id="126e0-209">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="126e0-210">En revanche, `MyUnion2_2` possède une disposition séquentielle, car les dispositions explicites ne sont pas autorisées avec les types référence.</span><span class="sxs-lookup"><span data-stu-id="126e0-210">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="126e0-211">L’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> définit l’énumération <xref:System.Runtime.InteropServices.UnmanagedType> sur **ByValTStr**, qui est utilisé pour les tableaux de caractères de longueur fixe inline qui apparaissent au sein de la représentation non managée de l’union.</span><span class="sxs-lookup"><span data-stu-id="126e0-211">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="126e0-212">La classe `NativeMethods` contient les prototypes des méthodes `TestUnion` et `TestUnion2`.</span><span class="sxs-lookup"><span data-stu-id="126e0-212">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="126e0-213">`TestUnion2` est surchargée pour déclarer `MyUnion2_1` ou `MyUnion2_2` en tant que paramètres.</span><span class="sxs-lookup"><span data-stu-id="126e0-213">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="126e0-214">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="126e0-214">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="126e0-215">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="126e0-215">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a><span data-ttu-id="126e0-216">Exemple de plateforme</span><span class="sxs-lookup"><span data-stu-id="126e0-216">Platform sample</span></span>

<span data-ttu-id="126e0-217">Dans certains scénarios, `struct` `union` les dispositions et peuvent différer selon la plateforme ciblée.</span><span class="sxs-lookup"><span data-stu-id="126e0-217">In some scenarios, `struct` and `union` layouts can differ depending on the targeted platform.</span></span> <span data-ttu-id="126e0-218">Par exemple, considérez le [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) type quand il est défini dans un scénario com :</span><span class="sxs-lookup"><span data-stu-id="126e0-218">For example, consider the [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) type when defined in a COM scenario:</span></span>

```c++
#include <pshpack8.h> /* Defines the packing of the struct */
typedef struct _STRRET
    {
    UINT uType;
    /* [switch_is][switch_type] */ union
        {
        /* [case()][string] */ LPWSTR pOleStr;
        /* [case()] */ UINT uOffset;
        /* [case()] */ char cStr[ 260 ];
        }  DUMMYUNIONNAME;
    }  STRRET;
#include <poppack.h>
```

<span data-ttu-id="126e0-219">Les éléments ci-dessus `struct` sont déclarés avec des en-têtes Windows qui influencent la disposition de la mémoire du type.</span><span class="sxs-lookup"><span data-stu-id="126e0-219">The above `struct` is declared with Windows' headers that influence the memory layout of the type.</span></span> <span data-ttu-id="126e0-220">Lorsqu’ils sont définis dans un environnement géré, ces détails de disposition sont nécessaires pour interagir correctement avec le code natif.</span><span class="sxs-lookup"><span data-stu-id="126e0-220">When defined in a managed environment, these layout details are needed to properly interoperate with native code.</span></span>

<span data-ttu-id="126e0-221">La définition managée correcte de ce type dans un processus 32 bits est la suivante :</span><span class="sxs-lookup"><span data-stu-id="126e0-221">The correct managed definition of this type in a 32-bit process is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 264)]
public struct STRRET_32
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(4)]
    public IntPtr pOleStr;

    [FieldOffset(4)]
    public uint uOffset;

    [FieldOffset(4)]
    public IntPtr cStr;
}
```

<span data-ttu-id="126e0-222">Sur un processus 64 bits, les décalages de taille *et* de champ sont différents.</span><span class="sxs-lookup"><span data-stu-id="126e0-222">On a 64-bit process, the size *and* field offsets are different.</span></span> <span data-ttu-id="126e0-223">La disposition correcte est la suivante :</span><span class="sxs-lookup"><span data-stu-id="126e0-223">The correct layout is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 272)]
public struct STRRET_64
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(8)]
    public IntPtr pOleStr;

    [FieldOffset(8)]
    public uint uOffset;

    [FieldOffset(8)]
    public IntPtr cStr;
}
```

<span data-ttu-id="126e0-224">L’échec de la prise en compte de la disposition native dans un scénario d’interopérabilité peut entraîner des blocages aléatoires ou pire, des calculs incorrects.</span><span class="sxs-lookup"><span data-stu-id="126e0-224">Failure to properly consider the native layout in an interop scenario can result in random crashes or worse, incorrect computations.</span></span>

<span data-ttu-id="126e0-225">Par défaut, les assemblys .NET peuvent s’exécuter à la fois dans une version 32 bits et 64 bits du Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="126e0-225">By default, .NET assemblies can run in both a 32-bit and 64-bit version of the .NET runtime.</span></span> <span data-ttu-id="126e0-226">L’application doit attendre jusqu’à l’exécution pour décider des définitions précédentes à utiliser.</span><span class="sxs-lookup"><span data-stu-id="126e0-226">The app must wait until run time to decide which of the previous definitions to use.</span></span>

<span data-ttu-id="126e0-227">L’extrait de code suivant montre un exemple montrant comment choisir entre la définition 32 bits et 64 bits au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="126e0-227">The following code snippet shows an example of how to choose between the 32-bit and 64-bit definition at run time.</span></span>

```CSharp
if (IntPtr.Size == 8)
{
    // Use the STRRET_64 definition
}
else
{
    Debug.Assert(IntPtr.Size == 4);
    // Use the STRRET_32 definition
}
```

## <a name="systime-sample"></a><span data-ttu-id="126e0-228">SysTime (exemple)</span><span class="sxs-lookup"><span data-stu-id="126e0-228">SysTime sample</span></span>

<span data-ttu-id="126e0-229">Cet exemple montre comment passer un pointeur d'une classe à une fonction non managée qui attend un pointeur d'une structure.</span><span class="sxs-lookup"><span data-stu-id="126e0-229">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="126e0-230">L'exemple SysTime utilise la fonction non managée ci-dessous, accompagnée de sa déclaration de fonction d'origine :</span><span class="sxs-lookup"><span data-stu-id="126e0-230">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="126e0-231">**GetSystemTime** exportée depuis Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="126e0-231">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="126e0-232">La structure d'origine passée à la fonction contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="126e0-232">The original structure passed to the function contains the following elements:</span></span>

```cpp
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
```

<span data-ttu-id="126e0-233">Dans cet exemple, la classe `SystemTime` contient les éléments de la structure d'origine représentés en tant que membres de classe.</span><span class="sxs-lookup"><span data-stu-id="126e0-233">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="126e0-234">L'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est défini pour s'assurer que les membres soient disposés en mémoire de manière séquentielle, dans l'ordre dans lequel ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="126e0-234">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="126e0-235">La classe `NativeMethods` contient un prototype managé de la méthode `GetSystemTime`, qui passe la classe `SystemTime` en tant que paramètre In/Out par défaut.</span><span class="sxs-lookup"><span data-stu-id="126e0-235">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="126e0-236">Le paramètre doit être déclaré avec les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute>, car les classes, qui sont des types référence, sont passées en tant que paramètres In par défaut.</span><span class="sxs-lookup"><span data-stu-id="126e0-236">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="126e0-237">Pour que l’appelant reçoive les résultats, ces [attributs directionnels](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) doivent être appliqués de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="126e0-237">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="126e0-238">La classe `App` crée une nouvelle instance de la classe `SystemTime` et accède à ses champs de données.</span><span class="sxs-lookup"><span data-stu-id="126e0-238">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="126e0-239">Exemples de code</span><span class="sxs-lookup"><span data-stu-id="126e0-239">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="126e0-240">OutArrayOfStructs (exemple)</span><span class="sxs-lookup"><span data-stu-id="126e0-240">OutArrayOfStructs sample</span></span>

<span data-ttu-id="126e0-241">Cet exemple montre comment passer un tableau de structures contenant des entiers et des chaînes comme paramètres Out à une fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="126e0-241">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="126e0-242">Cet exemple montre comment appeler une fonction native à l'aide de la classe <xref:System.Runtime.InteropServices.Marshal> et à l'aide de code unsafe.</span><span class="sxs-lookup"><span data-stu-id="126e0-242">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="126e0-243">Cet exemple utilise des fonctions wrapper et des appels de code non managé définis dans [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), également fournis dans les fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="126e0-243">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="126e0-244">Il utilise la fonction `TestOutArrayOfStructs` et la structure `MYSTRSTRUCT2`.</span><span class="sxs-lookup"><span data-stu-id="126e0-244">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="126e0-245">La structure contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="126e0-245">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="126e0-246">La classe `MyStruct` contient un objet chaîne composé de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="126e0-246">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="126e0-247">Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> spécifie le format ANSI.</span><span class="sxs-lookup"><span data-stu-id="126e0-247">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="126e0-248">`MyUnsafeStruct` est une structure contenant un type <xref:System.IntPtr> plutôt qu'une chaîne.</span><span class="sxs-lookup"><span data-stu-id="126e0-248">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="126e0-249">La classe `NativeMethods` contient la méthode de prototype surchargée `TestOutArrayOfStructs`.</span><span class="sxs-lookup"><span data-stu-id="126e0-249">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="126e0-250">Si une méthode déclare un pointeur en tant que paramètre, la classe doit être marquée avec le mot clé `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="126e0-250">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="126e0-251">Étant donné que Visual Basic ne peut pas utiliser de code unsafe, la méthode surchargée, le modificateur unsafe et la structure `MyUnsafeStruct` ne sont pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="126e0-251">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="126e0-252">La classe `App` implémente la méthode `UsingMarshaling` qui effectue toutes les tâches nécessaires au passage du tableau.</span><span class="sxs-lookup"><span data-stu-id="126e0-252">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="126e0-253">Le tableau est marqué avec le mot clé `out` (`ByRef` en Visual Basic) pour indiquer que les données passent de l'appelé à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="126e0-253">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="126e0-254">L'implémentation utilise les méthodes de la classe <xref:System.Runtime.InteropServices.Marshal> suivantes :</span><span class="sxs-lookup"><span data-stu-id="126e0-254">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="126e0-255"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> pour marshaler des données à partir de la mémoire tampon non managée vers un objet managé.</span><span class="sxs-lookup"><span data-stu-id="126e0-255"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="126e0-256"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> pour libérer la mémoire réservée aux chaînes de la structure.</span><span class="sxs-lookup"><span data-stu-id="126e0-256"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="126e0-257"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> pour libérer la mémoire réservée au tableau.</span><span class="sxs-lookup"><span data-stu-id="126e0-257"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="126e0-258">Comme mentionné précédemment, le langage C# autorise le code unsafe, contrairement à Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="126e0-258">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="126e0-259">Dans l'exemple C#, `UsingUnsafePointer` est une autre implémentation de méthode qui utilise des pointeurs plutôt que la classe <xref:System.Runtime.InteropServices.Marshal> pour passer le tableau contenant la structure `MyUnsafeStruct`.</span><span class="sxs-lookup"><span data-stu-id="126e0-259">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="126e0-260">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="126e0-260">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="126e0-261">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="126e0-261">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="126e0-262">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="126e0-262">See also</span></span>

- [<span data-ttu-id="126e0-263">Marshaling de données à l’aide de l’appel de code managé</span><span class="sxs-lookup"><span data-stu-id="126e0-263">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="126e0-264">Marshaling de chaînes</span><span class="sxs-lookup"><span data-stu-id="126e0-264">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="126e0-265">Marshaling de différents types de tableaux</span><span class="sxs-lookup"><span data-stu-id="126e0-265">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
