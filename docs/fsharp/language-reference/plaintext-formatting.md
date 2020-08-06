---
title: Mise en forme de texte brut
description: 'Découvrez comment utiliser printf et d’autres mises en forme de texte brut dans des scripts et des applications F #.'
ms.date: 07/22/2020
ms.openlocfilehash: a0f2c52431be894c4f74dd2940345a518f620589
ms.sourcegitcommit: 09bad6ec0cbf18be7cd7f62e77286d305a18b607
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87795747"
---
# <a name="plain-text-formatting"></a><span data-ttu-id="b4a78-103">Mise en forme de texte brut</span><span class="sxs-lookup"><span data-stu-id="b4a78-103">Plain text formatting</span></span>

<span data-ttu-id="b4a78-104">F # prend en charge la mise en forme du texte brut par type vérifié à l’aide de `printf` ,, `printfn` et des `sprintf` fonctions associées.</span><span class="sxs-lookup"><span data-stu-id="b4a78-104">F# supports type-checked formatting of plain text using `printf`, `printfn`, `sprintf`, and related functions.</span></span>
<span data-ttu-id="b4a78-105">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-105">For example,</span></span>

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

<span data-ttu-id="b4a78-106">donne la sortie</span><span class="sxs-lookup"><span data-stu-id="b4a78-106">gives the output</span></span>

```fsharp
Hello world, 2 + 2 is 4
```

<span data-ttu-id="b4a78-107">F # permet également aux valeurs structurées d’être mises en forme en texte brut.</span><span class="sxs-lookup"><span data-stu-id="b4a78-107">F# also allows structured values to be formatted as plain text.</span></span>
<span data-ttu-id="b4a78-108">Par exemple, considérez l’exemple suivant qui met en forme la sortie sous la forme d’un affichage de tuples de type matrice.</span><span class="sxs-lookup"><span data-stu-id="b4a78-108">For example, consider the following example that formats the output as a matrix-like display of tuples.</span></span>

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

<span data-ttu-id="b4a78-109">La mise en forme du texte brut structuré est activée lorsque vous utilisez le `%A` format dans les `printf` chaînes de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b4a78-109">Structured plain text formatting is activated when you use the `%A` format in `printf` formatting strings.</span></span>
<span data-ttu-id="b4a78-110">Il est également activé lors de la mise en forme de la sortie des valeurs dans F # Interactive, où la sortie contient des informations supplémentaires et peut également être personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b4a78-110">It's also activated when formatting the output of values in F# interactive, where the output includes extra information and is additionally customizable.</span></span>
<span data-ttu-id="b4a78-111">La mise en forme de texte brut est également observable par le biais de tous les appels à `x.ToString()` sur les valeurs d’Union et d’enregistrement F #, y compris celles qui se produisent implicitement dans le débogage, la journalisation et d’autres outils.</span><span class="sxs-lookup"><span data-stu-id="b4a78-111">Plain text formatting is also observable through any calls to `x.ToString()` on F# union and record values, including those that occur implicitly in debugging, logging, and other tooling.</span></span>

## <a name="checking-of-printf-format-strings"></a><span data-ttu-id="b4a78-112">Vérification des `printf` chaînes de format</span><span class="sxs-lookup"><span data-stu-id="b4a78-112">Checking of `printf`-format strings</span></span>

<span data-ttu-id="b4a78-113">Une erreur de compilation est signalée si une `printf` fonction de mise en forme est utilisée avec un argument qui ne correspond pas aux spécificateurs de format printf dans la chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="b4a78-113">A compile-time error will be reported if a `printf` formatting function is used with an argument that doesn't match the printf format specifiers in the format string.</span></span>  <span data-ttu-id="b4a78-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-114">For example,</span></span>

```fsharp
sprintf "Hello %s" (2+2)
```

<span data-ttu-id="b4a78-115">donne la sortie</span><span class="sxs-lookup"><span data-stu-id="b4a78-115">gives the output</span></span>

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

<span data-ttu-id="b4a78-116">Techniquement parlant, lorsque `printf` vous utilisez et d’autres fonctions associées, une règle spéciale dans le compilateur F # vérifie le littéral de chaîne passé comme chaîne de format, ce qui garantit que les arguments suivants appliqués sont du type correct pour correspondre aux spécificateurs de format utilisés.</span><span class="sxs-lookup"><span data-stu-id="b4a78-116">Technically speaking, when using `printf` and other related functions, a special rule in the F# compiler checks the string literal passed as the format string, ensuring the subsequent arguments applied are of the correct type to match the format specifiers used.</span></span>

