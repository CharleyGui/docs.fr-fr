---
title: Vue d’ensemble des attributs
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: 97a2a13102718b6ee8829fca678b2b49df21e5d1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349481"
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="8c5fd-102">Vue d’ensemble des attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c5fd-102">Attributes overview (Visual Basic)</span></span>

<span data-ttu-id="8c5fd-103">Les attributs fournissent une méthode puissante permettant d’associer des métadonnées ou des informations déclaratives avec du code (assemblys, types, méthodes, propriétés, etc.).</span><span class="sxs-lookup"><span data-stu-id="8c5fd-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="8c5fd-104">Une fois associé à une entité de programme, l’attribut peut être interrogé à l’exécution à l’aide d’une technique appelée *réflexion*.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="8c5fd-105">Pour plus d’informations, consultez [Réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="8c5fd-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>

<span data-ttu-id="8c5fd-106">Les attributs ont les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="8c5fd-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="8c5fd-107">Les attributs ajoutent des métadonnées à un programme.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="8c5fd-108">Les *métadonnées* sont des informations sur les types définis dans un programme.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="8c5fd-109">Tous les assemblys .NET contiennent un ensemble spécifié de métadonnées qui décrivent les types et membres de types définis dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="8c5fd-110">Vous pouvez ajouter des attributs personnalisés pour spécifier des informations supplémentaires si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="8c5fd-111">Pour plus d’informations, consultez la page [Création d’attributs personnalisés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="8c5fd-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>

- <span data-ttu-id="8c5fd-112">Vous pouvez appliquer un ou plusieurs attributs à des modules ou des assemblys entiers ou à de plus petits éléments de programmes, comme des classes et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>

- <span data-ttu-id="8c5fd-113">Les attributs peuvent accepter des arguments de la même façon que les méthodes et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-113">Attributes can accept arguments in the same way as methods and properties.</span></span>

