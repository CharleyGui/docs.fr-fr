---
title: Attributs (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 7b78d5832c15d3d1142b80d2ccb96a72e4e20390
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374366"
---
# <a name="attributes-c"></a><span data-ttu-id="aacff-102">Attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="aacff-102">Attributes (C#)</span></span>

<span data-ttu-id="aacff-103">Les attributs fournissent une méthode puissante permettant d’associer des métadonnées ou des informations déclaratives avec du code (assemblys, types, méthodes, propriétés, etc.).</span><span class="sxs-lookup"><span data-stu-id="aacff-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="aacff-104">Une fois associé à une entité de programme, l’attribut peut être interrogé à l’exécution à l’aide d’une technique appelée *réflexion*.</span><span class="sxs-lookup"><span data-stu-id="aacff-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="aacff-105">Pour plus d’informations, consultez [Réflexion (C#)](../reflection.md).</span><span class="sxs-lookup"><span data-stu-id="aacff-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="aacff-106">Les attributs ont les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="aacff-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="aacff-107">Les attributs ajoutent des métadonnées à un programme.</span><span class="sxs-lookup"><span data-stu-id="aacff-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="aacff-108">Les *métadonnées* sont des informations sur les types définis dans un programme.</span><span class="sxs-lookup"><span data-stu-id="aacff-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="aacff-109">Tous les assemblys .NET contiennent un ensemble spécifié de métadonnées qui décrivent les types et membres de types définis dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="aacff-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="aacff-110">Vous pouvez ajouter des attributs personnalisés pour spécifier des informations supplémentaires si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="aacff-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="aacff-111">Pour plus d’informations, consultez [Création d’attributs personnalisés (C#)](creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="aacff-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="aacff-112">Vous pouvez appliquer un ou plusieurs attributs à des modules ou des assemblys entiers ou à de plus petits éléments de programmes, comme des classes et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="aacff-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="aacff-113">Les attributs peuvent accepter des arguments de la même façon que les méthodes et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="aacff-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="aacff-114">Votre programme peut examiner ses propres métadonnées ou celles d’autres programmes grâce à la réflexion.</span><span class="sxs-lookup"><span data-stu-id="aacff-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="aacff-115">Pour plus d’informations, consultez [Accès à des attributs à l’aide de la réflexion (C#)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="aacff-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="aacff-116">Utilisation d’attributs</span><span class="sxs-lookup"><span data-stu-id="aacff-116">Using attributes</span></span>

<span data-ttu-id="aacff-117">Les attributs peuvent être placés sur la quasi-totalité des déclarations, même si un attribut donné peut restreindre les types de déclarations sur lesquels il est valide.</span><span class="sxs-lookup"><span data-stu-id="aacff-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="aacff-118">En C#, vous spécifiez un attribut en plaçant son nom entre crochets ([]) au-dessus de la déclaration de l’entité à laquelle il s’applique.</span><span class="sxs-lookup"><span data-stu-id="aacff-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="aacff-119">Dans cet exemple, l’attribut <xref:System.SerializableAttribute> est utilisé pour appliquer une caractéristique spécifique à une classe :</span><span class="sxs-lookup"><span data-stu-id="aacff-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="aacff-120">Une méthode avec l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute> est déclarée comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="aacff-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="aacff-121">Plusieurs attributs peuvent être placés dans une déclaration comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="aacff-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="aacff-122">Certains attributs peuvent être spécifiés plusieurs fois pour une entité donnée.</span><span class="sxs-lookup"><span data-stu-id="aacff-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="aacff-123"><xref:System.Diagnostics.ConditionalAttribute> est un exemple d’attribut à utilisation multiple :</span><span class="sxs-lookup"><span data-stu-id="aacff-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="aacff-124">Par convention, tous les noms d’attributs se terminent par le mot « Attribute » pour les différencier d’autres éléments dans les bibliothèques .NET.</span><span class="sxs-lookup"><span data-stu-id="aacff-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="aacff-125">Toutefois, il est inutile de spécifier le suffixe d’attribut lorsque les attributs sont utilisés dans le code.</span><span class="sxs-lookup"><span data-stu-id="aacff-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="aacff-126">Par exemple, `[DllImport]` équivaut à `[DllImportAttribute]`, mais `DllImportAttribute` est le nom réel de l’attribut dans la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aacff-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="aacff-127">Paramètres d’attributs</span><span class="sxs-lookup"><span data-stu-id="aacff-127">Attribute parameters</span></span>

<span data-ttu-id="aacff-128">Beaucoup d’attributs possèdent des paramètres. Ceux-ci peuvent être positionnels, sans nom ou nommés.</span><span class="sxs-lookup"><span data-stu-id="aacff-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="aacff-129">Les paramètres positionnels doivent être spécifiés dans un certain ordre et ne peut pas être omis.</span><span class="sxs-lookup"><span data-stu-id="aacff-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="aacff-130">Les paramètres nommés sont facultatifs et peuvent être spécifiés dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="aacff-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="aacff-131">Les paramètres positionnels sont spécifiés en premier.</span><span class="sxs-lookup"><span data-stu-id="aacff-131">Positional parameters are specified first.</span></span> <span data-ttu-id="aacff-132">Par exemple, ces trois attributs sont équivalents :</span><span class="sxs-lookup"><span data-stu-id="aacff-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="aacff-133">Le premier paramètre, le nom de la DLL, est positionnel et se place toujours en premier ; les autres sont nommés.</span><span class="sxs-lookup"><span data-stu-id="aacff-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="aacff-134">Dans ce cas, les deux paramètres nommés ont la valeur false par défaut ; ainsi, ils peuvent être omis.</span><span class="sxs-lookup"><span data-stu-id="aacff-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="aacff-135">Les paramètres positionnels correspondent aux paramètres du constructeur d’attribut.</span><span class="sxs-lookup"><span data-stu-id="aacff-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="aacff-136">Les paramètres nommés ou facultatifs correspondent aux propriétés ou champs de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="aacff-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="aacff-137">Reportez-vous à la documentation de chaque attribut pour plus d’informations sur les valeurs des paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="aacff-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="aacff-138">Cibles d’attribut</span><span class="sxs-lookup"><span data-stu-id="aacff-138">Attribute targets</span></span>

<span data-ttu-id="aacff-139">La *cible* d’un attribut est l’entité à laquelle s’applique l’attribut.</span><span class="sxs-lookup"><span data-stu-id="aacff-139">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="aacff-140">Par exemple, un attribut peut s’appliquer à une classe, à une méthode particulière ou à un assembly entier.</span><span class="sxs-lookup"><span data-stu-id="aacff-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="aacff-141">Par défaut, un attribut s’applique à l’élément qui le suit.</span><span class="sxs-lookup"><span data-stu-id="aacff-141">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="aacff-142">Mais vous pouvez également identifier de manière explicite, par exemple, si un attribut s’applique à une méthode, à son paramètre ou à sa valeur renvoyée.</span><span class="sxs-lookup"><span data-stu-id="aacff-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="aacff-143">Pour identifier de manière explicite une cible d’attribut, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="aacff-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="aacff-144">La liste des valeurs `target` possibles est présentée dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="aacff-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="aacff-145">Valeur cible</span><span class="sxs-lookup"><span data-stu-id="aacff-145">Target value</span></span>|<span data-ttu-id="aacff-146">S'applique à</span><span class="sxs-lookup"><span data-stu-id="aacff-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="aacff-147">Assembly entier</span><span class="sxs-lookup"><span data-stu-id="aacff-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="aacff-148">Module d’assembly actuel</span><span class="sxs-lookup"><span data-stu-id="aacff-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="aacff-149">Champ dans une classe ou un struct</span><span class="sxs-lookup"><span data-stu-id="aacff-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="aacff-150">Événement</span><span class="sxs-lookup"><span data-stu-id="aacff-150">Event</span></span>|
|`method`|<span data-ttu-id="aacff-151">Méthode ou accesseurs de propriété `get` et `set`</span><span class="sxs-lookup"><span data-stu-id="aacff-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="aacff-152">Paramètres de méthode ou paramètres d’accesseur de propriété `set`</span><span class="sxs-lookup"><span data-stu-id="aacff-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="aacff-153">Propriété</span><span class="sxs-lookup"><span data-stu-id="aacff-153">Property</span></span>|
|`return`|<span data-ttu-id="aacff-154">Valeur de retour d’une méthode, indexeur de propriété ou accesseur de propriété `get`</span><span class="sxs-lookup"><span data-stu-id="aacff-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="aacff-155">Struct, classe, interface, énumération ou délégué</span><span class="sxs-lookup"><span data-stu-id="aacff-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="aacff-156">Vous devez spécifier la valeur cible de `field` pour appliquer un attribut au champ de stockage créé pour une [propriété implémentée automatiquement](../../../properties.md).</span><span class="sxs-lookup"><span data-stu-id="aacff-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="aacff-157">L’exemple suivant montre comment appliquer des attributs à des modules et assemblys.</span><span class="sxs-lookup"><span data-stu-id="aacff-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="aacff-158">Pour plus d’informations, consultez [Attributs courants (C#)](common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="aacff-158">For more information, see [Common Attributes (C#)](common-attributes.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="aacff-159">L’exemple suivant montre comment appliquer des attributs à des méthodes, des paramètres de méthode et des valeurs de retour de méthode en C#.</span><span class="sxs-lookup"><span data-stu-id="aacff-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="aacff-160">Quelle que soit la cible sur laquelle `ValidatedContract` est défini comme étant valide, la cible `return` doit être spécifiée, même si `ValidatedContract` a été défini pour s’appliquer seulement aux valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="aacff-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="aacff-161">En d’autres termes, le compilateur n’utilise pas les informations `AttributeUsage` pour résoudre les cibles d’attribut ambiguës.</span><span class="sxs-lookup"><span data-stu-id="aacff-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="aacff-162">Pour plus d’informations, consultez [AttributeUsage (C#)](attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="aacff-162">For more information, see [AttributeUsage (C#)](attributeusage.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="aacff-163">Utilisations courantes des attributs</span><span class="sxs-lookup"><span data-stu-id="aacff-163">Common uses for attributes</span></span>

<span data-ttu-id="aacff-164">La liste suivante comprend certaines des utilisations courantes des attributs dans le code :</span><span class="sxs-lookup"><span data-stu-id="aacff-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="aacff-165">Marquer des méthodes avec l’attribut `WebMethod` dans les services web pour indiquer que la méthode doit pouvoir être appelée via le protocole SOAP.</span><span class="sxs-lookup"><span data-stu-id="aacff-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="aacff-166">Pour plus d'informations, consultez <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="aacff-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="aacff-167">Décrire comment marshaler les paramètres de méthode en cas d’interaction avec du code natif.</span><span class="sxs-lookup"><span data-stu-id="aacff-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="aacff-168">Pour plus d'informations, consultez <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="aacff-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="aacff-169">Décrire les propriétés COM des classes, méthodes et interfaces.</span><span class="sxs-lookup"><span data-stu-id="aacff-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="aacff-170">Appeler du code non managé à l’aide de la classe <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="aacff-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="aacff-171">Décrire un assembly : titre, version, description ou marque.</span><span class="sxs-lookup"><span data-stu-id="aacff-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="aacff-172">Décrire les membres d’une classe à sérialiser à des fins de persistance.</span><span class="sxs-lookup"><span data-stu-id="aacff-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="aacff-173">Décrire le mappage entre les membres de classe et des nœuds XML à des fins de sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="aacff-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="aacff-174">Décrire les exigences de sécurité des méthodes.</span><span class="sxs-lookup"><span data-stu-id="aacff-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="aacff-175">Spécifier les caractéristiques employées pour appliquer la sécurité.</span><span class="sxs-lookup"><span data-stu-id="aacff-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="aacff-176">Contrôler les optimisations par le compilateur juste-à-temps (JIT) pour que le code reste facile à déboguer.</span><span class="sxs-lookup"><span data-stu-id="aacff-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="aacff-177">Obtenir des informations sur l’appelant d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="aacff-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="aacff-178">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="aacff-178">Related sections</span></span>

<span data-ttu-id="aacff-179">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="aacff-179">For more information, see:</span></span>

- [<span data-ttu-id="aacff-180">Création d’attributs personnalisés (C#)</span><span class="sxs-lookup"><span data-stu-id="aacff-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="aacff-181">Accès à des attributs à l’aide de la réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="aacff-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="aacff-182">Guide pratique : créer une union C/C++ à l’aide d’attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="aacff-182">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="aacff-183">Attributs courants (C#)</span><span class="sxs-lookup"><span data-stu-id="aacff-183">Common Attributes (C#)</span></span>](common-attributes.md)  
- [<span data-ttu-id="aacff-184">Informations relatives à l’appelant (C#)</span><span class="sxs-lookup"><span data-stu-id="aacff-184">Caller Information (C#)</span></span>](../caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="aacff-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aacff-185">See also</span></span>

- [<span data-ttu-id="aacff-186">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="aacff-186">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="aacff-187">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="aacff-187">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="aacff-188">Attributs</span><span class="sxs-lookup"><span data-stu-id="aacff-188">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="aacff-189">Utilisation d’attributs en C#</span><span class="sxs-lookup"><span data-stu-id="aacff-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