## <a name="format-specifiers-for-printf"></a><span data-ttu-id="b4a78-117">Spécificateurs de format pour`printf`</span><span class="sxs-lookup"><span data-stu-id="b4a78-117">Format specifiers for `printf`</span></span>

<span data-ttu-id="b4a78-118">Les spécifications de format pour les `printf` formats sont des chaînes avec des `%` marqueurs qui indiquent le format.</span><span class="sxs-lookup"><span data-stu-id="b4a78-118">Format specifications for `printf` formats are strings with `%` markers that indicate format.</span></span> <span data-ttu-id="b4a78-119">Les espaces réservés de format se composent de `%[flags][width][.precision][type]` là où le type est interprété comme suit :</span><span class="sxs-lookup"><span data-stu-id="b4a78-119">Format placeholders consist of `%[flags][width][.precision][type]` where the type is interpreted as follows:</span></span>

| <span data-ttu-id="b4a78-120">Spécificateur de format</span><span class="sxs-lookup"><span data-stu-id="b4a78-120">Format specifier</span></span>   | <span data-ttu-id="b4a78-121">Type (s)</span><span class="sxs-lookup"><span data-stu-id="b4a78-121">Type(s)</span></span>        | <span data-ttu-id="b4a78-122">Notes</span><span class="sxs-lookup"><span data-stu-id="b4a78-122">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | <span data-ttu-id="b4a78-123">bool</span><span class="sxs-lookup"><span data-stu-id="b4a78-123">bool</span></span>      | <span data-ttu-id="b4a78-124">Mise en forme en tant que `true` ou`false`</span><span class="sxs-lookup"><span data-stu-id="b4a78-124">Formatted as `true` or `false`</span></span>                |
| `%s`               | <span data-ttu-id="b4a78-125">string</span><span class="sxs-lookup"><span data-stu-id="b4a78-125">string</span></span>    | <span data-ttu-id="b4a78-126">Mise en forme en tant que contenu sans séquence d’échappement</span><span class="sxs-lookup"><span data-stu-id="b4a78-126">Formatted as its unescaped contents</span></span>         |
| `%c`               | <span data-ttu-id="b4a78-127">char</span><span class="sxs-lookup"><span data-stu-id="b4a78-127">char</span></span>      | <span data-ttu-id="b4a78-128">Mise en forme en tant que littéral de caractère</span><span class="sxs-lookup"><span data-stu-id="b4a78-128">Formatted as the character literal</span></span>  |
| <span data-ttu-id="b4a78-129">`%d`, `%i`</span><span class="sxs-lookup"><span data-stu-id="b4a78-129">`%d`, `%i`</span></span>         | <span data-ttu-id="b4a78-130">type entier de base</span><span class="sxs-lookup"><span data-stu-id="b4a78-130">a basic integer type</span></span> | <span data-ttu-id="b4a78-131">Formaté comme un entier décimal, signé si le type entier de base est signé</span><span class="sxs-lookup"><span data-stu-id="b4a78-131">Formatted as a decimal integer, signed if the basic integer type is signed</span></span> |
| `%u`               | <span data-ttu-id="b4a78-132">type entier de base</span><span class="sxs-lookup"><span data-stu-id="b4a78-132">a basic integer type</span></span> | <span data-ttu-id="b4a78-133">Mise en forme en tant qu’entier décimal non signé</span><span class="sxs-lookup"><span data-stu-id="b4a78-133">Formatted as an unsigned decimal integer</span></span>   |
| <span data-ttu-id="b4a78-134">`%x`, `%X`</span><span class="sxs-lookup"><span data-stu-id="b4a78-134">`%x`, `%X`</span></span>         | <span data-ttu-id="b4a78-135">type entier de base</span><span class="sxs-lookup"><span data-stu-id="b4a78-135">a basic integer type</span></span> | <span data-ttu-id="b4a78-136">Mise en forme en tant que nombre hexadécimal non signé (a-f ou A-F pour les chiffres hexadécimaux, respectivement)</span><span class="sxs-lookup"><span data-stu-id="b4a78-136">Formatted as an unsigned hexadecimal number (a-f or A-F for hex digits respectively)</span></span>  |
|  `%o`              | <span data-ttu-id="b4a78-137">type entier de base</span><span class="sxs-lookup"><span data-stu-id="b4a78-137">a basic integer type</span></span> | <span data-ttu-id="b4a78-138">Mise en forme en tant que nombre octal non signé</span><span class="sxs-lookup"><span data-stu-id="b4a78-138">Formatted as an unsigned octal number</span></span> |
| <span data-ttu-id="b4a78-139">`%e`, `%E`</span><span class="sxs-lookup"><span data-stu-id="b4a78-139">`%e`, `%E`</span></span>         | <span data-ttu-id="b4a78-140">type à virgule flottante de base</span><span class="sxs-lookup"><span data-stu-id="b4a78-140">a basic floating point type</span></span> | <span data-ttu-id="b4a78-141">Mise en forme sous la forme d’une valeur signée, `[-]d.dddde[sign]ddd` où d est un chiffre décimal unique, dddd est un ou plusieurs chiffres décimaux, ddd est exactement trois chiffres décimaux, et signe est `+` ou`-`</span><span class="sxs-lookup"><span data-stu-id="b4a78-141">Formatted as a signed value having the form `[-]d.dddde[sign]ddd` where d is a single decimal digit, dddd is one or more decimal digits, ddd is exactly three decimal digits, and sign is `+` or `-`</span></span> |
| `%f`               | <span data-ttu-id="b4a78-142">type à virgule flottante de base</span><span class="sxs-lookup"><span data-stu-id="b4a78-142">a basic floating point type</span></span> | <span data-ttu-id="b4a78-143">Mise en forme sous forme de valeur signée sous la forme `[-]dddd.dddd` , où `dddd` représente un ou plusieurs chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="b4a78-143">Formatted as a signed value having the form `[-]dddd.dddd`, where `dddd` is one or more decimal digits.</span></span> <span data-ttu-id="b4a78-144">Le nombre de chiffres avant la virgule décimale dépend de l'ampleur du nombre, et le nombre de chiffres après que la virgule décimale dépend de la précision demandée.</span><span class="sxs-lookup"><span data-stu-id="b4a78-144">The number of digits before the decimal point depends on the magnitude of the number, and the number of digits after the decimal point depends on the requested precision.</span></span> |
| <span data-ttu-id="b4a78-145">`%g`, `%G`</span><span class="sxs-lookup"><span data-stu-id="b4a78-145">`%g`, `%G`</span></span> | <span data-ttu-id="b4a78-146">type à virgule flottante de base</span><span class="sxs-lookup"><span data-stu-id="b4a78-146">a basic floating point type</span></span> |  <span data-ttu-id="b4a78-147">Mise en forme à l’aide de comme valeur signée imprimée `%f` ou `%e` formatée, selon la valeur la plus petite pour la valeur et la précision données.</span><span class="sxs-lookup"><span data-stu-id="b4a78-147">Formatted using as a signed value printed in `%f` or `%e` format, whichever is more compact for the given value and precision.</span></span> |
| `%M` | <span data-ttu-id="b4a78-148">une `System.Decimal` valeur</span><span class="sxs-lookup"><span data-stu-id="b4a78-148">a `System.Decimal` value</span></span>  |    <span data-ttu-id="b4a78-149">Mis en forme à l’aide du `"G"` spécificateur de format pour`System.Decimal.ToString(format)`</span><span class="sxs-lookup"><span data-stu-id="b4a78-149">Formatted using the `"G"` format specifier for `System.Decimal.ToString(format)`</span></span> |
| `%O` | <span data-ttu-id="b4a78-150">toute valeur</span><span class="sxs-lookup"><span data-stu-id="b4a78-150">any value</span></span>  |   <span data-ttu-id="b4a78-151">Mise en forme par boxing de l’objet et valling de sa `System.Object.ToString()` méthode</span><span class="sxs-lookup"><span data-stu-id="b4a78-151">Formatted by boxing the object and valling its `System.Object.ToString()` method</span></span> |
| `%A` | <span data-ttu-id="b4a78-152">toute valeur</span><span class="sxs-lookup"><span data-stu-id="b4a78-152">any value</span></span>  |   <span data-ttu-id="b4a78-153">Formaté à l’aide de la [mise en forme du texte brut structuré](plaintext-formatting.md) avec les paramètres de disposition par défaut</span><span class="sxs-lookup"><span data-stu-id="b4a78-153">Formatted using [structured plain text formatting](plaintext-formatting.md) with the default layout settings</span></span> |
| `%a` | <span data-ttu-id="b4a78-154">toute valeur</span><span class="sxs-lookup"><span data-stu-id="b4a78-154">any value</span></span>  |   <span data-ttu-id="b4a78-155">Nécessite deux arguments : une fonction de mise en forme qui accepte un paramètre de contexte et la valeur, ainsi que la valeur particulière à imprimer.</span><span class="sxs-lookup"><span data-stu-id="b4a78-155">Requires two arguments - a formatting function accepting a context parameter and the value, and the particular value to print</span></span> |
| `%t` | <span data-ttu-id="b4a78-156">toute valeur</span><span class="sxs-lookup"><span data-stu-id="b4a78-156">any value</span></span>  |   <span data-ttu-id="b4a78-157">Nécessite un argument, une fonction de mise en forme qui accepte un paramètre de contexte qui génère ou retourne le texte approprié.</span><span class="sxs-lookup"><span data-stu-id="b4a78-157">Requires one argument, a formatting function accepting a context parameter that either outputs or returns the appropriate text</span></span> |

