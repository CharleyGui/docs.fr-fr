---
title: Enregistrements
description: 'Découvrez comment les enregistrements F # représentent des agrégats simples de valeurs nommées, éventuellement avec des membres.'
ms.date: 08/15/2020
ms.openlocfilehash: 2da31da0ec830d458a370e64ca105048181f5d74
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899637"
---
# <a name="records"></a><span data-ttu-id="d4220-103">Enregistrements</span><span class="sxs-lookup"><span data-stu-id="d4220-103">Records</span></span>

<span data-ttu-id="d4220-104">Les enregistrements représentent des agrégats simples de valeurs nommées, éventuellement avec des membres.</span><span class="sxs-lookup"><span data-stu-id="d4220-104">Records represent simple aggregates of named values, optionally with members.</span></span> <span data-ttu-id="d4220-105">Ils peuvent être des structs ou des types référence.</span><span class="sxs-lookup"><span data-stu-id="d4220-105">They can either be structs or reference types.</span></span>  <span data-ttu-id="d4220-106">Il s’agit de types référence par défaut.</span><span class="sxs-lookup"><span data-stu-id="d4220-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4220-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4220-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="d4220-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d4220-108">Remarks</span></span>

<span data-ttu-id="d4220-109">Dans la syntaxe précédente, *TypeName* est le nom du type d’enregistrement, *Label1* et *Label2* sont des noms de valeurs, appelés *étiquettes*, et *type1* et *type2* sont les types de ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="d4220-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="d4220-110">*member-List* est la liste facultative de membres pour le type.</span><span class="sxs-lookup"><span data-stu-id="d4220-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="d4220-111">Vous pouvez utiliser l' `[<Struct>]` attribut pour créer un enregistrement de struct plutôt qu’un enregistrement qui est un type référence.</span><span class="sxs-lookup"><span data-stu-id="d4220-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="d4220-112">Voici quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="d4220-112">Following are some examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="d4220-113">Lorsque chaque étiquette se trouve sur une ligne distincte, le point-virgule est facultatif.</span><span class="sxs-lookup"><span data-stu-id="d4220-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="d4220-114">Vous pouvez définir des valeurs dans des expressions appelées *expressions d’enregistrement*.</span><span class="sxs-lookup"><span data-stu-id="d4220-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="d4220-115">Le compilateur déduit le type à partir des étiquettes utilisées (si les étiquettes sont suffisamment distinctes de celles des autres types d’enregistrements).</span><span class="sxs-lookup"><span data-stu-id="d4220-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="d4220-116">Les accolades ({}) encadrent l’expression d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d4220-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="d4220-117">Le code suivant montre une expression d’enregistrement qui initialise un enregistrement avec trois éléments flottants avec des étiquettes `x` , `y` et `z` .</span><span class="sxs-lookup"><span data-stu-id="d4220-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="d4220-118">N’utilisez pas la forme abrégée s’il peut y avoir un autre type qui a également les mêmes étiquettes.</span><span class="sxs-lookup"><span data-stu-id="d4220-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="d4220-119">Les étiquettes du type déclaré le plus récemment sont prioritaires sur celles du type déclaré précédemment. par conséquent, dans l’exemple précédent, `mypoint3D` est déduit comme étant `Point3D` .</span><span class="sxs-lookup"><span data-stu-id="d4220-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="d4220-120">Vous pouvez spécifier explicitement le type d’enregistrement, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d4220-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="d4220-121">Les méthodes peuvent être définies pour les types d’enregistrements comme pour les types de classe.</span><span class="sxs-lookup"><span data-stu-id="d4220-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="d4220-122">Création d’enregistrements à l’aide d’expressions d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="d4220-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="d4220-123">Vous pouvez initialiser des enregistrements à l’aide des étiquettes définies dans l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d4220-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="d4220-124">Une expression qui le fait est appelée *expression d’enregistrement*.</span><span class="sxs-lookup"><span data-stu-id="d4220-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="d4220-125">Utilisez des accolades pour encadrer l’expression d’enregistrement et utilisez le point-virgule comme délimiteur.</span><span class="sxs-lookup"><span data-stu-id="d4220-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="d4220-126">L’exemple suivant montre comment créer un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d4220-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="d4220-127">Les points-virgules situés après le dernier champ dans l’expression d’enregistrement et dans la définition de type sont facultatifs, que les champs soient tous en une seule ligne ou non.</span><span class="sxs-lookup"><span data-stu-id="d4220-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="d4220-128">Lorsque vous créez un enregistrement, vous devez fournir des valeurs pour chaque champ.</span><span class="sxs-lookup"><span data-stu-id="d4220-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="d4220-129">Vous ne pouvez pas faire référence aux valeurs d’autres champs dans l’expression d’initialisation d’un champ.</span><span class="sxs-lookup"><span data-stu-id="d4220-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="d4220-130">Dans le code suivant, le type de `myRecord2` est déduit à partir des noms des champs.</span><span class="sxs-lookup"><span data-stu-id="d4220-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="d4220-131">Si vous le souhaitez, vous pouvez spécifier le nom du type explicitement.</span><span class="sxs-lookup"><span data-stu-id="d4220-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="d4220-132">Une autre forme de construction d’enregistrement peut être utile lorsque vous devez copier un enregistrement existant et éventuellement modifier certaines valeurs de champ.</span><span class="sxs-lookup"><span data-stu-id="d4220-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="d4220-133">La ligne de code suivante illustre cela.</span><span class="sxs-lookup"><span data-stu-id="d4220-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="d4220-134">Cette forme de l’expression d’enregistrement est appelée *expression d’enregistrement de copie et de mise à jour*.</span><span class="sxs-lookup"><span data-stu-id="d4220-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="d4220-135">Les enregistrements sont immuables par défaut ; Toutefois, vous pouvez facilement créer des enregistrements modifiés à l’aide d’une expression de copie et de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="d4220-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="d4220-136">Vous pouvez également spécifier explicitement un champ mutable.</span><span class="sxs-lookup"><span data-stu-id="d4220-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="d4220-137">N’utilisez pas l’attribut DefaultValue avec les champs d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d4220-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="d4220-138">Une meilleure approche consiste à définir des instances par défaut d’enregistrements avec des champs qui sont initialisés aux valeurs par défaut, puis à utiliser une expression d’enregistrement de copie et de mise à jour pour définir tous les champs qui diffèrent des valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="d4220-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

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

