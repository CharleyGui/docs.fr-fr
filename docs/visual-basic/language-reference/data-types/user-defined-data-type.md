---
title: Type de données défini par l’utilisateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 42aecd0a5d948ab76d7bd11990d4cdbdce611015
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646947"
---
# <a name="user-defined-data-type"></a><span data-ttu-id="0fdee-102">Type de données défini par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0fdee-102">User-Defined Data Type</span></span>
<span data-ttu-id="0fdee-103">Contient des données dans un format que vous définissez.</span><span class="sxs-lookup"><span data-stu-id="0fdee-103">Holds data in a format you define.</span></span> <span data-ttu-id="0fdee-104">La `Structure` instruction définit le format.</span><span class="sxs-lookup"><span data-stu-id="0fdee-104">The `Structure` statement defines the format.</span></span>  
  
 <span data-ttu-id="0fdee-105">Les versions précédentes de Visual Basic prennent en charge le type défini par l’utilisateur (UDT).</span><span class="sxs-lookup"><span data-stu-id="0fdee-105">Previous versions of Visual Basic support the user-defined type (UDT).</span></span> <span data-ttu-id="0fdee-106">La version actuelle développe l’UDT puisse un *structure*.</span><span class="sxs-lookup"><span data-stu-id="0fdee-106">The current version expands the UDT to a *structure*.</span></span> <span data-ttu-id="0fdee-107">Une structure est une concaténation d’une ou plusieurs *membres* de différents types de données.</span><span class="sxs-lookup"><span data-stu-id="0fdee-107">A structure is a concatenation of one or more *members* of various data types.</span></span> <span data-ttu-id="0fdee-108">Visual Basic traite une structure comme une unité unique, bien que vous pouvez également accéder à ses membres individuellement.</span><span class="sxs-lookup"><span data-stu-id="0fdee-108">Visual Basic treats a structure as a single unit, although you can also access its members individually.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fdee-109">Notes</span><span class="sxs-lookup"><span data-stu-id="0fdee-109">Remarks</span></span>  
 <span data-ttu-id="0fdee-110">Définir et utiliser un type de données de structure lorsque vous avez besoin combiner différents types de données en une seule unité, ou lorsque aucun des types de données élémentaires répondre à vos besoins.</span><span class="sxs-lookup"><span data-stu-id="0fdee-110">Define and use a structure data type when you need to combine various data types into a single unit, or when none of the elementary data types serve your needs.</span></span>  
  
 <span data-ttu-id="0fdee-111">La valeur par défaut d’un type de données de structure se compose de la combinaison des valeurs par défaut de chacun de ses membres.</span><span class="sxs-lookup"><span data-stu-id="0fdee-111">The default value of a structure data type consists of the combination of the default values of each of its members.</span></span>  
  
## <a name="declaration-format"></a><span data-ttu-id="0fdee-112">Format de déclaration</span><span class="sxs-lookup"><span data-stu-id="0fdee-112">Declaration Format</span></span>  
 <span data-ttu-id="0fdee-113">Une déclaration de structure démarre avec le [instruction Structure](../../../visual-basic/language-reference/statements/structure-statement.md) et se termine par le `End Structure` instruction.</span><span class="sxs-lookup"><span data-stu-id="0fdee-113">A structure declaration starts with the [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) and ends with the `End Structure` statement.</span></span> <span data-ttu-id="0fdee-114">La `Structure` instruction fournit le nom de la structure, qui est également l’identificateur du type de données défini par la structure.</span><span class="sxs-lookup"><span data-stu-id="0fdee-114">The `Structure` statement supplies the name of the structure, which is also the identifier of the data type the structure is defining.</span></span> <span data-ttu-id="0fdee-115">Autres parties du code peuvent utiliser cet identificateur pour déclarer des variables, paramètres et fonction retournent des valeurs de type de données de cette structure.</span><span class="sxs-lookup"><span data-stu-id="0fdee-115">Other parts of the code can use this identifier to declare variables, parameters, and function return values to be of this structure's data type.</span></span>  
  
 <span data-ttu-id="0fdee-116">Les déclarations entre le `Structure` et `End Structure` instructions définissent les membres de la structure.</span><span class="sxs-lookup"><span data-stu-id="0fdee-116">The declarations between the `Structure` and `End Structure` statements define the members of the structure.</span></span>  
  
## <a name="member-access-levels"></a><span data-ttu-id="0fdee-117">Niveaux d’accès de membre</span><span class="sxs-lookup"><span data-stu-id="0fdee-117">Member Access Levels</span></span>  
 <span data-ttu-id="0fdee-118">Vous devez déclarer chaque membre à l’aide un [instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md) ou une instruction qui spécifie le niveau d’accès, tel que [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), ou [privé](../../../visual-basic/language-reference/modifiers/private.md).</span><span class="sxs-lookup"><span data-stu-id="0fdee-118">You must declare every member using a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) or a statement that specifies access level, such as [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../visual-basic/language-reference/modifiers/private.md).</span></span> <span data-ttu-id="0fdee-119">Si vous utilisez un `Dim` instruction, les valeurs par défaut au niveau de l’accès public.</span><span class="sxs-lookup"><span data-stu-id="0fdee-119">If you use a `Dim` statement, the access level defaults to public.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="0fdee-120">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="0fdee-120">Programming Tips</span></span>  
  
