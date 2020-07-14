---
title: Vue d'ensemble du modèle de programmation par attributs (MEF)
description: Prise en main du modèle de programmation par attributs, qui est le modèle de programmation par défaut pour le Managed Extensibility Framework (MEF) dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
ms.openlocfilehash: aea3a19ffe6f177901e5c0839b618bb36f573beb
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281366"
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="69acf-103">Vue d'ensemble du modèle de programmation par attributs (MEF)</span><span class="sxs-lookup"><span data-stu-id="69acf-103">Attributed Programming Model Overview (MEF)</span></span>

<span data-ttu-id="69acf-104">Dans Managed Extensibility Framework (MEF), un *modèle de programmation* est une méthode particulière qui permet de définir l'ensemble d'objets conceptuels sur lequel MEF fonctionne.</span><span class="sxs-lookup"><span data-stu-id="69acf-104">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="69acf-105">Ces objets conceptuels incluent des composants, des importations et des exportations.</span><span class="sxs-lookup"><span data-stu-id="69acf-105">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="69acf-106">MEF utilise ces objets mais ne spécifie pas comment ils doivent être représentés.</span><span class="sxs-lookup"><span data-stu-id="69acf-106">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="69acf-107">Par conséquent, une grande variété de modèles de programmation sont possibles, y compris des modèles de programmation personnalisés.</span><span class="sxs-lookup"><span data-stu-id="69acf-107">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>

<span data-ttu-id="69acf-108">Le modèle de programmation par défaut utilisé dans MEF est le *modèle de programmation avec attributs*.</span><span class="sxs-lookup"><span data-stu-id="69acf-108">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="69acf-109">Dans le modèle de programmation avec attributs, les composants, les importations, les exportations et les autres objets sont définis avec des attributs qui décorent les classes .NET Framework ordinaires.</span><span class="sxs-lookup"><span data-stu-id="69acf-109">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="69acf-110">Cette rubrique explique comment utiliser les attributs fournis par le modèle de programmation avec attributs pour créer une application MEF.</span><span class="sxs-lookup"><span data-stu-id="69acf-110">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a><span data-ttu-id="69acf-111">Concepts de base liés aux importations et exportations</span><span class="sxs-lookup"><span data-stu-id="69acf-111">Import and Export Basics</span></span>

<span data-ttu-id="69acf-112">Une *exportation* est une valeur qu'un composant fournit à d'autres composants dans le conteneur, et une *importation* est une spécification exprimée par un composant au conteneur, qui doit être remplie à partir des exportations disponibles.</span><span class="sxs-lookup"><span data-stu-id="69acf-112">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="69acf-113">Dans le modèle de programmation avec attributs, les importations et les exportations sont déclarées en décorant des classes ou des membres avec les attributs `Import` et `Export` .</span><span class="sxs-lookup"><span data-stu-id="69acf-113">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="69acf-114">L'attribut `Export` peut décorer une classe, un champ, une propriété ou une méthode, tandis que l'attribut `Import` peut décorer un champ, une propriété ou un paramètre de constructeur.</span><span class="sxs-lookup"><span data-stu-id="69acf-114">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>

<span data-ttu-id="69acf-115">Pour qu'une importation soit mise en correspondance avec une exportation, l'importation et l'exportation doivent avoir le même *contrat*.</span><span class="sxs-lookup"><span data-stu-id="69acf-115">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="69acf-116">Le contrat se compose d'une chaîne, appelée *nom de contrat*, et du titre de l'objet exporté ou importé, appelé *type de contrat*.</span><span class="sxs-lookup"><span data-stu-id="69acf-116">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="69acf-117">Il faut que le nom de contrat et le type de contrat correspondent tous les deux pour qu'une exportation soit considérée comme satisfaisant une importation particulière.</span><span class="sxs-lookup"><span data-stu-id="69acf-117">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>

<span data-ttu-id="69acf-118">Un seul ou les deux paramètres de contrat peuvent être implicites ou explicites.</span><span class="sxs-lookup"><span data-stu-id="69acf-118">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="69acf-119">Le code suivant illustre une classe qui déclare une importation élémentaire.</span><span class="sxs-lookup"><span data-stu-id="69acf-119">The following code shows a class that declares a basic import.</span></span>

```vb
Public Class MyClass1
    <Import()>
    Public Property MyAddin As IMyAddin
End Class
```

```csharp
public class MyClass
{
    [Import]
    public IMyAddin MyAddin { get; set; }
}
```

