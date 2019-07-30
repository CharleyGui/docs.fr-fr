---
title: Surcharge d'opérateur
description: Découvrez comment surcharger les opérateurs arithmétiques dans une classe ou un type d’enregistrement et F#au niveau global dans.
ms.date: 05/16/2016
ms.openlocfilehash: c656c1c47938e62386c8f063cf9a6caaaf69d0fe
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627392"
---
# <a name="operator-overloading"></a><span data-ttu-id="d13a3-103">Surcharge d'opérateur</span><span class="sxs-lookup"><span data-stu-id="d13a3-103">Operator Overloading</span></span>

<span data-ttu-id="d13a3-104">Cette rubrique décrit comment surcharger les opérateurs arithmétiques dans une classe ou un type d’enregistrement, et au niveau global.</span><span class="sxs-lookup"><span data-stu-id="d13a3-104">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>

## <a name="syntax"></a><span data-ttu-id="d13a3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d13a3-105">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="d13a3-106">Notes</span><span class="sxs-lookup"><span data-stu-id="d13a3-106">Remarks</span></span>

<span data-ttu-id="d13a3-107">Dans la syntaxe précédente, *Operator-Symbol* est l’un des `+`caractères `-` `=`, `*`, `/`,,, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="d13a3-107">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="d13a3-108">La *liste de paramètres* spécifie les opérandes dans l’ordre dans lequel ils apparaissent dans la syntaxe habituelle pour cet opérateur.</span><span class="sxs-lookup"><span data-stu-id="d13a3-108">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="d13a3-109">Le *corps de la méthode* construit la valeur résultante.</span><span class="sxs-lookup"><span data-stu-id="d13a3-109">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="d13a3-110">Les surcharges d’opérateur pour les opérateurs doivent être statiques.</span><span class="sxs-lookup"><span data-stu-id="d13a3-110">Operator overloads for operators must be static.</span></span> <span data-ttu-id="d13a3-111">Les surcharges d’opérateur pour les opérateurs unaires `-`, tels que `+` et, doivent`~`utiliser un tilde () dans le *symbole d’opérateur* pour indiquer que l’opérateur est un opérateur unaire et non un opérateur binaire, comme indiqué dans l’exemple suivant: déclaré.</span><span class="sxs-lookup"><span data-stu-id="d13a3-111">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="d13a3-112">Le code suivant illustre une classe Vector qui n’a que deux opérateurs, l’un pour le moins unaire et l’autre pour la multiplication par un scalaire.</span><span class="sxs-lookup"><span data-stu-id="d13a3-112">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="d13a3-113">Dans l’exemple, deux surcharges pour la multiplication scalaire sont nécessaires, car l’opérateur doit fonctionner indépendamment de l’ordre dans lequel le vecteur et la scalaire apparaissent.</span><span class="sxs-lookup"><span data-stu-id="d13a3-113">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="d13a3-114">Créer des opérateurs</span><span class="sxs-lookup"><span data-stu-id="d13a3-114">Creating New Operators</span></span>

<span data-ttu-id="d13a3-115">Vous pouvez surcharger tous les opérateurs standard, mais vous pouvez également créer des opérateurs à partir de séquences de certains caractères.</span><span class="sxs-lookup"><span data-stu-id="d13a3-115">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="d13a3-116">Les caractères d’opérateur `!`autorisés `%`sont `&`, `*`, `+`, `-`,,, `.`, ,,`<`, ,`>` `/` `=` `?`,,, et`~`. `@` `^` `|`</span><span class="sxs-lookup"><span data-stu-id="d13a3-116">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="d13a3-117">Le `~` caractère a la signification particulière de la création d’un opérateur unaire et ne fait pas partie de la séquence de caractères de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="d13a3-117">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="d13a3-118">Tous les opérateurs ne peuvent pas être rendus unaires.</span><span class="sxs-lookup"><span data-stu-id="d13a3-118">Not all operators can be made unary.</span></span>

