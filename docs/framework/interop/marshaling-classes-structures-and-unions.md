---
title: Marshaling de classes, de structures, et d'unions
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
ms.openlocfilehash: d761d8ed7488e99f29d4844d061867915a624b96
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960004"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="5b7b7-102">Marshaling de classes, de structures, et d'unions</span><span class="sxs-lookup"><span data-stu-id="5b7b7-102">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="5b7b7-103">Les classes et les structures sont similaires dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="5b7b7-104">Elles peuvent toutes deux posséder des champs, des propriétés et des événements.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="5b7b7-105">Elles peuvent également posséder des méthodes statiques et non statiques.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="5b7b7-106">Une différence notable existe toutefois : les structures sont des types valeur et les classes sont des types référence.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-106">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="5b7b7-107">Le tableau suivant répertorie les options de marshaling pour les classes, les structures et les unions. Il décrit leur utilisation et fournit un lien vers l'exemple d'appel de code non managé correspondant.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="5b7b7-108">Type</span><span class="sxs-lookup"><span data-stu-id="5b7b7-108">Type</span></span>|<span data-ttu-id="5b7b7-109">Description</span><span class="sxs-lookup"><span data-stu-id="5b7b7-109">Description</span></span>|<span data-ttu-id="5b7b7-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="5b7b7-110">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="5b7b7-111">Classe par valeur.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-111">Class by value.</span></span>|<span data-ttu-id="5b7b7-112">Passe une classe avec des membres entiers en tant que paramètre In/Out, comme le cas managé.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="5b7b7-113">SysTime (exemple)</span><span class="sxs-lookup"><span data-stu-id="5b7b7-113">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="5b7b7-114">Structure par valeur.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-114">Structure by value.</span></span>|<span data-ttu-id="5b7b7-115">Passe des structures en tant que paramètres In.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-115">Passes structures as In parameters.</span></span>|[<span data-ttu-id="5b7b7-116">Exemple de structures</span><span class="sxs-lookup"><span data-stu-id="5b7b7-116">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="5b7b7-117">Structure par référence.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-117">Structure by reference.</span></span>|<span data-ttu-id="5b7b7-118">Passe des structures en tant que paramètres In/Out.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="5b7b7-119">[OSInfo (exemple)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5b7b7-119">[OSInfo sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="5b7b7-120">Structure avec structures imbriquées (aplaties).</span><span class="sxs-lookup"><span data-stu-id="5b7b7-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="5b7b7-121">Passe une classe représentant une structure avec structures imbriquées dans la fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="5b7b7-122">La structure est aplatie sous la forme d'une même grande structure dans le prototype managé.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-122">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="5b7b7-123">FindFile (exemple)</span><span class="sxs-lookup"><span data-stu-id="5b7b7-123">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="5b7b7-124">Structure avec un pointeur vers une autre structure.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="5b7b7-125">Passe une structure contenant un pointeur vers une autre structure en tant que membre.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="5b7b7-126">Exemple structures</span><span class="sxs-lookup"><span data-stu-id="5b7b7-126">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="5b7b7-127">Tableau de structures avec des entiers par valeur.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="5b7b7-128">Passe un tableau de structures contenant uniquement des entiers en tant que paramètre In/Out.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="5b7b7-129">Les membres du tableau peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-129">Members of the array can be changed.</span></span>|[<span data-ttu-id="5b7b7-130">Arrays, exemple</span><span class="sxs-lookup"><span data-stu-id="5b7b7-130">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="5b7b7-131">Tableau de structures avec des entiers et des chaînes par référence.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="5b7b7-132">Passe un tableau de structures contenant des entiers et des chaînes en tant que paramètre Out.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="5b7b7-133">La fonction appelée alloue de la mémoire pour le tableau.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-133">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="5b7b7-134">OutArrayOfStructs, exemple</span><span class="sxs-lookup"><span data-stu-id="5b7b7-134">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="5b7b7-135">Unions avec types valeur.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-135">Unions with value types.</span></span>|<span data-ttu-id="5b7b7-136">Passe des unions avec des types valeur (entier et double).</span><span class="sxs-lookup"><span data-stu-id="5b7b7-136">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="5b7b7-137">Unions (exemple)</span><span class="sxs-lookup"><span data-stu-id="5b7b7-137">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="5b7b7-138">Unions avec types mixtes.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-138">Unions with mixed types.</span></span>|<span data-ttu-id="5b7b7-139">Passe des unions avec des types mixtes (entier et chaîne).</span><span class="sxs-lookup"><span data-stu-id="5b7b7-139">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="5b7b7-140">Unions (exemple)</span><span class="sxs-lookup"><span data-stu-id="5b7b7-140">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="5b7b7-141">Valeurs Null dans la structure.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-141">Null values in structure.</span></span>|<span data-ttu-id="5b7b7-142">Passe une référence null (**Nothing** en Visual Basic) au lieu d’une référence à un type valeur.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="5b7b7-143">[HandleRef (exemple)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5b7b7-143">[HandleRef sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="5b7b7-144">Exemple de structures</span><span class="sxs-lookup"><span data-stu-id="5b7b7-144">Structures sample</span></span>

<span data-ttu-id="5b7b7-145">Cet exemple montre comment passer une structure qui pointe vers une autre structure, comment passer une structure avec structure incorporée et comment passer une structure avec tableau incorporé.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="5b7b7-146">L'exemple Structures utilise les fonctions non managées ci-dessous, accompagnées de leur déclaration de fonction d'origine :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="5b7b7-147">**TestStructInStruct** exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="5b7b7-148">**TestStructInStruct3** exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="5b7b7-149">**TestArrayInStruct** exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="5b7b7-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) est une bibliothèque non managée personnalisée qui contient des implémentations des fonctions précédemment répertoriées, ainsi que quatre structures : **MYPERSON**, **MYPERSON2**, **MYPERSON3** et **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-150">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="5b7b7-151">Ces structures contiennent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-151">These structures contain the following elements:</span></span>

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

<span data-ttu-id="5b7b7-152">Les structures managées `MyPerson`,`MyPerson2`, `MyPerson3` et `MyArrayStruct` ont les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="5b7b7-153">`MyPerson` contient uniquement des membres de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="5b7b7-154">Le champ [CharSet](specifying-a-character-set.md) affecte le format ANSI aux chaînes quand elles sont passées à la fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-154">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="5b7b7-155">`MyPerson2`contient un **IntPtr** à la `MyPerson` structure.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="5b7b7-156">Le type **IntPtr** remplace le pointeur d’origine vers la structure non managée, car les applications .NET Framework n’utilisent pas de pointeurs, sauf si le code est marqué comme étant **unsafe**.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="5b7b7-157">`MyPerson3` contient `MyPerson` comme structure incorporée.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="5b7b7-158">Une structure incorporée dans une autre structure peut être aplatie en plaçant les éléments de la structure incorporée directement dans la structure principale. Elle peut également être conservée comme une structure incorporée, comme dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="5b7b7-159">`MyArrayStruct` contient un tableau d'entiers.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="5b7b7-160">L’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> définit la valeur d’énumération <xref:System.Runtime.InteropServices.UnmanagedType> sur **ByValArray**, qui est utilisée pour indiquer le nombre d’éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="5b7b7-161">Pour toutes les structures de cet exemple, l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est appliqué pour garantir que les membres soient classés de manière séquentielle dans la mémoire, dans l'ordre dans lequel ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="5b7b7-162">La classe `NativeMethods` contient des prototypes managés pour les méthodes `TestStructInStruct`, `TestStructInStruct3` et `TestArrayInStruct` appelées par la classe `App`.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-162">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="5b7b7-163">Chaque prototype déclare un seul paramètre de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-163">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="5b7b7-164">`TestStructInStruct` déclare une référence au type `MyPerson2` comme son paramètre.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="5b7b7-165">`TestStructInStruct3` déclare le type `MyPerson3` en tant que paramètre et passe le paramètre par valeur.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="5b7b7-166">`TestArrayInStruct` déclare une référence au type `MyArrayStruct` comme son paramètre.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="5b7b7-167">Les structures en tant qu’arguments de méthodes sont passées par valeur, sauf si le paramètre contient le mot clé **ref** (**ByRef** dans Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5b7b7-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="5b7b7-168">Par exemple, la méthode `TestStructInStruct` passe une référence (la valeur d'une adresse) à un objet de type `MyPerson2` au code non managé.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="5b7b7-169">Pour manipuler la structure vers laquelle pointe `MyPerson2`, l'exemple crée une mémoire tampon d'une taille spécifiée et retourne son adresse en combinant les méthodes <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> et <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="5b7b7-170">Ensuite, l'exemple copie le contenu de la structure managée vers la mémoire tampon non managée.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="5b7b7-171">Enfin, l'exemple utilise la méthode <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> pour marshaler des données à partir de la mémoire tampon non managée vers un objet managé, ainsi que la méthode <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> pour libérer le bloc de mémoire non managé.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="5b7b7-172">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="5b7b7-172">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="5b7b7-173">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="5b7b7-173">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="5b7b7-174">FindFile (exemple)</span><span class="sxs-lookup"><span data-stu-id="5b7b7-174">FindFile sample</span></span>

<span data-ttu-id="5b7b7-175">Cet exemple montre comment passer une structure qui contient une autre structure incorporée à une fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-175">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="5b7b7-176">Il montre également comment utiliser l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> pour déclarer un tableau de longueur fixe au sein de la structure.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-176">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="5b7b7-177">Dans cet exemple, les éléments de la structure incorporée sont ajoutés à la structure parent.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-177">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="5b7b7-178">Pour obtenir un exemple de structure incorporée non aplatie, consultez [Exemples de structures](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5b7b7-178">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="5b7b7-179">L'exemple FindFile utilise la fonction non managée ci-dessous, accompagnée de sa déclaration de fonction d'origine :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-179">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="5b7b7-180">**FindFirstFile** exportée depuis Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-180">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="5b7b7-181">La structure d'origine passée à la fonction contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-181">The original structure passed to the function contains the following elements:</span></span>

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

<span data-ttu-id="5b7b7-182">Dans cet exemple, la classe `FindData` contient un membre de données correspondant pour chaque élément de la structure d'origine et de la structure incorporée.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-182">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="5b7b7-183">À la place des deux tampons caractère d'origine, la classe substitue des chaînes.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-183">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="5b7b7-184">**MarshalAsAttribute** définit l’énumération <xref:System.Runtime.InteropServices.UnmanagedType> sur **ByValTStr**, qui est utilisé pour identifier les tableaux de caractères de longueur fixe inline qui apparaissent au sein des structures non managées.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-184">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="5b7b7-185">La classe `NativeMethods` contient un prototype managé de la méthode `FindFirstFile`, qui passe la classe `FindData` en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-185">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="5b7b7-186">Le paramètre doit être déclaré avec les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute>, car les classes, qui sont des types référence, sont passées en tant que paramètres In par défaut.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-186">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="5b7b7-187">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="5b7b7-187">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="5b7b7-188">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="5b7b7-188">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="5b7b7-189">Unions (exemple)</span><span class="sxs-lookup"><span data-stu-id="5b7b7-189">Unions sample</span></span>

<span data-ttu-id="5b7b7-190">Cet exemple montre comment passer des structures contenant uniquement des types valeur, ainsi que des structures contenant un type valeur et une chaîne en tant que paramètres, à une fonction non managée nécessitant une union.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-190">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="5b7b7-191">Une union représente un emplacement de mémoire qui peut être partagé par plusieurs variables.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-191">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="5b7b7-192">L'exemple Unions utilise la fonction non managée ci-dessous, accompagnée de sa déclaration de fonction d'origine :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-192">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="5b7b7-193">**TestUnion** exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-193">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="5b7b7-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) est une bibliothèque non managée personnalisée qui contient une implémentation de la fonction précédemment répertoriée, ainsi que deux unions, **MYUNION** et **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-194">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="5b7b7-195">Les unions peuvent contenir les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-195">The unions contain the following elements:</span></span>

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

<span data-ttu-id="5b7b7-196">Dans du code managé, les unions sont définies en tant que structures.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-196">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="5b7b7-197">La structure `MyUnion` contient deux types valeur comme ses membres : un entier et un double.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-197">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="5b7b7-198">L'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est défini pour contrôler la position précise de chaque membre de données.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-198">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="5b7b7-199">L'attribut <xref:System.Runtime.InteropServices.FieldOffsetAttribute> fournit la position physique des champs dans la représentation non managée d'une union.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-199">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="5b7b7-200">Notez que les deux membres possèdent les mêmes valeurs de décalage. Ils peuvent donc définir la même zone de mémoire.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-200">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="5b7b7-201">`MyUnion2_1` et `MyUnion2_2` contiennent respectivement un type valeur (entier) et une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-201">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="5b7b7-202">Dans du code managé, les types valeur et les types référence ne sont pas autorisés à se chevaucher.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-202">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="5b7b7-203">Cet exemple utilise la surcharge de méthode pour permettre à l'appelant d'utiliser les deux types quand il appelle la même fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-203">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="5b7b7-204">La disposition de `MyUnion2_1` est explicite et possède une valeur de décalage précise.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-204">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="5b7b7-205">En revanche, `MyUnion2_2` possède une disposition séquentielle, car les dispositions explicites ne sont pas autorisées avec les types référence.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-205">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="5b7b7-206">L’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> définit l’énumération <xref:System.Runtime.InteropServices.UnmanagedType> sur **ByValTStr**, qui est utilisé pour les tableaux de caractères de longueur fixe inline qui apparaissent au sein de la représentation non managée de l’union.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-206">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="5b7b7-207">La classe `NativeMethods` contient les prototypes des méthodes `TestUnion` et `TestUnion2`.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-207">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="5b7b7-208">`TestUnion2` est surchargée pour déclarer `MyUnion2_1` ou `MyUnion2_2` en tant que paramètres.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-208">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="5b7b7-209">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="5b7b7-209">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="5b7b7-210">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="5b7b7-210">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="systime-sample"></a><span data-ttu-id="5b7b7-211">SysTime (exemple)</span><span class="sxs-lookup"><span data-stu-id="5b7b7-211">SysTime sample</span></span>

<span data-ttu-id="5b7b7-212">Cet exemple montre comment passer un pointeur d'une classe à une fonction non managée qui attend un pointeur d'une structure.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-212">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="5b7b7-213">L'exemple SysTime utilise la fonction non managée ci-dessous, accompagnée de sa déclaration de fonction d'origine :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-213">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="5b7b7-214">**GetSystemTime** exportée depuis Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-214">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="5b7b7-215">La structure d'origine passée à la fonction contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-215">The original structure passed to the function contains the following elements:</span></span>

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

<span data-ttu-id="5b7b7-216">Dans cet exemple, la classe `SystemTime` contient les éléments de la structure d'origine représentés en tant que membres de classe.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-216">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="5b7b7-217">L'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est défini pour s'assurer que les membres soient disposés en mémoire de manière séquentielle, dans l'ordre dans lequel ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-217">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="5b7b7-218">La classe `NativeMethods` contient un prototype managé de la méthode `GetSystemTime`, qui passe la classe `SystemTime` en tant que paramètre In/Out par défaut.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-218">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="5b7b7-219">Le paramètre doit être déclaré avec les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute>, car les classes, qui sont des types référence, sont passées en tant que paramètres In par défaut.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-219">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="5b7b7-220">Pour que l’appelant reçoive les résultats, ces [attributs directionnels](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) doivent être appliqués de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-220">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="5b7b7-221">La classe `App` crée une nouvelle instance de la classe `SystemTime` et accède à ses champs de données.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-221">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="5b7b7-222">Exemples de code</span><span class="sxs-lookup"><span data-stu-id="5b7b7-222">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="5b7b7-223">OutArrayOfStructs (exemple)</span><span class="sxs-lookup"><span data-stu-id="5b7b7-223">OutArrayOfStructs sample</span></span>

<span data-ttu-id="5b7b7-224">Cet exemple montre comment passer un tableau de structures contenant des entiers et des chaînes comme paramètres Out à une fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-224">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="5b7b7-225">Cet exemple montre comment appeler une fonction native à l'aide de la classe <xref:System.Runtime.InteropServices.Marshal> et à l'aide de code unsafe.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-225">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="5b7b7-226">Cet exemple utilise des fonctions wrapper et des appels de code non managé définis dans [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), également fournis dans les fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-226">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="5b7b7-227">Il utilise la fonction `TestOutArrayOfStructs` et la structure `MYSTRSTRUCT2`.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-227">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="5b7b7-228">La structure contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-228">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="5b7b7-229">La classe `MyStruct` contient un objet chaîne composé de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-229">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="5b7b7-230">Le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> spécifie le format ANSI.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-230">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="5b7b7-231">`MyUnsafeStruct` est une structure contenant un type <xref:System.IntPtr> plutôt qu'une chaîne.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-231">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="5b7b7-232">La classe `NativeMethods` contient la méthode de prototype surchargée `TestOutArrayOfStructs`.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-232">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="5b7b7-233">Si une méthode déclare un pointeur en tant que paramètre, la classe doit être marquée avec le mot clé `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-233">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="5b7b7-234">Étant donné que Visual Basic ne peut pas utiliser de code unsafe, la méthode surchargée, le modificateur unsafe et la structure `MyUnsafeStruct` ne sont pas nécessaires.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-234">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="5b7b7-235">La classe `App` implémente la méthode `UsingMarshaling` qui effectue toutes les tâches nécessaires au passage du tableau.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-235">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="5b7b7-236">Le tableau est marqué avec le mot clé `out` (`ByRef` en Visual Basic) pour indiquer que les données passent de l'appelé à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-236">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="5b7b7-237">L'implémentation utilise les méthodes de la classe <xref:System.Runtime.InteropServices.Marshal> suivantes :</span><span class="sxs-lookup"><span data-stu-id="5b7b7-237">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="5b7b7-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> pour marshaler des données à partir de la mémoire tampon non managée vers un objet managé.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-238"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="5b7b7-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> pour libérer la mémoire réservée aux chaînes de la structure.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-239"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="5b7b7-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> pour libérer la mémoire réservée au tableau.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-240"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="5b7b7-241">Comme mentionné précédemment, le langage C# autorise le code unsafe, contrairement à Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-241">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="5b7b7-242">Dans l'exemple C#, `UsingUnsafePointer` est une autre implémentation de méthode qui utilise des pointeurs plutôt que la classe <xref:System.Runtime.InteropServices.Marshal> pour passer le tableau contenant la structure `MyUnsafeStruct`.</span><span class="sxs-lookup"><span data-stu-id="5b7b7-242">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="5b7b7-243">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="5b7b7-243">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="5b7b7-244">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="5b7b7-244">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="5b7b7-245">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b7b7-245">See also</span></span>

- [<span data-ttu-id="5b7b7-246">Marshaling de données à l’aide de l’appel de code managé</span><span class="sxs-lookup"><span data-stu-id="5b7b7-246">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="5b7b7-247">Marshaling des chaînes</span><span class="sxs-lookup"><span data-stu-id="5b7b7-247">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="5b7b7-248">Marshaling de différents types de tableaux</span><span class="sxs-lookup"><span data-stu-id="5b7b7-248">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)