<span data-ttu-id="69acf-120">Dans cette importation, l'attribut `Import` n'a pas de type de contrat ni de paramètre de nom de contrat joint.</span><span class="sxs-lookup"><span data-stu-id="69acf-120">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="69acf-121">Par conséquent, ces deux paramètres sont déduits de la propriété décorée.</span><span class="sxs-lookup"><span data-stu-id="69acf-121">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="69acf-122">Dans ce cas, le type de contrat est `IMyAddin`et le nom de contrat est une chaîne unique créée à partir du type de contrat.</span><span class="sxs-lookup"><span data-stu-id="69acf-122">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="69acf-123">(En d'autres termes, le nom de contrat correspond uniquement aux exportations dont les noms sont également déduits du type `IMyAddin`.)</span><span class="sxs-lookup"><span data-stu-id="69acf-123">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>

<span data-ttu-id="69acf-124">Le code ci-dessous illustre une exportation qui correspond à l'importation précédente.</span><span class="sxs-lookup"><span data-stu-id="69acf-124">The following shows an export that matches the previous import.</span></span>

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="69acf-125">Dans cette exportation, le type de contrat est `IMyAddin` car il est spécifié en tant que paramètre de l'attribut `Export` .</span><span class="sxs-lookup"><span data-stu-id="69acf-125">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="69acf-126">Le type exporté doit être identique au type de contrat, dériver du type de contrat ou implémenter le type de contrat s'il s'agit d'une interface.</span><span class="sxs-lookup"><span data-stu-id="69acf-126">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="69acf-127">Dans cette exportation, le type `MyLogger` réel implémente l'interface `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="69acf-127">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="69acf-128">Le nom de contrat est déduit du type de contrat, ce qui signifie que cette exportation correspondra à l'importation précédente.</span><span class="sxs-lookup"><span data-stu-id="69acf-128">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>

> [!NOTE]
> <span data-ttu-id="69acf-129">Les exportations et importations doivent habituellement être déclarées sur des classes publiques ou des membres publics.</span><span class="sxs-lookup"><span data-stu-id="69acf-129">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="69acf-130">D'autres déclarations sont prises en charge, mais l'exportation ou l'importation d'un membre privé, protégé ou interne interrompt le modèle d'isolation pour le composant et n'est donc pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="69acf-130">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>

<span data-ttu-id="69acf-131">Le type de contrat doit correspondre exactement pour que l'exportation et l'importation soient considérées concordantes.</span><span class="sxs-lookup"><span data-stu-id="69acf-131">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="69acf-132">Considérons l'exportation suivante.</span><span class="sxs-lookup"><span data-stu-id="69acf-132">Consider the following export.</span></span>

```vb
<Export()> 'WILL NOT match the previous import!
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export] //WILL NOT match the previous import!
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="69acf-133">Dans cette exportation, le type de contrat est `MyLogger` et non pas `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="69acf-133">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="69acf-134">Bien que `MyLogger` implémente `IMyAddin`, et pourrait donc être casté en un objet `IMyAddin` , cette exportation ne correspond pas à l'importation précédente, car les types de contrat ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="69acf-134">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>

<span data-ttu-id="69acf-135">En règle générale, il n'est pas nécessaire de spécifier le nom de contrat et la plupart des contrats doivent être définis en termes de type de contrat et de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="69acf-135">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="69acf-136">Toutefois, dans certaines circonstances, il est important de spécifier directement le nom de contrat.</span><span class="sxs-lookup"><span data-stu-id="69acf-136">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="69acf-137">Le cas le plus courant est quand une classe exporte plusieurs valeurs qui partagent un type commun, telles que des primitives.</span><span class="sxs-lookup"><span data-stu-id="69acf-137">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="69acf-138">Le nom de contrat peut être spécifié comme premier paramètre de l'attribut `Import` ou `Export` .</span><span class="sxs-lookup"><span data-stu-id="69acf-138">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="69acf-139">Le code suivant illustre une importation et une exportation avec `MajorRevision`comme nom de contrat spécifié.</span><span class="sxs-lookup"><span data-stu-id="69acf-139">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>

```vb
Public Class MyExportClass

    'This one will match
    <Export("MajorRevision")>
    Public ReadOnly Property MajorRevision As Integer
        Get
            Return 4
        End Get
    End Property

    <Export("MinorRevision")>
    Public ReadOnly Property MinorRevision As Integer
        Get
            Return 16
        End Get
    End Property
End Class
```

```csharp
public class MyClass
{
    [Import("MajorRevision")]
    public int MajorRevision { get; set; }
}

public class MyExportClass
{
    [Export("MajorRevision")] //This one will match.
    public int MajorRevision = 4;

    [Export("MinorRevision")]
    public int MinorRevision = 16;
}
```

<span data-ttu-id="69acf-140">Si le type de contrat n'est pas spécifié, il est encore déduit du type de l'importation ou de l'exportation.</span><span class="sxs-lookup"><span data-stu-id="69acf-140">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="69acf-141">Toutefois, même si le nom de contrat est spécifié explicitement, le type de contrat doit également correspondre exactement pour que l'importation et l'exportation soit considérées concordantes.</span><span class="sxs-lookup"><span data-stu-id="69acf-141">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="69acf-142">Par exemple, si le champ `MajorRevision` était une chaîne, les types de contrat déduits ne correspondraient pas et l'exportation ne correspondrait pas à l'importation, bien qu'ils aient le même nom de contrat.</span><span class="sxs-lookup"><span data-stu-id="69acf-142">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>

### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="69acf-143">Importation et exportation d'une méthode</span><span class="sxs-lookup"><span data-stu-id="69acf-143">Importing and Exporting a Method</span></span>

<span data-ttu-id="69acf-144">L'attribut `Export` peut également décorer une méthode, de la même façon qu'une classe, une propriété ou une fonction.</span><span class="sxs-lookup"><span data-stu-id="69acf-144">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="69acf-145">Les exportations de méthode doivent spécifier un type de contrat ou un nom de contrat, car le type ne peut pas être déduit.</span><span class="sxs-lookup"><span data-stu-id="69acf-145">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="69acf-146">Le type spécifié peut être un délégué personnalisé ou un type générique, tel que `Func`.</span><span class="sxs-lookup"><span data-stu-id="69acf-146">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="69acf-147">La classe suivante exporte une méthode nommée `DoSomething`.</span><span class="sxs-lookup"><span data-stu-id="69acf-147">The following class exports a method named `DoSomething`.</span></span>

```vb
Public Class MyAddin

    'Explicitly specifying a generic type
    <Export(GetType(Func(Of Integer, String)))>
    Public Function DoSomething(ByVal TheParam As Integer) As String
        Return Nothing 'Function body goes here
    End Function

End Class
```

```csharp
public class MyAddin
{
    //Explicitly specifying a generic type.
    [Export(typeof(Func<int, string>))]
    public string DoSomething(int TheParam);
}
```

<span data-ttu-id="69acf-148">Dans cette classe, la méthode `DoSomething` accepte un paramètre unique `int` et retourne une `string`.</span><span class="sxs-lookup"><span data-stu-id="69acf-148">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="69acf-149">Pour correspondre à cette exportation, le composant d'importation doit déclarer un membre approprié.</span><span class="sxs-lookup"><span data-stu-id="69acf-149">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="69acf-150">La classe suivante importe la méthode `DoSomething` .</span><span class="sxs-lookup"><span data-stu-id="69acf-150">The following class imports the `DoSomething` method.</span></span>

```vb
Public Class MyClass1

    'Contract name must match!
    <Import()>
    Public Property MajorRevision As Func(Of Integer, String)
End Class
```

```csharp
public class MyClass
{
    [Import] //Contract name must match!
    public Func<int, string> DoSomething { get; set; }
}
```

<span data-ttu-id="69acf-151">Pour plus d'informations sur l'utilisation de l'objet `Func<T, T>` , consultez <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="69acf-151">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a><span data-ttu-id="69acf-152">Types d'importations</span><span class="sxs-lookup"><span data-stu-id="69acf-152">Types of Imports</span></span>

<span data-ttu-id="69acf-153">MEF prend en charge plusieurs types d'importations, y compris des importations dynamiques, différées, requises et facultatives.</span><span class="sxs-lookup"><span data-stu-id="69acf-153">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>

### <a name="dynamic-imports"></a><span data-ttu-id="69acf-154">Importations dynamiques</span><span class="sxs-lookup"><span data-stu-id="69acf-154">Dynamic Imports</span></span>

<span data-ttu-id="69acf-155">Dans certains cas, la classe d'importation peut correspondre à des exportations d'un type quelconque, dotées d'un nom de contrat particulier.</span><span class="sxs-lookup"><span data-stu-id="69acf-155">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="69acf-156">Dans ce scénario, la classe peut déclarer une *importation dynamique*.</span><span class="sxs-lookup"><span data-stu-id="69acf-156">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="69acf-157">L'importation suivante correspond à toute exportation dont le nom de contrat est « TheString ».</span><span class="sxs-lookup"><span data-stu-id="69acf-157">The following import matches any export with contract name "TheString".</span></span>

```vb
Public Class MyClass1

    <Import("TheString")>
    Public Property MyAddin

End Class
```

```csharp
public class MyClass
{
    [Import("TheString")]
    public dynamic MyAddin { get; set; }
}
```

<span data-ttu-id="69acf-158">Quand le type de contrat est déduit du mot clé `dynamic` , il correspond à tout type de contrat.</span><span class="sxs-lookup"><span data-stu-id="69acf-158">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="69acf-159">Dans ce cas, une importation doit **toujours** spécifier un nom de contrat à respecter.</span><span class="sxs-lookup"><span data-stu-id="69acf-159">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="69acf-160">(Si aucun nom de contrat n’est spécifié, l’importation sera considérée comme ne correspondant à aucune exportation.) Les deux exportations suivantes correspondent à l’importation précédente.</span><span class="sxs-lookup"><span data-stu-id="69acf-160">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>

```vb
<Export("TheString", GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class

<Export("TheString")>
Public Class MyToolbar

End Class
```

```csharp
[Export("TheString", typeof(IMyAddin))]
public class MyLogger : IMyAddin { }

[Export("TheString")]
public class MyToolbar { }
```

<span data-ttu-id="69acf-161">De toute évidence, la classe d'importation doit être préparée pour traiter un objet de type arbitraire.</span><span class="sxs-lookup"><span data-stu-id="69acf-161">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>

### <a name="lazy-imports"></a><span data-ttu-id="69acf-162">Importations différées</span><span class="sxs-lookup"><span data-stu-id="69acf-162">Lazy Imports</span></span>

<span data-ttu-id="69acf-163">Dans certains cas, la classe d'importation peut exiger une référence indirecte à l'objet importé, afin que l'objet ne soit pas instancié immédiatement.</span><span class="sxs-lookup"><span data-stu-id="69acf-163">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="69acf-164">Dans ce scénario, la classe peut déclarer une *importation différée* en utilisant un type de contrat `Lazy<T>`.</span><span class="sxs-lookup"><span data-stu-id="69acf-164">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="69acf-165">La propriété d'importation suivante déclare une importation différée.</span><span class="sxs-lookup"><span data-stu-id="69acf-165">The following importing property declares a lazy import.</span></span>

```vb
Public Class MyClass1

    <Import()>
    Public Property MyAddin As Lazy(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [Import]
    public Lazy<IMyAddin> MyAddin { get; set; }
}
```

<span data-ttu-id="69acf-166">Du point de vue du moteur de composition, le type de contrat `Lazy<T>` est considéré comme identique au type de contrat `T`.</span><span class="sxs-lookup"><span data-stu-id="69acf-166">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="69acf-167">Par conséquent, l'importation précédente correspond à l'exportation suivante.</span><span class="sxs-lookup"><span data-stu-id="69acf-167">Therefore, the previous import would match the following export.</span></span>

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="69acf-168">Le nom de contrat et le type de contrat peuvent être spécifiés dans l'attribut `Import` pour une importation différée, comme cela a été décrit plus tôt dans la section « Concepts de base liés aux importations et exportations ».</span><span class="sxs-lookup"><span data-stu-id="69acf-168">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>

### <a name="prerequisite-imports"></a><span data-ttu-id="69acf-169">Importations requises</span><span class="sxs-lookup"><span data-stu-id="69acf-169">Prerequisite Imports</span></span>

<span data-ttu-id="69acf-170">Les composants MEF exportés sont généralement créés par le moteur de composition, en réponse à une demande directe ou au besoin de remplir une importation dotée d'une correspondance.</span><span class="sxs-lookup"><span data-stu-id="69acf-170">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="69acf-171">Par défaut, lors de la création d'un composant, le moteur de composition utilise le constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="69acf-171">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="69acf-172">Pour que le moteur utilise un autre constructeur, vous pouvez le marquer avec l'attribut `ImportingConstructor` .</span><span class="sxs-lookup"><span data-stu-id="69acf-172">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>

<span data-ttu-id="69acf-173">Chaque composant peut faire utiliser un seul constructeur au moteur de composition.</span><span class="sxs-lookup"><span data-stu-id="69acf-173">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="69acf-174">Ne fournir aucun constructeur sans paramètre ni aucun attribut `ImportingConstructor`, ou fournir plusieurs attributs `ImportingConstructor`, génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="69acf-174">Providing no parameterless constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>

<span data-ttu-id="69acf-175">Pour remplir les paramètres d'un constructeur marqué avec l'attribut `ImportingConstructor` , tous ces paramètres sont automatiquement déclarés en tant qu'importations.</span><span class="sxs-lookup"><span data-stu-id="69acf-175">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="69acf-176">Il s'agit d'une méthode pratique pour déclarer des importations utilisées pendant l'initialisation des composants.</span><span class="sxs-lookup"><span data-stu-id="69acf-176">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="69acf-177">La classe suivante utilise `ImportingConstructor` pour déclarer une importation.</span><span class="sxs-lookup"><span data-stu-id="69acf-177">The following class uses `ImportingConstructor` to declare an import.</span></span>

```vb
Public Class MyClass1

    Private _theAddin As IMyAddin

    'Parameterless constructor will NOT be used
    'because the ImportingConstructor
    'attribute is present.
    Public Sub New()

    End Sub

    'This constructor will be used.
    'An import with contract type IMyAddin
    'is declared automatically.
    <ImportingConstructor()>
    Public Sub New(ByVal MyAddin As IMyAddin)
        _theAddin = MyAddin
    End Sub

End Class
```

```csharp
public class MyClass
{
    private IMyAddin _theAddin;

    //Parameterless constructor will NOT be
    //used because the ImportingConstructor
    //attribute is present.
    public MyClass() { }

    //This constructor will be used.
    //An import with contract type IMyAddin is
    //declared automatically.
    [ImportingConstructor]
    public MyClass(IMyAddin MyAddin)
    {
        _theAddin = MyAddin;
    }
}
```

<span data-ttu-id="69acf-178">Par défaut, l'attribut `ImportingConstructor` utilise des types de contrat et des noms de contrat déduits pour toutes les importations de paramètres.</span><span class="sxs-lookup"><span data-stu-id="69acf-178">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="69acf-179">Il est possible de remplacer cela en décorant les paramètres avec des attributs `Import` , qui peuvent alors définir explicitement le type de contrat et le nom de contrat.</span><span class="sxs-lookup"><span data-stu-id="69acf-179">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="69acf-180">Le code ci-dessous illustre un constructeur qui utilise cette syntaxe pour importer une classe dérivée à la place d'une classe parente.</span><span class="sxs-lookup"><span data-stu-id="69acf-180">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>

```vb
<ImportingConstructor()>
Public Sub New(<Import(GetType(IMySubAddin))> ByVal MyAddin As IMyAddin)

End Sub
```

```csharp
[ImportingConstructor]
public MyClass([Import(typeof(IMySubAddin))]IMyAddin MyAddin)
{
    _theAddin = MyAddin;
}
```

<span data-ttu-id="69acf-181">En particulier, vous devez être prudent avec les paramètres de collection.</span><span class="sxs-lookup"><span data-stu-id="69acf-181">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="69acf-182">Par exemple, si vous spécifiez `ImportingConstructor` sur un constructeur avec un paramètre de type `IEnumerable<int>`, l'importation correspond à une exportation unique de type `IEnumerable<int>`, à la place d'un ensemble d'exportations de type `int`.</span><span class="sxs-lookup"><span data-stu-id="69acf-182">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="69acf-183">Pour établir une correspondance avec un ensemble d'exportations de type `int`, vous devez décorer le paramètre avec l'attribut `ImportMany` .</span><span class="sxs-lookup"><span data-stu-id="69acf-183">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>

<span data-ttu-id="69acf-184">Les paramètres déclarés en tant qu'importations par l'attribut `ImportingConstructor` sont également marqués en tant qu' *importations requises*.</span><span class="sxs-lookup"><span data-stu-id="69acf-184">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="69acf-185">MEF permet normalement aux exportations et importations de former un *cycle*.</span><span class="sxs-lookup"><span data-stu-id="69acf-185">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="69acf-186">Par exemple, dans un cycle, l’objet A importe l’objet B, qui importe à son tour l’objet A. Dans des circonstances ordinaires, un cycle n’est pas un problème et le conteneur de composition construit les deux objets normalement.</span><span class="sxs-lookup"><span data-stu-id="69acf-186">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>

<span data-ttu-id="69acf-187">Quand une valeur importée est requise par le constructeur d'un composant, cet objet ne peut pas participer à un cycle.</span><span class="sxs-lookup"><span data-stu-id="69acf-187">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="69acf-188">Si l'objet A exige que l'objet B soit construit avant de pouvoir être construit lui-même, et que l'objet B importe l'objet A, il est impossible de résoudre le cycle et une erreur de composition survient.</span><span class="sxs-lookup"><span data-stu-id="69acf-188">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="69acf-189">Les importations déclarées sur des paramètres de constructeur sont, par conséquent, des importations prérequises, qui doivent toutes être remplies avant qu'aucune des exportations issues de l'objet qui les requiert puisse être utilisée.</span><span class="sxs-lookup"><span data-stu-id="69acf-189">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>

### <a name="optional-imports"></a><span data-ttu-id="69acf-190">Importations facultatives</span><span class="sxs-lookup"><span data-stu-id="69acf-190">Optional Imports</span></span>

<span data-ttu-id="69acf-191">L'attribut `Import` spécifie une exigence pour que le composant fonctionne.</span><span class="sxs-lookup"><span data-stu-id="69acf-191">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="69acf-192">Si une importation ne peut pas être satisfaite, la composition de ce composant échouera et le composant ne sera pas disponible.</span><span class="sxs-lookup"><span data-stu-id="69acf-192">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>

<span data-ttu-id="69acf-193">Vous pouvez définir une importation comme *facultative* en utilisant la propriété `AllowDefault` .</span><span class="sxs-lookup"><span data-stu-id="69acf-193">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="69acf-194">Dans ce cas, la composition fonctionnera même si l’importation ne correspond à aucune exportation disponible, et la propriété d’importation sera définie sur la valeur par défaut pour son type de propriété ( `null` pour les propriétés d’objet, `false` pour les valeurs booléennes ou zéro pour les propriétés numériques.) La classe suivante utilise une importation facultative.</span><span class="sxs-lookup"><span data-stu-id="69acf-194">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>

```vb
Public Class MyClass1

    <Import(AllowDefault:=True)>
    Public Property thePlugin As Plugin

    'If no matching export is available,
    'thePlugin will be set to null.
End Class
```

```csharp
public class MyClass
{
    [Import(AllowDefault = true)]
    public Plugin thePlugin { get; set; }

    //If no matching export is available,
    //thePlugin will be set to null.
}
```

### <a name="importing-multiple-objects"></a><span data-ttu-id="69acf-195">Importation de plusieurs objets</span><span class="sxs-lookup"><span data-stu-id="69acf-195">Importing Multiple Objects</span></span>

<span data-ttu-id="69acf-196">L'attribut `Import` sera composé avec succès uniquement lorsqu'il correspondra à une seule exportation.</span><span class="sxs-lookup"><span data-stu-id="69acf-196">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="69acf-197">Les autres cas génèrent une erreur de composition.</span><span class="sxs-lookup"><span data-stu-id="69acf-197">Other cases will produce a composition error.</span></span> <span data-ttu-id="69acf-198">Pour importer plusieurs exportations correspondant au même contrat, utilisez l'attribut `ImportMany` .</span><span class="sxs-lookup"><span data-stu-id="69acf-198">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="69acf-199">Les importations marquées de cet attribut sont toujours facultatives.</span><span class="sxs-lookup"><span data-stu-id="69acf-199">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="69acf-200">Par exemple, la composition n'échouera pas si aucune exportation correspondante n'est présente.</span><span class="sxs-lookup"><span data-stu-id="69acf-200">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="69acf-201">La classe suivante importe un nombre quelconque d'exportations de type `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="69acf-201">The following class imports any number of exports of type `IMyAddin`.</span></span>

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<IMyAddin> MyAddin { get; set; }
}
```

<span data-ttu-id="69acf-202">Il est possible d'accéder au tableau importé en utilisant les méthodes et la syntaxe `IEnumerable<T>` ordinaires.</span><span class="sxs-lookup"><span data-stu-id="69acf-202">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="69acf-203">Il est également possible d'utiliser un tableau ordinaire (`IMyAddin[]`) à la place.</span><span class="sxs-lookup"><span data-stu-id="69acf-203">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>

<span data-ttu-id="69acf-204">Ce modèle peut être très important quand vous l'utilisez en association avec la syntaxe `Lazy<T>` .</span><span class="sxs-lookup"><span data-stu-id="69acf-204">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="69acf-205">Par exemple, en utilisant `ImportMany`, `IEnumerable<T>`et `Lazy<T>`, vous pouvez importer des références indirectes à un nombre quelconque d'objets et instancier uniquement ceux qui deviennent nécessaires.</span><span class="sxs-lookup"><span data-stu-id="69acf-205">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="69acf-206">La classe suivante illustre ce modèle.</span><span class="sxs-lookup"><span data-stu-id="69acf-206">The following class shows this pattern.</span></span>

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of Lazy(Of IMyAddin))

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<Lazy<IMyAddin>> MyAddin { get; set; }
}
```

<a name="avoiding_discovery"></a>

## <a name="avoiding-discovery"></a><span data-ttu-id="69acf-207">Éviter la découverte</span><span class="sxs-lookup"><span data-stu-id="69acf-207">Avoiding Discovery</span></span>

<span data-ttu-id="69acf-208">Dans certains cas, vous pouvez souhaiter empêcher la découverte d'un composant dans le cadre d'un catalogue.</span><span class="sxs-lookup"><span data-stu-id="69acf-208">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="69acf-209">Par exemple, ce composant peut être une classe de base qui ne sera pas utilisée, mais dont les enfants hériteront.</span><span class="sxs-lookup"><span data-stu-id="69acf-209">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="69acf-210">Il existe deux façons d'accomplir cela.</span><span class="sxs-lookup"><span data-stu-id="69acf-210">There are two ways to accomplish this.</span></span> <span data-ttu-id="69acf-211">Vous pouvez utiliser le mot clé `abstract` sur la classe du composant.</span><span class="sxs-lookup"><span data-stu-id="69acf-211">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="69acf-212">Les classes abstraites ne fournissent jamais d'exportations, bien qu'elles puissent fournir des exportations héritées aux classes qui dérivent d'elles.</span><span class="sxs-lookup"><span data-stu-id="69acf-212">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>

<span data-ttu-id="69acf-213">Si la classe ne peut pas être rendue abstraite, vous pouvez la décorer avec l'attribut `PartNotDiscoverable` .</span><span class="sxs-lookup"><span data-stu-id="69acf-213">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="69acf-214">Un composant décoré avec cet attribut ne sera inclus dans aucun catalogue.</span><span class="sxs-lookup"><span data-stu-id="69acf-214">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="69acf-215">L'exemple suivant illustre ces modèles :</span><span class="sxs-lookup"><span data-stu-id="69acf-215">The following example demonstrates these patterns.</span></span> <span data-ttu-id="69acf-216">`DataOne` sera découvert par le catalogue.</span><span class="sxs-lookup"><span data-stu-id="69acf-216">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="69acf-217">Comme `DataTwo` est abstrait, il ne sera pas découvert.</span><span class="sxs-lookup"><span data-stu-id="69acf-217">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="69acf-218">Comme `DataThree` utilisait l'attribut `PartNotDiscoverable` , il ne sera pas découvert.</span><span class="sxs-lookup"><span data-stu-id="69acf-218">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>

```vb
<Export()>
Public Class DataOne
    'This part will be discovered
    'as normal by the catalog.
