---
title: Attributs
description: Découvrez comment F# les attributs permettent d’appliquer des métadonnées à une construction de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: 223263f5789b0fc7eb2b3ef2905f6436980bd14a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424799"
---
# <a name="attributes"></a><span data-ttu-id="bbb57-103">Attributs</span><span class="sxs-lookup"><span data-stu-id="bbb57-103">Attributes</span></span>

<span data-ttu-id="bbb57-104">Les attributs permettent d’appliquer des métadonnées à une construction de programmation.</span><span class="sxs-lookup"><span data-stu-id="bbb57-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="bbb57-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbb57-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="bbb57-106">Notes</span><span class="sxs-lookup"><span data-stu-id="bbb57-106">Remarks</span></span>

<span data-ttu-id="bbb57-107">Dans la syntaxe précédente, la *cible* est facultative et, si elle est présente, spécifie le genre d’entité de programme à laquelle l’attribut s’applique.</span><span class="sxs-lookup"><span data-stu-id="bbb57-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="bbb57-108">Les valeurs valides pour la *cible* sont indiquées dans le tableau qui apparaît plus loin dans ce document.</span><span class="sxs-lookup"><span data-stu-id="bbb57-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="bbb57-109">L' *attribut-Name* fait référence au nom (éventuellement qualifié avec des espaces de noms) d’un type d’attribut valide, avec ou sans le suffixe `Attribute` qui est généralement utilisé dans les noms de types d’attributs.</span><span class="sxs-lookup"><span data-stu-id="bbb57-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="bbb57-110">Par exemple, le type `ObsoleteAttribute` peut être abrégé en `Obsolete` dans ce contexte.</span><span class="sxs-lookup"><span data-stu-id="bbb57-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="bbb57-111">Les *arguments* sont les arguments du constructeur pour le type d’attribut.</span><span class="sxs-lookup"><span data-stu-id="bbb57-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="bbb57-112">Si un attribut a un constructeur sans paramètre, la liste d’arguments et les parenthèses peuvent être omises.</span><span class="sxs-lookup"><span data-stu-id="bbb57-112">If an attribute has a parameterless constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="bbb57-113">Les attributs prennent en charge les arguments positionnels et les arguments nommés.</span><span class="sxs-lookup"><span data-stu-id="bbb57-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="bbb57-114">Les *arguments positionnels* sont des arguments utilisés dans l’ordre dans lequel ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="bbb57-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="bbb57-115">Les arguments nommés peuvent être utilisés si l’attribut a des propriétés publiques.</span><span class="sxs-lookup"><span data-stu-id="bbb57-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="bbb57-116">Vous pouvez les définir à l’aide de la syntaxe suivante dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="bbb57-116">You can set these by using the following syntax in the argument list.</span></span>

```fsharp
property-name = property-value
```

