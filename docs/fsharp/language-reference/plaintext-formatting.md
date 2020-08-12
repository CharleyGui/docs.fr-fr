---
title: Mise en forme en texte brut
description: 'Découvrez comment utiliser printf et d’autres mises en forme de texte brut dans des scripts et des applications F #.'
ms.date: 07/22/2020
ms.openlocfilehash: 90a861736dae69dfbc199a19e24f587c42404737
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063781"
---
# <a name="plain-text-formatting"></a><span data-ttu-id="0a12f-103">Mise en forme de texte brut</span><span class="sxs-lookup"><span data-stu-id="0a12f-103">Plain text formatting</span></span>

<span data-ttu-id="0a12f-104">F # prend en charge la mise en forme du texte brut par type vérifié à l’aide de `printf` ,, `printfn` et des `sprintf` fonctions associées.</span><span class="sxs-lookup"><span data-stu-id="0a12f-104">F# supports type-checked formatting of plain text using `printf`, `printfn`, `sprintf`, and related functions.</span></span>
<span data-ttu-id="0a12f-105">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-105">For example,</span></span>

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

<span data-ttu-id="0a12f-106">donne la sortie</span><span class="sxs-lookup"><span data-stu-id="0a12f-106">gives the output</span></span>

```fsharp
Hello world, 2 + 2 is 4
```

<span data-ttu-id="0a12f-107">F # permet également aux valeurs structurées d’être mises en forme en texte brut.</span><span class="sxs-lookup"><span data-stu-id="0a12f-107">F# also allows structured values to be formatted as plain text.</span></span>
<span data-ttu-id="0a12f-108">Par exemple, considérez l’exemple suivant qui met en forme la sortie sous la forme d’un affichage de tuples de type matrice.</span><span class="sxs-lookup"><span data-stu-id="0a12f-108">For example, consider the following example that formats the output as a matrix-like display of tuples.</span></span>

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

<span data-ttu-id="0a12f-109">La mise en forme du texte brut structuré est activée lorsque vous utilisez le `%A` format dans les `printf` chaînes de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0a12f-109">Structured plain text formatting is activated when you use the `%A` format in `printf` formatting strings.</span></span>
<span data-ttu-id="0a12f-110">Il est également activé lors de la mise en forme de la sortie des valeurs dans F # Interactive, où la sortie contient des informations supplémentaires et peut également être personnalisée.</span><span class="sxs-lookup"><span data-stu-id="0a12f-110">It's also activated when formatting the output of values in F# interactive, where the output includes extra information and is additionally customizable.</span></span>
<span data-ttu-id="0a12f-111">La mise en forme de texte brut est également observable par le biais de tous les appels à `x.ToString()` sur les valeurs d’Union et d’enregistrement F #, y compris celles qui se produisent implicitement dans le débogage, la journalisation et d’autres outils.</span><span class="sxs-lookup"><span data-stu-id="0a12f-111">Plain text formatting is also observable through any calls to `x.ToString()` on F# union and record values, including those that occur implicitly in debugging, logging, and other tooling.</span></span>

## <a name="checking-of-printf-format-strings"></a><span data-ttu-id="0a12f-112">Vérification des `printf` chaînes de format</span><span class="sxs-lookup"><span data-stu-id="0a12f-112">Checking of `printf`-format strings</span></span>

<span data-ttu-id="0a12f-113">Une erreur de compilation est signalée si une `printf` fonction de mise en forme est utilisée avec un argument qui ne correspond pas aux spécificateurs de format printf dans la chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="0a12f-113">A compile-time error will be reported if a `printf` formatting function is used with an argument that doesn't match the printf format specifiers in the format string.</span></span>  <span data-ttu-id="0a12f-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-114">For example,</span></span>

```fsharp
sprintf "Hello %s" (2+2)
```

<span data-ttu-id="0a12f-115">donne la sortie</span><span class="sxs-lookup"><span data-stu-id="0a12f-115">gives the output</span></span>

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

<span data-ttu-id="0a12f-116">Techniquement parlant, lorsque `printf` vous utilisez et d’autres fonctions associées, une règle spéciale dans le compilateur F # vérifie le littéral de chaîne passé comme chaîne de format, ce qui garantit que les arguments suivants appliqués sont du type correct pour correspondre aux spécificateurs de format utilisés.</span><span class="sxs-lookup"><span data-stu-id="0a12f-116">Technically speaking, when using `printf` and other related functions, a special rule in the F# compiler checks the string literal passed as the format string, ensuring the subsequent arguments applied are of the correct type to match the format specifiers used.</span></span>