<span data-ttu-id="d13a3-119">Selon la séquence de caractères exacte que vous utilisez, votre opérateur aura une certaine priorité et associativité.</span><span class="sxs-lookup"><span data-stu-id="d13a3-119">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="d13a3-120">L’associativité peut être de gauche à droite ou de droite à gauche et est utilisée chaque fois que des opérateurs du même niveau de priorité apparaissent sans parenthèses dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="d13a3-120">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="d13a3-121">Le caractère `.` d’opérateur n’affecte pas la précédence. ainsi, par exemple, si vous souhaitez définir votre propre version de la multiplication qui a la même priorité et associativité que la multiplication ordinaire, vous pouvez créer des opérateurs tels que `.*`.</span><span class="sxs-lookup"><span data-stu-id="d13a3-121">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="d13a3-122">Seuls les opérateurs `?` et `?<-` peuvent commencer par `?`.</span><span class="sxs-lookup"><span data-stu-id="d13a3-122">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="d13a3-123">Une table qui affiche la priorité de tous les opérateurs F# dans se trouve dans les informations de référence sur les [symboles et](./symbol-and-operator-reference/index.md)les opérateurs.</span><span class="sxs-lookup"><span data-stu-id="d13a3-123">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](./symbol-and-operator-reference/index.md).</span></span>

## <a name="overloaded-operator-names"></a><span data-ttu-id="d13a3-124">Noms des opérateurs surchargés</span><span class="sxs-lookup"><span data-stu-id="d13a3-124">Overloaded Operator Names</span></span>

<span data-ttu-id="d13a3-125">Lorsque le F# compilateur compile une expression d’opérateur, il génère une méthode qui a un nom généré par le compilateur pour cet opérateur.</span><span class="sxs-lookup"><span data-stu-id="d13a3-125">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="d13a3-126">Il s’agit du nom qui s’affiche dans le langage MSIL (Microsoft Intermediate Language) pour la méthode et également dans la réflexion et IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="d13a3-126">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="d13a3-127">Normalement, vous n’avez pas besoin d’utiliser ces F# noms dans le code.</span><span class="sxs-lookup"><span data-stu-id="d13a3-127">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="d13a3-128">Le tableau suivant présente les opérateurs standard et leurs noms générés correspondants.</span><span class="sxs-lookup"><span data-stu-id="d13a3-128">The following table shows the standard operators and their corresponding generated names.</span></span>

|<span data-ttu-id="d13a3-129">Opérateur</span><span class="sxs-lookup"><span data-stu-id="d13a3-129">Operator</span></span>|<span data-ttu-id="d13a3-130">Nom généré</span><span class="sxs-lookup"><span data-stu-id="d13a3-130">Generated name</span></span>|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|

<span data-ttu-id="d13a3-131">D’autres combinaisons de caractères d’opérateur qui ne sont pas répertoriées ici peuvent être utilisées en tant qu’opérateurs et ont des noms qui sont composés en concaténant des noms pour les caractères individuels du tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d13a3-131">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="d13a3-132">Par exemple, +!</span><span class="sxs-lookup"><span data-stu-id="d13a3-132">For example, +!</span></span> <span data-ttu-id="d13a3-133">devient `op_PlusBang`.</span><span class="sxs-lookup"><span data-stu-id="d13a3-133">becomes `op_PlusBang`.</span></span>

|<span data-ttu-id="d13a3-134">Caractère d’opérateur</span><span class="sxs-lookup"><span data-stu-id="d13a3-134">Operator character</span></span>|<span data-ttu-id="d13a3-135">Name</span><span class="sxs-lookup"><span data-stu-id="d13a3-135">Name</span></span>|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="d13a3-136">Opérateurs prefix et infixe</span><span class="sxs-lookup"><span data-stu-id="d13a3-136">Prefix and Infix Operators</span></span>

