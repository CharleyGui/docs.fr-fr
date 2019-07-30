---
title: Attributs
description: Découvrez comment F# les attributs permettent d’appliquer des métadonnées à une construction de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: 3f3c3469192c09aa51f31ef3f00aca0196e3c382
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630075"
---
# <a name="attributes"></a><span data-ttu-id="a580c-103">Attributs</span><span class="sxs-lookup"><span data-stu-id="a580c-103">Attributes</span></span>

<span data-ttu-id="a580c-104">Les attributs permettent d’appliquer des métadonnées à une construction de programmation.</span><span class="sxs-lookup"><span data-stu-id="a580c-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="a580c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a580c-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="a580c-106">Notes</span><span class="sxs-lookup"><span data-stu-id="a580c-106">Remarks</span></span>

<span data-ttu-id="a580c-107">Dans la syntaxe précédente, la *cible* est facultative et, si elle est présente, spécifie le genre d’entité de programme à laquelle l’attribut s’applique.</span><span class="sxs-lookup"><span data-stu-id="a580c-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="a580c-108">Les valeurs valides pour la *cible* sont indiquées dans le tableau qui apparaît plus loin dans ce document.</span><span class="sxs-lookup"><span data-stu-id="a580c-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="a580c-109">L' *attribut-Name* fait référence au nom (éventuellement qualifié avec des espaces de noms) d’un type d’attribut valide, avec ou `Attribute` sans le suffixe habituellement utilisé dans les noms de types d’attributs.</span><span class="sxs-lookup"><span data-stu-id="a580c-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="a580c-110">Par exemple, le type `ObsoleteAttribute` peut être abrégé en juste `Obsolete` dans ce contexte.</span><span class="sxs-lookup"><span data-stu-id="a580c-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="a580c-111">Les *arguments* sont les arguments du constructeur pour le type d’attribut.</span><span class="sxs-lookup"><span data-stu-id="a580c-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="a580c-112">Si un attribut a un constructeur par défaut, la liste d’arguments et les parenthèses peuvent être omises.</span><span class="sxs-lookup"><span data-stu-id="a580c-112">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="a580c-113">Les attributs prennent en charge les arguments positionnels et les arguments nommés.</span><span class="sxs-lookup"><span data-stu-id="a580c-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="a580c-114">Les *arguments positionnels* sont des arguments utilisés dans l’ordre dans lequel ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="a580c-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="a580c-115">Les arguments nommés peuvent être utilisés si l’attribut a des propriétés publiques.</span><span class="sxs-lookup"><span data-stu-id="a580c-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="a580c-116">Vous pouvez les définir à l’aide de la syntaxe suivante dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="a580c-116">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="a580c-117">Ces initialisations de propriété peuvent être dans n’importe quel ordre, mais elles doivent suivre tous les arguments positionnels.</span><span class="sxs-lookup"><span data-stu-id="a580c-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="a580c-118">Voici un exemple d’un attribut qui utilise des arguments positionnels et des initialisations de propriété.</span><span class="sxs-lookup"><span data-stu-id="a580c-118">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="a580c-119">Dans cet exemple, l’attribut est `DllImportAttribute`, ici utilisé sous une forme abrégée.</span><span class="sxs-lookup"><span data-stu-id="a580c-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="a580c-120">Le premier argument est un paramètre positionnel et le second est une propriété.</span><span class="sxs-lookup"><span data-stu-id="a580c-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="a580c-121">Les attributs sont une construction de programmation .NET qui permet à un objet connu comme un *attribut* d’être associé à un type ou à un autre élément de programme.</span><span class="sxs-lookup"><span data-stu-id="a580c-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="a580c-122">L’élément de programme auquel un attribut est appliqué est appelé la *cible d’attribut*.</span><span class="sxs-lookup"><span data-stu-id="a580c-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="a580c-123">L’attribut contient généralement des métadonnées sur sa cible.</span><span class="sxs-lookup"><span data-stu-id="a580c-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="a580c-124">Dans ce contexte, les métadonnées peuvent être des données relatives au type autres que ses champs et membres.</span><span class="sxs-lookup"><span data-stu-id="a580c-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="a580c-125">Les attributs F# dans peuvent être appliqués aux constructions de programmation suivantes: fonctions, méthodes, assemblys, modules, types (classes, enregistrements, structures, interfaces, délégués, énumérations, unions, etc.), constructeurs, propriétés, champs, paramètres, paramètres de type et valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="a580c-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="a580c-126">Les attributs ne sont pas `let` autorisés sur les liaisons dans des classes, des expressions ou des expressions de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="a580c-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="a580c-127">En règle générale, la déclaration d’attribut apparaît directement avant la déclaration de la cible de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="a580c-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="a580c-128">Plusieurs déclarations d’attribut peuvent être utilisées ensemble, comme suit.</span><span class="sxs-lookup"><span data-stu-id="a580c-128">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="a580c-129">Vous pouvez interroger des attributs au moment de l’exécution à l’aide de la réflexion .NET.</span><span class="sxs-lookup"><span data-stu-id="a580c-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="a580c-130">Vous pouvez déclarer plusieurs attributs individuellement, comme dans l’exemple de code précédent, ou vous pouvez les déclarer en un seul jeu de crochets si vous utilisez un point-virgule pour séparer les attributs et les constructeurs individuels, comme indiqué ici.</span><span class="sxs-lookup"><span data-stu-id="a580c-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="a580c-131">Les attributs généralement rencontrés incluent `Obsolete` l’attribut, les attributs pour les considérations de sécurité, les attributs pour la prise en charge de com, les attributs liés à la propriété du code et les attributs indiquant si un type peut être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="a580c-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="a580c-132">L’exemple suivant illustre l’utilisation de l' `Obsolete` attribut.</span><span class="sxs-lookup"><span data-stu-id="a580c-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="a580c-133">Pour les cibles `assembly` d’attribut `module`et, vous appliquez les attributs à une liaison de `do` niveau supérieur dans votre assembly.</span><span class="sxs-lookup"><span data-stu-id="a580c-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="a580c-134">Vous pouvez inclure le mot `assembly` ou `module` dans la déclaration d’attribut, comme suit.</span><span class="sxs-lookup"><span data-stu-id="a580c-134">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="a580c-135">Si vous omettez la cible d’attribut pour un attribut appliqué à `do` une liaison, F# le compilateur tente de déterminer la cible d’attribut qui est logique pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="a580c-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="a580c-136">De nombreuses classes d’attributs ont un attribut `System.AttributeUsageAttribute` de type qui contient des informations sur les cibles possibles prises en charge pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="a580c-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="a580c-137">Si le `System.AttributeUsageAttribute` indique que l’attribut prend en charge les fonctions en tant que cibles, l’attribut est pris pour s’appliquer au point d’entrée principal du programme.</span><span class="sxs-lookup"><span data-stu-id="a580c-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="a580c-138">Si le `System.AttributeUsageAttribute` indique que l’attribut prend en charge les assemblys en tant que cibles, le compilateur prend l’attribut à appliquer à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a580c-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="a580c-139">La plupart des attributs ne s’appliquent pas aux fonctions et aux assemblys, mais dans les cas où ils le font, l’attribut est pris pour s’appliquer à la fonction principale du programme.</span><span class="sxs-lookup"><span data-stu-id="a580c-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="a580c-140">Si la cible de l’attribut est spécifiée explicitement, l’attribut est appliqué à la cible spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a580c-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="a580c-141">Bien qu’il ne soit généralement pas nécessaire de spécifier explicitement la cible de l’attribut, les valeurs valides pour la *cible* dans un attribut sont indiquées dans le tableau suivant, ainsi que des exemples d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="a580c-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="a580c-142">Cible d’attribut</span><span class="sxs-lookup"><span data-stu-id="a580c-142">Attribute target</span></span></td>
    <th><span data-ttu-id="a580c-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="a580c-143">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="a580c-144">assembly</span><span class="sxs-lookup"><span data-stu-id="a580c-144">assembly</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]<code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="a580c-145">return</span><span class="sxs-lookup"><span data-stu-id="a580c-145">return</span></span></td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1<code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="a580c-146">field</span><span class="sxs-lookup"><span data-stu-id="a580c-146">field</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int<code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="a580c-147">propriété</span><span class="sxs-lookup"><span data-stu-id="a580c-147">property</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x<code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="a580c-148">param</span><span class="sxs-lookup"><span data-stu-id="a580c-148">param</span></span></td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10<code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="a580c-149">type</span><span class="sxs-lookup"><span data-stu-id="a580c-149">type</span></span></td>
    <td>
        <pre lang="fsharp"><code>
        [&lt;type: StructLayout(Sequential)&gt;] 
        type MyStruct = 
        struct 
        x : byte
        y : int
        end
        <code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="a580c-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a580c-150">See also</span></span>

- [<span data-ttu-id="a580c-151">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="a580c-151">F# Language Reference</span></span>](index.md)