## <a name="format-specifiers-for-printf"></a><span data-ttu-id="0a12f-117">Spécificateurs de format pour`printf`</span><span class="sxs-lookup"><span data-stu-id="0a12f-117">Format specifiers for `printf`</span></span>

<span data-ttu-id="0a12f-118">Les spécifications de format pour les `printf` formats sont des chaînes avec des `%` marqueurs qui indiquent le format.</span><span class="sxs-lookup"><span data-stu-id="0a12f-118">Format specifications for `printf` formats are strings with `%` markers that indicate format.</span></span> <span data-ttu-id="0a12f-119">Les espaces réservés de format se composent de `%[flags][width][.precision][type]` là où le type est interprété comme suit :</span><span class="sxs-lookup"><span data-stu-id="0a12f-119">Format placeholders consist of `%[flags][width][.precision][type]` where the type is interpreted as follows:</span></span>

| <span data-ttu-id="0a12f-120">Spécificateur de format</span><span class="sxs-lookup"><span data-stu-id="0a12f-120">Format specifier</span></span>   | <span data-ttu-id="0a12f-121">Type (s)</span><span class="sxs-lookup"><span data-stu-id="0a12f-121">Type(s)</span></span>        | <span data-ttu-id="0a12f-122">Notes</span><span class="sxs-lookup"><span data-stu-id="0a12f-122">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | <span data-ttu-id="0a12f-123">bool</span><span class="sxs-lookup"><span data-stu-id="0a12f-123">bool</span></span>      | <span data-ttu-id="0a12f-124">Mise en forme en tant que `true` ou`false`</span><span class="sxs-lookup"><span data-stu-id="0a12f-124">Formatted as `true` or `false`</span></span>                |
| `%s`               | <span data-ttu-id="0a12f-125">string</span><span class="sxs-lookup"><span data-stu-id="0a12f-125">string</span></span>    | <span data-ttu-id="0a12f-126">Mise en forme en tant que contenu sans séquence d’échappement</span><span class="sxs-lookup"><span data-stu-id="0a12f-126">Formatted as its unescaped contents</span></span>         |
| `%c`               | <span data-ttu-id="0a12f-127">char</span><span class="sxs-lookup"><span data-stu-id="0a12f-127">char</span></span>      | <span data-ttu-id="0a12f-128">Mise en forme en tant que littéral de caractère</span><span class="sxs-lookup"><span data-stu-id="0a12f-128">Formatted as the character literal</span></span>  |
| <span data-ttu-id="0a12f-129">`%d`, `%i`</span><span class="sxs-lookup"><span data-stu-id="0a12f-129">`%d`, `%i`</span></span>         | <span data-ttu-id="0a12f-130">type entier de base</span><span class="sxs-lookup"><span data-stu-id="0a12f-130">a basic integer type</span></span> | <span data-ttu-id="0a12f-131">Formaté comme un entier décimal, signé si le type entier de base est signé</span><span class="sxs-lookup"><span data-stu-id="0a12f-131">Formatted as a decimal integer, signed if the basic integer type is signed</span></span> |
| `%u`               | <span data-ttu-id="0a12f-132">type entier de base</span><span class="sxs-lookup"><span data-stu-id="0a12f-132">a basic integer type</span></span> | <span data-ttu-id="0a12f-133">Mise en forme en tant qu’entier décimal non signé</span><span class="sxs-lookup"><span data-stu-id="0a12f-133">Formatted as an unsigned decimal integer</span></span>   |
| <span data-ttu-id="0a12f-134">`%x`, `%X`</span><span class="sxs-lookup"><span data-stu-id="0a12f-134">`%x`, `%X`</span></span>         | <span data-ttu-id="0a12f-135">type entier de base</span><span class="sxs-lookup"><span data-stu-id="0a12f-135">a basic integer type</span></span> | <span data-ttu-id="0a12f-136">Mise en forme en tant que nombre hexadécimal non signé (a-f ou A-F pour les chiffres hexadécimaux, respectivement)</span><span class="sxs-lookup"><span data-stu-id="0a12f-136">Formatted as an unsigned hexadecimal number (a-f or A-F for hex digits respectively)</span></span>  |
|  `%o`              | <span data-ttu-id="0a12f-137">type entier de base</span><span class="sxs-lookup"><span data-stu-id="0a12f-137">a basic integer type</span></span> | <span data-ttu-id="0a12f-138">Mise en forme en tant que nombre octal non signé</span><span class="sxs-lookup"><span data-stu-id="0a12f-138">Formatted as an unsigned octal number</span></span> |
| <span data-ttu-id="0a12f-139">`%e`, `%E`</span><span class="sxs-lookup"><span data-stu-id="0a12f-139">`%e`, `%E`</span></span>         | <span data-ttu-id="0a12f-140">type à virgule flottante de base</span><span class="sxs-lookup"><span data-stu-id="0a12f-140">a basic floating point type</span></span> | <span data-ttu-id="0a12f-141">Mise en forme sous la forme d’une valeur signée, `[-]d.dddde[sign]ddd` où d est un chiffre décimal unique, dddd est un ou plusieurs chiffres décimaux, ddd est exactement trois chiffres décimaux, et signe est `+` ou`-`</span><span class="sxs-lookup"><span data-stu-id="0a12f-141">Formatted as a signed value having the form `[-]d.dddde[sign]ddd` where d is a single decimal digit, dddd is one or more decimal digits, ddd is exactly three decimal digits, and sign is `+` or `-`</span></span> |
| `%f`               | <span data-ttu-id="0a12f-142">type à virgule flottante de base</span><span class="sxs-lookup"><span data-stu-id="0a12f-142">a basic floating point type</span></span> | <span data-ttu-id="0a12f-143">Mise en forme sous forme de valeur signée sous la forme `[-]dddd.dddd` , où `dddd` représente un ou plusieurs chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="0a12f-143">Formatted as a signed value having the form `[-]dddd.dddd`, where `dddd` is one or more decimal digits.</span></span> <span data-ttu-id="0a12f-144">Le nombre de chiffres avant la virgule décimale dépend de l'ampleur du nombre, et le nombre de chiffres après que la virgule décimale dépend de la précision demandée.</span><span class="sxs-lookup"><span data-stu-id="0a12f-144">The number of digits before the decimal point depends on the magnitude of the number, and the number of digits after the decimal point depends on the requested precision.</span></span> |
| <span data-ttu-id="0a12f-145">`%g`, `%G`</span><span class="sxs-lookup"><span data-stu-id="0a12f-145">`%g`, `%G`</span></span> | <span data-ttu-id="0a12f-146">type à virgule flottante de base</span><span class="sxs-lookup"><span data-stu-id="0a12f-146">a basic floating point type</span></span> |  <span data-ttu-id="0a12f-147">Mise en forme à l’aide de comme valeur signée imprimée `%f` ou `%e` formatée, selon la valeur la plus petite pour la valeur et la précision données.</span><span class="sxs-lookup"><span data-stu-id="0a12f-147">Formatted using as a signed value printed in `%f` or `%e` format, whichever is more compact for the given value and precision.</span></span> |
| `%M` | <span data-ttu-id="0a12f-148">une `System.Decimal` valeur</span><span class="sxs-lookup"><span data-stu-id="0a12f-148">a `System.Decimal` value</span></span>  |    <span data-ttu-id="0a12f-149">Mis en forme à l’aide du `"G"` spécificateur de format pour`System.Decimal.ToString(format)`</span><span class="sxs-lookup"><span data-stu-id="0a12f-149">Formatted using the `"G"` format specifier for `System.Decimal.ToString(format)`</span></span> |
| `%O` | <span data-ttu-id="0a12f-150">toute valeur</span><span class="sxs-lookup"><span data-stu-id="0a12f-150">any value</span></span>  |   <span data-ttu-id="0a12f-151">Mis en forme en effectuant un boxing de l’objet et en appelant sa `System.Object.ToString()` méthode</span><span class="sxs-lookup"><span data-stu-id="0a12f-151">Formatted by boxing the object and calling its `System.Object.ToString()` method</span></span> |
| `%A` | <span data-ttu-id="0a12f-152">toute valeur</span><span class="sxs-lookup"><span data-stu-id="0a12f-152">any value</span></span>  |   <span data-ttu-id="0a12f-153">Formaté à l’aide de la [mise en forme du texte brut structuré](plaintext-formatting.md) avec les paramètres de disposition par défaut</span><span class="sxs-lookup"><span data-stu-id="0a12f-153">Formatted using [structured plain text formatting](plaintext-formatting.md) with the default layout settings</span></span> |
| `%a` | <span data-ttu-id="0a12f-154">toute valeur</span><span class="sxs-lookup"><span data-stu-id="0a12f-154">any value</span></span>  |   <span data-ttu-id="0a12f-155">Nécessite deux arguments : une fonction de mise en forme qui accepte un paramètre de contexte et la valeur, ainsi que la valeur particulière à imprimer.</span><span class="sxs-lookup"><span data-stu-id="0a12f-155">Requires two arguments: a formatting function accepting a context parameter and the value, and the particular value to print</span></span> |
| `%t` | <span data-ttu-id="0a12f-156">toute valeur</span><span class="sxs-lookup"><span data-stu-id="0a12f-156">any value</span></span>  |   <span data-ttu-id="0a12f-157">Nécessite un argument : une fonction de mise en forme qui accepte un paramètre de contexte qui génère ou retourne le texte approprié.</span><span class="sxs-lookup"><span data-stu-id="0a12f-157">Requires one argument: a formatting function accepting a context parameter that either outputs or returns the appropriate text</span></span> |
| `%%` | <span data-ttu-id="0a12f-158">(aucun)</span><span class="sxs-lookup"><span data-stu-id="0a12f-158">(none)</span></span>  |   <span data-ttu-id="0a12f-159">Ne requiert aucun argument et imprime un signe de pourcentage simple :`%`</span><span class="sxs-lookup"><span data-stu-id="0a12f-159">Requires no arguments and prints a plain percent sign: `%`</span></span> |