<span data-ttu-id="bbb57-117">Ces initialisations de propriété peuvent être dans n’importe quel ordre, mais elles doivent suivre tous les arguments positionnels.</span><span class="sxs-lookup"><span data-stu-id="bbb57-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="bbb57-118">Voici un exemple d’un attribut qui utilise des arguments positionnels et des initialisations de propriétés :</span><span class="sxs-lookup"><span data-stu-id="bbb57-118">The following is an example of an attribute that uses positional arguments and property initializations:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="bbb57-119">Dans cet exemple, l’attribut est `DllImportAttribute`, ici utilisé sous forme abrégée.</span><span class="sxs-lookup"><span data-stu-id="bbb57-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="bbb57-120">Le premier argument est un paramètre positionnel et le second est une propriété.</span><span class="sxs-lookup"><span data-stu-id="bbb57-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="bbb57-121">Les attributs sont une construction de programmation .NET qui permet à un objet connu comme un *attribut* d’être associé à un type ou à un autre élément de programme.</span><span class="sxs-lookup"><span data-stu-id="bbb57-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="bbb57-122">L’élément de programme auquel un attribut est appliqué est appelé la *cible d’attribut*.</span><span class="sxs-lookup"><span data-stu-id="bbb57-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="bbb57-123">L’attribut contient généralement des métadonnées sur sa cible.</span><span class="sxs-lookup"><span data-stu-id="bbb57-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="bbb57-124">Dans ce contexte, les métadonnées peuvent être des données relatives au type autres que ses champs et membres.</span><span class="sxs-lookup"><span data-stu-id="bbb57-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="bbb57-125">Les attributs F# dans peuvent être appliqués aux constructions de programmation suivantes : fonctions, méthodes, assemblys, modules, types (classes, enregistrements, structures, interfaces, délégués, énumérations, unions, etc.), constructeurs, propriétés, champs, paramètres, paramètres de type et valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="bbb57-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="bbb57-126">Les attributs ne sont pas autorisés sur les liaisons `let` dans des classes, des expressions ou des expressions de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="bbb57-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="bbb57-127">En règle générale, la déclaration d’attribut apparaît directement avant la déclaration de la cible de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="bbb57-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="bbb57-128">Plusieurs déclarations d’attribut peuvent être utilisées ensemble, comme suit :</span><span class="sxs-lookup"><span data-stu-id="bbb57-128">Multiple attribute declarations can be used together, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="bbb57-129">Vous pouvez interroger des attributs au moment de l’exécution à l’aide de la réflexion .NET.</span><span class="sxs-lookup"><span data-stu-id="bbb57-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="bbb57-130">Vous pouvez déclarer plusieurs attributs individuellement, comme dans l’exemple de code précédent, ou vous pouvez les déclarer dans un jeu de crochets si vous utilisez un point-virgule pour séparer les attributs et les constructeurs individuels, comme suit :</span><span class="sxs-lookup"><span data-stu-id="bbb57-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="bbb57-131">Les attributs généralement rencontrés incluent l’attribut `Obsolete`, les attributs pour les considérations de sécurité, les attributs pour la prise en charge de COM, les attributs liés à la propriété du code et les attributs indiquant si un type peut être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="bbb57-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="bbb57-132">L’exemple suivant illustre l’utilisation de l’attribut `Obsolete`.</span><span class="sxs-lookup"><span data-stu-id="bbb57-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="bbb57-133">Pour les cibles d’attribut `assembly` et `module`, vous appliquez les attributs à une liaison de `do` de niveau supérieur dans votre assembly.</span><span class="sxs-lookup"><span data-stu-id="bbb57-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="bbb57-134">Vous pouvez inclure le mot `assembly` ou `module` dans la déclaration d’attribut, comme suit :</span><span class="sxs-lookup"><span data-stu-id="bbb57-134">You can include the word `assembly` or `module` in the attribute declaration, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="bbb57-135">Si vous omettez la cible d’attribut pour un attribut appliqué à une liaison de `do` F# , le compilateur tente de déterminer la cible d’attribut qui est logique pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="bbb57-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="bbb57-136">De nombreuses classes d’attributs ont un attribut de type `System.AttributeUsageAttribute` qui contient des informations sur les cibles possibles prises en charge pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="bbb57-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="bbb57-137">Si le `System.AttributeUsageAttribute` indique que l’attribut prend en charge les fonctions en tant que cibles, l’attribut est pris pour s’appliquer au point d’entrée principal du programme.</span><span class="sxs-lookup"><span data-stu-id="bbb57-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="bbb57-138">Si le `System.AttributeUsageAttribute` indique que l’attribut prend en charge les assemblys en tant que cibles, le compilateur prend l’attribut à appliquer à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bbb57-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="bbb57-139">La plupart des attributs ne s’appliquent pas aux fonctions et aux assemblys, mais dans les cas où ils le font, l’attribut est pris pour s’appliquer à la fonction principale du programme.</span><span class="sxs-lookup"><span data-stu-id="bbb57-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="bbb57-140">Si la cible de l’attribut est spécifiée explicitement, l’attribut est appliqué à la cible spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bbb57-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="bbb57-141">Bien qu’il ne soit généralement pas nécessaire de spécifier explicitement la cible de l’attribut, les valeurs valides pour *target* dans un attribut, ainsi que des exemples d’utilisation, sont indiquées dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="bbb57-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute along with examples of usage are shown in the following table:</span></span>

<table>
  <tr>
    <th><span data-ttu-id="bbb57-142">Cible d’attribut</span><span class="sxs-lookup"><span data-stu-id="bbb57-142">Attribute target</span></span></td>
    <th><span data-ttu-id="bbb57-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="bbb57-143">Example</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="bbb57-144">assembly</span><span class="sxs-lookup"><span data-stu-id="bbb57-144">assembly</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="bbb57-145">return</span><span class="sxs-lookup"><span data-stu-id="bbb57-145">return</span></span></td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="bbb57-146">champ</span><span class="sxs-lookup"><span data-stu-id="bbb57-146">field</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="bbb57-147">Propriété</span><span class="sxs-lookup"><span data-stu-id="bbb57-147">property</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="bbb57-148">param</span><span class="sxs-lookup"><span data-stu-id="bbb57-148">param</span></span></td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="bbb57-149">type</span><span class="sxs-lookup"><span data-stu-id="bbb57-149">type</span></span></td>
    <td>
        <pre lang="fsharp"><code>
[&lt;type: StructLayout(Sequential)&gt;]
type MyStruct =
struct
x : byte
y : int
end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="bbb57-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbb57-150">See also</span></span>

- [<span data-ttu-id="bbb57-151">Informations de référence sur le langage F#</span><span class="sxs-lookup"><span data-stu-id="bbb57-151">F# Language Reference</span></span>](index.md)