End Class

<Export()>
Public MustInherit Class DataTwo
    'This part will not be discovered
    'by the catalog.
End Class

<PartNotDiscoverable()>
<Export()>
Public Class DataThree
    'This part will also not be discovered
    'by the catalog.
End Class
```

```csharp
[Export]
public class DataOne
{
    //This part will be discovered
    //as normal by the catalog.
}

[Export]
public abstract class DataTwo
{
    //This part will not be discovered
    //by the catalog.
}

[PartNotDiscoverable]
[Export]
public class DataThree
{
    //This part will also not be discovered
    //by the catalog.
}
```

<a name="metadata_and_metadata_views"></a>

## <a name="metadata-and-metadata-views"></a><span data-ttu-id="69acf-219">Métadonnées et vues des métadonnées</span><span class="sxs-lookup"><span data-stu-id="69acf-219">Metadata and Metadata Views</span></span>

<span data-ttu-id="69acf-220">Les exportations peuvent fournir des informations supplémentaires sur elles-mêmes, appelées *métadonnées*.</span><span class="sxs-lookup"><span data-stu-id="69acf-220">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="69acf-221">Les métadonnées peuvent être utilisées pour acheminer des propriétés de l'objet exporté jusqu'au composant d'importation.</span><span class="sxs-lookup"><span data-stu-id="69acf-221">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="69acf-222">Le composant d'importation peut utiliser ces données pour décider quelles exportations utiliser ou pour rassembler des informations sur une exportation sans avoir à la construire.</span><span class="sxs-lookup"><span data-stu-id="69acf-222">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="69acf-223">Pour cette raison, une importation doit être différée pour utiliser des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="69acf-223">For this reason, an import must be lazy to use metadata.</span></span>

<span data-ttu-id="69acf-224">Pour utiliser des métadonnées, vous déclarez en général une interface connue en tant que *vue de métadonnées*, qui déclare les métadonnées qui seront disponibles.</span><span class="sxs-lookup"><span data-stu-id="69acf-224">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="69acf-225">L'interface de la vue de métadonnées doit posséder seulement des propriétés et ces dernières doivent posséder des accesseurs `get` .</span><span class="sxs-lookup"><span data-stu-id="69acf-225">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="69acf-226">L'interface suivante est un exemple de vue de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="69acf-226">The following interface is an example metadata view.</span></span>

```vb
Public Interface IPluginMetadata

    ReadOnly Property Name As String

    <DefaultValue(1)>
    ReadOnly Property Version As Integer