<span data-ttu-id="0a12f-160">Les types entiers de base sont `byte` ( `System.Byte` ), `sbyte` ( `System.SByte` ), `int16` ( `System.Int16` ), `uint16` ( `System.UInt16` ), `int32` ( `System.Int32` ), `uint32` ( `System.UInt32` ), `int64` ( `System.Int64` ), `uint64` ( `System.UInt64` ), `nativeint` ( `System.IntPtr` ) et `unativeint` ( `System.UIntPtr` ).</span><span class="sxs-lookup"><span data-stu-id="0a12f-160">Basic integer types are `byte` (`System.Byte`), `sbyte` (`System.SByte`), `int16` (`System.Int16`), `uint16` (`System.UInt16`), `int32` (`System.Int32`), `uint32` (`System.UInt32`), `int64` (`System.Int64`), `uint64` (`System.UInt64`), `nativeint`  (`System.IntPtr`), and `unativeint`  (`System.UIntPtr`).</span></span>
<span data-ttu-id="0a12f-161">Les types à virgule flottante de base sont `float` ( `System.Double` ) et `float32` ( `System.Single` ).</span><span class="sxs-lookup"><span data-stu-id="0a12f-161">Basic floating point types are `float` (`System.Double`) and `float32` (`System.Single`).</span></span>