- <span data-ttu-id="0fdee-121">**Consommation de mémoire.**</span><span class="sxs-lookup"><span data-stu-id="0fdee-121">**Memory Consumption.**</span></span> <span data-ttu-id="0fdee-122">Comme avec tous les types de données composites, vous ne peut pas calculer en toute sécurité la consommation totale de la mémoire d’une structure en additionnant les allocations de stockage nominal de ses membres.</span><span class="sxs-lookup"><span data-stu-id="0fdee-122">As with all composite data types, you cannot safely calculate the total memory consumption of a structure by adding together the nominal storage allocations of its members.</span></span> <span data-ttu-id="0fdee-123">En outre, vous ne pouvez pas raisonnablement supposer que l’ordre de stockage en mémoire est identique à l’ordre de déclaration.</span><span class="sxs-lookup"><span data-stu-id="0fdee-123">Furthermore, you cannot safely assume that the order of storage in memory is the same as your order of declaration.</span></span> <span data-ttu-id="0fdee-124">Si vous avez besoin contrôler la disposition de stockage d’une structure, vous pouvez appliquer le <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut le `Structure` instruction.</span><span class="sxs-lookup"><span data-stu-id="0fdee-124">If you need to control the storage layout of a structure, you can apply the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute to the `Structure` statement.</span></span>  
  
- <span data-ttu-id="0fdee-125">**Considérations sur l’interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="0fdee-125">**Interop Considerations.**</span></span> <span data-ttu-id="0fdee-126">Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types définis par l’utilisateur dans d’autres environnements ne sont pas compatibles avec Visual Basic les types de structure.</span><span class="sxs-lookup"><span data-stu-id="0fdee-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that user-defined types in other environments are not compatible with Visual Basic structure types.</span></span>  
  
- <span data-ttu-id="0fdee-127">**Étendues.**</span><span class="sxs-lookup"><span data-stu-id="0fdee-127">**Widening.**</span></span> <span data-ttu-id="0fdee-128">Il n’existe aucune conversion automatique vers ou à partir de n’importe quel type de données de structure.</span><span class="sxs-lookup"><span data-stu-id="0fdee-128">There is no automatic conversion to or from any structure data type.</span></span> <span data-ttu-id="0fdee-129">Vous pouvez définir des opérateurs de conversion sur votre structure à l’aide de la [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), et vous pouvez déclarer chaque opérateur de conversion pour être `Widening` ou `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="0fdee-129">You can define conversion operators on your structure using the [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md), and you can declare each conversion operator to be `Widening` or `Narrowing`.</span></span>  
  
- <span data-ttu-id="0fdee-130">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="0fdee-130">**Type Characters.**</span></span> <span data-ttu-id="0fdee-131">Types de données de structure n’ont aucun caractère de type littéral ou un caractère de type identificateur.</span><span class="sxs-lookup"><span data-stu-id="0fdee-131">Structure data types have no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="0fdee-132">**Type de Framework.**</span><span class="sxs-lookup"><span data-stu-id="0fdee-132">**Framework Type.**</span></span> <span data-ttu-id="0fdee-133">Il n’existe pas de type correspondant dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0fdee-133">There is no corresponding type in the .NET Framework.</span></span> <span data-ttu-id="0fdee-134">Toutes les structures héritent de la classe .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, mais aucune structure individuelle ne correspond à <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0fdee-134">All structures inherit from the .NET Framework class <xref:System.ValueType?displayProperty=nameWithType>, but no individual structure corresponds to <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fdee-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="0fdee-135">Example</span></span>  
 <span data-ttu-id="0fdee-136">Le paradigme suivant montre le contour de la déclaration d’une structure.</span><span class="sxs-lookup"><span data-stu-id="0fdee-136">The following paradigm shows the outline of the declaration of a structure.</span></span>  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fdee-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fdee-137">See also</span></span>

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [<span data-ttu-id="0fdee-138">Types de données</span><span class="sxs-lookup"><span data-stu-id="0fdee-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="0fdee-139">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="0fdee-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="0fdee-140">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="0fdee-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="0fdee-141">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="0fdee-141">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="0fdee-142">Widening</span><span class="sxs-lookup"><span data-stu-id="0fdee-142">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="0fdee-143">Narrowing</span><span class="sxs-lookup"><span data-stu-id="0fdee-143">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="0fdee-144">Structures</span><span class="sxs-lookup"><span data-stu-id="0fdee-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0fdee-145">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="0fdee-145">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