End Interface
```

```csharp
public interface IPluginMetadata
{
    string Name { get; }

    [DefaultValue(1)]
    int Version { get; }
}
```

<span data-ttu-id="69acf-227">Il est également possible d'utiliser une collection générique, `IDictionary<string, object>`, comme vue de métadonnées, mais cela annule les avantages de la vérification de type et devrait être évité.</span><span class="sxs-lookup"><span data-stu-id="69acf-227">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>

<span data-ttu-id="69acf-228">En règle générale, toutes les propriétés nommées dans la vue de métadonnées sont requises et toute exportation qui ne les fournit pas sera considérée comme non concordante.</span><span class="sxs-lookup"><span data-stu-id="69acf-228">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="69acf-229">L'attribut `DefaultValue` spécifie qu'une propriété est facultative.</span><span class="sxs-lookup"><span data-stu-id="69acf-229">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="69acf-230">Si la propriété n'est pas incluse, il lui sera attribué la valeur par défaut spécifiée comme paramètre de `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="69acf-230">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="69acf-231">Voici deux classes différentes, décorées avec des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="69acf-231">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="69acf-232">Ces deux classes correspondent à la vue de métadonnées précédente.</span><span class="sxs-lookup"><span data-stu-id="69acf-232">Both of these classes would match the previous metadata view.</span></span>

