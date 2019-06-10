---
title: Enregistrements
description: Découvrez comment F# enregistrements représentent des agrégats simples de valeurs nommées, éventuellement avec des membres.
ms.date: 06/09/2019
ms.openlocfilehash: cfb8de8272b479571119ae4cf91ea1d6fd5db73c
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816193"
---
# <a name="records"></a><span data-ttu-id="4b86c-103">Enregistrements</span><span class="sxs-lookup"><span data-stu-id="4b86c-103">Records</span></span>

<span data-ttu-id="4b86c-104">Les enregistrements représentent des agrégats simples de valeurs nommées, éventuellement avec des membres.</span><span class="sxs-lookup"><span data-stu-id="4b86c-104">Records represent simple aggregates of named values, optionally with members.</span></span> <span data-ttu-id="4b86c-105">Ils peuvent être soit les types de structures ou de référence.</span><span class="sxs-lookup"><span data-stu-id="4b86c-105">They can either be structs or reference types.</span></span>  <span data-ttu-id="4b86c-106">Ils sont des types de référence par défaut.</span><span class="sxs-lookup"><span data-stu-id="4b86c-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b86c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b86c-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="4b86c-108">Notes</span><span class="sxs-lookup"><span data-stu-id="4b86c-108">Remarks</span></span>

<span data-ttu-id="4b86c-109">Dans la syntaxe précédente, *typename* est le nom du type d’enregistrement, *label1* et *label2* sont des noms de valeurs, appelés *étiquettes*, et *type1* et *type2* sont les types de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="4b86c-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="4b86c-110">*liste des membres* est la liste facultative de membres pour le type.</span><span class="sxs-lookup"><span data-stu-id="4b86c-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="4b86c-111">Vous pouvez utiliser le `[<Struct>]` attribut pour créer un enregistrement struct plutôt qu’un enregistrement qui est un type référence.</span><span class="sxs-lookup"><span data-stu-id="4b86c-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="4b86c-112">Voici quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="4b86c-112">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="4b86c-113">Lorsque chaque étiquette se trouve sur une ligne distincte, le point-virgule est facultatif.</span><span class="sxs-lookup"><span data-stu-id="4b86c-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="4b86c-114">Vous pouvez définir des valeurs dans les expressions appelées *enregistrer expressions*.</span><span class="sxs-lookup"><span data-stu-id="4b86c-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="4b86c-115">Le compilateur déduit le type à partir des étiquettes utilisées (si les étiquettes sont suffisamment différents de ceux des autres types d’enregistrements).</span><span class="sxs-lookup"><span data-stu-id="4b86c-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="4b86c-116">Accolades ({}) placez l’expression d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="4b86c-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="4b86c-117">Le code suivant montre une expression d’enregistrement qui initialise un enregistrement avec trois éléments flottants avec des étiquettes `x`, `y` et `z`.</span><span class="sxs-lookup"><span data-stu-id="4b86c-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="4b86c-118">S’il peut y avoir un autre type qui possède également les étiquettes de mêmes, n’utilisez pas la forme abrégée.</span><span class="sxs-lookup"><span data-stu-id="4b86c-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="4b86c-119">Les étiquettes de type le plus récemment déclaré ont priorité sur ceux du type déclaré précédemment, c’est le cas dans l’exemple précédent, `mypoint3D` est déduite comme étant `Point3D`.</span><span class="sxs-lookup"><span data-stu-id="4b86c-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="4b86c-120">Vous pouvez spécifier explicitement le type d’enregistrement, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4b86c-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="4b86c-121">Méthodes peuvent être définies pour les types d’enregistrements comme pour les types de classe.</span><span class="sxs-lookup"><span data-stu-id="4b86c-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="4b86c-122">Création d’enregistrements à l’aide d’Expressions d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="4b86c-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="4b86c-123">Vous pouvez initialiser des enregistrements en utilisant les étiquettes qui sont définis dans l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="4b86c-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="4b86c-124">Une expression qui s’en charge est appelée un *enregistrement expression*.</span><span class="sxs-lookup"><span data-stu-id="4b86c-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="4b86c-125">Utiliser des accolades pour encadrer l’expression d’enregistrement et le point-virgule comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="4b86c-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="4b86c-126">L’exemple suivant montre comment créer un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="4b86c-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="4b86c-127">Les points-virgules après le dernier champ dans l’expression d’enregistrement et dans la définition de type sont facultatifs, que les champs soient tous sur une ligne.</span><span class="sxs-lookup"><span data-stu-id="4b86c-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="4b86c-128">Lorsque vous créez un enregistrement, vous devez fournir des valeurs pour chaque champ.</span><span class="sxs-lookup"><span data-stu-id="4b86c-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="4b86c-129">Vous ne pouvez pas référencer les valeurs des autres champs dans l’expression d’initialisation pour n’importe quel champ.</span><span class="sxs-lookup"><span data-stu-id="4b86c-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="4b86c-130">Dans le code suivant, le type de `myRecord2` est déduit des noms des champs.</span><span class="sxs-lookup"><span data-stu-id="4b86c-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="4b86c-131">Si vous le souhaitez, vous pouvez spécifier le nom de type explicitement.</span><span class="sxs-lookup"><span data-stu-id="4b86c-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="4b86c-132">Une autre forme de construction d’enregistrement peut être utile lorsque vous devez copier un enregistrement existant et éventuellement modifier certaines valeurs de champ.</span><span class="sxs-lookup"><span data-stu-id="4b86c-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="4b86c-133">La ligne de code suivante illustre cela.</span><span class="sxs-lookup"><span data-stu-id="4b86c-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="4b86c-134">Cette forme de l’expression d’enregistrement est appelée le *copier et mettre à jour d’expression d’enregistrement*.</span><span class="sxs-lookup"><span data-stu-id="4b86c-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="4b86c-135">Les enregistrements sont immuables par défaut ; Toutefois, vous pouvez créer facilement des enregistrements modifiés à l’aide d’une expression de copie et de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="4b86c-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="4b86c-136">Vous pouvez également spécifier explicitement un champ mutable.</span><span class="sxs-lookup"><span data-stu-id="4b86c-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="4b86c-137">N’utilisez pas l’attribut DefaultValue avec des champs d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="4b86c-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="4b86c-138">Une meilleure approche consiste à définir les instances par défaut des enregistrements avec des champs qui sont initialisées aux valeurs par défaut et utiliser une copie, puis mettre à jour d’expression d’enregistrement pour définir tous les champs qui diffèrent des valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="4b86c-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="creating-mutually-recursive-records"></a><span data-ttu-id="4b86c-139">Création de mutuellement récursives enregistrements</span><span class="sxs-lookup"><span data-stu-id="4b86c-139">Creating Mutually Recursive Records</span></span>