- <span data-ttu-id="8c5fd-114">Votre programme peut examiner ses propres métadonnées ou celles d’autres programmes grâce à la réflexion.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="8c5fd-115">Pour plus d’informations, consultez la page [Accéder à des attributs grâce à la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="8c5fd-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="8c5fd-116">Utilisation d'attributs</span><span class="sxs-lookup"><span data-stu-id="8c5fd-116">Using Attributes</span></span>

<span data-ttu-id="8c5fd-117">Les attributs peuvent être placés sur la quasi-totalité des déclarations, même si un attribut donné peut restreindre les types de déclarations sur lesquels il est valide.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="8c5fd-118">En Visual Basic, un attribut est placé entre chevrons (\< >).</span><span class="sxs-lookup"><span data-stu-id="8c5fd-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="8c5fd-119">Il doit apparaître immédiatement avant l’élément auquel il s’applique, sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>

<span data-ttu-id="8c5fd-120">Dans cet exemple, l’attribut <xref:System.SerializableAttribute> est utilisé pour appliquer une caractéristique spécifique à une classe :</span><span class="sxs-lookup"><span data-stu-id="8c5fd-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

```vb
<System.Serializable()> Public Class SampleClass
    ' Objects of this type can be serialized.
End Class
```

 <span data-ttu-id="8c5fd-121">Une méthode avec l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute> est déclarée comme suit :</span><span class="sxs-lookup"><span data-stu-id="8c5fd-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
<System.Runtime.InteropServices.DllImport("user32.dll")>
Sub SampleMethod()
End Sub
```

<span data-ttu-id="8c5fd-122">Plusieurs attributs peuvent être placés dans une déclaration :</span><span class="sxs-lookup"><span data-stu-id="8c5fd-122">More than one attribute can be placed on a declaration:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
Sub MethodA(<[In](), Out()> ByVal x As Double)
End Sub
Sub MethodB(<Out(), [In]()> ByVal x As Double)
End Sub
```

<span data-ttu-id="8c5fd-123">Certains attributs peuvent être spécifiés plusieurs fois pour une entité donnée.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="8c5fd-124"><xref:System.Diagnostics.ConditionalAttribute> est un exemple d’attribut à utilisation multiple :</span><span class="sxs-lookup"><span data-stu-id="8c5fd-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

```vb
<Conditional("DEBUG"), Conditional("TEST1")>
Sub TraceMethod()
End Sub
```

> [!NOTE]
> <span data-ttu-id="8c5fd-125">Par convention, tous les noms d’attributs se terminent par le mot « Attribute » pour les différencier d’autres éléments de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="8c5fd-126">Toutefois, il est inutile de spécifier le suffixe d’attribut lorsque les attributs sont utilisés dans le code.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="8c5fd-127">Par exemple, `[DllImport]` équivaut à `[DllImportAttribute]`, mais `DllImportAttribute` est le nom réel de l’attribut dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="8c5fd-128">Paramètres d’attributs</span><span class="sxs-lookup"><span data-stu-id="8c5fd-128">Attribute Parameters</span></span>

<span data-ttu-id="8c5fd-129">Beaucoup d’attributs possèdent des paramètres. Ceux-ci peuvent être positionnels, sans nom ou nommés.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="8c5fd-130">Les paramètres positionnels doivent être spécifiés dans un certain ordre et ne peuvent pas être omis ; les paramètres nommés sont facultatifs et peuvent être spécifiés dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="8c5fd-131">Les paramètres positionnels sont spécifiés en premier.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-131">Positional parameters are specified first.</span></span> <span data-ttu-id="8c5fd-132">Par exemple, ces trois attributs sont équivalents :</span><span class="sxs-lookup"><span data-stu-id="8c5fd-132">For example, these three attributes are equivalent:</span></span>

```vb
<DllImport("user32.dll")>
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>
```

<span data-ttu-id="8c5fd-133">Le premier paramètre, le nom de la DLL, est positionnel et se place toujours en premier ; les autres sont nommés.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="8c5fd-134">Dans ce cas, les deux paramètres nommés ont la valeur false par défaut ; ainsi, ils peuvent être omis.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="8c5fd-135">Reportez-vous à la documentation de chaque attribut pour plus d’informations sur les valeurs des paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="8c5fd-136">Cibles d'attribut</span><span class="sxs-lookup"><span data-stu-id="8c5fd-136">Attribute Targets</span></span>

<span data-ttu-id="8c5fd-137">La *cible* d’un attribut est l’entité à laquelle s’applique l’attribut.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="8c5fd-138">Par exemple, un attribut peut s’appliquer à une classe, à une méthode particulière ou à un assembly entier.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="8c5fd-139">Par défaut, un attribut s’applique à l’élément qu’il précède.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="8c5fd-140">Mais vous pouvez également identifier de manière explicite, par exemple, si un attribut s’applique à une méthode, à son paramètre ou à sa valeur renvoyée.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="8c5fd-141">Pour identifier de manière explicite une cible d’attribut, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="8c5fd-141">To explicitly identify an attribute target, use the following syntax:</span></span>

```vb
<target : attribute-list>
```

<span data-ttu-id="8c5fd-142">La liste des valeurs `target` possibles est présentée dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-142">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="8c5fd-143">Valeur cible</span><span class="sxs-lookup"><span data-stu-id="8c5fd-143">Target value</span></span>|<span data-ttu-id="8c5fd-144">Application</span><span class="sxs-lookup"><span data-stu-id="8c5fd-144">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="8c5fd-145">Assembly entier</span><span class="sxs-lookup"><span data-stu-id="8c5fd-145">Entire assembly</span></span>|
|`module`|<span data-ttu-id="8c5fd-146">Module d’assembly actif (différent d’un module Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c5fd-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|

 <span data-ttu-id="8c5fd-147">L’exemple suivant montre comment appliquer des attributs à des modules et assemblys.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="8c5fd-148">Pour plus d’informations, consultez la page [Attributs courants (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="8c5fd-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>

```vb
Imports System.Reflection
<Assembly: AssemblyTitleAttribute("Production assembly 4"),
Module: CLSCompliant(True)>
```

## <a name="common-uses-for-attributes"></a><span data-ttu-id="8c5fd-149">Utilisations courantes des attributs</span><span class="sxs-lookup"><span data-stu-id="8c5fd-149">Common Uses for Attributes</span></span>

<span data-ttu-id="8c5fd-150">La liste suivante comprend certaines des utilisations courantes des attributs dans le code :</span><span class="sxs-lookup"><span data-stu-id="8c5fd-150">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="8c5fd-151">Marquer des méthodes avec l’attribut `WebMethod` dans les services web pour indiquer que la méthode doit pouvoir être appelée via le protocole SOAP.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="8c5fd-152">Pour plus d'informations, consultez <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>

- <span data-ttu-id="8c5fd-153">Décrire comment marshaler les paramètres de méthode en cas d’interaction avec du code natif.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="8c5fd-154">Pour plus d'informations, consultez <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

- <span data-ttu-id="8c5fd-155">Décrire les propriétés COM des classes, méthodes et interfaces.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-155">Describing the COM properties for classes, methods, and interfaces.</span></span>

- <span data-ttu-id="8c5fd-156">Appeler du code non managé à l’aide de la classe <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>

- <span data-ttu-id="8c5fd-157">Décrire un assembly : titre, version, description ou marque.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>

- <span data-ttu-id="8c5fd-158">Décrire les membres d’une classe à sérialiser à des fins de persistance.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-158">Describing which members of a class to serialize for persistence.</span></span>

- <span data-ttu-id="8c5fd-159">Décrire le mappage entre les membres de classe et des nœuds XML à des fins de sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>

- <span data-ttu-id="8c5fd-160">Décrire les exigences de sécurité des méthodes.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-160">Describing the security requirements for methods.</span></span>

- <span data-ttu-id="8c5fd-161">Spécifier les caractéristiques employées pour appliquer la sécurité.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-161">Specifying characteristics used to enforce security.</span></span>

- <span data-ttu-id="8c5fd-162">Contrôler les optimisations par le compilateur juste-à-temps (JIT) pour que le code reste facile à déboguer.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>

- <span data-ttu-id="8c5fd-163">Obtenir des informations sur l’appelant d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="8c5fd-163">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="8c5fd-164">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="8c5fd-164">Related Sections</span></span>

<span data-ttu-id="8c5fd-165">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="8c5fd-165">For more information, see:</span></span>

- [<span data-ttu-id="8c5fd-166">Créer des attributs personnalisés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c5fd-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)

- [<span data-ttu-id="8c5fd-167">Accéder à des attributs à l’aide de la réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c5fd-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

- [<span data-ttu-id="8c5fd-168">Guide pratique : créer une union C/C++ à l’aide d’attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c5fd-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)

- [<span data-ttu-id="8c5fd-169">Attributs courants (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c5fd-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)

- [<span data-ttu-id="8c5fd-170">Informations relatives à l’appelant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c5fd-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)

## <a name="see-also"></a><span data-ttu-id="8c5fd-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c5fd-171">See also</span></span>

- [<span data-ttu-id="8c5fd-172">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c5fd-172">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="8c5fd-173">Réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c5fd-173">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="8c5fd-174">Attributs</span><span class="sxs-lookup"><span data-stu-id="8c5fd-174">Attributes</span></span>](../../../../standard/attributes/index.md)