```vb
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class MyLogger
    Implements IPlugin

End Class

'Version is not required because of the DefaultValue
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Disk Writer")>
Public Class DWriter
    Implements IPlugin

End Class
```

```csharp
[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
}

[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Disk Writer")]
    //Version is not required because of the DefaultValue
public class DWriter : IPlugin
{
}
```

<span data-ttu-id="69acf-233">Les métadonnées sont exprimées après l'attribut `Export` au moyen de l'attribut `ExportMetadata` .</span><span class="sxs-lookup"><span data-stu-id="69acf-233">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="69acf-234">Chaque unité de métadonnées est composée d'une paire nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="69acf-234">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="69acf-235">La partie du nom des métadonnées doit correspondre au nom de la propriété appropriée dans la vue de métadonnées, et la valeur sera attribuée à cette propriété.</span><span class="sxs-lookup"><span data-stu-id="69acf-235">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>

<span data-ttu-id="69acf-236">C'est l'importateur qui spécifie la vue de métadonnées, le cas échéant, qui sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="69acf-236">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="69acf-237">Une importation avec des métadonnées est déclarée en tant qu'importation différée, avec l'interface des métadonnées comme second paramètre de type de `Lazy<T,T>`.</span><span class="sxs-lookup"><span data-stu-id="69acf-237">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="69acf-238">La classe suivante importe le composant précédent avec les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="69acf-238">The following class imports the previous part with metadata.</span></span>

```vb
Public Class Addin

    <Import()>
    Public Property plugin As Lazy(Of IPlugin, IPluginMetadata)
End Class
```

```csharp
public class Addin
{
    [Import]
    public Lazy<IPlugin, IPluginMetadata> plugin;
}
```

<span data-ttu-id="69acf-239">Dans de nombreux cas, vous souhaiterez associer des métadonnées avec l'attribut `ImportMany` , afin d'analyser les importations disponibles et d'en choisir et instancier une seule, ou de filtrer une collection pour satisfaire une condition donnée.</span><span class="sxs-lookup"><span data-stu-id="69acf-239">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="69acf-240">La classe suivante instancie uniquement les objets `IPlugin` ayant une valeur `Name` égale à "Logger".</span><span class="sxs-lookup"><span data-stu-id="69acf-240">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>

```vb
Public Class User

    <ImportMany()>
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))

    Public Function InstantiateLogger() As IPlugin

        Dim logger As IPlugin
        logger = Nothing

        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins
            If Plugin.Metadata.Name = "Logger" Then
                logger = Plugin.Value
            End If
        Next
        Return logger
    End Function

End Class
```

```csharp
public class User
{
    [ImportMany]
    public IEnumerable<Lazy<IPlugin, IPluginMetadata>> plugins;

    public IPlugin InstantiateLogger()
    {
        IPlugin logger = null;

        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)
        {
            if (plugin.Metadata.Name == "Logger")
                logger = plugin.Value;
        }
        return logger;
    }
}
```

<a name="import_and_export_inheritance"></a>

## <a name="import-and-export-inheritance"></a><span data-ttu-id="69acf-241">Héritage des importations et exportations</span><span class="sxs-lookup"><span data-stu-id="69acf-241">Import and Export Inheritance</span></span>

<span data-ttu-id="69acf-242">Si une classe hérite d'un composant, elle peut également devenir un composant.</span><span class="sxs-lookup"><span data-stu-id="69acf-242">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="69acf-243">Les importations sont toujours héritées par les sous-classes.</span><span class="sxs-lookup"><span data-stu-id="69acf-243">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="69acf-244">Par conséquent, une sous-classe d'un composant est toujours un composant, avec les mêmes importations que sa classe parente.</span><span class="sxs-lookup"><span data-stu-id="69acf-244">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>

<span data-ttu-id="69acf-245">Les exportations déclarées à l'aide de l'attribut `Export` ne sont pas héritées par les sous-classes.</span><span class="sxs-lookup"><span data-stu-id="69acf-245">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="69acf-246">Toutefois, un composant peut s'exporter lui-même en utilisant l'attribut `InheritedExport` .</span><span class="sxs-lookup"><span data-stu-id="69acf-246">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="69acf-247">Les sous-classes du composant hériteront et fourniront la même exportation, y compris le nom de contrat et le type de contrat.</span><span class="sxs-lookup"><span data-stu-id="69acf-247">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="69acf-248">À la différence d'un attribut `Export` , `InheritedExport` peut être appliqué uniquement au niveau de la classe et non pas au niveau du membre.</span><span class="sxs-lookup"><span data-stu-id="69acf-248">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="69acf-249">Par conséquent, les exportations au niveau d'un membre ne peuvent jamais être héritées.</span><span class="sxs-lookup"><span data-stu-id="69acf-249">Therefore, member-level exports can never be inherited.</span></span>

<span data-ttu-id="69acf-250">Les quatre classes suivantes illustrent les principes de l'héritage des importations et des exportations.</span><span class="sxs-lookup"><span data-stu-id="69acf-250">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="69acf-251">`NumTwo` hérite de `NumOne`, si bien que `NumTwo` importera `IMyData`.</span><span class="sxs-lookup"><span data-stu-id="69acf-251">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="69acf-252">Les exportations ordinaires ne sont pas héritées, si bien que `NumTwo` n'exportera rien.</span><span class="sxs-lookup"><span data-stu-id="69acf-252">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="69acf-253">`NumFour` hérite de `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="69acf-253">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="69acf-254">Comme `NumThree` a utilisé `InheritedExport`, `NumFour` possède une exportation dotée du type de contrat `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="69acf-254">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="69acf-255">Les exportations au niveau d'un membre ne sont jamais héritées, si bien que `IMyData` n'est pas exporté.</span><span class="sxs-lookup"><span data-stu-id="69acf-255">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>

