---
title: Type List
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: 7e22ad6e32ec13f081391e1d47a80df8b1e65063
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412986"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="9138a-102">Liste de types (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9138a-102">Type List (Visual Basic)</span></span>

<span data-ttu-id="9138a-103">Spécifie les *paramètres de type* pour un élément de programmation *générique* .</span><span class="sxs-lookup"><span data-stu-id="9138a-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="9138a-104">Plusieurs paramètres sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="9138a-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="9138a-105">Voici la syntaxe d’un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="9138a-105">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="9138a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9138a-106">Syntax</span></span>

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="9138a-107">Éléments</span><span class="sxs-lookup"><span data-stu-id="9138a-107">Parts</span></span>

|<span data-ttu-id="9138a-108">Terme</span><span class="sxs-lookup"><span data-stu-id="9138a-108">Term</span></span>|<span data-ttu-id="9138a-109">Définition</span><span class="sxs-lookup"><span data-stu-id="9138a-109">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="9138a-110">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="9138a-110">Optional.</span></span> <span data-ttu-id="9138a-111">Peut être utilisé uniquement dans les interfaces et les délégués génériques.</span><span class="sxs-lookup"><span data-stu-id="9138a-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="9138a-112">Vous pouvez déclarer un covariant de type à l’aide du mot clé [out](../modifiers/out-generic-modifier.md) ou de contravariant à l’aide du mot clé [in](../modifiers/in-generic-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="9138a-112">You can declare a type covariant by using the [Out](../modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="9138a-113">Consultez [Covariance et contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="9138a-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="9138a-114">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9138a-114">Required.</span></span> <span data-ttu-id="9138a-115">Nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="9138a-115">Name of the type parameter.</span></span> <span data-ttu-id="9138a-116">Il s’agit d’un espace réservé, à remplacer par un type défini fourni par l’argument de type correspondant.</span><span class="sxs-lookup"><span data-stu-id="9138a-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="9138a-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="9138a-117">Optional.</span></span> <span data-ttu-id="9138a-118">Liste des exigences qui contraignent le type de données qui peut être fourni pour `typename` .</span><span class="sxs-lookup"><span data-stu-id="9138a-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="9138a-119">Si vous avez plusieurs contraintes, mettez-les entre accolades ( `{ }` ) et séparez-les par des virgules.</span><span class="sxs-lookup"><span data-stu-id="9138a-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="9138a-120">Vous devez introduire la liste de contraintes avec le mot clé [As](as-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="9138a-120">You must introduce the constraint list with the [As](as-clause.md) keyword.</span></span> <span data-ttu-id="9138a-121">Vous ne devez utiliser `As` qu’une seule fois, au début de la liste.</span><span class="sxs-lookup"><span data-stu-id="9138a-121">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9138a-122">Notes</span><span class="sxs-lookup"><span data-stu-id="9138a-122">Remarks</span></span>