<span data-ttu-id="d13a3-137">Les opérateurs de préfixe sont censés être placés devant un opérande ou des opérandes, à l’instar d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="d13a3-137">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="d13a3-138">Les opérateurs infixes sont censés être placés entre les deux opérandes.</span><span class="sxs-lookup"><span data-stu-id="d13a3-138">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="d13a3-139">Seuls certains opérateurs peuvent être utilisés comme opérateurs de préfixe.</span><span class="sxs-lookup"><span data-stu-id="d13a3-139">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="d13a3-140">Certains opérateurs sont toujours des opérateurs de préfixe, d’autres peuvent être infixes ou préfixes, tandis que les autres sont toujours des opérateurs infixes.</span><span class="sxs-lookup"><span data-stu-id="d13a3-140">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="d13a3-141">Les opérateurs qui commencent `!`par, `!=`except et l’opérateur `~`, ou les séquences répétées de, sont toujours des opérateurs de`~`préfixe.</span><span class="sxs-lookup"><span data-stu-id="d13a3-141">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="d13a3-142">Les opérateurs `+` `-` ,,`%`, ,,`-.`, et peuventêtredesopérateursdepréfixeoudesopérateursinfixes.`%%` `&` `+.` `&&`</span><span class="sxs-lookup"><span data-stu-id="d13a3-142">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="d13a3-143">Vous pouvez distinguer la version préfixée de ces opérateurs de la version infix `~` en ajoutant un au début d’un opérateur préfixé lorsqu’il est défini.</span><span class="sxs-lookup"><span data-stu-id="d13a3-143">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="d13a3-144">Le `~` n’est pas utilisé lorsque vous utilisez l’opérateur, uniquement lorsqu’il est défini.</span><span class="sxs-lookup"><span data-stu-id="d13a3-144">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="d13a3-145">Exemples</span><span class="sxs-lookup"><span data-stu-id="d13a3-145">Example</span></span>

<span data-ttu-id="d13a3-146">Le code suivant illustre l’utilisation de la surcharge d’opérateur pour implémenter un type de fraction.</span><span class="sxs-lookup"><span data-stu-id="d13a3-146">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="d13a3-147">Une fraction est représentée par un numérateur et un dénominateur.</span><span class="sxs-lookup"><span data-stu-id="d13a3-147">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="d13a3-148">La fonction `hcf` est utilisée pour déterminer le facteur commun le plus élevé, qui est utilisé pour réduire les fractions.</span><span class="sxs-lookup"><span data-stu-id="d13a3-148">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="d13a3-149">**Output:**</span><span class="sxs-lookup"><span data-stu-id="d13a3-149">**Output:**</span></span>

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="d13a3-150">Opérateurs au niveau global</span><span class="sxs-lookup"><span data-stu-id="d13a3-150">Operators at the Global Level</span></span>

<span data-ttu-id="d13a3-151">Vous pouvez également définir des opérateurs au niveau global.</span><span class="sxs-lookup"><span data-stu-id="d13a3-151">You can also define operators at the global level.</span></span> <span data-ttu-id="d13a3-152">Le code suivant définit un opérateur `+?`.</span><span class="sxs-lookup"><span data-stu-id="d13a3-152">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="d13a3-153">La sortie du code ci-dessus `12`est.</span><span class="sxs-lookup"><span data-stu-id="d13a3-153">The output of the above code is `12`.</span></span>

<span data-ttu-id="d13a3-154">Vous pouvez redéfinir les opérateurs arithmétiques normaux de cette manière, car les F# règles de portée pour déterminent que les opérateurs nouvellement définis sont prioritaires sur les opérateurs intégrés.</span><span class="sxs-lookup"><span data-stu-id="d13a3-154">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="d13a3-155">Le mot `inline` clé est souvent utilisé avec les opérateurs globaux, qui sont souvent des petites fonctions qui sont mieux intégrées dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="d13a3-155">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="d13a3-156">La création d’une fonction d’opérateur Inline permet également de travailler avec des paramètres de type résolus statiquement pour produire du code générique résolu statiquement.</span><span class="sxs-lookup"><span data-stu-id="d13a3-156">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="d13a3-157">Pour plus d’informations, consultez [fonctions inline](./functions/inline-functions.md) et [paramètres de type résolus statiquement](./generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="d13a3-157">For more information, see [Inline Functions](./functions/inline-functions.md) and [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d13a3-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d13a3-158">See also</span></span>

- [<span data-ttu-id="d13a3-159">Membres</span><span class="sxs-lookup"><span data-stu-id="d13a3-159">Members</span></span>](./members/index.md)