<span data-ttu-id="b4a78-158">Les types entiers de base sont `byte` ( `System.Byte` ), `sbyte` ( `System.SByte` ), `int16` ( `System.Int16` ), `uint16` ( `System.UInt16` ), `int32` ( `System.Int32` ), `uint32` ( `System.UInt32` ), `int64` ( `System.Int64` ), `uint64` ( `System.UInt64` ), `nativeint` ( `System.IntPtr` ) et `unativeint` ( `System.UIntPtr` ).</span><span class="sxs-lookup"><span data-stu-id="b4a78-158">Basic integer types are `byte` (`System.Byte`), `sbyte` (`System.SByte`), `int16` (`System.Int16`), `uint16` (`System.UInt16`), `int32` (`System.Int32`), `uint32` (`System.UInt32`), `int64` (`System.Int64`), `uint64` (`System.UInt64`), `nativeint`  (`System.IntPtr`), and `unativeint`  (`System.UIntPtr`).</span></span>
<span data-ttu-id="b4a78-159">Les types à virgule flottante de base sont `float` ( `System.Double` ) et `float32` ( `System.Single` ).</span><span class="sxs-lookup"><span data-stu-id="b4a78-159">Basic floating point types are `float` (`System.Double`) and `float32` (`System.Single`).</span></span>