```vb
<Export()>
Public Class NumOne
    <Import()>
    Public Property MyData As IMyData
End Class

Public Class NumTwo
    Inherits NumOne

    'Imports are always inherited, so NumTwo will
    'Import IMyData

    'Ordinary exports are not inherited, so
    'NumTwo will NOT export anything.  As a result it
    'will not be discovered by the catalog!

End Class

<InheritedExport()>
Public Class NumThree

    <Export()>
    Public Property MyData As IMyData

    'This part provides two exports, one of
    'contract type NumThree, and one of
    'contract type IMyData.

End Class

Public Class NumFour
    Inherits NumThree

    'Because NumThree used InheritedExport,
    'this part has one export with contract
    'type NumThree.

    'Member-level exports are never inherited,
    'so IMyData is not exported.

End Class
```

```csharp
[Export]
public class NumOne
{
    [Import]
    public IMyData MyData { get; set; }
}

public class NumTwo : NumOne
{
    //Imports are always inherited, so NumTwo will
    //import IMyData.

    //Ordinary exports are not inherited, so
    //NumTwo will NOT export anything. As a result it
    //will not be discovered by the catalog!
}

[InheritedExport]
public class NumThree
{
    [Export]
    Public IMyData MyData { get; set; }

    //This part provides two exports, one of
    //contract type NumThree, and one of
    //contract type IMyData.
}

public class NumFour : NumThree
{
    //Because NumThree used InheritedExport,
    //this part has one export with contract
    //type NumThree.

    //Member-level exports are never inherited,
    //so IMyData is not exported.
}
```

<span data-ttu-id="69acf-256">Si des métadonnées sont associées à un attribut `InheritedExport` , elles seront également héritées.</span><span class="sxs-lookup"><span data-stu-id="69acf-256">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="69acf-257">(Pour plus d’informations, consultez la section « métadonnées et vues de métadonnées » précédentes.) Les métadonnées héritées ne peuvent pas être modifiées par la sous-classe.</span><span class="sxs-lookup"><span data-stu-id="69acf-257">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="69acf-258">Toutefois, en redéclarant l'attribut `InheritedExport` avec les mêmes nom de contrat et type de contrat, mais avec de nouvelles métadonnées, la sous-classe peut remplacer les métadonnées héritées par de nouvelles métadonnées.</span><span class="sxs-lookup"><span data-stu-id="69acf-258">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="69acf-259">La classe suivante illustre ce principe.</span><span class="sxs-lookup"><span data-stu-id="69acf-259">The following class demonstrates this principle.</span></span> <span data-ttu-id="69acf-260">Le composant `MegaLogger` hérite de `Logger` et inclut l'attribut `InheritedExport` .</span><span class="sxs-lookup"><span data-stu-id="69acf-260">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="69acf-261">Comme `MegaLogger` redéclare de nouvelles métadonnées nommées Status, il n'hérite pas les métadonnées Name et Version de `Logger`.</span><span class="sxs-lookup"><span data-stu-id="69acf-261">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>

```vb
<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class Logger
    Implements IPlugin

    'Exports with contract type IPlugin
    'and metadata "Name" and "Version".
End Class

Public Class SuperLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Name" and "Version", exactly the same
    'as the Logger class.

End Class

<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Status", "Green")>
Public Class MegaLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Status" only. Re-declaring
    'the attribute replaces all metadata.

End Class
```

```csharp
[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version".
}

public class SuperLogger : Logger
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version", exactly the same
    //as the Logger class.
}

[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Status", "Green")]
public class MegaLogger : Logger        {
    //Exports with contract type IPlugin and
    //metadata "Status" only. Re-declaring
    //the attribute replaces all metadata.
}
```

<span data-ttu-id="69acf-262">Lors de la redéclaration de l'attribut `InheritedExport` pour remplacer les métadonnées, assurez-vous que les types de contrat sont les mêmes.</span><span class="sxs-lookup"><span data-stu-id="69acf-262">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="69acf-263">(Dans l’exemple précédent, `IPlugin` est le type de contrat.) Si elles diffèrent, au lieu de se substituer, le deuxième attribut crée une deuxième exportation indépendante à partir de la partie.</span><span class="sxs-lookup"><span data-stu-id="69acf-263">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="69acf-264">En règle générale, cela signifie que vous devez spécifier explicitement le type de contrat quand vous remplacez un attribut `InheritedExport` , comme illustré dans l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="69acf-264">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>

<span data-ttu-id="69acf-265">Comme les interfaces ne peuvent pas être instanciées directement, elles ne peuvent généralement pas être décorées avec des attributs `Export` ou `Import` .</span><span class="sxs-lookup"><span data-stu-id="69acf-265">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="69acf-266">Toutefois, une interface peut être décorée avec un attribut `InheritedExport` au niveau de l'interface et cette exportation, ainsi que toutes les métadonnées associées, sera héritée par toutes les classes d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="69acf-266">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="69acf-267">Toutefois, l'interface elle-même ne sera pas disponible en tant que composant.</span><span class="sxs-lookup"><span data-stu-id="69acf-267">The interface itself will not be available as a part, however.</span></span>

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a><span data-ttu-id="69acf-268">Attributs d'exportation personnalisés</span><span class="sxs-lookup"><span data-stu-id="69acf-268">Custom Export Attributes</span></span>

<span data-ttu-id="69acf-269">Il est possible d'étendre les attributs d'exportation élémentaires, `Export` et `InheritedExport`, pour inclure des métadonnées en tant que propriétés d'attribut.</span><span class="sxs-lookup"><span data-stu-id="69acf-269">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="69acf-270">Cette technique est utile pour appliquer des métadonnées similaires à de nombreux composants ou pour créer une arborescence d'héritage des attributs de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="69acf-270">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>