<span data-ttu-id="4b86c-140">Un certain temps lorsque vous créez un enregistrement, vous souhaiterez probablement qu’il dépend d’un autre type que vous souhaitez définir par la suite.</span><span class="sxs-lookup"><span data-stu-id="4b86c-140">Sometime when creating a record, you may want to have it depend on another type that you would like to define afterwards.</span></span> <span data-ttu-id="4b86c-141">Il s’agit d’une erreur de compilation, sauf si vous définissez les types d’enregistrement pour être mutuellement récursives.</span><span class="sxs-lookup"><span data-stu-id="4b86c-141">This is a compile error unless you define the record types to be mutually recursive.</span></span>

<span data-ttu-id="4b86c-142">Définition mutuellement récursives enregistrements est effectuée avec la `and` mot clé.</span><span class="sxs-lookup"><span data-stu-id="4b86c-142">Defining mutually recursive records is done with the `and` keyword.</span></span> <span data-ttu-id="4b86c-143">Cela vous permet de relier les types de 2 ou plus d’enregistrements.</span><span class="sxs-lookup"><span data-stu-id="4b86c-143">This lets you link 2 or more record types together.</span></span>

<span data-ttu-id="4b86c-144">Par exemple, le code suivant définit un `Person` et `Address` type comme mutuellement récursives :</span><span class="sxs-lookup"><span data-stu-id="4b86c-144">For example, the following code defines a `Person` and `Address` type as mutually recursive:</span></span>

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string }
```

<span data-ttu-id="4b86c-145">Si vous deviez définir l’exemple précédent, sans le `and` mot clé, puis il n’est pas compilée.</span><span class="sxs-lookup"><span data-stu-id="4b86c-145">If you were to define the previous example without the `and` keyword, then it would not compile.</span></span> <span data-ttu-id="4b86c-146">Le `and` mot clé est requise pour les définitions récursives s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="4b86c-146">The `and` keyword is required for mutually recursive definitions.</span></span>

## <a name="pattern-matching-with-records"></a><span data-ttu-id="4b86c-147">Critères spéciaux avec enregistrements</span><span class="sxs-lookup"><span data-stu-id="4b86c-147">Pattern Matching with Records</span></span>

<span data-ttu-id="4b86c-148">Enregistrements peuvent être utilisés avec les critères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="4b86c-148">Records can be used with pattern matching.</span></span> <span data-ttu-id="4b86c-149">Vous pouvez spécifier des champs explicitement et fournir des variables pour les autres champs qui seront affectés lors d’une correspondance est trouvée.</span><span class="sxs-lookup"><span data-stu-id="4b86c-149">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="4b86c-150">L'exemple de code suivant illustre ceci.</span><span class="sxs-lookup"><span data-stu-id="4b86c-150">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="4b86c-151">La sortie de ce code est comme suit.</span><span class="sxs-lookup"><span data-stu-id="4b86c-151">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="4b86c-152">Différences entre les Classes et les enregistrements</span><span class="sxs-lookup"><span data-stu-id="4b86c-152">Differences Between Records and Classes</span></span>

<span data-ttu-id="4b86c-153">Champs d’enregistrement diffèrent des classes dans la mesure où ils sont automatiquement exposés en tant que propriétés, et ils sont utilisés dans la création et de copie d’enregistrements.</span><span class="sxs-lookup"><span data-stu-id="4b86c-153">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="4b86c-154">Construction d’enregistrement diffère également de construction de classe.</span><span class="sxs-lookup"><span data-stu-id="4b86c-154">Record construction also differs from class construction.</span></span> <span data-ttu-id="4b86c-155">Dans un type d’enregistrement, vous ne pouvez pas définir un constructeur.</span><span class="sxs-lookup"><span data-stu-id="4b86c-155">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="4b86c-156">Au lieu de cela, la syntaxe de construction décrite dans cette rubrique s’applique.</span><span class="sxs-lookup"><span data-stu-id="4b86c-156">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="4b86c-157">Classes n’ont aucune relation directe entre les paramètres du constructeur, des champs et propriétés.</span><span class="sxs-lookup"><span data-stu-id="4b86c-157">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="4b86c-158">Comme les types d’union et de structure, les enregistrements ont une sémantique d’égalité structurelle.</span><span class="sxs-lookup"><span data-stu-id="4b86c-158">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="4b86c-159">Classes ont référence une sémantique d’égalité.</span><span class="sxs-lookup"><span data-stu-id="4b86c-159">Classes have reference equality semantics.</span></span> <span data-ttu-id="4b86c-160">L'exemple de code suivant illustre cette tâche.</span><span class="sxs-lookup"><span data-stu-id="4b86c-160">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="4b86c-161">La sortie de ce code est comme suit :</span><span class="sxs-lookup"><span data-stu-id="4b86c-161">The output of this code is as follows:</span></span>

```
The records are equal.
```

<span data-ttu-id="4b86c-162">Si vous écrivez le même code avec les classes, les deux objets de classe seraient inégaux, car les deux valeurs représenteraient deux objets sur le tas et seules les adresses seraient comparées (à moins que le type de la classe substitue la `System.Object.Equals` méthode).</span><span class="sxs-lookup"><span data-stu-id="4b86c-162">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="4b86c-163">Si vous avez besoin de référencer l’égalité des enregistrements, ajoutez l’attribut `[<ReferenceEquality>]` au-dessus de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="4b86c-163">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b86c-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b86c-164">See also</span></span>

- [<span data-ttu-id="4b86c-165">Types F#</span><span class="sxs-lookup"><span data-stu-id="4b86c-165">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="4b86c-166">Classes</span><span class="sxs-lookup"><span data-stu-id="4b86c-166">Classes</span></span>](classes.md)
- [<span data-ttu-id="4b86c-167">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="4b86c-167">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4b86c-168">Égalité de référence</span><span class="sxs-lookup"><span data-stu-id="4b86c-168">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [<span data-ttu-id="4b86c-169">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="4b86c-169">Pattern Matching</span></span>](pattern-matching.md)