<span data-ttu-id="b4a78-160">La largeur facultative est un entier indiquant la largeur minimale du résultat.</span><span class="sxs-lookup"><span data-stu-id="b4a78-160">The optional width is an integer indicating the minimal width of the result.</span></span> <span data-ttu-id="b4a78-161">Par exemple, `%6d` imprime un entier, en le préfixant avec des espaces pour remplir au moins 6 caractères.</span><span class="sxs-lookup"><span data-stu-id="b4a78-161">For instance, `%6d` prints an integer, prefixing it with spaces to fill at least 6 characters.</span></span> <span data-ttu-id="b4a78-162">Si width est `*` , un argument entier supplémentaire est utilisé pour spécifier la largeur correspondante.</span><span class="sxs-lookup"><span data-stu-id="b4a78-162">If width is `*`, then an extra integer  argument is taken to specify the corresponding width.</span></span>

<span data-ttu-id="b4a78-163">Les indicateurs valides sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="b4a78-163">Valid flags are:</span></span>

| <span data-ttu-id="b4a78-164">Indicateur</span><span class="sxs-lookup"><span data-stu-id="b4a78-164">Flag</span></span>   | <span data-ttu-id="b4a78-165">Résultat</span><span class="sxs-lookup"><span data-stu-id="b4a78-165">Effect</span></span>        | <span data-ttu-id="b4a78-166">Notes</span><span class="sxs-lookup"><span data-stu-id="b4a78-166">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | <span data-ttu-id="b4a78-167">Ajoutez des zéros à la place des espaces pour créer la largeur requise</span><span class="sxs-lookup"><span data-stu-id="b4a78-167">Add zeros instead of spaces to make up the required width</span></span> |    |
| `-` |  <span data-ttu-id="b4a78-168">Aligner à gauche le résultat dans la largeur spécifiée</span><span class="sxs-lookup"><span data-stu-id="b4a78-168">Left justify the result within the specified width</span></span> |   |
| `+`  | <span data-ttu-id="b4a78-169">Ajoutez un `+` caractère si le nombre est positif (pour correspondre à un `-` signe pour les négatifs)</span><span class="sxs-lookup"><span data-stu-id="b4a78-169">Add a `+` character if the number is positive (to match a `-` sign for negatives)</span></span> |   |
| <span data-ttu-id="b4a78-170">espace</span><span class="sxs-lookup"><span data-stu-id="b4a78-170">space character</span></span> | <span data-ttu-id="b4a78-171">Ajoutez un espace supplémentaire si le nombre est positif (pour correspondre à un signe « - » pour les valeurs négatives)</span><span class="sxs-lookup"><span data-stu-id="b4a78-171">Add an extra space if the number is positive (to match a '-' sign for negatives)</span></span> |