<span data-ttu-id="0a12f-162">La largeur facultative est un entier indiquant la largeur minimale du résultat.</span><span class="sxs-lookup"><span data-stu-id="0a12f-162">The optional width is an integer indicating the minimal width of the result.</span></span> <span data-ttu-id="0a12f-163">Par exemple, `%6d` imprime un entier, en le préfixant avec des espaces pour remplir au moins six caractères.</span><span class="sxs-lookup"><span data-stu-id="0a12f-163">For instance, `%6d` prints an integer, prefixing it with spaces to fill at least six characters.</span></span> <span data-ttu-id="0a12f-164">Si width est `*` , un argument entier supplémentaire est utilisé pour spécifier la largeur correspondante.</span><span class="sxs-lookup"><span data-stu-id="0a12f-164">If width is `*`, then an extra integer  argument is taken to specify the corresponding width.</span></span>

<span data-ttu-id="0a12f-165">Les indicateurs valides sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="0a12f-165">Valid flags are:</span></span>

| <span data-ttu-id="0a12f-166">Indicateur</span><span class="sxs-lookup"><span data-stu-id="0a12f-166">Flag</span></span>   | <span data-ttu-id="0a12f-167">Effet</span><span class="sxs-lookup"><span data-stu-id="0a12f-167">Effect</span></span>        | <span data-ttu-id="0a12f-168">Notes</span><span class="sxs-lookup"><span data-stu-id="0a12f-168">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | <span data-ttu-id="0a12f-169">Ajoutez des zéros à la place des espaces pour créer la largeur requise</span><span class="sxs-lookup"><span data-stu-id="0a12f-169">Add zeros instead of spaces to make up the required width</span></span> |    |
| `-` |  <span data-ttu-id="0a12f-170">Aligner à gauche le résultat dans la largeur spécifiée</span><span class="sxs-lookup"><span data-stu-id="0a12f-170">Left justify the result within the specified width</span></span> |   |
| `+`  | <span data-ttu-id="0a12f-171">Ajoutez un `+` caractère si le nombre est positif (pour correspondre à un `-` signe pour les négatifs)</span><span class="sxs-lookup"><span data-stu-id="0a12f-171">Add a `+` character if the number is positive (to match a `-` sign for negatives)</span></span> |   |
| <span data-ttu-id="0a12f-172">espace</span><span class="sxs-lookup"><span data-stu-id="0a12f-172">space character</span></span> | <span data-ttu-id="0a12f-173">Ajoutez un espace supplémentaire si le nombre est positif (pour correspondre à un signe « - » pour les valeurs négatives)</span><span class="sxs-lookup"><span data-stu-id="0a12f-173">Add an extra space if the number is positive (to match a '-' sign for negatives)</span></span> |