<span data-ttu-id="69acf-271">Un attribut personnalisé peut spécifier le type de contrat, le nom de contrat ou d'autres métadonnées.</span><span class="sxs-lookup"><span data-stu-id="69acf-271">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="69acf-272">Pour définir un attribut personnalisé, une classe qui hérite d' `ExportAttribute` (ou d' `InheritedExportAttribute`) doit être décorée avec l'attribut `MetadataAttribute` .</span><span class="sxs-lookup"><span data-stu-id="69acf-272">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="69acf-273">La classe suivante définit un attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="69acf-273">The following class defines a custom attribute.</span></span>

```vb
<MetadataAttribute()>
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=false)>
Public Class MyAttribute
    Inherits ExportAttribute

    Public Property MyMetadata As String

    Public Sub New(ByVal myMetadata As String)
        MyBase.New(GetType(IMyAddin))

        myMetadata = myMetadata
    End Sub

End Class
```

```csharp
[MetadataAttribute]
[AttributeUsage(AttributeTargets.Class, AllowMultiple=false)]
public class MyAttribute : ExportAttribute
{
    public MyAttribute(string myMetadata)
        : base(typeof(IMyAddin))
    {
        MyMetadata = myMetadata;
    }

    public string MyMetadata { get; private set; }
}
```

<span data-ttu-id="69acf-274">Cette classe définit un attribut personnalisé nommé `MyAttribute` avec le type de contrat `IMyAddin` et certaines métadonnées nommées `MyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="69acf-274">This class defines a custom attribute named `MyAttribute` with contract type `IMyAddin` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="69acf-275">Toutes les propriétés figurant dans une classe marquée avec l'attribut `MetadataAttribute` sont considérées comme des métadonnées définies dans l'attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="69acf-275">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="69acf-276">Les deux déclarations suivantes sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="69acf-276">The following two declarations are equivalent.</span></span>

```vb
<Export(GetType(IMyAddin))>
<ExportMetadata("MyMetadata", "theData")>
Public Property myAddin As MyAddin
```

```vb
<MyAttribute("theData")>
Public Property myAddin As MyAddin
```

```csharp
[Export(typeof(IMyAddin)),
    ExportMetadata("MyMetadata", "theData")]
public MyAddin myAddin { get; set; }
```

```csharp
[MyAttribute("theData")]
public MyAddin myAddin { get; set; }
```

<span data-ttu-id="69acf-277">Dans la première déclaration, le type de contrat et les métadonnées sont explicitement définis.</span><span class="sxs-lookup"><span data-stu-id="69acf-277">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="69acf-278">Dans la seconde déclaration, le type de contrat et les métadonnées sont implicites dans l'attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="69acf-278">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="69acf-279">Notamment dans les cas où une grande quantité de métadonnées identiques doivent être appliquées à de nombreux composants (par exemple, les informations d'auteur ou de copyright), l'utilisation d'un attribut personnalisé permet d'économiser beaucoup de temps et d'éviter la duplication.</span><span class="sxs-lookup"><span data-stu-id="69acf-279">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="69acf-280">En outre, des arborescences d'héritage des attributs personnalisés peuvent être créées pour permettre les variations.</span><span class="sxs-lookup"><span data-stu-id="69acf-280">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>

<span data-ttu-id="69acf-281">Pour créer des métadonnées facultatives dans un attribut personnalisé, vous pouvez utiliser l'attribut `DefaultValue` .</span><span class="sxs-lookup"><span data-stu-id="69acf-281">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="69acf-282">Quand cet attribut est appliqué à une propriété dans une classe d'attributs personnalisée, il spécifie que la propriété décorée est facultative et n'est pas tenue d'être fournie par un exportateur.</span><span class="sxs-lookup"><span data-stu-id="69acf-282">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="69acf-283">Si aucune valeur n'est fournie pour la propriété, il lui sera attribué la valeur par défaut pour son type de propriété (habituellement `null`, `false`ou 0.)</span><span class="sxs-lookup"><span data-stu-id="69acf-283">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>

<a name="creation_policies"></a>

## <a name="creation-policies"></a><span data-ttu-id="69acf-284">Stratégies de création</span><span class="sxs-lookup"><span data-stu-id="69acf-284">Creation Policies</span></span>

<span data-ttu-id="69acf-285">Quand un composant spécifie une importation et qu'une composition est effectuée, le conteneur de composition essaie de trouver une exportation correspondante.</span><span class="sxs-lookup"><span data-stu-id="69acf-285">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="69acf-286">S'il parvient à mettre en correspondance l'importation et une exportation, le membre d'importation est défini sur une instance de l'objet exporté.</span><span class="sxs-lookup"><span data-stu-id="69acf-286">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="69acf-287">L'origine de cette instance est contrôlée par la *stratégie de création*du composant d'exportation.</span><span class="sxs-lookup"><span data-stu-id="69acf-287">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>

<span data-ttu-id="69acf-288">Les deux stratégies de création possibles sont *partagée* et *non partagée*.</span><span class="sxs-lookup"><span data-stu-id="69acf-288">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="69acf-289">Un composant doté d'une stratégie de création partagée sera partagé entre chaque importation dans le conteneur pour un composant avec ce contrat.</span><span class="sxs-lookup"><span data-stu-id="69acf-289">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="69acf-290">Quand le moteur de composition trouve une correspondance et doit définir une propriété d'importation, il instancie une nouvelle copie du composant seulement si aucune n'existe encore. Dans le cas contraire, il fournit la copie existante.</span><span class="sxs-lookup"><span data-stu-id="69acf-290">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="69acf-291">Cela signifie que de nombreux objets peuvent avoir des références au même composant.</span><span class="sxs-lookup"><span data-stu-id="69acf-291">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="69acf-292">De tels composants ne doivent pas s'appuyer sur l'état interne susceptible d'être modifié à partir de nombreux emplacements.</span><span class="sxs-lookup"><span data-stu-id="69acf-292">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="69acf-293">Cette stratégie est appropriée pour les composants statiques, les composants qui fournissent des services et les composants qui consomment beaucoup de mémoire ou d'autres ressources.</span><span class="sxs-lookup"><span data-stu-id="69acf-293">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>

<span data-ttu-id="69acf-294">Un composant doté de la stratégie de création non partagée est créé chaque fois qu'une importation correspondante est trouvée pour l'une de ses exportations.</span><span class="sxs-lookup"><span data-stu-id="69acf-294">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="69acf-295">Une nouvelle copie est donc instanciée pour chaque importation dans le conteneur qui correspond à l'un des contrats exportés du composant.</span><span class="sxs-lookup"><span data-stu-id="69acf-295">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="69acf-296">L'état interne de ces copies ne sera pas partagé.</span><span class="sxs-lookup"><span data-stu-id="69acf-296">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="69acf-297">Cette stratégie est appropriée pour les composants pour lesquels chaque importation exige son propre état interne.</span><span class="sxs-lookup"><span data-stu-id="69acf-297">This policy is appropriate for parts where each import requires its own internal state.</span></span>

<span data-ttu-id="69acf-298">L'importation et l'exportation peuvent spécifier la stratégie de création d'un composant, parmi les valeurs `Shared`, `NonShared`et `Any`.</span><span class="sxs-lookup"><span data-stu-id="69acf-298">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="69acf-299">La valeur par défaut est `Any` pour les importations et les exportations.</span><span class="sxs-lookup"><span data-stu-id="69acf-299">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="69acf-300">Une exportation qui spécifie `Shared` ou `NonShared` correspondra uniquement à une importation qui spécifie la même chose ou `Any`.</span><span class="sxs-lookup"><span data-stu-id="69acf-300">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="69acf-301">De même, une importation qui spécifie `Shared` ou `NonShared` correspondra uniquement à une exportation qui spécifie la même chose ou `Any`.</span><span class="sxs-lookup"><span data-stu-id="69acf-301">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="69acf-302">Des importations et des exportations dotées de stratégies de création incompatibles ne sont pas considérées comme concordantes, de la même façon qu'une importation et une exportation dont les noms de contrat ou les types de contrat ne correspondent pas.</span><span class="sxs-lookup"><span data-stu-id="69acf-302">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="69acf-303">Si l'importation et l'exportation spécifient `Any`, ou ne spécifient pas de stratégie de création et sont dotées par défaut de la stratégie `Any`, la stratégie de création sera partagée par défaut.</span><span class="sxs-lookup"><span data-stu-id="69acf-303">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>

<span data-ttu-id="69acf-304">L'exemple suivant illustre des importations et des exportations qui spécifient des stratégies de création.</span><span class="sxs-lookup"><span data-stu-id="69acf-304">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="69acf-305">`PartOne` ne spécifie aucune stratégie de création. La valeur par défaut est donc `Any`.</span><span class="sxs-lookup"><span data-stu-id="69acf-305">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="69acf-306">`PartTwo` ne spécifie aucune stratégie de création. La valeur par défaut est donc `Any`.</span><span class="sxs-lookup"><span data-stu-id="69acf-306">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="69acf-307">Comme l'importation et l'exportation présentent la valeur par défaut `Any`, `PartOne` est partagé.</span><span class="sxs-lookup"><span data-stu-id="69acf-307">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="69acf-308">`PartThree` spécifie une stratégie de création `Shared` , de sorte que `PartTwo` et `PartThree` partageront la même copie de `PartOne`.</span><span class="sxs-lookup"><span data-stu-id="69acf-308">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="69acf-309">`PartFour` spécifie une stratégie de création `NonShared` , de sorte que `PartFour` ne sera pas partagé dans `PartFive`.</span><span class="sxs-lookup"><span data-stu-id="69acf-309">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="69acf-310">`PartSix` spécifie une stratégie de création `NonShared` .</span><span class="sxs-lookup"><span data-stu-id="69acf-310">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="69acf-311">`PartFive` et `PartSix` recevront chacun des copies distinctes de `PartFour`.</span><span class="sxs-lookup"><span data-stu-id="69acf-311">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="69acf-312">`PartSeven` spécifie une stratégie de création `Shared` .</span><span class="sxs-lookup"><span data-stu-id="69acf-312">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="69acf-313">Comme il n'existe aucun `PartFour` exporté avec une stratégie de création `Shared`, l'importation `PartSeven` ne correspond à rien et ne sera pas remplie.</span><span class="sxs-lookup"><span data-stu-id="69acf-313">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>

```vb
<Export()>
Public Class PartOne
    'The default creation policy for an export is Any.
End Class

Public Class PartTwo

    <Import()>
    Public Property partOne As PartOne

    'The default creation policy for an import is Any.
    'If both policies are Any, the part will be shared.

End Class

Public Class PartThree

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partOne As PartOne

    'The Shared creation policy is explicitly specified.
    'PartTwo and PartThree will receive references to the
    'SAME copy of PartOne.

End Class

<Export()>
<PartCreationPolicy(CreationPolicy.NonShared)>
Public Class PartFour
    'The NonShared creation policy is explicitly specified.
End Class

Public Class PartFive

    <Import()>
    Public Property partFour As PartFour

    'The default creation policy for an import is Any.
    'Since the export's creation policy was explicitly
    'defined, the creation policy for this property will
    'be non-shared.

End Class

Public Class PartSix

    <Import(RequiredCreationPolicy:=CreationPolicy.NonShared)>
    Public Property partFour As PartFour

    'Both import and export specify matching creation
    'policies.  PartFive and PartSix will each receive
    'SEPARATE copies of PartFour, each with its own
    'internal state.

End Class

Public Class PartSeven

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partFour As PartFour

    'A creation policy mismatch.  Because there is no
    'exported PartFour with a creation policy of Shared,
    'this import does not match anything and will not be
    'filled.

End Class
```

```csharp
[Export]
public class PartOne
{
    //The default creation policy for an export is Any.
}

public class PartTwo
{
    [Import]
    public PartOne partOne { get; set; }

    //The default creation policy for an import is Any.
    //If both policies are Any, the part will be shared.
}

public class PartThree
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartOne partOne { get; set; }

    //The Shared creation policy is explicitly specified.
    //PartTwo and PartThree will receive references to the
    //SAME copy of PartOne.
}