<span data-ttu-id="b4a78-172">L' `#` indicateur printf n’est pas valide et une erreur de compilation est signalée s’il est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b4a78-172">The printf `#` flag is invalid and a compile-time error will be reported if it is used.</span></span>

<span data-ttu-id="b4a78-173">Les valeurs sont mises en forme à l’aide de la culture dite indifférente.</span><span class="sxs-lookup"><span data-stu-id="b4a78-173">Values are formatted using invariant culture.</span></span> <span data-ttu-id="b4a78-174">Les paramètres de culture ne sont pas pertinents pour `printf` la mise en forme, sauf lorsqu’ils affectent les résultats `%O` et la `%A` mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b4a78-174">Culture settings are irrelevant to `printf` formatting except when they affect the results of `%O` and `%A` formatting.</span></span> <span data-ttu-id="b4a78-175">Pour plus d’informations, consultez [mise en forme du texte brut structuré](plaintext-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="b4a78-175">For more information, see [structured plain text formatting](plaintext-formatting.md).</span></span>

## <a name="a-formatting"></a><span data-ttu-id="b4a78-176">`%A`mise en forme</span><span class="sxs-lookup"><span data-stu-id="b4a78-176">`%A` formatting</span></span>

<span data-ttu-id="b4a78-177">Le `%A` spécificateur de format est utilisé pour mettre en forme les valeurs de façon lisible par l’utilisateur, et peut également être utile pour signaler des informations de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="b4a78-177">The `%A` format specifier is used to format values in a human-readable way, and can also be useful for reporting diagnostic information.</span></span>

### <a name="primitive-values"></a><span data-ttu-id="b4a78-178">Valeurs primitives</span><span class="sxs-lookup"><span data-stu-id="b4a78-178">Primitive values</span></span>

<span data-ttu-id="b4a78-179">Lors de la mise en forme de texte brut à l’aide du `%A` spécificateur, les valeurs numériques F # sont mises en forme avec leur suffixe et leur culture dite indifférente.</span><span class="sxs-lookup"><span data-stu-id="b4a78-179">When formatting plain text using the `%A` specifier, F# numeric values are formatted with their suffix and invariant culture.</span></span> <span data-ttu-id="b4a78-180">Les valeurs à virgule flottante sont mises en forme à l’aide de 10 emplacements de précision à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="b4a78-180">Floating point values are formatted using 10 places of floating point precision.</span></span> <span data-ttu-id="b4a78-181">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-181">For example,</span></span>

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

<span data-ttu-id="b4a78-182">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-182">produces</span></span>

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

<span data-ttu-id="b4a78-183">Lors de l’utilisation du `%A` spécificateur, les chaînes sont mises en forme à l’aide de guillemets.</span><span class="sxs-lookup"><span data-stu-id="b4a78-183">When using the `%A` specifier, strings are formatted using quotes.</span></span> <span data-ttu-id="b4a78-184">Les codes d’échappement ne sont pas ajoutés, mais les caractères bruts sont imprimés.</span><span class="sxs-lookup"><span data-stu-id="b4a78-184">Escape codes are not added and instead the raw characters are printed.</span></span> <span data-ttu-id="b4a78-185">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-185">For example,</span></span>

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

<span data-ttu-id="b4a78-186">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-186">produces</span></span>

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a><span data-ttu-id="b4a78-187">Valeurs .NET</span><span class="sxs-lookup"><span data-stu-id="b4a78-187">.NET values</span></span>

<span data-ttu-id="b4a78-188">Lors de la mise en forme de texte brut à l’aide du `%A` spécificateur, les objets non F # .net sont mis en forme à l’aide `x.ToString()` des paramètres par défaut de .net fournis par `System.Globalization.CultureInfo.CurrentCulture` et `System.Globalization.CultureInfo.CurrentUICulture` .</span><span class="sxs-lookup"><span data-stu-id="b4a78-188">When formatting plain text using the `%A` specifier, non-F# .NET objects are formatted by using `x.ToString()` using the default settings of .NET given by `System.Globalization.CultureInfo.CurrentCulture` and `System.Globalization.CultureInfo.CurrentUICulture`.</span></span>  <span data-ttu-id="b4a78-189">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-189">For example,</span></span>

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

<span data-ttu-id="b4a78-190">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-190">produces</span></span>

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a><span data-ttu-id="b4a78-191">Valeurs structurées</span><span class="sxs-lookup"><span data-stu-id="b4a78-191">Structured values</span></span>