## <a name="creating-mutually-recursive-records"></a><span data-ttu-id="d4220-139">Création d’enregistrements mutuellement récursifs</span><span class="sxs-lookup"><span data-stu-id="d4220-139">Creating Mutually Recursive Records</span></span>

<span data-ttu-id="d4220-140">Pendant la création d’un enregistrement, vous souhaiterez peut-être qu’il dépende d’un autre type que vous aimeriez définir par la suite.</span><span class="sxs-lookup"><span data-stu-id="d4220-140">Sometime when creating a record, you may want to have it depend on another type that you would like to define afterwards.</span></span> <span data-ttu-id="d4220-141">Il s’agit d’une erreur de compilation, sauf si vous définissez les types d’enregistrements qui doivent être mutuellement récursifs.</span><span class="sxs-lookup"><span data-stu-id="d4220-141">This is a compile error unless you define the record types to be mutually recursive.</span></span>

<span data-ttu-id="d4220-142">La définition des enregistrements mutuellement récursifs s’effectue à l’aide du `and` mot clé.</span><span class="sxs-lookup"><span data-stu-id="d4220-142">Defining mutually recursive records is done with the `and` keyword.</span></span> <span data-ttu-id="d4220-143">Cela vous permet de lier simultanément 2 types d’enregistrements ou plus.</span><span class="sxs-lookup"><span data-stu-id="d4220-143">This lets you link 2 or more record types together.</span></span>

<span data-ttu-id="d4220-144">Par exemple, le code suivant définit un `Person` `Address` type et comme étant mutuellement récursif :</span><span class="sxs-lookup"><span data-stu-id="d4220-144">For example, the following code defines a `Person` and `Address` type as mutually recursive:</span></span>

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
    PostCode: string
    Occupant: Person }
```

<span data-ttu-id="d4220-145">Si vous deviez définir l’exemple précédent sans le `and` mot clé, il n’est pas compilé.</span><span class="sxs-lookup"><span data-stu-id="d4220-145">If you were to define the previous example without the `and` keyword, then it would not compile.</span></span> <span data-ttu-id="d4220-146">Le `and` mot clé est requis pour les définitions mutuellement récursives.</span><span class="sxs-lookup"><span data-stu-id="d4220-146">The `and` keyword is required for mutually recursive definitions.</span></span>

## <a name="pattern-matching-with-records"></a><span data-ttu-id="d4220-147">Critères spéciaux avec enregistrements</span><span class="sxs-lookup"><span data-stu-id="d4220-147">Pattern Matching with Records</span></span>

<span data-ttu-id="d4220-148">Les enregistrements peuvent être utilisés avec des critères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="d4220-148">Records can be used with pattern matching.</span></span> <span data-ttu-id="d4220-149">Vous pouvez spécifier des champs explicitement et fournir des variables pour d’autres champs qui seront affectés quand une correspondance se produit.</span><span class="sxs-lookup"><span data-stu-id="d4220-149">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="d4220-150">L'exemple de code suivant illustre ceci.</span><span class="sxs-lookup"><span data-stu-id="d4220-150">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="d4220-151">Le résultat de ce code est le suivant.</span><span class="sxs-lookup"><span data-stu-id="d4220-151">The output of this code is as follows.</span></span>

```console
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="records-and-members"></a><span data-ttu-id="d4220-152">Enregistrements et membres</span><span class="sxs-lookup"><span data-stu-id="d4220-152">Records and members</span></span>