<span data-ttu-id="0a12f-174">L' `#` indicateur printf n’est pas valide et une erreur de compilation est signalée s’il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0a12f-174">The printf `#` flag is invalid and a compile-time error will be reported if it is used.</span></span>

<span data-ttu-id="0a12f-175">Les valeurs sont mises en forme à l’aide de la culture dite indifférente.</span><span class="sxs-lookup"><span data-stu-id="0a12f-175">Values are formatted using invariant culture.</span></span> <span data-ttu-id="0a12f-176">Les paramètres de culture ne sont pas pertinents pour `printf` la mise en forme, sauf lorsqu’ils affectent les résultats `%O` et la `%A` mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0a12f-176">Culture settings are irrelevant to `printf` formatting except when they affect the results of `%O` and `%A` formatting.</span></span> <span data-ttu-id="0a12f-177">Pour plus d’informations, consultez [mise en forme du texte brut structuré](plaintext-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="0a12f-177">For more information, see [structured plain text formatting](plaintext-formatting.md).</span></span>

## <a name="a-formatting"></a><span data-ttu-id="0a12f-178">`%A`mise en forme</span><span class="sxs-lookup"><span data-stu-id="0a12f-178">`%A` formatting</span></span>

<span data-ttu-id="0a12f-179">Le `%A` spécificateur de format est utilisé pour mettre en forme les valeurs de façon lisible par l’utilisateur, et peut également être utile pour signaler des informations de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="0a12f-179">The `%A` format specifier is used to format values in a human-readable way, and can also be useful for reporting diagnostic information.</span></span>

### <a name="primitive-values"></a><span data-ttu-id="0a12f-180">Valeurs primitives</span><span class="sxs-lookup"><span data-stu-id="0a12f-180">Primitive values</span></span>

<span data-ttu-id="0a12f-181">Lors de la mise en forme de texte brut à l’aide du `%A` spécificateur, les valeurs numériques F # sont mises en forme avec leur suffixe et leur culture dite indifférente.</span><span class="sxs-lookup"><span data-stu-id="0a12f-181">When formatting plain text using the `%A` specifier, F# numeric values are formatted with their suffix and invariant culture.</span></span> <span data-ttu-id="0a12f-182">Les valeurs à virgule flottante sont mises en forme à l’aide de 10 emplacements de précision à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="0a12f-182">Floating point values are formatted using 10 places of floating point precision.</span></span> <span data-ttu-id="0a12f-183">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-183">For example,</span></span>

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

<span data-ttu-id="0a12f-184">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-184">produces</span></span>

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

<span data-ttu-id="0a12f-185">Lors de l’utilisation du `%A` spécificateur, les chaînes sont mises en forme à l’aide de guillemets.</span><span class="sxs-lookup"><span data-stu-id="0a12f-185">When using the `%A` specifier, strings are formatted using quotes.</span></span> <span data-ttu-id="0a12f-186">Les codes d’échappement ne sont pas ajoutés, mais les caractères bruts sont imprimés.</span><span class="sxs-lookup"><span data-stu-id="0a12f-186">Escape codes are not added and instead the raw characters are printed.</span></span> <span data-ttu-id="0a12f-187">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-187">For example,</span></span>

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

<span data-ttu-id="0a12f-188">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-188">produces</span></span>

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a><span data-ttu-id="0a12f-189">Valeurs .NET</span><span class="sxs-lookup"><span data-stu-id="0a12f-189">.NET values</span></span>

<span data-ttu-id="0a12f-190">Lors de la mise en forme de texte brut à l’aide du `%A` spécificateur, les objets non F # .net sont mis en forme à l’aide `x.ToString()` des paramètres par défaut de .net fournis par `System.Globalization.CultureInfo.CurrentCulture` et `System.Globalization.CultureInfo.CurrentUICulture` .</span><span class="sxs-lookup"><span data-stu-id="0a12f-190">When formatting plain text using the `%A` specifier, non-F# .NET objects are formatted by using `x.ToString()` using the default settings of .NET given by `System.Globalization.CultureInfo.CurrentCulture` and `System.Globalization.CultureInfo.CurrentUICulture`.</span></span>  <span data-ttu-id="0a12f-191">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-191">For example,</span></span>

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

<span data-ttu-id="0a12f-192">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-192">produces</span></span>

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a><span data-ttu-id="0a12f-193">Valeurs structurées</span><span class="sxs-lookup"><span data-stu-id="0a12f-193">Structured values</span></span>