<span data-ttu-id="9138a-123">Chaque élément de programmation générique doit accepter au moins un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="9138a-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="9138a-124">Un paramètre de type est un espace réservé pour un type spécifique (un *élément construit*) que le code client spécifie lorsqu’il crée une instance du type générique.</span><span class="sxs-lookup"><span data-stu-id="9138a-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="9138a-125">Vous pouvez définir une classe, une structure, une interface, une procédure ou un délégué générique.</span><span class="sxs-lookup"><span data-stu-id="9138a-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="9138a-126">Pour plus d’informations sur la définition d’un type générique, consultez [types génériques dans Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="9138a-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="9138a-127">Pour plus d’informations sur les noms de paramètres de type, consultez [noms d’éléments déclarés](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="9138a-127">For more information on type parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="9138a-128">Règles</span><span class="sxs-lookup"><span data-stu-id="9138a-128">Rules</span></span>

- <span data-ttu-id="9138a-129">**Parenthèses.**</span><span class="sxs-lookup"><span data-stu-id="9138a-129">**Parentheses.**</span></span> <span data-ttu-id="9138a-130">Si vous fournissez une liste de paramètres de type, vous devez la placer entre parenthèses, et vous devez introduire la liste avec le mot clé [of](of-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="9138a-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](of-clause.md) keyword.</span></span> <span data-ttu-id="9138a-131">Vous ne devez utiliser `Of` qu’une seule fois, au début de la liste.</span><span class="sxs-lookup"><span data-stu-id="9138a-131">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="9138a-132">**Contraintes.**</span><span class="sxs-lookup"><span data-stu-id="9138a-132">**Constraints.**</span></span> <span data-ttu-id="9138a-133">Une liste de *contraintes* sur un paramètre de type peut inclure les éléments suivants dans n’importe quelle combinaison :</span><span class="sxs-lookup"><span data-stu-id="9138a-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="9138a-134">N’importe quel nombre d’interfaces.</span><span class="sxs-lookup"><span data-stu-id="9138a-134">Any number of interfaces.</span></span> <span data-ttu-id="9138a-135">Le type fourni doit implémenter chaque interface dans cette liste.</span><span class="sxs-lookup"><span data-stu-id="9138a-135">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="9138a-136">Au plus une classe.</span><span class="sxs-lookup"><span data-stu-id="9138a-136">At most one class.</span></span> <span data-ttu-id="9138a-137">Le type fourni doit hériter de cette classe.</span><span class="sxs-lookup"><span data-stu-id="9138a-137">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="9138a-138">Mot clé `New`.</span><span class="sxs-lookup"><span data-stu-id="9138a-138">The `New` keyword.</span></span> <span data-ttu-id="9138a-139">Le type fourni doit exposer un constructeur sans paramètre auquel votre type générique peut accéder.</span><span class="sxs-lookup"><span data-stu-id="9138a-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="9138a-140">Cela est utile si vous limitez un paramètre de type par une ou plusieurs interfaces.</span><span class="sxs-lookup"><span data-stu-id="9138a-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="9138a-141">Un type qui implémente des interfaces n’expose pas nécessairement un constructeur et, selon le niveau d’accès d’un constructeur, le code dans le type générique peut ne pas être en mesure d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="9138a-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="9138a-142">Le `Class` mot clé ou le `Structure` mot clé.</span><span class="sxs-lookup"><span data-stu-id="9138a-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="9138a-143">Le `Class` mot clé contraindre un paramètre de type générique à exiger que tout argument de type soit passé comme type de référence, par exemple une chaîne, un tableau ou un délégué, ou un objet créé à partir d’une classe.</span><span class="sxs-lookup"><span data-stu-id="9138a-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="9138a-144">Le `Structure` mot clé limite un paramètre de type générique pour exiger que tout argument de type qui lui est passé soit un type valeur, par exemple une structure, une énumération ou un type de données élémentaire.</span><span class="sxs-lookup"><span data-stu-id="9138a-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="9138a-145">Vous ne pouvez pas `Class` inclure `Structure` à la fois et dans le même `constraintlist` .</span><span class="sxs-lookup"><span data-stu-id="9138a-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="9138a-146">Le type fourni doit satisfaire à toutes les exigences que vous incluez dans `constraintlist` .</span><span class="sxs-lookup"><span data-stu-id="9138a-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="9138a-147">Les contraintes sur chaque paramètre de type sont indépendantes des contraintes sur d’autres paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="9138a-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="9138a-148">Comportement</span><span class="sxs-lookup"><span data-stu-id="9138a-148">Behavior</span></span>

- <span data-ttu-id="9138a-149">**Substitution au moment de la compilation.**</span><span class="sxs-lookup"><span data-stu-id="9138a-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="9138a-150">Lorsque vous créez un type construit à partir d’un élément de programmation générique, vous fournissez un type défini pour chaque paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="9138a-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="9138a-151">Le compilateur Visual Basic remplace ce type fourni pour chaque occurrence de `typename` dans l’élément générique.</span><span class="sxs-lookup"><span data-stu-id="9138a-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="9138a-152">**Absence de contraintes.**</span><span class="sxs-lookup"><span data-stu-id="9138a-152">**Absence of Constraints.**</span></span> <span data-ttu-id="9138a-153">Si vous ne spécifiez pas de contraintes sur un paramètre de type, votre code est limité aux opérations et aux membres pris en charge par le [type de données objet](../data-types/object-data-type.md) pour ce paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="9138a-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="9138a-154">Exemple</span><span class="sxs-lookup"><span data-stu-id="9138a-154">Example</span></span>

<span data-ttu-id="9138a-155">L’exemple suivant montre une définition squelette d’une classe Dictionary générique, y compris une fonction squelette pour ajouter une nouvelle entrée au dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="9138a-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="9138a-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="9138a-156">Example</span></span>

<span data-ttu-id="9138a-157">Étant donné que `dictionary` est générique, le code qui l’utilise peut créer divers objets à partir de celui-ci, chacun ayant les mêmes fonctionnalités, mais agissant sur un type de données différent.</span><span class="sxs-lookup"><span data-stu-id="9138a-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="9138a-158">L’exemple suivant montre une ligne de code qui crée un `dictionary` objet avec des `String` entrées et des `Integer` clés.</span><span class="sxs-lookup"><span data-stu-id="9138a-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="9138a-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="9138a-159">Example</span></span>

<span data-ttu-id="9138a-160">L’exemple suivant illustre la définition de squelette équivalente générée par l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="9138a-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="9138a-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9138a-161">See also</span></span>

- [<span data-ttu-id="9138a-162">Of</span><span class="sxs-lookup"><span data-stu-id="9138a-162">Of</span></span>](of-clause.md)
- [<span data-ttu-id="9138a-163">Nouvel opérateur</span><span class="sxs-lookup"><span data-stu-id="9138a-163">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="9138a-164">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9138a-164">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="9138a-165">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="9138a-165">Object Data Type</span></span>](../data-types/object-data-type.md)
- [<span data-ttu-id="9138a-166">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="9138a-166">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="9138a-167">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="9138a-167">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="9138a-168">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="9138a-168">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="9138a-169">Procédure : Utiliser une classe générique</span><span class="sxs-lookup"><span data-stu-id="9138a-169">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="9138a-170">Covariance et contravariance</span><span class="sxs-lookup"><span data-stu-id="9138a-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="9138a-171">Dans</span><span class="sxs-lookup"><span data-stu-id="9138a-171">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="9138a-172">À</span><span class="sxs-lookup"><span data-stu-id="9138a-172">Out</span></span>](../modifiers/out-generic-modifier.md)
