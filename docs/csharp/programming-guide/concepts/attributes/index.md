---
title: Attributs (C#)
description: Découvrez comment utiliser des attributs pour associer des métadonnées ou des informations déclaratives au code en C#. Un attribut peut être interrogé au moment de l’exécution à l’aide de la réflexion.
ms.date: 04/26/2018
ms.openlocfilehash: 5c57838b649531d8e8fe89919771adf8830e7f54
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924983"
---
# <a name="attributes-c"></a><span data-ttu-id="a79c7-104">Attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="a79c7-104">Attributes (C#)</span></span>

<span data-ttu-id="a79c7-105">Les attributs fournissent une méthode puissante permettant d’associer des métadonnées ou des informations déclaratives avec du code (assemblys, types, méthodes, propriétés, etc.).</span><span class="sxs-lookup"><span data-stu-id="a79c7-105">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="a79c7-106">Une fois associé à une entité de programme, l’attribut peut être interrogé à l’exécution à l’aide d’une technique appelée *réflexion*.</span><span class="sxs-lookup"><span data-stu-id="a79c7-106">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="a79c7-107">Pour plus d’informations, consultez [Réflexion (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="a79c7-107">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="a79c7-108">Les attributs ont les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a79c7-108">Attributes have the following properties:</span></span>

- <span data-ttu-id="a79c7-109">Les attributs ajoutent des métadonnées à un programme.</span><span class="sxs-lookup"><span data-stu-id="a79c7-109">Attributes add metadata to your program.</span></span> <span data-ttu-id="a79c7-110">Les *métadonnées* sont des informations sur les types définis dans un programme.</span><span class="sxs-lookup"><span data-stu-id="a79c7-110">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="a79c7-111">Tous les assemblys .NET contiennent un ensemble spécifié de métadonnées qui décrivent les types et membres de types définis dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a79c7-111">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="a79c7-112">Vous pouvez ajouter des attributs personnalisés pour spécifier des informations supplémentaires si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a79c7-112">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="a79c7-113">Pour plus d’informations, consultez [Création d’attributs personnalisés (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a79c7-113">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="a79c7-114">Vous pouvez appliquer un ou plusieurs attributs à des modules ou des assemblys entiers ou à de plus petits éléments de programmes, comme des classes et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="a79c7-114">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="a79c7-115">Les attributs peuvent accepter des arguments de la même façon que les méthodes et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="a79c7-115">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="a79c7-116">Votre programme peut examiner ses propres métadonnées ou celles d’autres programmes grâce à la réflexion.</span><span class="sxs-lookup"><span data-stu-id="a79c7-116">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="a79c7-117">Pour plus d’informations, consultez [Accès à des attributs à l’aide de la réflexion (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="a79c7-117">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="a79c7-118">Utilisation des attributs</span><span class="sxs-lookup"><span data-stu-id="a79c7-118">Using attributes</span></span>

<span data-ttu-id="a79c7-119">Les attributs peuvent être placés sur la quasi-totalité des déclarations, même si un attribut donné peut restreindre les types de déclarations sur lesquels il est valide.</span><span class="sxs-lookup"><span data-stu-id="a79c7-119">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="a79c7-120">En C#, vous spécifiez un attribut en plaçant son nom entre crochets ([]) au-dessus de la déclaration de l’entité à laquelle il s’applique.</span><span class="sxs-lookup"><span data-stu-id="a79c7-120">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="a79c7-121">Dans cet exemple, l’attribut <xref:System.SerializableAttribute> est utilisé pour appliquer une caractéristique spécifique à une classe :</span><span class="sxs-lookup"><span data-stu-id="a79c7-121">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="a79c7-122">Une méthode avec l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute> est déclarée comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a79c7-122">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="a79c7-123">Plusieurs attributs peuvent être placés dans une déclaration comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a79c7-123">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="a79c7-124">Certains attributs peuvent être spécifiés plusieurs fois pour une entité donnée.</span><span class="sxs-lookup"><span data-stu-id="a79c7-124">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="a79c7-125"><xref:System.Diagnostics.ConditionalAttribute> est un exemple d’attribut à utilisation multiple :</span><span class="sxs-lookup"><span data-stu-id="a79c7-125">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="a79c7-126">Par convention, tous les noms d’attributs se terminent par le mot « Attribute » pour les différencier d’autres éléments dans les bibliothèques .NET.</span><span class="sxs-lookup"><span data-stu-id="a79c7-126">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="a79c7-127">Toutefois, il est inutile de spécifier le suffixe d’attribut lorsque les attributs sont utilisés dans le code.</span><span class="sxs-lookup"><span data-stu-id="a79c7-127">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="a79c7-128">Par exemple, `[DllImport]` est équivalent à `[DllImportAttribute]` , mais `DllImportAttribute` est le nom réel de l’attribut dans la bibliothèque de classes .net.</span><span class="sxs-lookup"><span data-stu-id="a79c7-128">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="a79c7-129">Paramètres d’attributs</span><span class="sxs-lookup"><span data-stu-id="a79c7-129">Attribute parameters</span></span>

<span data-ttu-id="a79c7-130">Beaucoup d’attributs possèdent des paramètres. Ceux-ci peuvent être positionnels, sans nom ou nommés.</span><span class="sxs-lookup"><span data-stu-id="a79c7-130">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="a79c7-131">Les paramètres positionnels doivent être spécifiés dans un certain ordre et ne peut pas être omis.</span><span class="sxs-lookup"><span data-stu-id="a79c7-131">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="a79c7-132">Les paramètres nommés sont facultatifs et peuvent être spécifiés dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="a79c7-132">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="a79c7-133">Les paramètres positionnels sont spécifiés en premier.</span><span class="sxs-lookup"><span data-stu-id="a79c7-133">Positional parameters are specified first.</span></span> <span data-ttu-id="a79c7-134">Par exemple, ces trois attributs sont équivalents :</span><span class="sxs-lookup"><span data-stu-id="a79c7-134">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="a79c7-135">Le premier paramètre, le nom de la DLL, est positionnel et se place toujours en premier ; les autres sont nommés.</span><span class="sxs-lookup"><span data-stu-id="a79c7-135">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="a79c7-136">Dans ce cas, les deux paramètres nommés ont la valeur false par défaut ; ainsi, ils peuvent être omis.</span><span class="sxs-lookup"><span data-stu-id="a79c7-136">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="a79c7-137">Les paramètres positionnels correspondent aux paramètres du constructeur d’attribut.</span><span class="sxs-lookup"><span data-stu-id="a79c7-137">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="a79c7-138">Les paramètres nommés ou facultatifs correspondent aux propriétés ou champs de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="a79c7-138">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="a79c7-139">Reportez-vous à la documentation de chaque attribut pour plus d’informations sur les valeurs des paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="a79c7-139">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="a79c7-140">Cibles d’attribut</span><span class="sxs-lookup"><span data-stu-id="a79c7-140">Attribute targets</span></span>

<span data-ttu-id="a79c7-141">La *cible* d’un attribut est l’entité à laquelle s’applique l’attribut.</span><span class="sxs-lookup"><span data-stu-id="a79c7-141">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="a79c7-142">Par exemple, un attribut peut s’appliquer à une classe, à une méthode particulière ou à un assembly entier.</span><span class="sxs-lookup"><span data-stu-id="a79c7-142">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="a79c7-143">Par défaut, un attribut s’applique à l’élément qui le suit.</span><span class="sxs-lookup"><span data-stu-id="a79c7-143">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="a79c7-144">Mais vous pouvez également identifier de manière explicite, par exemple, si un attribut s’applique à une méthode, à son paramètre ou à sa valeur renvoyée.</span><span class="sxs-lookup"><span data-stu-id="a79c7-144">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="a79c7-145">Pour identifier de manière explicite une cible d’attribut, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="a79c7-145">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="a79c7-146">La liste des valeurs `target` possibles est présentée dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="a79c7-146">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="a79c7-147">Valeur cible</span><span class="sxs-lookup"><span data-stu-id="a79c7-147">Target value</span></span>|<span data-ttu-id="a79c7-148">S’applique à</span><span class="sxs-lookup"><span data-stu-id="a79c7-148">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="a79c7-149">Assembly entier</span><span class="sxs-lookup"><span data-stu-id="a79c7-149">Entire assembly</span></span>|
|`module`|<span data-ttu-id="a79c7-150">Module d’assembly actuel</span><span class="sxs-lookup"><span data-stu-id="a79c7-150">Current assembly module</span></span>|
|`field`|<span data-ttu-id="a79c7-151">Champ dans une classe ou un struct</span><span class="sxs-lookup"><span data-stu-id="a79c7-151">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="a79c7-152">Événement</span><span class="sxs-lookup"><span data-stu-id="a79c7-152">Event</span></span>|
|`method`|<span data-ttu-id="a79c7-153">Méthode ou accesseurs de propriété `get` et `set`</span><span class="sxs-lookup"><span data-stu-id="a79c7-153">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="a79c7-154">Paramètres de méthode ou paramètres d’accesseur de propriété `set`</span><span class="sxs-lookup"><span data-stu-id="a79c7-154">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="a79c7-155">Propriété</span><span class="sxs-lookup"><span data-stu-id="a79c7-155">Property</span></span>|
|`return`|<span data-ttu-id="a79c7-156">Valeur de retour d’une méthode, indexeur de propriété ou accesseur de propriété `get`</span><span class="sxs-lookup"><span data-stu-id="a79c7-156">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="a79c7-157">Struct, classe, interface, énumération ou délégué</span><span class="sxs-lookup"><span data-stu-id="a79c7-157">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="a79c7-158">Vous devez spécifier la valeur cible de `field` pour appliquer un attribut au champ de stockage créé pour une [propriété implémentée automatiquement](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="a79c7-158">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="a79c7-159">L’exemple suivant montre comment appliquer des attributs à des modules et assemblys.</span><span class="sxs-lookup"><span data-stu-id="a79c7-159">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="a79c7-160">Pour plus d’informations, consultez [Attributs courants (C#)](../../../language-reference/attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="a79c7-160">For more information, see [Common Attributes (C#)](../../../language-reference/attributes/global.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="a79c7-161">L’exemple suivant montre comment appliquer des attributs à des méthodes, des paramètres de méthode et des valeurs de retour de méthode en C#.</span><span class="sxs-lookup"><span data-stu-id="a79c7-161">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="a79c7-162">Quelle que soit la cible sur laquelle `ValidatedContract` est défini comme étant valide, la cible `return` doit être spécifiée, même si `ValidatedContract` a été défini pour s’appliquer seulement aux valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="a79c7-162">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="a79c7-163">En d’autres termes, le compilateur n’utilise pas les informations `AttributeUsage` pour résoudre les cibles d’attribut ambiguës.</span><span class="sxs-lookup"><span data-stu-id="a79c7-163">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="a79c7-164">Pour plus d’informations, consultez [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span><span class="sxs-lookup"><span data-stu-id="a79c7-164">For more information, see [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="a79c7-165">Utilisations courantes des attributs</span><span class="sxs-lookup"><span data-stu-id="a79c7-165">Common uses for attributes</span></span>

<span data-ttu-id="a79c7-166">La liste suivante comprend certaines des utilisations courantes des attributs dans le code :</span><span class="sxs-lookup"><span data-stu-id="a79c7-166">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="a79c7-167">Marquer des méthodes avec l’attribut `WebMethod` dans les services web pour indiquer que la méthode doit pouvoir être appelée via le protocole SOAP.</span><span class="sxs-lookup"><span data-stu-id="a79c7-167">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="a79c7-168">Pour plus d’informations, consultez <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a79c7-168">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="a79c7-169">Décrire comment marshaler les paramètres de méthode en cas d’interaction avec du code natif.</span><span class="sxs-lookup"><span data-stu-id="a79c7-169">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="a79c7-170">Pour plus d’informations, consultez <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a79c7-170">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="a79c7-171">Décrire les propriétés COM des classes, méthodes et interfaces.</span><span class="sxs-lookup"><span data-stu-id="a79c7-171">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="a79c7-172">Appeler du code non managé à l’aide de la classe <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a79c7-172">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="a79c7-173">Décrire un assembly : titre, version, description ou marque.</span><span class="sxs-lookup"><span data-stu-id="a79c7-173">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="a79c7-174">Décrire les membres d’une classe à sérialiser à des fins de persistance.</span><span class="sxs-lookup"><span data-stu-id="a79c7-174">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="a79c7-175">Décrire le mappage entre les membres de classe et des nœuds XML à des fins de sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="a79c7-175">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="a79c7-176">Décrire les exigences de sécurité des méthodes.</span><span class="sxs-lookup"><span data-stu-id="a79c7-176">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="a79c7-177">Spécifier les caractéristiques employées pour appliquer la sécurité.</span><span class="sxs-lookup"><span data-stu-id="a79c7-177">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="a79c7-178">Contrôler les optimisations par le compilateur juste-à-temps (JIT) pour que le code reste facile à déboguer.</span><span class="sxs-lookup"><span data-stu-id="a79c7-178">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="a79c7-179">Obtenir des informations sur l’appelant d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="a79c7-179">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a79c7-180">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="a79c7-180">Related sections</span></span>

<span data-ttu-id="a79c7-181">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="a79c7-181">For more information, see:</span></span>

- [<span data-ttu-id="a79c7-182">Création d’attributs personnalisés (C#)</span><span class="sxs-lookup"><span data-stu-id="a79c7-182">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="a79c7-183">Accès à des attributs à l’aide de la réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="a79c7-183">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="a79c7-184">Guide pratique pour créer une Union C/C++ à l’aide d’attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="a79c7-184">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="a79c7-185">Attributs courants (C#)</span><span class="sxs-lookup"><span data-stu-id="a79c7-185">Common Attributes (C#)</span></span>](../../../language-reference/attributes/global.md)  
- [<span data-ttu-id="a79c7-186">Informations relatives à l’appelant (C#)</span><span class="sxs-lookup"><span data-stu-id="a79c7-186">Caller Information (C#)</span></span>](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="a79c7-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a79c7-187">See also</span></span>

- [<span data-ttu-id="a79c7-188">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a79c7-188">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="a79c7-189">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="a79c7-189">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="a79c7-190">Attributs</span><span class="sxs-lookup"><span data-stu-id="a79c7-190">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="a79c7-191">Utilisation d’attributs en C #</span><span class="sxs-lookup"><span data-stu-id="a79c7-191">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