<span data-ttu-id="d4220-153">Vous pouvez spécifier des membres sur des enregistrements de la même façon que vous pouvez utiliser des classes.</span><span class="sxs-lookup"><span data-stu-id="d4220-153">You can specify members on records much like you can with classes.</span></span> <span data-ttu-id="d4220-154">Les champs ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d4220-154">There is no support for fields.</span></span> <span data-ttu-id="d4220-155">Une approche courante consiste à définir un `Default` membre statique pour une création d’enregistrement facile :</span><span class="sxs-lookup"><span data-stu-id="d4220-155">A common approach is to define a `Default` static member for easy record construction:</span></span>

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    static member Default =
        { Name = "Phillip"
          Age = 12
          Address = "123 happy fun street" }

let defaultPerson = Person.Default
```

<span data-ttu-id="d4220-156">Si vous utilisez un auto-identificateur, cet identificateur fait référence à l’instance de l’enregistrement dont le membre est appelé :</span><span class="sxs-lookup"><span data-stu-id="d4220-156">If you use a self identifier, that identifier refers to the instance of the record whose member is called:</span></span>

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    member this.WeirdToString() =
        this.Name + this.Address + string this.Age

let p = { Name = "a"; Age = 12; Address = "abc123" }
let weirdString = p.WeirdToString()
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="d4220-157">Différences entre les enregistrements et les classes</span><span class="sxs-lookup"><span data-stu-id="d4220-157">Differences Between Records and Classes</span></span>

<span data-ttu-id="d4220-158">Les champs d’enregistrement diffèrent des champs de classe dans la mesure où ils sont automatiquement exposés en tant que propriétés et sont utilisés lors de la création et de la copie des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="d4220-158">Record fields differ from class fields in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="d4220-159">La construction d’enregistrement diffère également de la construction de classe.</span><span class="sxs-lookup"><span data-stu-id="d4220-159">Record construction also differs from class construction.</span></span> <span data-ttu-id="d4220-160">Dans un type d’enregistrement, vous ne pouvez pas définir un constructeur.</span><span class="sxs-lookup"><span data-stu-id="d4220-160">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="d4220-161">Au lieu de cela, la syntaxe de construction décrite dans cette rubrique s’applique.</span><span class="sxs-lookup"><span data-stu-id="d4220-161">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="d4220-162">Les classes n’ont aucune relation directe entre les paramètres de constructeur, les champs et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="d4220-162">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="d4220-163">Comme les types d’Union et de structure, les enregistrements ont une sémantique d’égalité structurelle.</span><span class="sxs-lookup"><span data-stu-id="d4220-163">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="d4220-164">Les classes ont une sémantique d’égalité des références.</span><span class="sxs-lookup"><span data-stu-id="d4220-164">Classes have reference equality semantics.</span></span> <span data-ttu-id="d4220-165">L'exemple de code suivant illustre cette tâche.</span><span class="sxs-lookup"><span data-stu-id="d4220-165">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="d4220-166">Le résultat de ce code est le suivant :</span><span class="sxs-lookup"><span data-stu-id="d4220-166">The output of this code is as follows:</span></span>

```console
The records are equal.
```

<span data-ttu-id="d4220-167">Si vous écrivez le même code avec des classes, les deux objets de classe seraient inégaux, car les deux valeurs représenteront deux objets sur le tas et seules les adresses seraient comparées (sauf si le type de classe substitue la `System.Object.Equals` méthode).</span><span class="sxs-lookup"><span data-stu-id="d4220-167">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="d4220-168">Si vous avez besoin d’une égalité de référence pour les enregistrements, ajoutez l’attribut `[<ReferenceEquality>]` au-dessus de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d4220-168">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4220-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4220-169">See also</span></span>

- [<span data-ttu-id="d4220-170">Types F#</span><span class="sxs-lookup"><span data-stu-id="d4220-170">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="d4220-171">Classes</span><span class="sxs-lookup"><span data-stu-id="d4220-171">Classes</span></span>](classes.md)
- [<span data-ttu-id="d4220-172">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="d4220-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="d4220-173">Référence-égalité</span><span class="sxs-lookup"><span data-stu-id="d4220-173">Reference-Equality</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-referenceequalityattribute.html)
- [<span data-ttu-id="d4220-174">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="d4220-174">Pattern Matching</span></span>](pattern-matching.md)