[Export]
[PartCreationPolicy(CreationPolicy.NonShared)]
public class PartFour
{
    //The NonShared creation policy is explicitly specified.
}

public class PartFive
{
    [Import]
    public PartFour partFour { get; set; }

    //The default creation policy for an import is Any.
    //Since the export's creation policy was explicitly
    //defined, the creation policy for this property will
    //be non-shared.
}

public class PartSix
{
    [Import(RequiredCreationPolicy = CreationPolicy.NonShared)]
    public PartFour partFour { get; set; }

    //Both import and export specify matching creation
    //policies.  PartFive and PartSix will each receive
    //SEPARATE copies of PartFour, each with its own
    //internal state.
}

public class PartSeven
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartFour partFour { get; set; }

    //A creation policy mismatch.  Because there is no
    //exported PartFour with a creation policy of Shared,
    //this import does not match anything and will not be
    //filled.
}
```

<a name="life_cycle_and_disposing"></a>

## <a name="life-cycle-and-disposing"></a><span data-ttu-id="69acf-314">Cycle de vie et suppression</span><span class="sxs-lookup"><span data-stu-id="69acf-314">Life Cycle and Disposing</span></span>

<span data-ttu-id="69acf-315">Comme les composants sont hébergés dans le conteneur de composition, leur cycle de vie peut être plus complexe que celui d'objets ordinaires.</span><span class="sxs-lookup"><span data-stu-id="69acf-315">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="69acf-316">Les composants peuvent implémenter deux interfaces importantes liées au cycle de vie : `IDisposable` et `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="69acf-316">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>

<span data-ttu-id="69acf-317">Les composants pour lesquels des opérations doivent être effectuées au moment de l'arrêt ou qui ont besoin de libérer des ressources doivent implémenter `IDisposable`, comme d'habitude pour les objets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69acf-317">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="69acf-318">Toutefois, étant donné que le conteneur crée et tient à jour des références aux composants, seul le conteneur qui détient un composant doit appeler la méthode `Dispose` sur ce dernier.</span><span class="sxs-lookup"><span data-stu-id="69acf-318">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="69acf-319">Le conteneur lui-même implémente `IDisposable`et, dans le cadre de son nettoyage dans `Dispose` , il appellera `Dispose` sur tous les composants qu'il détient.</span><span class="sxs-lookup"><span data-stu-id="69acf-319">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="69acf-320">Pour cette raison, vous devez toujours supprimer le conteneur de composition quand lui et tous les composants qu'il détient ne sont plus requis.</span><span class="sxs-lookup"><span data-stu-id="69acf-320">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>

<span data-ttu-id="69acf-321">Pour les conteneurs de composition durables, la consommation de mémoire par les composants dotés d'une stratégie de création non partagée peut devenir un problème.</span><span class="sxs-lookup"><span data-stu-id="69acf-321">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="69acf-322">Ces composants non partagés peuvent être créés plusieurs fois et ne seront pas supprimés temps que le conteneur lui-même ne le sera pas.</span><span class="sxs-lookup"><span data-stu-id="69acf-322">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="69acf-323">Pour gérer cela, le conteneur fournit la méthode `ReleaseExport` .</span><span class="sxs-lookup"><span data-stu-id="69acf-323">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="69acf-324">L'appel de cette méthode sur une exportation non partagée supprime cette exportation du conteneur de composition et supprime ce dernier.</span><span class="sxs-lookup"><span data-stu-id="69acf-324">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="69acf-325">Les composants utilisés seulement par l'exportation supprimée, et ainsi de suite jusqu'au bas de l'arborescence, sont également supprimés.</span><span class="sxs-lookup"><span data-stu-id="69acf-325">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="69acf-326">De cette manière, les ressources peuvent être récupérées sans que le conteneur de composition lui-même soit supprimé.</span><span class="sxs-lookup"><span data-stu-id="69acf-326">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>

<span data-ttu-id="69acf-327">`IPartImportsSatisfiedNotification` contient une méthode nommée `OnImportsSatisfied`.</span><span class="sxs-lookup"><span data-stu-id="69acf-327">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="69acf-328">Cette méthode est appelée par le conteneur de composition sur tous les composants qui implémentent l'interface, une fois la composition terminée et les importations du composant prêtes à l'emploi.</span><span class="sxs-lookup"><span data-stu-id="69acf-328">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="69acf-329">Les composants sont créés par le moteur de composition pour remplir les importations des autres composants.</span><span class="sxs-lookup"><span data-stu-id="69acf-329">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="69acf-330">Avant que les importations d'un composant aient été définies, vous ne pouvez pas effectuer d'initialisation qui manipule ou s'appuie sur des valeurs importées dans le constructeur du composant, à moins que ces valeurs aient été spécifiées en tant que composants prérequis à l'aide de l'attribut `ImportingConstructor` .</span><span class="sxs-lookup"><span data-stu-id="69acf-330">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="69acf-331">Ceci est normalement la méthode conseillée mais, dans certains cas, l'injection de constructeur peut ne pas être disponible.</span><span class="sxs-lookup"><span data-stu-id="69acf-331">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="69acf-332">Dans ce cas, il est possible d'effectuer l'initialisation dans `OnImportsSatisfied`et le composant doit implémenter `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="69acf-332">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>

## <a name="see-also"></a><span data-ttu-id="69acf-333">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69acf-333">See also</span></span>

- [<span data-ttu-id="69acf-334">Vidéo Channel 9 : Ouvrir vos applications avec Managed Extensibility Framework</span><span class="sxs-lookup"><span data-stu-id="69acf-334">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [<span data-ttu-id="69acf-335">Vidéo Channel 9 : Managed Extensibility Framework (MEF) 2.0</span><span class="sxs-lookup"><span data-stu-id="69acf-335">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