<span data-ttu-id="0a12f-194">Lors de la mise en forme de texte brut à l’aide du `%A` spécificateur, le retrait de bloc est utilisé pour les listes et les tuples F #.</span><span class="sxs-lookup"><span data-stu-id="0a12f-194">When formatting plain text using the `%A` specifier, block indentation is used for F# lists and tuples.</span></span> <span data-ttu-id="0a12f-195">Cela est illustré dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="0a12f-195">This shown in the previous example.</span></span>
<span data-ttu-id="0a12f-196">La structure des tableaux est également utilisée, y compris les tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="0a12f-196">The structure of arrays is also used, including multi-dimensional arrays.</span></span>  <span data-ttu-id="0a12f-197">Les tableaux unidimensionnels sont affichés avec la `[| ... |]` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="0a12f-197">Single-dimensional arrays are shown with `[| ... |]` syntax.</span></span> <span data-ttu-id="0a12f-198">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-198">For example,</span></span>

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

<span data-ttu-id="0a12f-199">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-199">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

<span data-ttu-id="0a12f-200">La largeur d’impression par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="0a12f-200">The default print width is 80.</span></span>  <span data-ttu-id="0a12f-201">Cette largeur peut être personnalisée à l’aide d’une largeur d’impression dans le spécificateur de format.</span><span class="sxs-lookup"><span data-stu-id="0a12f-201">This width can be customized by using a print width in the format specifier.</span></span> <span data-ttu-id="0a12f-202">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-202">For example,</span></span>

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

<span data-ttu-id="0a12f-203">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-203">produces</span></span>

```console
[|(1, 1);
  (2, 4);
  (3, 9);
  (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4);
  (3, 9); (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
```

<span data-ttu-id="0a12f-204">Si vous spécifiez une largeur d’impression égale à 0, aucune largeur d’impression n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0a12f-204">Specifying a print width of 0 results in no print width being used.</span></span> <span data-ttu-id="0a12f-205">Une seule ligne de texte se produit, sauf lorsque les chaînes incorporées dans la sortie contiennent des sauts de ligne.</span><span class="sxs-lookup"><span data-stu-id="0a12f-205">A single line of text will result, except where embedded strings in the output contain line breaks.</span></span>  <span data-ttu-id="0a12f-206">Par exemple</span><span class="sxs-lookup"><span data-stu-id="0a12f-206">For example</span></span>

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef" |]
```

<span data-ttu-id="0a12f-207">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-207">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

<span data-ttu-id="0a12f-208">Une limite de profondeur de 4 est utilisée pour les `IEnumerable` valeurs Sequence (), qui sont affichées sous la forme `seq { ...}` .</span><span class="sxs-lookup"><span data-stu-id="0a12f-208">A depth limit of 4 is used for sequence (`IEnumerable`) values, which are shown as `seq { ...}`.</span></span> <span data-ttu-id="0a12f-209">Une limite de profondeur de 100 est utilisée pour les valeurs de liste et de tableau.</span><span class="sxs-lookup"><span data-stu-id="0a12f-209">A depth limit of 100 is used for list and array values.</span></span>
<span data-ttu-id="0a12f-210">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-210">For example,</span></span>

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

<span data-ttu-id="0a12f-211">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-211">produces</span></span>

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

<span data-ttu-id="0a12f-212">La mise en retrait de bloc est également utilisée pour la structure des valeurs d’enregistrement et d’Union publiques.</span><span class="sxs-lookup"><span data-stu-id="0a12f-212">Block indentation is also used for the structure of public record and union values.</span></span> <span data-ttu-id="0a12f-213">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-213">For example,</span></span>

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="0a12f-214">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-214">produces</span></span>

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="0a12f-215">Si `%+A` est utilisé, la structure privée des enregistrements et des unions est également révélée à l’aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="0a12f-215">If `%+A` is used, then the private structure of records and unions is also revealed by using reflection.</span></span> <span data-ttu-id="0a12f-216">Par exemple</span><span class="sxs-lookup"><span data-stu-id="0a12f-216">For example</span></span>

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

<span data-ttu-id="0a12f-217">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-217">produces</span></span>

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a><span data-ttu-id="0a12f-218">Valeurs volumineuses, cycliques ou profondément imbriquées</span><span class="sxs-lookup"><span data-stu-id="0a12f-218">Large, cyclic, or deeply nested values</span></span>

<span data-ttu-id="0a12f-219">Les valeurs structurées volumineuses sont mises en forme sur un nombre total de nœuds objet de 10000.</span><span class="sxs-lookup"><span data-stu-id="0a12f-219">Large structured values are formatted to a maximum overall object node count of 10000.</span></span>
<span data-ttu-id="0a12f-220">Les valeurs profondément imbriquées sont mises en forme à une profondeur de 100.</span><span class="sxs-lookup"><span data-stu-id="0a12f-220">Deeply nested values are formatted to a depth of 100.</span></span>  <span data-ttu-id="0a12f-221">Dans les deux cas, `...` est utilisé pour Elide une partie de la sortie.</span><span class="sxs-lookup"><span data-stu-id="0a12f-221">In both cases `...` is used to elide some of the output.</span></span>  <span data-ttu-id="0a12f-222">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-222">For example,</span></span>

```fsharp
type Tree =
    | Tip
    | Node of Tree * Tree