<span data-ttu-id="b4a78-192">Lors de la mise en forme de texte brut à l’aide du `%A` spécificateur, le retrait de bloc est utilisé pour les listes et les tuples F #.</span><span class="sxs-lookup"><span data-stu-id="b4a78-192">When formatting plain text using the `%A` specifier, block indentation is used for F# lists and tuples.</span></span> <span data-ttu-id="b4a78-193">Le est illustré dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="b4a78-193">The is shown in the previous example.</span></span>
<span data-ttu-id="b4a78-194">La structure des tableaux est également utilisée, y compris les tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="b4a78-194">The structure of arrays is also used, including multi-dimensional arrays.</span></span>  <span data-ttu-id="b4a78-195">Les tableaux unidimensionnels sont affichés avec la `[| ... |]` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="b4a78-195">Single-dimensional arrays are shown with `[| ... |]` syntax.</span></span> <span data-ttu-id="b4a78-196">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-196">For example,</span></span>

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

<span data-ttu-id="b4a78-197">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-197">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

<span data-ttu-id="b4a78-198">La largeur d’impression par défaut est 80.</span><span class="sxs-lookup"><span data-stu-id="b4a78-198">The default print width is 80.</span></span>  <span data-ttu-id="b4a78-199">Cette largeur peut être personnalisée à l’aide d’une largeur d’impression dans le spécificateur de format.</span><span class="sxs-lookup"><span data-stu-id="b4a78-199">This width can be customized by using a print width in the format specifier.</span></span> <span data-ttu-id="b4a78-200">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-200">For example,</span></span>

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

<span data-ttu-id="b4a78-201">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-201">produces</span></span>

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