let rec make n =
    if n = 0 then
        Tip
    else
        Node(Tip, make (n-1))

printfn "%A" (make 1000)
```

<span data-ttu-id="0a12f-223">produit une sortie volumineuse avec quelques parties élidé :</span><span class="sxs-lookup"><span data-stu-id="0a12f-223">produces a large output with some parts elided:</span></span>

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

<span data-ttu-id="0a12f-224">Les cycles sont détectés dans les graphiques d’objets et `...` sont utilisés aux endroits où les cycles sont détectés.</span><span class="sxs-lookup"><span data-stu-id="0a12f-224">Cycles are detected in the object graphs and `...` is used at places where cycles are detected.</span></span> <span data-ttu-id="0a12f-225">Par exemple</span><span class="sxs-lookup"><span data-stu-id="0a12f-225">For example</span></span>

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

<span data-ttu-id="0a12f-226">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-226">produces</span></span>

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a><span data-ttu-id="0a12f-227">Valeurs tardive, NULL et de fonction</span><span class="sxs-lookup"><span data-stu-id="0a12f-227">Lazy, null, and function values</span></span>

<span data-ttu-id="0a12f-228">Les valeurs tardives sont imprimées sous forme de `Value is not created` texte ou équivalent lorsque la valeur n’a pas encore été évaluée.</span><span class="sxs-lookup"><span data-stu-id="0a12f-228">Lazy values are printed as `Value is not created` or equivalent text when the value has not yet been evaluated.</span></span>

<span data-ttu-id="0a12f-229">Les valeurs NULL sont imprimées sous `null` la forme, sauf si le type statique de la valeur est déterminé comme étant un type d’Union où `null` est une représentation autorisée.</span><span class="sxs-lookup"><span data-stu-id="0a12f-229">Null values are printed as `null` unless the static type of the value is determined to be a union type where `null` is a permitted representation.</span></span>

<span data-ttu-id="0a12f-230">Les valeurs de fonction F # sont imprimées comme nom de fermeture généré en interne, par exemple, `<fun:it@43-7>` .</span><span class="sxs-lookup"><span data-stu-id="0a12f-230">F# function values are printed as their internally generated closure name, for example, `<fun:it@43-7>`.</span></span>

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a><span data-ttu-id="0a12f-231">Personnaliser la mise en forme du texte brut avec`StructuredFormatDisplay`</span><span class="sxs-lookup"><span data-stu-id="0a12f-231">Customize plain text formatting with `StructuredFormatDisplay`</span></span>

<span data-ttu-id="0a12f-232">Lors de l’utilisation du `%A` spécificateur, la présence de l' `StructuredFormatDisplay` attribut sur les déclarations de type est respectée.</span><span class="sxs-lookup"><span data-stu-id="0a12f-232">When using the `%A` specifier, the presence of the `StructuredFormatDisplay` attribute on type declarations is respected.</span></span>  <span data-ttu-id="0a12f-233">Cela peut être utilisé pour spécifier le texte de substitution et la propriété pour afficher une valeur.</span><span class="sxs-lookup"><span data-stu-id="0a12f-233">This can be used to specify surrogate text and property to display a value.</span></span> <span data-ttu-id="0a12f-234">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-234">For example:</span></span>

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

<span data-ttu-id="0a12f-235">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-235">produces</span></span>

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a><span data-ttu-id="0a12f-236">Personnaliser la mise en forme du texte brut en remplaçant`ToString`</span><span class="sxs-lookup"><span data-stu-id="0a12f-236">Customize plain text formatting by overriding `ToString`</span></span>

<span data-ttu-id="0a12f-237">L’implémentation par défaut de `ToString` est observable dans la programmation F #.</span><span class="sxs-lookup"><span data-stu-id="0a12f-237">The default implementation of `ToString` is observable in F# programming.</span></span> <span data-ttu-id="0a12f-238">Souvent, les résultats par défaut ne sont pas adaptés à une utilisation dans l’affichage des informations du programmeur ou la sortie utilisateur, et par conséquent, il est courant de remplacer l’implémentation par défaut.</span><span class="sxs-lookup"><span data-stu-id="0a12f-238">Often, the default results aren't suitable for use in either programmer-facing information display or user output, and as a result it is common to override the default implementation.</span></span>  

<span data-ttu-id="0a12f-239">Par défaut, les types d’enregistrement et d’Union F # remplacent l’implémentation de `ToString` par une implémentation de qui utilise `sprintf "%+A"` .</span><span class="sxs-lookup"><span data-stu-id="0a12f-239">By default, F# record and union types override the implementation of `ToString` with an implementation that uses `sprintf "%+A"`.</span></span>  <span data-ttu-id="0a12f-240">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-240">For example,</span></span>

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

<span data-ttu-id="0a12f-241">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-241">produces</span></span>

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

<span data-ttu-id="0a12f-242">Pour les types de classe, aucune implémentation par défaut de `ToString` n’est fournie et la valeur par défaut .net est utilisée, qui indique le nom du type.</span><span class="sxs-lookup"><span data-stu-id="0a12f-242">For class types, no default implementation of `ToString` is provided and the .NET default is used, which reports the name of the type.</span></span> <span data-ttu-id="0a12f-243">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0a12f-243">For example,</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="0a12f-244">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-244">produces</span></span>

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

<span data-ttu-id="0a12f-245">L’ajout d’un remplacement pour `ToString` peut offrir une meilleure mise en forme.</span><span class="sxs-lookup"><span data-stu-id="0a12f-245">Adding an override for `ToString` can give better formatting.</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="0a12f-246">tiges</span><span class="sxs-lookup"><span data-stu-id="0a12f-246">produces</span></span>

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="0a12f-247">F# Interactive l’impression structurée</span><span class="sxs-lookup"><span data-stu-id="0a12f-247">F# Interactive structured printing</span></span>

<span data-ttu-id="0a12f-248">F# Interactive ( `dotnet fsi` ) utilise une version étendue de la mise en forme de texte brut structurée pour signaler des valeurs et permet une personnalisation supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="0a12f-248">F# Interactive (`dotnet fsi`) uses an extended version of structured plain text formatting to report values and allows additional customizability.</span></span> <span data-ttu-id="0a12f-249">Pour plus d’informations, consultez [F# Interactive](fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="0a12f-249">For more information, see [F# Interactive](fsharp-interactive-options.md).</span></span>

## <a name="customize-debug-displays"></a><span data-ttu-id="0a12f-250">Personnaliser les affichages de débogage</span><span class="sxs-lookup"><span data-stu-id="0a12f-250">Customize debug displays</span></span>

<span data-ttu-id="0a12f-251">Les débogueurs pour .NET respectent l’utilisation d’attributs tels que `DebuggerDisplay` et `DebuggerTypeProxy` , et ceux-ci affectent l’affichage structuré des objets dans les fenêtres d’inspection du débogueur.</span><span class="sxs-lookup"><span data-stu-id="0a12f-251">Debuggers for .NET respect the use of attributes such as `DebuggerDisplay` and `DebuggerTypeProxy`, and these affect the structured display of objects in debugger inspection windows.</span></span>
<span data-ttu-id="0a12f-252">Le compilateur F # a généré automatiquement ces attributs pour les types d’Union et d’enregistrement discriminés, mais pas pour les types de classe, d’interface ou de struct.</span><span class="sxs-lookup"><span data-stu-id="0a12f-252">The F# compiler automatically generated these attributes for discriminated union and record types, but not class, interface, or struct types.</span></span>

<span data-ttu-id="0a12f-253">Ces attributs sont ignorés dans la mise en forme de texte brut F #, mais il peut être utile d’implémenter ces méthodes pour améliorer les affichages lors du débogage de types F #.</span><span class="sxs-lookup"><span data-stu-id="0a12f-253">These attributes are ignored in F# plain text formatting, but it can be useful to implement these methods to improve displays when debugging F# types.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a12f-254">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a12f-254">See also</span></span>

- [<span data-ttu-id="0a12f-255">Chaînes</span><span class="sxs-lookup"><span data-stu-id="0a12f-255">Strings</span></span>](strings.md)
- [<span data-ttu-id="0a12f-256">Enregistrements</span><span class="sxs-lookup"><span data-stu-id="0a12f-256">Records</span></span>](records.md)
- [<span data-ttu-id="0a12f-257">Unions discriminées</span><span class="sxs-lookup"><span data-stu-id="0a12f-257">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="0a12f-258">F# Interactive</span><span class="sxs-lookup"><span data-stu-id="0a12f-258">F# Interactive</span></span>](fsharp-interactive-options.md)