<span data-ttu-id="b4a78-202">Si vous spécifiez une largeur d’impression égale à 0, aucune largeur d’impression n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b4a78-202">Specifying a print width of 0 results in no print width being used.</span></span> <span data-ttu-id="b4a78-203">Une seule ligne de texte se produit, sauf lorsque les chaînes incorporées dans la sortie contiennent elles-mêmes sauts.</span><span class="sxs-lookup"><span data-stu-id="b4a78-203">A single line of text will result, except where embedded strings in the output themselves contain linebreaks.</span></span>  <span data-ttu-id="b4a78-204">Par exemple</span><span class="sxs-lookup"><span data-stu-id="b4a78-204">For example</span></span>

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef |]
```

<span data-ttu-id="b4a78-205">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-205">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

<span data-ttu-id="b4a78-206">Une limite de profondeur de 4 est utilisée pour les `IEnumerable` valeurs Sequence (), qui sont affichées sous la forme `seq { ...}` .</span><span class="sxs-lookup"><span data-stu-id="b4a78-206">A depth limit of 4 is used for sequence (`IEnumerable`) values, which are shown as `seq { ...}`.</span></span> <span data-ttu-id="b4a78-207">Une limite de profondeur de 100 est utilisée pour les valeurs de liste et de tableau.</span><span class="sxs-lookup"><span data-stu-id="b4a78-207">A depth limit of 100 is used for list and array values.</span></span>
<span data-ttu-id="b4a78-208">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-208">For example,</span></span>

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

<span data-ttu-id="b4a78-209">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-209">produces</span></span>

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

<span data-ttu-id="b4a78-210">La mise en retrait de bloc est également utilisée pour la structure des valeurs d’enregistrement et d’Union publiques.</span><span class="sxs-lookup"><span data-stu-id="b4a78-210">Block indentation is also used for the the structure of public record and union values.</span></span> <span data-ttu-id="b4a78-211">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-211">For example,</span></span>

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="b4a78-212">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-212">produces</span></span>

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="b4a78-213">Si `%+A` est utilisé, la structure privée des enregistrements et des unions est également révélée à l’aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="b4a78-213">If `%+A` is used, then the private structure of records and unions is also revealed by using reflection.</span></span> <span data-ttu-id="b4a78-214">Par exemple</span><span class="sxs-lookup"><span data-stu-id="b4a78-214">For example</span></span>

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

<span data-ttu-id="b4a78-215">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-215">produces</span></span>

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a><span data-ttu-id="b4a78-216">Valeurs volumineuses, cycliques ou profondément imbriquées</span><span class="sxs-lookup"><span data-stu-id="b4a78-216">Large, cyclic, or deeply nested values</span></span>

<span data-ttu-id="b4a78-217">Les valeurs structurées volumineuses sont mises en forme sur un nombre total de nœuds objet de 10000.</span><span class="sxs-lookup"><span data-stu-id="b4a78-217">Large structured values are formatted to a maximum overall object node count of 10000.</span></span>
<span data-ttu-id="b4a78-218">Les valeurs profondément imbriquées sont mises en forme à une profondeur de 100.</span><span class="sxs-lookup"><span data-stu-id="b4a78-218">Deeply nested values are formatted to a depth of 100.</span></span>  <span data-ttu-id="b4a78-219">Dans les deux cas, `...` est utilisé pour Elide une partie de la sortie.</span><span class="sxs-lookup"><span data-stu-id="b4a78-219">In both cases `...` is used to elide some of the output.</span></span>  <span data-ttu-id="b4a78-220">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-220">For example,</span></span>

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

<span data-ttu-id="b4a78-221">produit une sortie volumineuse avec quelques parties élidé :</span><span class="sxs-lookup"><span data-stu-id="b4a78-221">produces a large output with some parts elided:</span></span>

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

<span data-ttu-id="b4a78-222">Les cycles sont détectés dans les graphiques d’objets et `...` sont utilisés aux endroits où les cycles sont détectés.</span><span class="sxs-lookup"><span data-stu-id="b4a78-222">Cycles are detected in the object graphs and `...` is used at places where cycles are detected.</span></span> <span data-ttu-id="b4a78-223">Par exemple</span><span class="sxs-lookup"><span data-stu-id="b4a78-223">For example</span></span>

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

<span data-ttu-id="b4a78-224">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-224">produces</span></span>

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a><span data-ttu-id="b4a78-225">Valeurs tardive, NULL et de fonction</span><span class="sxs-lookup"><span data-stu-id="b4a78-225">Lazy, null, and function values</span></span>

<span data-ttu-id="b4a78-226">Les valeurs tardives sont imprimées sous forme de `Value is not created` texte ou équivalent lorsque la valeur n’a pas encore été évaluée.</span><span class="sxs-lookup"><span data-stu-id="b4a78-226">Lazy values are printed as `Value is not created` or equivalent text when the value has not yet been evaluated.</span></span>

<span data-ttu-id="b4a78-227">Les valeurs NULL sont imprimées sous `null` la forme, sauf si le type statique de la valeur est déterminé comme étant un type d’Union où `null` est un représentation autorisé.</span><span class="sxs-lookup"><span data-stu-id="b4a78-227">Null values are printed as `null` unless the static type of the value is determined to be a union type where `null` is a permitted represenation.</span></span>

<span data-ttu-id="b4a78-228">Les valeurs de fonction F # sont imprimées comme nom de fermeture généré en interne, par exemple, `<fun:it@43-7>` .</span><span class="sxs-lookup"><span data-stu-id="b4a78-228">F# function values are printed as their internally generated closure name, for example, `<fun:it@43-7>`.</span></span>

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a><span data-ttu-id="b4a78-229">Personnaliser la mise en forme du texte brut avec`StructuredFormatDisplay`</span><span class="sxs-lookup"><span data-stu-id="b4a78-229">Customize plain text formatting with `StructuredFormatDisplay`</span></span>

<span data-ttu-id="b4a78-230">Lors de l’utilisation du `%A` spécificateur, la présence de l' `StructuredFormatDisplay` attribut sur les déclarations de type est respectée.</span><span class="sxs-lookup"><span data-stu-id="b4a78-230">When using the `%A` specifier, the presence of the `StructuredFormatDisplay` attribute on type declarations is respected.</span></span>  <span data-ttu-id="b4a78-231">Cela peut être utilisé pour spécifier le texte de substitution et la propriété pour afficher une valeur.</span><span class="sxs-lookup"><span data-stu-id="b4a78-231">This can be used to specify surrogate text and property to display a value.</span></span> <span data-ttu-id="b4a78-232">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-232">For example:</span></span>

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

<span data-ttu-id="b4a78-233">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-233">produces</span></span>

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a><span data-ttu-id="b4a78-234">Personnaliser la mise en forme du texte brut en remplaçant`ToString`</span><span class="sxs-lookup"><span data-stu-id="b4a78-234">Customize plain text formatting by overriding `ToString`</span></span>

<span data-ttu-id="b4a78-235">L’implémentation par défaut de `ToString` est observable dans la programmation F #.</span><span class="sxs-lookup"><span data-stu-id="b4a78-235">The default implementation of `ToString` is observable in F# programming.</span></span> <span data-ttu-id="b4a78-236">Souvent, les résultats par défaut ne sont pas adaptés à une utilisation dans l’affichage des informations du programmeur ou la sortie utilisateur, et par conséquent, il est courant de remplacer l’implémentation par défaut.</span><span class="sxs-lookup"><span data-stu-id="b4a78-236">Often, the default results aren't suitable for use in either programmer-facing information display or user output, and as a result it is common to override the default implementation.</span></span>  

<span data-ttu-id="b4a78-237">Par défaut, les types d’enregistrement et d’Union F # remplacent l’implémentation de `ToString` par une implémentation de qui utilise `sprintf "%+A"` .</span><span class="sxs-lookup"><span data-stu-id="b4a78-237">By default, F# record and union types override the implementation of `ToString` with an implementation that uses `sprintf "%+A"`.</span></span>  <span data-ttu-id="b4a78-238">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-238">For example,</span></span>

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

<span data-ttu-id="b4a78-239">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-239">produces</span></span>

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

<span data-ttu-id="b4a78-240">Pour les types de classe, aucune implémentation par défaut de `ToString` n’est fournie et la valeur par défaut .net est utilisée, qui indique le nom du type.</span><span class="sxs-lookup"><span data-stu-id="b4a78-240">For class types, no default implementation of `ToString` is provided and the .NET default is used, which reports the name of the type.</span></span> <span data-ttu-id="b4a78-241">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b4a78-241">For example,</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="b4a78-242">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-242">produces</span></span>

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

<span data-ttu-id="b4a78-243">L’ajout d’un remplacement pour `ToString` peut offrir une meilleure mise en forme.</span><span class="sxs-lookup"><span data-stu-id="b4a78-243">Adding an override for `ToString` can give better formatting.</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="b4a78-244">tiges</span><span class="sxs-lookup"><span data-stu-id="b4a78-244">produces</span></span>

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="b4a78-245">F# Interactive l’impression structurée</span><span class="sxs-lookup"><span data-stu-id="b4a78-245">F# Interactive structured printing</span></span>

<span data-ttu-id="b4a78-246">F# Interactive ( `dotnet fsi` ) utilise une version étendue de la mise en forme de texte brut structurée pour signaler des valeurs et permet une personnalisation supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="b4a78-246">F# Interactive (`dotnet fsi`) uses an extended version of structured plain text formatting to report values and allows additional customizability.</span></span> <span data-ttu-id="b4a78-247">Pour plus d’informations, consultez [F# Interactive](fsharp-interactive-options.md).</span><span class="sxs-lookup"><span data-stu-id="b4a78-247">For more information, see [F# Interactive](fsharp-interactive-options.md).</span></span>

## <a name="customize-debug-displays"></a><span data-ttu-id="b4a78-248">Personnaliser les affichages de débogage</span><span class="sxs-lookup"><span data-stu-id="b4a78-248">Customize debug displays</span></span>

<span data-ttu-id="b4a78-249">Les débogueurs pour .NET respectent l’utilisation d’attributs tels que `DebuggerDisplay` et `DebuggerTypeProxy` , et ceux-ci affectent l’affichage structuré des objets dans les fenêtres d’inspection du débogueur.</span><span class="sxs-lookup"><span data-stu-id="b4a78-249">Debuggers for .NET respect the use of attributes such as `DebuggerDisplay` and `DebuggerTypeProxy`, and these affect the structured display of objects in debugger inspection windows.</span></span>
<span data-ttu-id="b4a78-250">Le compilateur F # a généré automatiquement ces attributs pour les types d’Union et d’enregistrement discriminés, mais pas pour les types de classe, d’interface ou de struct.</span><span class="sxs-lookup"><span data-stu-id="b4a78-250">The F# compiler automatically generated these attributes for discriminated union and record types, but not class, interface, or struct types.</span></span>

<span data-ttu-id="b4a78-251">Ces attributs sont ignorés dans la mise en forme de texte brut F #, mais il peut être utile d’implémenter ces méthodes pour améliorer les affichages lors du débogage de types F #.</span><span class="sxs-lookup"><span data-stu-id="b4a78-251">These attributes are ignored in F# plain text formatting, but it can be useful to implement these methods to improve displays when debugging F# types.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4a78-252">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4a78-252">See also</span></span>

- [<span data-ttu-id="b4a78-253">Chaînes</span><span class="sxs-lookup"><span data-stu-id="b4a78-253">Strings</span></span>](strings.md)
- [<span data-ttu-id="b4a78-254">Documents</span><span class="sxs-lookup"><span data-stu-id="b4a78-254">Records</span></span>](records.md)
- [<span data-ttu-id="b4a78-255">Unions discriminées</span><span class="sxs-lookup"><span data-stu-id="b4a78-255">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="b4a78-256">F# Interactive</span><span class="sxs-lookup"><span data-stu-id="b4a78-256">F# Interactive</span></span>](fsharp-interactive-options.md)
