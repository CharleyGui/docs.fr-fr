---
title: Indépendance du langage et composants indépendants du langage
description: Découvrez comment développer dans un des nombreux langages pris en charge dans .NET, tels que C#, C++/CLI, F#, IronPython, VB, Visual COBOL et PowerShell.
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: 813558299b40e0b90e8047f22b788c8f1419eb5e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504652"
---
# <a name="language-independence-and-language-independent-components"></a><span data-ttu-id="9170d-103">Indépendance du langage et composants indépendants du langage</span><span class="sxs-lookup"><span data-stu-id="9170d-103">Language independence and language-independent components</span></span>

<span data-ttu-id="9170d-104">.NET est indépendant du langage.</span><span class="sxs-lookup"><span data-stu-id="9170d-104">.NET is language independent.</span></span> <span data-ttu-id="9170d-105">Cela signifie qu’en tant que développeur, vous pouvez développer dans un des nombreux langages qui ciblent des implémentations de .NET, comme C#, F# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9170d-105">This means that, as a developer, you can develop in one of the many languages that target .NET implementations, such as C#, F#, and Visual Basic.</span></span> <span data-ttu-id="9170d-106">Vous pouvez accéder aux types et aux membres des bibliothèques de classes développées pour des implémentations de .NET sans avoir à connaître le langage dans lequel ils ont été initialement écrits ni à suivre les conventions du langage d’origine.</span><span class="sxs-lookup"><span data-stu-id="9170d-106">You can access the types and members of class libraries developed for .NET implementations without having to know the language in which they were originally written and without having to follow any of the original language's conventions.</span></span> <span data-ttu-id="9170d-107">Si vous êtes un développeur de composants, votre composant est accessible par n’importe quelle application .NET, quelle que soit sa langue.</span><span class="sxs-lookup"><span data-stu-id="9170d-107">If you're a component developer, your component can be accessed by any .NET app, regardless of its language.</span></span>

> [!NOTE]
> <span data-ttu-id="9170d-108">Cette première partie de cet article traite de la création de composants indépendants du langage, c’est-à-dire de composants qui peuvent être utilisés par des applications écrites dans n’importe quel langage.</span><span class="sxs-lookup"><span data-stu-id="9170d-108">This first part of this article discusses creating language-independent components, that is, components that can be consumed by apps that are written in any language.</span></span> <span data-ttu-id="9170d-109">Vous pouvez également créer un composant ou une application unique à partir de code source écrit dans plusieurs langages. Consultez [Interopérabilité multilingue](#cross-language-interoperability) dans la deuxième partie de cet article.</span><span class="sxs-lookup"><span data-stu-id="9170d-109">You can also create a single component or app from source code written in multiple languages; see [Cross-Language Interoperability](#cross-language-interoperability) in the second part of this article.</span></span>

<span data-ttu-id="9170d-110">Pour interagir entièrement avec d’autres objets écrits dans un langage quelconque, les objets ne doivent exposer aux appelants que les fonctionnalités communes à tous les langages.</span><span class="sxs-lookup"><span data-stu-id="9170d-110">To fully interact with other objects written in any language, objects must expose to callers only those features that are common to all languages.</span></span> <span data-ttu-id="9170d-111">Cet ensemble commun de fonctionnalités est défini par la spécification CLS (Common Language Specification), qui est un ensemble de règles qui s’appliquent aux assemblys générés.</span><span class="sxs-lookup"><span data-stu-id="9170d-111">This common set of features is defined by the Common Language Specification (CLS), which is a set of rules that apply to generated assemblies.</span></span> <span data-ttu-id="9170d-112">La spécification CLS (Common Language Specification) est définie dans la Partition I, clauses 7 à 11 du document [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="9170d-112">The Common Language Specification is defined in Partition I, Clauses 7 through 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

<span data-ttu-id="9170d-113">Si votre composant est conforme à la spécification CLS, il est garanti d'être conforme CLS et accessible à partir du code dans les assemblys écrits dans n'importe quel langage de programmation qui prend en charge la spécification CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-113">If your component conforms to the Common Language Specification, it is guaranteed to be CLS-compliant and can be accessed from code in assemblies written in any programming language that supports the CLS.</span></span> <span data-ttu-id="9170d-114">Vous pouvez déterminer si votre composant est conforme à la spécification CLS (Common Language Specification) au moment de la compilation en appliquant l’attribut [CSLCompliantAttribute](xref:System.CLSCompliantAttribute) à votre code source.</span><span class="sxs-lookup"><span data-stu-id="9170d-114">You can determine whether your component conforms to the Common Language Specification at compile time by applying the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute to your source code.</span></span> <span data-ttu-id="9170d-115">Pour plus d’informations, consultez [Attribut CLSCompliantAttribute](#the-clscompliantattribute-attribute).</span><span class="sxs-lookup"><span data-stu-id="9170d-115">For more information, see [The CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute).</span></span>

## <a name="cls-compliance-rules"></a><span data-ttu-id="9170d-116">Règles de conformité CLS</span><span class="sxs-lookup"><span data-stu-id="9170d-116">CLS compliance rules</span></span>

<span data-ttu-id="9170d-117">Cette section présente les règles de création d'un composant conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-117">This section discusses the rules for creating a CLS-compliant component.</span></span> <span data-ttu-id="9170d-118">Pour obtenir une liste complète des règles, consultez la Partition I, clause 11 du document [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="9170d-118">For a complete list of rules, see Partition I, Clause 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

> [!NOTE]
> <span data-ttu-id="9170d-119">La spécification CLS (Common Language Specification) présente chaque règle de conformité CLS telle qu'elle s'applique aux consommateurs (les développeurs qui accèdent par programme à un composant conforme CLS), aux infrastructures (les développeurs qui utilisent un compilateur de langage pour créer des bibliothèques conformes CLS) et aux extendeurs (les développeurs qui créent un outil tel qu'un compilateur de langage ou un analyseur de code qui crée des composants conformes CLS).</span><span class="sxs-lookup"><span data-stu-id="9170d-119">The Common Language Specification discusses each rule for CLS compliance as it applies to consumers (developers who are programmatically accessing a component that is CLS-compliant), frameworks (developers who are using a language compiler to create CLS-compliant libraries), and extenders (developers who are creating a tool such as a language compiler or a code parser that creates CLS-compliant components).</span></span> <span data-ttu-id="9170d-120">Cet article se concentre sur les règles applicables aux infrastructures.</span><span class="sxs-lookup"><span data-stu-id="9170d-120">This article focuses on the rules as they apply to frameworks.</span></span> <span data-ttu-id="9170d-121">Notez, toutefois, que certaines des règles qui s’appliquent aux extendeurs peuvent également s’appliquer aux assemblys créés à l’aide de [Reflection. Emit](xref:System.Reflection.Emit).</span><span class="sxs-lookup"><span data-stu-id="9170d-121">Note, though, that some of the rules that apply to extenders may also apply to assemblies that are created using [Reflection.Emit](xref:System.Reflection.Emit).</span></span>

<span data-ttu-id="9170d-122">Pour concevoir un composant indépendant du langage, vous n'avez qu'à appliquer les règles de conformité CLS à l'interface publique de votre composant.</span><span class="sxs-lookup"><span data-stu-id="9170d-122">To design a component that is language independent, you only need to apply the rules for CLS compliance to your component's public interface.</span></span> <span data-ttu-id="9170d-123">Votre implémentation privée n'a pas besoin d'être conforme à la spécification.</span><span class="sxs-lookup"><span data-stu-id="9170d-123">Your private implementation does not have to conform to the specification.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9170d-124">Les règles de conformité CLS s'appliquent uniquement à l'interface publique d'un composant, pas à son implémentation privée.</span><span class="sxs-lookup"><span data-stu-id="9170d-124">The rules for CLS compliance apply only to a component's public interface, not to its private implementation.</span></span>

<span data-ttu-id="9170d-125">Par exemple, les entiers non signés autres que [Byte](xref:System.Byte) ne sont pas conformes CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-125">For example, unsigned integers other than [Byte](xref:System.Byte) are not CLS-compliant.</span></span> <span data-ttu-id="9170d-126">Étant donné que la classe `Person` de l’exemple suivant expose une propriété `Age` de type [UInt16](xref:System.UInt16), le code suivant affiche un avertissement du compilateur.</span><span class="sxs-lookup"><span data-stu-id="9170d-126">Because the `Person` class in the following example exposes an `Age` property of type [UInt16](xref:System.UInt16), the following code displays a compiler warning.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge
      End Get
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

<span data-ttu-id="9170d-127">Vous pouvez rendre la classe Person conforme CLS en remplaçant le type `UInt16` de la propriété `Age` par [Int16](xref:System.Int16), qui est un entier signé 16 bits conforme CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-127">You can make the Person class CLS-compliant by changing the type of `Age` property from `UInt16` to [Int16](xref:System.Int16), which is a CLS-compliant, 16-bit signed integer.</span></span> <span data-ttu-id="9170d-128">Il n'est pas nécessaire de modifier le type du champ privé `personAge`.</span><span class="sxs-lookup"><span data-stu-id="9170d-128">You do not have to change the type of the private `personAge` field.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)
      End Get
   End Property
End Class
```

<span data-ttu-id="9170d-129">L'interface publique d'une bibliothèque inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9170d-129">A library's public interface consists of the following:</span></span>

* <span data-ttu-id="9170d-130">Définitions des classes publiques.</span><span class="sxs-lookup"><span data-stu-id="9170d-130">Definitions of public classes.</span></span>

* <span data-ttu-id="9170d-131">Définitions des membres publics des classes publiques et définitions des membres accessibles aux classes dérivées (à savoir, membres protégés).</span><span class="sxs-lookup"><span data-stu-id="9170d-131">Definitions of the public members of public classes, and definitions of members accessible to derived classes (that is, protected members).</span></span>

* <span data-ttu-id="9170d-132">Paramètres et types de retour des méthodes publiques des classes publiques, et paramètres et types de retour des méthodes accessibles aux classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="9170d-132">Parameters and return types of public methods of public classes, and parameters and return types of methods accessible to derived classes.</span></span>

<span data-ttu-id="9170d-133">Les règles de conformité CLS sont répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="9170d-133">The rules for CLS compliance are listed in the following table.</span></span> <span data-ttu-id="9170d-134">Le texte des règles est repris mot pour mot du document [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), qui est protégé par copyright 2012 par Ecma International.</span><span class="sxs-lookup"><span data-stu-id="9170d-134">The text of the rules is taken verbatim from the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), which is Copyright 2012 by Ecma International.</span></span> <span data-ttu-id="9170d-135">Vous trouverez des informations plus détaillées sur ces règles dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="9170d-135">More detailed information about these rules is found in the following sections.</span></span>

<span data-ttu-id="9170d-136">Category</span><span class="sxs-lookup"><span data-stu-id="9170d-136">Category</span></span> | <span data-ttu-id="9170d-137">Consultez</span><span class="sxs-lookup"><span data-stu-id="9170d-137">See</span></span> | <span data-ttu-id="9170d-138">Règle</span><span class="sxs-lookup"><span data-stu-id="9170d-138">Rule</span></span> | <span data-ttu-id="9170d-139">Numéro de règle</span><span class="sxs-lookup"><span data-stu-id="9170d-139">Rule Number</span></span>
-------- | --- | ---- | -----------
<span data-ttu-id="9170d-140">Accessibilité</span><span class="sxs-lookup"><span data-stu-id="9170d-140">Accessibility</span></span> | [<span data-ttu-id="9170d-141">Accessibilité des membres</span><span class="sxs-lookup"><span data-stu-id="9170d-141">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="9170d-142">L'accessibilité ne devra pas être changée lors du remplacement de méthodes héritées, sauf en cas de remplacement d'une méthode héritée d'un assembly différent avec accessibilité `family-or-assembly`.</span><span class="sxs-lookup"><span data-stu-id="9170d-142">Accessibility shall not be changed when overriding inherited methods, except when overriding a method inherited from a different assembly with accessibility `family-or-assembly`.</span></span> <span data-ttu-id="9170d-143">Dans ce cas, le remplacement devra posséder l'accessibilité `family`.</span><span class="sxs-lookup"><span data-stu-id="9170d-143">In this case, the override shall have accessibility `family`.</span></span> | <span data-ttu-id="9170d-144">10</span><span class="sxs-lookup"><span data-stu-id="9170d-144">10</span></span>
<span data-ttu-id="9170d-145">Accessibilité</span><span class="sxs-lookup"><span data-stu-id="9170d-145">Accessibility</span></span> | [<span data-ttu-id="9170d-146">Accessibilité des membres</span><span class="sxs-lookup"><span data-stu-id="9170d-146">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="9170d-147">La visibilité et l'accessibilité des types et des membres seront déterminées de telle sorte que les types utilisés dans la signature d'un membre seront visibles et accessibles lorsque le membre proprement dit est visible et accessible.</span><span class="sxs-lookup"><span data-stu-id="9170d-147">The visibility and accessibility of types and members shall be such that types in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="9170d-148">Par exemple, une méthode publique qui est visible à l'extérieur de son assembly n'aura pas d'argument dont le type est visible uniquement dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9170d-148">For example, a public method that is visible outside its assembly shall not have an argument whose type is visible only within the assembly.</span></span> <span data-ttu-id="9170d-149">La visibilité et l'accessibilité des types composant un type générique instancié utilisé dans la signature d'un membre seront visibles et accessibles lorsque le membre proprement dit est visible et accessible.</span><span class="sxs-lookup"><span data-stu-id="9170d-149">The visibility and accessibility of types composing an instantiated generic type used in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="9170d-150">Par exemple, un type générique instancié présent dans la signature d'un membre qui est visible à l'extérieur de l'assembly n'aura pas d'argument générique dont le type est visible uniquement dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9170d-150">For example, an instantiated generic type present in the signature of a member that is visible outside its assembly shall not have a generic argument whose type is visible only within the assembly.</span></span> | <span data-ttu-id="9170d-151">12</span><span class="sxs-lookup"><span data-stu-id="9170d-151">12</span></span>
<span data-ttu-id="9170d-152">Tableaux</span><span class="sxs-lookup"><span data-stu-id="9170d-152">Arrays</span></span> | [<span data-ttu-id="9170d-153">Tableaux</span><span class="sxs-lookup"><span data-stu-id="9170d-153">Arrays</span></span>](#arrays) | <span data-ttu-id="9170d-154">Les tableaux auront des éléments avec un type conforme à CLS, et toutes les dimensions du tableau auront des limites inférieures égales à zéro.</span><span class="sxs-lookup"><span data-stu-id="9170d-154">Arrays shall have elements with a CLS-compliant type, and all dimensions of the array shall have lower bounds of zero.</span></span> <span data-ttu-id="9170d-155">Seul le fait qu'un élément soit un tableau et le type d'élément du tableau seront requis pour distinguer les surcharges.</span><span class="sxs-lookup"><span data-stu-id="9170d-155">Only the fact that an item is an array and the element type of the array shall be required to distinguish between overloads.</span></span> <span data-ttu-id="9170d-156">Lorsque la surcharge est basée sur deux ou plusieurs types tableau, les types d’éléments doivent être des types nommés.</span><span class="sxs-lookup"><span data-stu-id="9170d-156">When overloading is based on two or more array types, the element types shall be named types.</span></span> | <span data-ttu-id="9170d-157">16</span><span class="sxs-lookup"><span data-stu-id="9170d-157">16</span></span>
<span data-ttu-id="9170d-158">Attributs</span><span class="sxs-lookup"><span data-stu-id="9170d-158">Attributes</span></span> | [<span data-ttu-id="9170d-159">Attributs</span><span class="sxs-lookup"><span data-stu-id="9170d-159">Attributes</span></span>](#attributes) | <span data-ttu-id="9170d-160">Les attributs doivent être de type [System.Attribute](xref:System.Attribute) ou d’un type hérité de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="9170d-160">Attributes shall be of type [System.Attribute](xref:System.Attribute), or a type inheriting from it.</span></span> | <span data-ttu-id="9170d-161">41</span><span class="sxs-lookup"><span data-stu-id="9170d-161">41</span></span>
<span data-ttu-id="9170d-162">Attributs</span><span class="sxs-lookup"><span data-stu-id="9170d-162">Attributes</span></span> | [<span data-ttu-id="9170d-163">Attributs</span><span class="sxs-lookup"><span data-stu-id="9170d-163">Attributes</span></span>](#attributes) | <span data-ttu-id="9170d-164">La spécification CLS autorise uniquement un sous-ensemble des encodages d'attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="9170d-164">The CLS only allows a subset of the encodings of custom attributes.</span></span> <span data-ttu-id="9170d-165">Les seuls types qui doivent apparaître dans ces codages sont (voir Partition IV) : [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double) et tout type d’énumération reposant sur un type entier de base conforme CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-165">The only types that shall appear in these encodings are (see Partition IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), and any enumeration type based on a CLS-compliant base integer type.</span></span> | <span data-ttu-id="9170d-166">34</span><span class="sxs-lookup"><span data-stu-id="9170d-166">34</span></span>
<span data-ttu-id="9170d-167">Attributs</span><span class="sxs-lookup"><span data-stu-id="9170d-167">Attributes</span></span> | [<span data-ttu-id="9170d-168">Attributs</span><span class="sxs-lookup"><span data-stu-id="9170d-168">Attributes</span></span>](#attributes) | <span data-ttu-id="9170d-169">La spécification CLS n'autorise pas les modificateurs obligatoires visibles publiquement (`modreq`, voir Partition II), mais autorise les modificateurs facultatifs (`modopt`, voir Partition II) qu'elle ne comprend pas.</span><span class="sxs-lookup"><span data-stu-id="9170d-169">The CLS does not allow publicly visible required modifiers (`modreq`, see Partition II), but does allow optional modifiers (`modopt`, see Partition II) it does not understand.</span></span> | <span data-ttu-id="9170d-170">35</span><span class="sxs-lookup"><span data-stu-id="9170d-170">35</span></span>
<span data-ttu-id="9170d-171">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="9170d-171">Constructors</span></span> | [<span data-ttu-id="9170d-172">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="9170d-172">Constructors</span></span>](#constructors) | <span data-ttu-id="9170d-173">Un constructeur d'objet appellera un constructeur d'instance de sa classe de base avant tout accès aux données d'instance héritées.</span><span class="sxs-lookup"><span data-stu-id="9170d-173">An object constructor shall call some instance constructor of its base class before any access occurs to inherited instance data.</span></span> <span data-ttu-id="9170d-174">(Cela ne s'applique pas aux types de valeurs, qui n'ont pas besoin de constructeurs.)</span><span class="sxs-lookup"><span data-stu-id="9170d-174">(This does not apply to value types, which need not have constructors.)</span></span>  | <span data-ttu-id="9170d-175">21</span><span class="sxs-lookup"><span data-stu-id="9170d-175">21</span></span>
<span data-ttu-id="9170d-176">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="9170d-176">Constructors</span></span> | [<span data-ttu-id="9170d-177">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="9170d-177">Constructors</span></span>](#constructors) | <span data-ttu-id="9170d-178">Un constructeur d'objet ne sera pas appelé sauf dans le cadre de la création d'un objet, et un objet ne sera pas initialisé deux fois.</span><span class="sxs-lookup"><span data-stu-id="9170d-178">An object constructor shall not be called except as part of the creation of an object, and an object shall not be initialized twice.</span></span> | <span data-ttu-id="9170d-179">22</span><span class="sxs-lookup"><span data-stu-id="9170d-179">22</span></span>
<span data-ttu-id="9170d-180">Énumérations</span><span class="sxs-lookup"><span data-stu-id="9170d-180">Enumerations</span></span> | [<span data-ttu-id="9170d-181">Énumérations</span><span class="sxs-lookup"><span data-stu-id="9170d-181">Enumerations</span></span>](#enumerations) | <span data-ttu-id="9170d-182">Le type sous-jacent d'une énumération devra être un type d'entier CLS intégré, le nom du champ devra être « valeur__ » et ce champ devra être marqué `RTSpecialName`.</span><span class="sxs-lookup"><span data-stu-id="9170d-182">The underlying type of an enum shall be a built-in CLS integer type, the name of the field shall be "value__", and that field shall be marked `RTSpecialName`.</span></span> |  <span data-ttu-id="9170d-183">7</span><span class="sxs-lookup"><span data-stu-id="9170d-183">7</span></span>
<span data-ttu-id="9170d-184">Énumérations</span><span class="sxs-lookup"><span data-stu-id="9170d-184">Enumerations</span></span> | [<span data-ttu-id="9170d-185">Énumérations</span><span class="sxs-lookup"><span data-stu-id="9170d-185">Enumerations</span></span>](#enumerations) | <span data-ttu-id="9170d-186">Il existe deux sortes distinctes d’énumérations, signalées par la présence ou l’absence de l’attribut personnalisé [System.FlagsAttribute](xref:System.FlagsAttribute) (voir Partition IV, Library).</span><span class="sxs-lookup"><span data-stu-id="9170d-186">There are two distinct kinds of enums, indicated by the presence or absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) (see Partition IV Library) custom attribute.</span></span> <span data-ttu-id="9170d-187">L'un représente des valeurs entières nommées ; l'autre représente les indicateurs binaires nommés qui peuvent être combinés pour générer une valeur sans nom.</span><span class="sxs-lookup"><span data-stu-id="9170d-187">One represents named integer values; the other represents named bit flags that can be combined to generate an unnamed value.</span></span> <span data-ttu-id="9170d-188">La valeur d'une `enum` n'est pas limitée aux valeurs spécifiées.</span><span class="sxs-lookup"><span data-stu-id="9170d-188">The value of an `enum` is not limited to the specified values.</span></span> |  <span data-ttu-id="9170d-189">8</span><span class="sxs-lookup"><span data-stu-id="9170d-189">8</span></span>
<span data-ttu-id="9170d-190">Énumérations</span><span class="sxs-lookup"><span data-stu-id="9170d-190">Enumerations</span></span> | [<span data-ttu-id="9170d-191">Énumérations</span><span class="sxs-lookup"><span data-stu-id="9170d-191">Enumerations</span></span>](#enumerations) | <span data-ttu-id="9170d-192">Les champs static littéraux d’une énumération auront le type de l’énumération elle-même.</span><span class="sxs-lookup"><span data-stu-id="9170d-192">Literal static fields of an enum shall have the type of the enum itself.</span></span> |  <span data-ttu-id="9170d-193">9</span><span class="sxs-lookup"><span data-stu-id="9170d-193">9</span></span>
<span data-ttu-id="9170d-194">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-194">Events</span></span> | [<span data-ttu-id="9170d-195">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-195">Events</span></span>](#events) | <span data-ttu-id="9170d-196">Les méthodes qui implémentent un événement doivent être marquées `SpecialName` dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9170d-196">The methods that implement an event shall be marked `SpecialName` in the metadata.</span></span> |<span data-ttu-id="9170d-197">29</span><span class="sxs-lookup"><span data-stu-id="9170d-197">29</span></span>
<span data-ttu-id="9170d-198">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-198">Events</span></span> | [<span data-ttu-id="9170d-199">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-199">Events</span></span>](#events) | <span data-ttu-id="9170d-200">L’accessibilité d’un événement et de ses accesseurs sera identique.</span><span class="sxs-lookup"><span data-stu-id="9170d-200">The accessibility of an event and of its accessors shall be identical.</span></span> |<span data-ttu-id="9170d-201">30</span><span class="sxs-lookup"><span data-stu-id="9170d-201">30</span></span>
<span data-ttu-id="9170d-202">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-202">Events</span></span> | [<span data-ttu-id="9170d-203">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-203">Events</span></span>](#events) | <span data-ttu-id="9170d-204">Les méthodes `add` et `remove` d'un événement devront toutes les deux être présentes ou absentes.</span><span class="sxs-lookup"><span data-stu-id="9170d-204">The `add` and `remove` methods for an event shall both either be present or absent.</span></span> |<span data-ttu-id="9170d-205">31</span><span class="sxs-lookup"><span data-stu-id="9170d-205">31</span></span>
<span data-ttu-id="9170d-206">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-206">Events</span></span> | [<span data-ttu-id="9170d-207">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-207">Events</span></span>](#events) | <span data-ttu-id="9170d-208">Les `add` `remove` méthodes et d’un événement doivent chacune accepter un paramètre dont le type définit le type de l’événement et qui doit être dérivé de [System. Delegate](xref:System.Delegate).</span><span class="sxs-lookup"><span data-stu-id="9170d-208">The `add` and `remove` methods for an event shall each take one parameter whose type defines the type of the event and that shall be derived from [System.Delegate](xref:System.Delegate).</span></span> |<span data-ttu-id="9170d-209">32</span><span class="sxs-lookup"><span data-stu-id="9170d-209">32</span></span>
<span data-ttu-id="9170d-210">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-210">Events</span></span> | [<span data-ttu-id="9170d-211">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-211">Events</span></span>](#events) | <span data-ttu-id="9170d-212">Les événements adhéreront à un modèle d’attribution de nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="9170d-212">Events shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="9170d-213">L’attribut SpecialName dont il est question dans la règle 29 de la spécification CLS doit être ignoré dans les comparaisons de noms appropriées et doit respecter les règles d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="9170d-213">The SpecialName attribute referred to in CLS rule 29 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span>  |<span data-ttu-id="9170d-214">33</span><span class="sxs-lookup"><span data-stu-id="9170d-214">33</span></span>
<span data-ttu-id="9170d-215">Exceptions</span><span class="sxs-lookup"><span data-stu-id="9170d-215">Exceptions</span></span> | [<span data-ttu-id="9170d-216">Exceptions</span><span class="sxs-lookup"><span data-stu-id="9170d-216">Exceptions</span></span>](#exceptions) | <span data-ttu-id="9170d-217">Les objets levés doivent être de type [System.Exception](xref:System.Exception) ou d’un type hérité de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="9170d-217">Objects that are thrown shall be of type [System.Exception](xref:System.Exception) or a type inheriting from it.</span></span> <span data-ttu-id="9170d-218">Néanmoins, les méthodes conformes à CLS ne sont pas requises pour bloquer la propagation d'autres types d'exceptions.</span><span class="sxs-lookup"><span data-stu-id="9170d-218">Nonetheless, CLS-compliant methods are not required to block the propagation of other types of exceptions.</span></span> | <span data-ttu-id="9170d-219">40</span><span class="sxs-lookup"><span data-stu-id="9170d-219">40</span></span>
<span data-ttu-id="9170d-220">Général</span><span class="sxs-lookup"><span data-stu-id="9170d-220">General</span></span> | [<span data-ttu-id="9170d-221">Règles de conformité CLS</span><span class="sxs-lookup"><span data-stu-id="9170d-221">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="9170d-222">Les règles CLS s'appliquent uniquement aux éléments d'un type qui sont accessibles ou visibles en dehors de l'assembly de définition.</span><span class="sxs-lookup"><span data-stu-id="9170d-222">CLS rules apply only to those parts of a type that are accessible or visible outside of the defining assembly.</span></span> | <span data-ttu-id="9170d-223">1</span><span class="sxs-lookup"><span data-stu-id="9170d-223">1</span></span>
<span data-ttu-id="9170d-224">Général</span><span class="sxs-lookup"><span data-stu-id="9170d-224">General</span></span> | [<span data-ttu-id="9170d-225">Règles de conformité CLS</span><span class="sxs-lookup"><span data-stu-id="9170d-225">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="9170d-226">Les membres de types non conformes à CLS ne seront pas marqués comme conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-226">Members of non-CLS compliant types shall not be marked CLS-compliant.</span></span> | <span data-ttu-id="9170d-227">2</span><span class="sxs-lookup"><span data-stu-id="9170d-227">2</span></span>
<span data-ttu-id="9170d-228">Génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-228">Generics</span></span> | [<span data-ttu-id="9170d-229">Types et membres génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-229">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="9170d-230">Les types imbriqués devront posséder au moins autant de paramètres génériques que le type englobant.</span><span class="sxs-lookup"><span data-stu-id="9170d-230">Nested types shall have at least as many generic parameters as the enclosing type.</span></span> <span data-ttu-id="9170d-231">Les paramètres génériques d'un type imbriqué ont la même position que les paramètres génériques du type englobant correspondant.</span><span class="sxs-lookup"><span data-stu-id="9170d-231">Generic parameters in a nested type correspond by position to the generic parameters in its enclosing type.</span></span>  | <span data-ttu-id="9170d-232">42</span><span class="sxs-lookup"><span data-stu-id="9170d-232">42</span></span>
<span data-ttu-id="9170d-233">Génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-233">Generics</span></span> | [<span data-ttu-id="9170d-234">Types et membres génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-234">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="9170d-235">Le nom d’un type générique devra encoder le nombre de paramètres de type déclarés sur le type non imbriqué ou récemment introduits dans le type s’il est imbriqué, selon les règles définies ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="9170d-235">The name of a generic type shall encode the number of type parameters declared on the non-nested type, or newly introduced to the type if nested, according to the rules defined above.</span></span> | <span data-ttu-id="9170d-236">43</span><span class="sxs-lookup"><span data-stu-id="9170d-236">43</span></span>
<span data-ttu-id="9170d-237">Génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-237">Generics</span></span> | [<span data-ttu-id="9170d-238">Types et membres génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-238">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="9170d-239">Un type générique devra redéclarer les contraintes suffisantes afin de garantir que les contraintes sur le type de base ou les interfaces seraient satisfaites par les contraintes de type générique.</span><span class="sxs-lookup"><span data-stu-id="9170d-239">A generic type shall redeclare sufficient constraints to guarantee that any constraints on the base type, or interfaces would be satisfied by the generic type constraints.</span></span> | <span data-ttu-id="9170d-240">44</span><span class="sxs-lookup"><span data-stu-id="9170d-240">44</span></span>
<span data-ttu-id="9170d-241">Génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-241">Generics</span></span> | [<span data-ttu-id="9170d-242">Types et membres génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-242">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="9170d-243">Les types utilisés comme contraintes sur les paramètres génériques devront eux-mêmes être conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-243">Types used as constraints on generic parameters shall themselves be CLS-compliant.</span></span> | <span data-ttu-id="9170d-244">45</span><span class="sxs-lookup"><span data-stu-id="9170d-244">45</span></span>
<span data-ttu-id="9170d-245">Génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-245">Generics</span></span> | [<span data-ttu-id="9170d-246">Types et membres génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-246">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="9170d-247">La visibilité et l'accessibilité des membres (y compris des types imbriqués) d'un type générique instancié devront être définies dans l'instanciation spécifique plutôt que dans la déclaration générale du type générique.</span><span class="sxs-lookup"><span data-stu-id="9170d-247">The visibility and accessibility of members (including nested types) in an instantiated generic type shall be considered to be scoped to the specific instantiation rather than the generic type declaration as a whole.</span></span> <span data-ttu-id="9170d-248">Sachant cela, les règles de visibilité et d'accessibilité de la règle 12 de la spécification CLS s'appliquent toujours.</span><span class="sxs-lookup"><span data-stu-id="9170d-248">Assuming this, the visibility and accessibility rules of CLS rule 12 still apply.</span></span> | <span data-ttu-id="9170d-249">46</span><span class="sxs-lookup"><span data-stu-id="9170d-249">46</span></span>
<span data-ttu-id="9170d-250">Génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-250">Generics</span></span> | [<span data-ttu-id="9170d-251">Types et membres génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-251">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="9170d-252">À chaque méthode générique abstraite ou virtuelle doit correspondre une implémentation concrète (non abstraite) par défaut</span><span class="sxs-lookup"><span data-stu-id="9170d-252">For each abstract or virtual generic method, there shall be a default concrete (nonabstract) implementation</span></span> | <span data-ttu-id="9170d-253">47</span><span class="sxs-lookup"><span data-stu-id="9170d-253">47</span></span>
<span data-ttu-id="9170d-254">Interfaces</span><span class="sxs-lookup"><span data-stu-id="9170d-254">Interfaces</span></span> | [<span data-ttu-id="9170d-255">Interfaces</span><span class="sxs-lookup"><span data-stu-id="9170d-255">Interfaces</span></span>](#interfaces) | <span data-ttu-id="9170d-256">Les interfaces conformes à CLS ne devront pas nécessiter la définition de méthodes non conformes à CLS pour pouvoir les implémenter.</span><span class="sxs-lookup"><span data-stu-id="9170d-256">CLS-compliant interfaces shall not require the definition of non-CLS compliant methods in order to implement them.</span></span> | <span data-ttu-id="9170d-257">18</span><span class="sxs-lookup"><span data-stu-id="9170d-257">18</span></span>
<span data-ttu-id="9170d-258">Interfaces</span><span class="sxs-lookup"><span data-stu-id="9170d-258">Interfaces</span></span> | [<span data-ttu-id="9170d-259">Interfaces</span><span class="sxs-lookup"><span data-stu-id="9170d-259">Interfaces</span></span>](#interfaces) | <span data-ttu-id="9170d-260">Les interfaces conformes à CLS ne devront pas définir de méthodes statiques ni de champs.</span><span class="sxs-lookup"><span data-stu-id="9170d-260">CLS-compliant interfaces shall not define static methods, nor shall they define fields.</span></span> | <span data-ttu-id="9170d-261">19</span><span class="sxs-lookup"><span data-stu-id="9170d-261">19</span></span>
<span data-ttu-id="9170d-262">Membres</span><span class="sxs-lookup"><span data-stu-id="9170d-262">Members</span></span> | [<span data-ttu-id="9170d-263">Membres de types en général</span><span class="sxs-lookup"><span data-stu-id="9170d-263">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="9170d-264">Les méthodes et les champs static globaux ne sont pas conformes CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-264">Global static fields and methods are not CLS-compliant.</span></span> | <span data-ttu-id="9170d-265">36</span><span class="sxs-lookup"><span data-stu-id="9170d-265">36</span></span>
<span data-ttu-id="9170d-266">Membres</span><span class="sxs-lookup"><span data-stu-id="9170d-266">Members</span></span> | -- | <span data-ttu-id="9170d-267">La valeur d'un champ statique littéral est spécifiée via l'utilisation de métadonnées d'initialisation de champ.</span><span class="sxs-lookup"><span data-stu-id="9170d-267">The value of a literal static is specified through the use of field initialization metadata.</span></span> <span data-ttu-id="9170d-268">Un littéral conforme à CLS doit avoir une valeur spécifiée dans les métadonnées d'initialisation de champ qui est exactement du même type que le littéral (ou du type sous-jacent, si ce littéral est une `enum`).</span><span class="sxs-lookup"><span data-stu-id="9170d-268">A CLS-compliant literal must have a value specified in field initialization metadata that is of exactly the same type as the literal (or of the underlying type, if that literal is an `enum`).</span></span> | <span data-ttu-id="9170d-269">13</span><span class="sxs-lookup"><span data-stu-id="9170d-269">13</span></span>
<span data-ttu-id="9170d-270">Membres</span><span class="sxs-lookup"><span data-stu-id="9170d-270">Members</span></span> | [<span data-ttu-id="9170d-271">Membres de types en général</span><span class="sxs-lookup"><span data-stu-id="9170d-271">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="9170d-272">La contrainte vararg ne fait pas partie de la spécification CLS, et la seule convention d’appel prise en charge par la spécification CLS est la convention d’appel managée standard.</span><span class="sxs-lookup"><span data-stu-id="9170d-272">The vararg constraint is not part of the CLS, and the only calling convention supported by the CLS is the standard managed calling convention.</span></span> | <span data-ttu-id="9170d-273">15</span><span class="sxs-lookup"><span data-stu-id="9170d-273">15</span></span>
<span data-ttu-id="9170d-274">Conventions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="9170d-274">Naming conventions</span></span> | [<span data-ttu-id="9170d-275">Conventions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="9170d-275">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="9170d-276">Les assemblys doivent suivre l’Annexe 7 du Rapport technique 15 de la norme Unicode 3.0 régissant l’ensemble des caractères autorisés pour lancer les identificateurs et être inclus dans ces derniers. Cette annexe est disponible en ligne sous [Unicode Normalization Forms](https://unicode.org/reports/tr15/) (Formes de normalisation Unicode).</span><span class="sxs-lookup"><span data-stu-id="9170d-276">Assemblies shall follow Annex 7 of Technical Report 15 of the Unicode Standard3.0 governing the set of characters permitted to start and be included in identifiers, available online at [Unicode Normalization Forms](https://unicode.org/reports/tr15/).</span></span> <span data-ttu-id="9170d-277">Les identificateurs doivent être dans un format canonique défini par la forme C de normalisation Unicode. Dans le cadre de la spécification CLS, deux identificateurs sont les mêmes si leurs mappages en minuscules (comme spécifié par les mappages en minuscules un-à-un insensibles aux paramètres régionaux Unicode) sont identiques.</span><span class="sxs-lookup"><span data-stu-id="9170d-277">Identifiers shall be in the canonical format defined by Unicode Normalization Form C. For CLS purposes, two identifiers are the same if their lowercase mappings (as specified by the Unicode locale-insensitive, one-to-one lowercase mappings) are the same.</span></span> <span data-ttu-id="9170d-278">Autrement dit, pour que deux identificateurs soient considérés comme différents dans le cadre de la spécification CLS, ils doivent être différenciés par d’autres éléments que leur casse.</span><span class="sxs-lookup"><span data-stu-id="9170d-278">That is, for two identifiers to be considered different under the CLS they shall differ in more than simply their case.</span></span> <span data-ttu-id="9170d-279">Toutefois, pour remplacer une définition héritée, l’infrastructure CLI nécessite l’utilisation de l’encodage exact de la déclaration d’origine.</span><span class="sxs-lookup"><span data-stu-id="9170d-279">However, in order to override an inherited definition the CLI requires the precise encoding of the original declaration be used.</span></span> | <span data-ttu-id="9170d-280">4</span><span class="sxs-lookup"><span data-stu-id="9170d-280">4</span></span>
<span data-ttu-id="9170d-281">Surcharge</span><span class="sxs-lookup"><span data-stu-id="9170d-281">Overloading</span></span> | [<span data-ttu-id="9170d-282">Conventions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="9170d-282">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="9170d-283">Tous les noms introduits dans une portée conforme CLS doivent être distincts, indépendamment de leur type, sauf quand les noms sont identiques et résolus par surcharge.</span><span class="sxs-lookup"><span data-stu-id="9170d-283">All names introduced in a CLS-compliant scope shall be distinct independent of kind, except where the names are identical and resolved via overloading.</span></span> <span data-ttu-id="9170d-284">Par exemple, alors que CTS autorise un type à utiliser le même nom pour une méthode et un champ, CLS ne l’autorise pas.</span><span class="sxs-lookup"><span data-stu-id="9170d-284">That is, while the CTS allows a single type to use the same name for a method and a field, the CLS does not.</span></span> | <span data-ttu-id="9170d-285">5</span><span class="sxs-lookup"><span data-stu-id="9170d-285">5</span></span>
<span data-ttu-id="9170d-286">Surcharge</span><span class="sxs-lookup"><span data-stu-id="9170d-286">Overloading</span></span> | [<span data-ttu-id="9170d-287">Conventions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="9170d-287">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="9170d-288">Les champs et les types imbriqués seront distincts par comparaison d'identificateurs seule, même si CTS autorise la distinction de signatures différentes.</span><span class="sxs-lookup"><span data-stu-id="9170d-288">Fields and nested types shall be distinct by identifier comparison alone, even though the CTS allows distinct signatures to be distinguished.</span></span> <span data-ttu-id="9170d-289">Les méthodes, les propriétés et les événements qui ont le même nom (par comparaison d’identificateur) ne doivent pas différer uniquement par le type de retour, sauf dans les cas spécifiés dans la règle CLS 39</span><span class="sxs-lookup"><span data-stu-id="9170d-289">Methods, properties, and events that have the same name (by identifier comparison) shall differ by more than just the return type, except as specified in CLS Rule 39</span></span> | <span data-ttu-id="9170d-290">6</span><span class="sxs-lookup"><span data-stu-id="9170d-290">6</span></span>
<span data-ttu-id="9170d-291">Surcharge</span><span class="sxs-lookup"><span data-stu-id="9170d-291">Overloading</span></span> | [<span data-ttu-id="9170d-292">Surcharges</span><span class="sxs-lookup"><span data-stu-id="9170d-292">Overloads</span></span>](#overloads) | <span data-ttu-id="9170d-293">Seules les propriétés et les méthodes peuvent être surchargées.</span><span class="sxs-lookup"><span data-stu-id="9170d-293">Only properties and methods can be overloaded.</span></span> | <span data-ttu-id="9170d-294">37</span><span class="sxs-lookup"><span data-stu-id="9170d-294">37</span></span>
<span data-ttu-id="9170d-295">Surcharge</span><span class="sxs-lookup"><span data-stu-id="9170d-295">Overloading</span></span> | [<span data-ttu-id="9170d-296">Surcharges</span><span class="sxs-lookup"><span data-stu-id="9170d-296">Overloads</span></span>](#overloads) |<span data-ttu-id="9170d-297">Les propriétés et les méthodes peuvent être surchargées en fonction du nombre et des types de leurs paramètres uniquement, à l'exception des opérateurs de conversion nommés `op_Implicit` et `op_Explicit`, qui peuvent également être surchargés selon leur type de retour.</span><span class="sxs-lookup"><span data-stu-id="9170d-297">Properties and methods can be overloaded based only on the number and types of their parameters, except the conversion operators named `op_Implicit` and `op_Explicit`, which can also be overloaded based on their return type.</span></span> | <span data-ttu-id="9170d-298">38</span><span class="sxs-lookup"><span data-stu-id="9170d-298">38</span></span>
<span data-ttu-id="9170d-299">Surcharge</span><span class="sxs-lookup"><span data-stu-id="9170d-299">Overloading</span></span> | -- | <span data-ttu-id="9170d-300">Si deux ou plusieurs méthodes conformes CLS déclarées dans un type ont le même nom et, pour un jeu spécifique d’instanciations de types, ont le même paramètre et les mêmes types de retour, alors toutes ces méthodes sont sémantiquement équivalentes à ces instanciations de type.</span><span class="sxs-lookup"><span data-stu-id="9170d-300">If two or more CLS-compliant methods declared in a type have the same name and, for a specific set of type instantiations, they have the same parameter and return types, then all these methods shall be semantically equivalent at those type instantiations.</span></span> | <span data-ttu-id="9170d-301">48</span><span class="sxs-lookup"><span data-stu-id="9170d-301">48</span></span>
<span data-ttu-id="9170d-302">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9170d-302">Properties</span></span> | [<span data-ttu-id="9170d-303">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9170d-303">Properties</span></span>](#properties) | <span data-ttu-id="9170d-304">Les méthodes qui implémentent les méthodes getter et setter d’une propriété doivent être marquées `SpecialName` dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9170d-304">The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.</span></span> | <span data-ttu-id="9170d-305">24</span><span class="sxs-lookup"><span data-stu-id="9170d-305">24</span></span>
<span data-ttu-id="9170d-306">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9170d-306">Properties</span></span> | [<span data-ttu-id="9170d-307">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9170d-307">Properties</span></span>](#properties) | <span data-ttu-id="9170d-308">Les accesseurs d’une propriété doivent tous être statiques, virtuels ou être des instances.</span><span class="sxs-lookup"><span data-stu-id="9170d-308">A property's accessors shall all be static, all be virtual, or all be instance.</span></span> | <span data-ttu-id="9170d-309">26</span><span class="sxs-lookup"><span data-stu-id="9170d-309">26</span></span>
<span data-ttu-id="9170d-310">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9170d-310">Properties</span></span> | [<span data-ttu-id="9170d-311">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9170d-311">Properties</span></span>](#properties) | <span data-ttu-id="9170d-312">Le type d’une propriété devra correspondre au type de retour de la méthode getter et au type du dernier argument de la méthode setter.</span><span class="sxs-lookup"><span data-stu-id="9170d-312">The type of a property shall be the return type of the getter and the type of the last argument of the setter.</span></span> <span data-ttu-id="9170d-313">Les types des paramètres de la propriété devront correspondre aux types des paramètres de la méthode getter et aux types de tous les paramètres de la méthode setter, sauf le dernier.</span><span class="sxs-lookup"><span data-stu-id="9170d-313">The types of the parameters of the property shall be the types of the parameters to the getter and the types of all but the final parameter of the setter.</span></span> <span data-ttu-id="9170d-314">Tous ces types devront être conformes à CLS et ne pas être des pointeurs managés (à savoir, ils ne doivent pas être passés par référence).</span><span class="sxs-lookup"><span data-stu-id="9170d-314">All of these types shall be CLS-compliant, and shall not be managed pointers (that is, shall not be passed by reference).</span></span> | <span data-ttu-id="9170d-315">27</span><span class="sxs-lookup"><span data-stu-id="9170d-315">27</span></span>
<span data-ttu-id="9170d-316">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9170d-316">Properties</span></span> | [<span data-ttu-id="9170d-317">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9170d-317">Properties</span></span>](#properties) | <span data-ttu-id="9170d-318">Les propriétés adhéreront à un modèle d’attribution de nom spécifique.</span><span class="sxs-lookup"><span data-stu-id="9170d-318">Properties shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="9170d-319">L'attribut `SpecialName` dont il est question dans la règle 24 de la spécification CLS sera ignoré dans les comparaisons de noms appropriées et respectera les règles d'identificateur.</span><span class="sxs-lookup"><span data-stu-id="9170d-319">The `SpecialName` attribute referred to in CLS rule 24 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span> <span data-ttu-id="9170d-320">Une propriété aura une méthode getter, une méthode setter ou les deux.</span><span class="sxs-lookup"><span data-stu-id="9170d-320">A property shall have a getter method, a setter method, or both.</span></span> | <span data-ttu-id="9170d-321">28</span><span class="sxs-lookup"><span data-stu-id="9170d-321">28</span></span>
<span data-ttu-id="9170d-322">Conversion de type</span><span class="sxs-lookup"><span data-stu-id="9170d-322">Type conversion</span></span> | [<span data-ttu-id="9170d-323">Conversion de type</span><span class="sxs-lookup"><span data-stu-id="9170d-323">Type conversion</span></span>](#type-conversion) | <span data-ttu-id="9170d-324">Si op_Implicit ou op_Explicit est fourni, un autre moyen est utilisé pour fournir la contrainte.</span><span class="sxs-lookup"><span data-stu-id="9170d-324">If either op_Implicit or op_Explicit is provided, an alternate means of providing the coercion shall be provided.</span></span> | <span data-ttu-id="9170d-325">39</span><span class="sxs-lookup"><span data-stu-id="9170d-325">39</span></span>
<span data-ttu-id="9170d-326">Types</span><span class="sxs-lookup"><span data-stu-id="9170d-326">Types</span></span> | [<span data-ttu-id="9170d-327">Types et signatures de membres de types</span><span class="sxs-lookup"><span data-stu-id="9170d-327">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="9170d-328">Les types de valeurs encadrés ne sont pas conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-328">Boxed value types are not CLS-compliant.</span></span> | <span data-ttu-id="9170d-329">3</span><span class="sxs-lookup"><span data-stu-id="9170d-329">3</span></span>
<span data-ttu-id="9170d-330">Types</span><span class="sxs-lookup"><span data-stu-id="9170d-330">Types</span></span> | [<span data-ttu-id="9170d-331">Types et signatures de membres de types</span><span class="sxs-lookup"><span data-stu-id="9170d-331">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="9170d-332">Tous les types apparaissant dans une signature devront être conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-332">All types appearing in a signature shall be CLS-compliant.</span></span> <span data-ttu-id="9170d-333">Tous les types composant un type générique instancié devront être conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-333">All types composing an instantiated generic type shall be CLS-compliant.</span></span> | <span data-ttu-id="9170d-334">11</span><span class="sxs-lookup"><span data-stu-id="9170d-334">11</span></span>
<span data-ttu-id="9170d-335">Types</span><span class="sxs-lookup"><span data-stu-id="9170d-335">Types</span></span> | [<span data-ttu-id="9170d-336">Types et signatures de membres de types</span><span class="sxs-lookup"><span data-stu-id="9170d-336">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="9170d-337">Les références typées ne sont pas conformes CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-337">Typed references are not CLS-compliant.</span></span> | <span data-ttu-id="9170d-338">14</span><span class="sxs-lookup"><span data-stu-id="9170d-338">14</span></span>
<span data-ttu-id="9170d-339">Types</span><span class="sxs-lookup"><span data-stu-id="9170d-339">Types</span></span> | [<span data-ttu-id="9170d-340">Types et signatures de membres de types</span><span class="sxs-lookup"><span data-stu-id="9170d-340">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="9170d-341">Les types de pointeurs non managés ne sont pas conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-341">Unmanaged pointer types are not CLS-compliant.</span></span> | <span data-ttu-id="9170d-342">17</span><span class="sxs-lookup"><span data-stu-id="9170d-342">17</span></span>
<span data-ttu-id="9170d-343">Types</span><span class="sxs-lookup"><span data-stu-id="9170d-343">Types</span></span> | [<span data-ttu-id="9170d-344">Types et signatures de membres de types</span><span class="sxs-lookup"><span data-stu-id="9170d-344">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="9170d-345">Les classes, les types de valeurs et les interfaces conformes CLS ne doivent pas nécessiter l’implémentation de membres non conformes CLS</span><span class="sxs-lookup"><span data-stu-id="9170d-345">CLS-compliant classes, value types, and interfaces shall not require the implementation of non-CLS-compliant members</span></span> | <span data-ttu-id="9170d-346">20</span><span class="sxs-lookup"><span data-stu-id="9170d-346">20</span></span>
<span data-ttu-id="9170d-347">Types</span><span class="sxs-lookup"><span data-stu-id="9170d-347">Types</span></span> | [<span data-ttu-id="9170d-348">Types et signatures de membres de types</span><span class="sxs-lookup"><span data-stu-id="9170d-348">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="9170d-349">[System.Object](xref:System.Object) est conforme CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-349">[System.Object](xref:System.Object) is CLS-compliant.</span></span> <span data-ttu-id="9170d-350">Toute autre classe conforme à CLS héritera d'une classe conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-350">Any other CLS-compliant class shall inherit from a CLS-compliant class.</span></span> | <span data-ttu-id="9170d-351">23</span><span class="sxs-lookup"><span data-stu-id="9170d-351">23</span></span>

<span data-ttu-id="9170d-352">Index des sous-sections :</span><span class="sxs-lookup"><span data-stu-id="9170d-352">Index to subsections:</span></span>

* [<span data-ttu-id="9170d-353">Types et signatures de membres de types</span><span class="sxs-lookup"><span data-stu-id="9170d-353">Types and type member signatures</span></span>](#types-and-type-member-signatures)
* [<span data-ttu-id="9170d-354">Conventions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="9170d-354">Naming conventions</span></span>](#naming-conventions)
* [<span data-ttu-id="9170d-355">Conversion de type</span><span class="sxs-lookup"><span data-stu-id="9170d-355">Type conversion</span></span>](#type-conversion)
* [<span data-ttu-id="9170d-356">Tableaux</span><span class="sxs-lookup"><span data-stu-id="9170d-356">Arrays</span></span>](#arrays)
* [<span data-ttu-id="9170d-357">Interfaces</span><span class="sxs-lookup"><span data-stu-id="9170d-357">Interfaces</span></span>](#interfaces)
* [<span data-ttu-id="9170d-358">Énumérations</span><span class="sxs-lookup"><span data-stu-id="9170d-358">Enumerations</span></span>](#enumerations)
* [<span data-ttu-id="9170d-359">Membres de types en général</span><span class="sxs-lookup"><span data-stu-id="9170d-359">Type members in general</span></span>](#type-members-in-general)
* [<span data-ttu-id="9170d-360">Accessibilité des membres</span><span class="sxs-lookup"><span data-stu-id="9170d-360">Member accessibility</span></span>](#member-accessibility)
* [<span data-ttu-id="9170d-361">Types et membres génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-361">Generic types and members</span></span>](#generic-types-and-members)
* [<span data-ttu-id="9170d-362">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="9170d-362">Constructors</span></span>](#constructors)
* [<span data-ttu-id="9170d-363">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9170d-363">Properties</span></span>](#properties)
* [<span data-ttu-id="9170d-364">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-364">Events</span></span>](#events)
* [<span data-ttu-id="9170d-365">Surcharges</span><span class="sxs-lookup"><span data-stu-id="9170d-365">Overloads</span></span>](#overloads)
* [<span data-ttu-id="9170d-366">Exceptions</span><span class="sxs-lookup"><span data-stu-id="9170d-366">Exceptions</span></span>](#exceptions)
* [<span data-ttu-id="9170d-367">Attributs</span><span class="sxs-lookup"><span data-stu-id="9170d-367">Attributes</span></span>](#attributes)

### <a name="types-and-type-member-signatures"></a><span data-ttu-id="9170d-368">Types et signatures de membres de types</span><span class="sxs-lookup"><span data-stu-id="9170d-368">Types and type member signatures</span></span>

<span data-ttu-id="9170d-369">Le type [System.Object](xref:System.Object) est conforme CLS et correspond au type de base de tous les types d’objets du système de types .Net Framework.</span><span class="sxs-lookup"><span data-stu-id="9170d-369">The [System.Object](xref:System.Object) type is CLS-compliant and is the base type of all object types in the .NET Framework type system.</span></span> <span data-ttu-id="9170d-370">Dans le .NET Framework, l’héritage est implicite (par exemple, la classe [String](xref:System.String) hérite implicitement de la classe `Object`) ou explicite (par exemple, la classe [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) hérite explicitement de la classe [ArgumentException](xref:System.ArgumentException), qui hérite explicitement de la classe [Exception](xref:System.Exception).</span><span class="sxs-lookup"><span data-stu-id="9170d-370">Inheritance in the .NET Framework is either implicit (for example, the [String](xref:System.String) class implicitly inherits from the `Object` class) or explicit (for example, the [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) class explicitly inherits from the [ArgumentException](xref:System.ArgumentException) class, which explicitly inherits from the [Exception](xref:System.Exception) class.</span></span> <span data-ttu-id="9170d-371">Pour qu'un type dérivé soit conforme à CLS, son type de base doit également être conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-371">For a derived type to be CLS compliant, its base type must also be CLS-compliant.</span></span>

<span data-ttu-id="9170d-372">L'exemple suivant montre un type dérivé dont le type de base n'est pas conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-372">The following example shows a derived type whose base type is not CLS-compliant.</span></span> <span data-ttu-id="9170d-373">Il définit une classe `Counter` de base qui utilise un entier 32 bits non signé en tant que compteur.</span><span class="sxs-lookup"><span data-stu-id="9170d-373">It defines a base `Counter` class that uses an unsigned 32-bit integer as a counter.</span></span> <span data-ttu-id="9170d-374">La classe fournissant une fonctionnalité de compteur en encapsulant un entier non signé, elle est marquée comme non conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-374">Because the class provides counter functionality by wrapping an unsigned integer, the class is marked as non-CLS-compliant.</span></span> <span data-ttu-id="9170d-375">Par conséquent, une classe dérivée, `NonZeroCounter`, n'est pas non plus conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-375">As a result, a derived class, `NonZeroCounter`, is also not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)]
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return $"{ctr}). ";
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment()
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return $"{ctr}). "
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant
'    because it derives from 'Counter', which is not CLS-compliant.
'
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

<span data-ttu-id="9170d-376">Tous les types qui apparaissent dans les signatures de membres, notamment le type de retour d’une méthode ou un type de propriété, doivent être conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-376">All types that appear in member signatures, including a method's return type or a property type, must be CLS-compliant.</span></span> <span data-ttu-id="9170d-377">En outre, pour les types génériques :</span><span class="sxs-lookup"><span data-stu-id="9170d-377">In addition, for generic types:</span></span>

* <span data-ttu-id="9170d-378">Tous les types qui composent un type générique instancié doivent être conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-378">All types that compose an instantiated generic type must be CLS-compliant.</span></span>

* <span data-ttu-id="9170d-379">Tous les types utilisés comme contraintes sur des paramètres génériques doivent eux-mêmes être conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-379">All types used as constraints on generic parameters must be CLS-compliant.</span></span>

<span data-ttu-id="9170d-380">Le [système de type commun](common-type-system.md) .NET inclut un certain nombre de types intégrés pris en charge directement par le Common Langage Runtime et qui sont spécialement encodés dans les métadonnées d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="9170d-380">The .NET [common type system](common-type-system.md) includes a number of built-in types that are supported directly by the common language runtime and are specially encoded in an assembly's metadata.</span></span> <span data-ttu-id="9170d-381">Parmi les types intrinsèques, les types répertoriés dans le tableau suivant sont conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-381">Of these intrinsic types, the types listed in the following table are CLS-compliant.</span></span>

<span data-ttu-id="9170d-382">Type conforme à CLS</span><span class="sxs-lookup"><span data-stu-id="9170d-382">CLS-compliant type</span></span> | <span data-ttu-id="9170d-383">Description</span><span class="sxs-lookup"><span data-stu-id="9170d-383">Description</span></span>
------------------ | -----------
[<span data-ttu-id="9170d-384">Poids</span><span class="sxs-lookup"><span data-stu-id="9170d-384">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="9170d-385">Entier 8 bits non signé</span><span class="sxs-lookup"><span data-stu-id="9170d-385">8-bit unsigned integer</span></span>
[<span data-ttu-id="9170d-386">Int16</span><span class="sxs-lookup"><span data-stu-id="9170d-386">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="9170d-387">Entier 16 bits signé</span><span class="sxs-lookup"><span data-stu-id="9170d-387">16-bit signed integer</span></span>
[<span data-ttu-id="9170d-388">Int32</span><span class="sxs-lookup"><span data-stu-id="9170d-388">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="9170d-389">Entier 32 bits signé</span><span class="sxs-lookup"><span data-stu-id="9170d-389">32-bit signed integer</span></span>
[<span data-ttu-id="9170d-390">Int64</span><span class="sxs-lookup"><span data-stu-id="9170d-390">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="9170d-391">Entier 64 bits signé</span><span class="sxs-lookup"><span data-stu-id="9170d-391">64-bit signed integer</span></span>
[<span data-ttu-id="9170d-392">Unique</span><span class="sxs-lookup"><span data-stu-id="9170d-392">Single</span></span>](xref:System.Single) | <span data-ttu-id="9170d-393">Valeur à virgule flottante simple précision</span><span class="sxs-lookup"><span data-stu-id="9170d-393">Single-precision floating-point value</span></span>
[<span data-ttu-id="9170d-394">Double</span><span class="sxs-lookup"><span data-stu-id="9170d-394">Double</span></span>](xref:System.Double) | <span data-ttu-id="9170d-395">Valeur à virgule flottante double précision</span><span class="sxs-lookup"><span data-stu-id="9170d-395">Double-precision floating-point value</span></span>
[<span data-ttu-id="9170d-396">Booléen</span><span class="sxs-lookup"><span data-stu-id="9170d-396">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="9170d-397">Type de valeur true ou false</span><span class="sxs-lookup"><span data-stu-id="9170d-397">true or false value type</span></span>
[<span data-ttu-id="9170d-398">Char</span><span class="sxs-lookup"><span data-stu-id="9170d-398">Char</span></span>](xref:System.Char) | <span data-ttu-id="9170d-399">Unité de code encodée en UTF-16</span><span class="sxs-lookup"><span data-stu-id="9170d-399">UTF-16 encoded code unit</span></span>
[<span data-ttu-id="9170d-400">Décimal</span><span class="sxs-lookup"><span data-stu-id="9170d-400">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="9170d-401">Nombre décimal à virgule fixe</span><span class="sxs-lookup"><span data-stu-id="9170d-401">Non-floating-point decimal number</span></span>
[<span data-ttu-id="9170d-402">IntPtr</span><span class="sxs-lookup"><span data-stu-id="9170d-402">IntPtr</span></span>](xref:System.IntPtr) | <span data-ttu-id="9170d-403">Pointeur ou handle d'une taille définie par la plateforme</span><span class="sxs-lookup"><span data-stu-id="9170d-403">Pointer or handle of a platform-defined size</span></span>
[<span data-ttu-id="9170d-404">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9170d-404">String</span></span>](xref:System.String) | <span data-ttu-id="9170d-405">Collection de zéro, un ou plusieurs objets Char</span><span class="sxs-lookup"><span data-stu-id="9170d-405">Collection of zero, one, or more Char objects</span></span>

<span data-ttu-id="9170d-406">Les types intrinsèques répertoriés dans le tableau suivant ne sont pas conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-406">The intrinsic types listed in the following table are not CLS-Compliant.</span></span>

<span data-ttu-id="9170d-407">Type non conforme</span><span class="sxs-lookup"><span data-stu-id="9170d-407">Non-compliant type</span></span> | <span data-ttu-id="9170d-408">Description</span><span class="sxs-lookup"><span data-stu-id="9170d-408">Description</span></span> | <span data-ttu-id="9170d-409">Alternative à la conformité CLS</span><span class="sxs-lookup"><span data-stu-id="9170d-409">CLS-compliant alternative</span></span>
------------------ | ----------- | -------------------------
[<span data-ttu-id="9170d-410">SByte</span><span class="sxs-lookup"><span data-stu-id="9170d-410">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="9170d-411">Type de données entier signé 8 bits</span><span class="sxs-lookup"><span data-stu-id="9170d-411">8-bit signed integer data type</span></span> | [<span data-ttu-id="9170d-412">Int16</span><span class="sxs-lookup"><span data-stu-id="9170d-412">Int16</span></span>](xref:System.Int16)
[<span data-ttu-id="9170d-413">UInt16</span><span class="sxs-lookup"><span data-stu-id="9170d-413">UInt16</span></span>](xref:System.UInt16) | <span data-ttu-id="9170d-414">Entier 16 bits non signé</span><span class="sxs-lookup"><span data-stu-id="9170d-414">16-bit unsigned integer</span></span> | [<span data-ttu-id="9170d-415">Int32</span><span class="sxs-lookup"><span data-stu-id="9170d-415">Int32</span></span>](xref:System.Int32)
[<span data-ttu-id="9170d-416">UInt32</span><span class="sxs-lookup"><span data-stu-id="9170d-416">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="9170d-417">Entier non signé 32 bits</span><span class="sxs-lookup"><span data-stu-id="9170d-417">32-bit unsigned integer</span></span> | [<span data-ttu-id="9170d-418">Int64</span><span class="sxs-lookup"><span data-stu-id="9170d-418">Int64</span></span>](xref:System.Int64)
[<span data-ttu-id="9170d-419">UInt64</span><span class="sxs-lookup"><span data-stu-id="9170d-419">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="9170d-420">Entier non signé 64 bits</span><span class="sxs-lookup"><span data-stu-id="9170d-420">64-bit unsigned integer</span></span> | <span data-ttu-id="9170d-421">[Int64](xref:System.Int64) (peut déborder), [BigInteger](xref:System.Numerics.BigInteger) ou [Double](xref:System.Double)</span><span class="sxs-lookup"><span data-stu-id="9170d-421">[Int64](xref:System.Int64) (may overflow), [BigInteger](xref:System.Numerics.BigInteger), or [Double](xref:System.Double)</span></span>
[<span data-ttu-id="9170d-422">UIntPtr</span><span class="sxs-lookup"><span data-stu-id="9170d-422">UIntPtr</span></span>](xref:System.UIntPtr) | <span data-ttu-id="9170d-423">Pointeur ou handle non signé</span><span class="sxs-lookup"><span data-stu-id="9170d-423">Unsigned pointer or handle</span></span> | [<span data-ttu-id="9170d-424">IntPtr</span><span class="sxs-lookup"><span data-stu-id="9170d-424">IntPtr</span></span>](xref:System.IntPtr)

<span data-ttu-id="9170d-425">La bibliothèque de classes du .NET Framework ou toute autre bibliothèque de classes peut inclure d'autres types non conformes à CLS. Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9170d-425">The .NET Framework Class Library or any other class library may include other types that aren't CLS-compliant; for example:</span></span>

* <span data-ttu-id="9170d-426">Types de valeurs encadrés.</span><span class="sxs-lookup"><span data-stu-id="9170d-426">Boxed value types.</span></span> <span data-ttu-id="9170d-427">L'exemple C# suivant crée une classe qui a une propriété publique de type `int*` nommée `Value`.</span><span class="sxs-lookup"><span data-stu-id="9170d-427">The following C# example creates a class that has a public property of type `int*` named `Value`.</span></span> <span data-ttu-id="9170d-428">Comme `int*` est un type de valeur encadré, le compilateur le signale comme non conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-428">Because an `int*` is a boxed value type, the compiler flags it as non-CLS-compliant.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public unsafe class TestClass
{
   private int* val;

   public TestClass(int number)
   {
      val = (int*) number;
   }

   public int* Value {
      get { return val; }
   }
}
// The compiler generates the following output when compiling this example:
//        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
```

* <span data-ttu-id="9170d-429">Références typées, qui sont des constructions spéciales qui contiennent une référence à un objet et une référence à un type.</span><span class="sxs-lookup"><span data-stu-id="9170d-429">Typed references, which are special constructs that contain a reference to an object and a reference to a type.</span></span>

<span data-ttu-id="9170d-430">Si un type n’est pas conforme CLS, vous devez lui appliquer l’attribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) avec un paramètre *isCompliant* dont la valeur est `false`.</span><span class="sxs-lookup"><span data-stu-id="9170d-430">If a type is not CLS-compliant, you should apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute with an *isCompliant* parameter with a value of `false` to it.</span></span> <span data-ttu-id="9170d-431">Pour plus d’informations, consultez la section [Attribut CLSCompliantAttribute](#the-clscompliantattribute-attribute).</span><span class="sxs-lookup"><span data-stu-id="9170d-431">For more information, see the [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute) section.</span></span>

<span data-ttu-id="9170d-432">L'exemple suivant illustre le problème de conformité CLS dans une signature de méthode et dans une instanciation de type générique.</span><span class="sxs-lookup"><span data-stu-id="9170d-432">The following example illustrates the problem of CLS compliance in a method signature and in generic type instantiation.</span></span> <span data-ttu-id="9170d-433">Il définit une classe `InvoiceItem` avec une propriété de type [UInt32](xref:System.UInt32), une propriété de type [Nullable(Of UInt32)](xref:System.Nullable%601) et un constructeur avec des paramètres de type `UInt32` et `Nullable(Of UInt32)`.</span><span class="sxs-lookup"><span data-stu-id="9170d-433">It defines an `InvoiceItem` class with a property of type [UInt32](xref:System.UInt32), a property of type [Nullable(Of UInt32)](xref:System.Nullable%601), and a constructor with parameters of type `UInt32` and `Nullable(Of UInt32)`.</span></span> <span data-ttu-id="9170d-434">Vous obtenez quatre avertissements du compilateur lorsque vous essayez de compiler cet exemple.</span><span class="sxs-lookup"><span data-stu-id="9170d-434">You get four compiler warnings when you try to compile this example.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As UInteger
      Get
         Return invId
      End Get
      Set
         invId = value
      End Set
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'
'       Public Property InvoiceId As UInteger
```

<span data-ttu-id="9170d-435">Pour supprimer les avertissements du compilateur, remplacez les types non conforme à CLS de l'interface publique `InvoiceItem` par des types conformes :</span><span class="sxs-lookup"><span data-stu-id="9170d-435">To eliminate the compiler warnings, replace the non-CLS-compliant types in the `InvoiceItem` public interface with compliant types:</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set {
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As Integer
      Get
         Return CInt(invId)
      End Get
      Set
         invId = CUInt(value)
      End Set
   End Property
End Class
```

<span data-ttu-id="9170d-436">Outre les types spécifiques répertoriés, certaines catégories de types ne sont pas conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-436">In addition to the specific types listed, some categories of types are not CLS compliant.</span></span> <span data-ttu-id="9170d-437">Celles-ci incluent les types de pointeurs non managés et les types de pointeurs de fonctions.</span><span class="sxs-lookup"><span data-stu-id="9170d-437">These include unmanaged pointer types and function pointer types.</span></span> <span data-ttu-id="9170d-438">L'exemple suivant génère un avertissement du compilateur, car il utilise un pointeur vers un entier pour créer un tableau d'entiers.</span><span class="sxs-lookup"><span data-stu-id="9170d-438">The following example generates a compiler warning because it uses a pointer to an integer to create an array of integers.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

<span data-ttu-id="9170d-439">Pour les classes abstraites conformes CLS (autrement dit, les classes marquées comme `abstract` en C#), tous les membres de la classe doivent également être conformes CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-439">For CLS-compliant abstract classes (that is, classes marked as `abstract` in C#), all members of the class must also be CLS-compliant.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="9170d-440">Conventions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="9170d-440">Naming conventions</span></span>

<span data-ttu-id="9170d-441">Étant donné que certains langages de programmation ne respectent pas la casse, les identificateurs (tels que les noms d'espaces de noms, de types et de membres) doivent se différencier par autre chose que la casse.</span><span class="sxs-lookup"><span data-stu-id="9170d-441">Because some programming languages are case-insensitive, identifiers (such as the names of namespaces, types, and members) must differ by more than case.</span></span> <span data-ttu-id="9170d-442">Deux identificateurs sont considérés comme équivalents si leurs mappages en minuscules sont identiques.</span><span class="sxs-lookup"><span data-stu-id="9170d-442">Two identifiers are considered equivalent if their lowercase mappings are the same.</span></span> <span data-ttu-id="9170d-443">L'exemple C# suivant définit deux classes publiques : `Person` et `person`.</span><span class="sxs-lookup"><span data-stu-id="9170d-443">The following C# example defines two public classes, `Person` and `person`.</span></span> <span data-ttu-id="9170d-444">Étant donné qu'elles ne diffèrent que par leur casse, le compilateur C# les signale comme étant non conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-444">Because they differ only by case, the C# compiler flags them as not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

<span data-ttu-id="9170d-445">Les identificateurs de langage de programmation, tels que les noms d’espaces de noms, de types et de membres, doivent être conformes à la [norme Unicode](https://unicode.org/reports/tr15/).</span><span class="sxs-lookup"><span data-stu-id="9170d-445">Programming language identifiers, such as the names of namespaces, types, and members, must conform to the [Unicode Standard](https://unicode.org/reports/tr15/).</span></span> <span data-ttu-id="9170d-446">Cela signifie que :</span><span class="sxs-lookup"><span data-stu-id="9170d-446">This means that:</span></span>

* <span data-ttu-id="9170d-447">Le premier caractère d'un identificateur peut être une lettre majuscule, une lettre minuscule, une initiale majuscule, une lettre de modificateur, une autre lettre ou un nombre sous forme de lettre, Unicode.</span><span class="sxs-lookup"><span data-stu-id="9170d-447">The first character of an identifier can be any Unicode uppercase letter, lowercase letter, title case letter, modifier letter, other letter, or letter number.</span></span> <span data-ttu-id="9170d-448">Pour plus d’informations sur les catégories de caractères Unicode, consultez l’énumération [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory).</span><span class="sxs-lookup"><span data-stu-id="9170d-448">For information on Unicode character categories, see the [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) enumeration.</span></span>

* <span data-ttu-id="9170d-449">Les caractères suivants peuvent provenir de n’importe quelle catégorie comme premier caractère, et peuvent également inclure des marques de non-espacement, des marques de l’espacement, des nombres décimaux, des signes de ponctuation de connecteur et des codes de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="9170d-449">Subsequent characters can be from any of the categories as the first character, and can also include non-spacing marks, spacing combining marks, decimal numbers, connector punctuation, and formatting codes.</span></span>

<span data-ttu-id="9170d-450">Avant de comparer les identificateurs, vous devez éliminer par filtrage les codes de mise en forme et convertir les identificateurs au formulaire de normalisation Unicode C, car un caractère unique peut être représenté par plusieurs unités de code encodées en UTF-16.</span><span class="sxs-lookup"><span data-stu-id="9170d-450">Before you compare identifiers, you should filter out formatting codes and convert the identifiers to Unicode Normalization Form C, because a single character can be represented by multiple UTF-16-encoded code units.</span></span> <span data-ttu-id="9170d-451">Les séquences de caractères qui produisent les mêmes unités de code dans un formulaire de normalisation Unicode C ne sont pas conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-451">Character sequences that produce the same code units in Unicode Normalization Form C are not CLS-compliant.</span></span> <span data-ttu-id="9170d-452">L'exemple suivant définit une propriété nommée `Å`, qui est constituée du caractère SYMBOLE ANGSTRÖM (U+212B), et une deuxième propriété nommée `Å`, qui est constituée du caractère LETTRE MAJUSCULE LATINE A AVEC DIACRITIQUE ROND EN CHEF (U+00C5).</span><span class="sxs-lookup"><span data-stu-id="9170d-452">The following example defines a property named `Å`, which consists of the character ANGSTROM SIGN (U+212B), and a second property named `Å`, which consists of the character LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5).</span></span> <span data-ttu-id="9170d-453">Le compilateur C# signale le code source comme non conforme CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-453">The C# compiler flags the source code as non-CLS-compliant.</span></span>

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set
          a1 = value
       End Set
   End Property

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'
'       Public Property Å As Double
'                       ~
```

<span data-ttu-id="9170d-454">Les noms de membres dans une portée donnée (tels que les espaces de noms dans un assembly, les types dans un espace de noms ou les membres dans un type) doivent être uniques, à l'exception des noms résolus par la surcharge.</span><span class="sxs-lookup"><span data-stu-id="9170d-454">Member names within a particular scope (such as the namespaces within an assembly, the types within a namespace, or the members within a type) must be unique except for names that are resolved through overloading.</span></span> <span data-ttu-id="9170d-455">Cette spécification est plus stricte que celle du système de type commun, qui autorise plusieurs membres d'une portée à avoir des noms identiques tant qu'il s'agit de types de membres différents (par exemple, l'un est une méthode et l'autre est un champ).</span><span class="sxs-lookup"><span data-stu-id="9170d-455">This requirement is more stringent than that of the common type system, which allows multiple members within a scope to have identical names as long as they are different kinds of members (for example, one is a method and one is a field).</span></span> <span data-ttu-id="9170d-456">En particulier, pour les membres de types :</span><span class="sxs-lookup"><span data-stu-id="9170d-456">In particular, for type members:</span></span>

* <span data-ttu-id="9170d-457">Les champs et les types imbriqués se distinguent par le nom uniquement.</span><span class="sxs-lookup"><span data-stu-id="9170d-457">Fields and nested types are distinguished by name alone.</span></span>

* <span data-ttu-id="9170d-458">Les méthodes, les propriétés et les événements qui portent le même nom doivent différer par autre chose que le type de retour.</span><span class="sxs-lookup"><span data-stu-id="9170d-458">Methods, properties, and events that have the same name must differ by more than just return type.</span></span>

<span data-ttu-id="9170d-459">L'exemple suivant illustre la spécification selon laquelle les noms de membres doivent être uniques dans leur portée.</span><span class="sxs-lookup"><span data-stu-id="9170d-459">The following example illustrates the requirement that member names must be unique within their scope.</span></span> <span data-ttu-id="9170d-460">Il définit une classe nommée `Converter` qui inclut quatre membres nommés `Conversion`.</span><span class="sxs-lookup"><span data-stu-id="9170d-460">It defines a class named `Converter` that includes four members named `Conversion`.</span></span> <span data-ttu-id="9170d-461">Trois sont des méthodes, le dernier est une propriété.</span><span class="sxs-lookup"><span data-stu-id="9170d-461">Three are methods, and one is a property.</span></span> <span data-ttu-id="9170d-462">La méthode qui inclut un paramètre `Int64` est nommée de manière unique, contrairement aux deux méthodes contenant un paramètre `Int32`, car la valeur de retour n'est pas considérée comme faisant partie de la signature d'un membre.</span><span class="sxs-lookup"><span data-stu-id="9170d-462">The method that includes an `Int64` parameter is uniquely named, but the two methods with an `Int32` parameter are not, because return value is not considered a part of a member's signature.</span></span> <span data-ttu-id="9170d-463">La propriété `Conversion` enfreint également cette spécification, car les propriétés ne peuvent pas avoir le même nom que les méthodes surchargées.</span><span class="sxs-lookup"><span data-stu-id="9170d-463">The `Conversion` property also violates this requirement, because properties cannot have the same name as overloaded methods.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }
}
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get
   End Property
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double'
'                    and 'Public Function Conversion(number As Integer) As Single' cannot
'                    overload each other because they differ only by return types.
'
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function
'                     Conversion(number As Integer) As Single' in this class.
'
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

<span data-ttu-id="9170d-464">Les langages individuels incluent des mots clés uniques de sorte que les langages qui ciblent le Common Langage Runtime doivent également fournir un mécanisme de référencement des identificateurs (tels que les noms de types) qui coïncident avec les mots clés.</span><span class="sxs-lookup"><span data-stu-id="9170d-464">Individual languages include unique keywords, so languages that target the common language runtime must also provide some mechanism for referencing identifiers (such as type names) that coincide with keywords.</span></span> <span data-ttu-id="9170d-465">Par exemple, `case` est un mot clé en C# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9170d-465">For example, `case` is a keyword in both C# and Visual Basic.</span></span> <span data-ttu-id="9170d-466">Toutefois, l'exemple Visual Basic suivant peut supprimer l'ambiguïté entre une classe nommée `case` et le mot clé `case` en utilisant des accolades ouvrantes et fermantes.</span><span class="sxs-lookup"><span data-stu-id="9170d-466">However, the following Visual Basic example is able to disambiguate a class named `case` from the `case` keyword by using opening and closing braces.</span></span> <span data-ttu-id="9170d-467">Sans cela, l'exemple générerait le message d'erreur : « Mot clé non valide en tant qu'identificateur » et échouerait lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="9170d-467">Otherwise, the example would produce the error message, "Keyword is not valid as an identifier," and fail to compile.</span></span>

```vb
Public Class [case]
   Private _id As Guid
   Private name As String

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name
   End Sub

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

<span data-ttu-id="9170d-468">L’exemple C# suivant peut instancier la classe `case` en utilisant le symbole @ pour lever l’ambiguïté de l’identificateur par rapport au mot clé de langage.</span><span class="sxs-lookup"><span data-stu-id="9170d-468">The following C# example is able to instantiate the `case` class by using the @ symbol to disambiguate the identifier from the language keyword.</span></span> <span data-ttu-id="9170d-469">Sans cela, le compilateur C# afficherait deux messages d'erreur : « Type attendu » et « Terme d'expression non valide 'case' ».</span><span class="sxs-lookup"><span data-stu-id="9170d-469">Without it, the C# compiler would display two error messages, "Type expected" and "Invalid expression term 'case'."</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a><span data-ttu-id="9170d-470">Conversion de type</span><span class="sxs-lookup"><span data-stu-id="9170d-470">Type conversion</span></span>

<span data-ttu-id="9170d-471">La spécification CLS (Common Language Specification) définit deux opérateurs de conversion :</span><span class="sxs-lookup"><span data-stu-id="9170d-471">The Common Language Specification defines two conversion operators:</span></span>

* <span data-ttu-id="9170d-472">`op_Implicit`, qui est utilisé pour les conversions étendues qui n'entraînent pas la perte de données ou de précision.</span><span class="sxs-lookup"><span data-stu-id="9170d-472">`op_Implicit`, which is used for widening conversions that do not result in loss of data or precision.</span></span> <span data-ttu-id="9170d-473">Par exemple, la structure [Decimal](xref:System.Decimal) inclut un opérateur `op_Implicit` surchargé pour convertir les valeurs de types intégraux et les valeurs [Char](xref:System.Char) en valeurs `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9170d-473">For example, the [Decimal](xref:System.Decimal) structure includes an overloaded `op_Implicit` operator to convert values of integral types and [Char](xref:System.Char) values to `Decimal` values.</span></span>

* <span data-ttu-id="9170d-474">`op_Explicit`, qui est utilisé pour les conversions restrictives qui peuvent entraîner la perte d'amplitude (une valeur est convertie en une valeur qui entraîne une plus petite plage) ou de précision.</span><span class="sxs-lookup"><span data-stu-id="9170d-474">`op_Explicit`, which is used for narrowing conversions that can result in loss of magnitude (a value is converted to a value that has a smaller range) or precision.</span></span> <span data-ttu-id="9170d-475">Par exemple, la structure `Decimal` inclut un opérateur `op_Explicit` surchargé pour convertir les valeurs [Double](xref:System.Double) et [Single](xref:System.Single) en `Decimal`, et convertir les valeurs `Decimal` en valeurs intégrales, `Double`, `Single` et `Char`.</span><span class="sxs-lookup"><span data-stu-id="9170d-475">For example, the `Decimal` structure includes an overloaded `op_Explicit` operator to convert [Double](xref:System.Double) and [Single](xref:System.Single) values to `Decimal` and to convert `Decimal` values to integral values, `Double`, `Single`, and `Char`.</span></span>

<span data-ttu-id="9170d-476">Toutefois, tous les langages ne prennent pas en charge la surcharge d'opérateur ou la définition d'opérateurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="9170d-476">However, not all languages support operator overloading or the definition of custom operators.</span></span> <span data-ttu-id="9170d-477">Si vous décidez d'implémenter ces opérateurs de conversion, vous devez également fournir une autre façon d'effectuer la conversion.</span><span class="sxs-lookup"><span data-stu-id="9170d-477">If you choose to implement these conversion operators, you should also provide an alternate way to perform the conversion.</span></span> <span data-ttu-id="9170d-478">Nous vous recommandons de fournir les méthodes `From`Xxx et `To`Xxx.</span><span class="sxs-lookup"><span data-stu-id="9170d-478">We recommend that you provide `From`Xxx and `To`Xxx methods.</span></span>

<span data-ttu-id="9170d-479">L'exemple suivant définit les conversions implicites et explicites conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-479">The following example defines CLS-compliant implicit and explicit conversions.</span></span> <span data-ttu-id="9170d-480">Il crée une `UDouble` classe qui représente un nombre à virgule flottante double précision signé.</span><span class="sxs-lookup"><span data-stu-id="9170d-480">It creates a `UDouble` class that represents a signed double-precision, floating-point number.</span></span> <span data-ttu-id="9170d-481">Il s'applique aux conversions implicites de `UDouble` à `Double` et aux conversions explicites de `UDouble` à `Single`, de `Double` à `UDouble` et de `Single` à `UDouble`.</span><span class="sxs-lookup"><span data-stu-id="9170d-481">It provides for implicit conversions from `UDouble` to `Double` and for explicit conversions from `UDouble` to `Single`, `Double` to `UDouble`, and `Single` to `UDouble`.</span></span> <span data-ttu-id="9170d-482">Il définit également une méthode `ToDouble` comme une alternative à l'opérateur de conversion implicite et les méthodes `ToSingle`, `FromDouble` et `FromSingle` comme alternatives aux opérateurs de conversion explicite.</span><span class="sxs-lookup"><span data-stu-id="9170d-482">It also defines a `ToDouble` method as an alternative to the implicit conversion operator and the `ToSingle`, `FromDouble`, and `FromSingle` methods as alternatives to the explicit conversion operators.</span></span>

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue)
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function
End Structure
```

### <a name="arrays"></a><span data-ttu-id="9170d-483">Tableaux</span><span class="sxs-lookup"><span data-stu-id="9170d-483">Arrays</span></span>

<span data-ttu-id="9170d-484">Les tableaux conformes à CLS respectent les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="9170d-484">CLS-compliant arrays conform to the following rules:</span></span>

* <span data-ttu-id="9170d-485">Toutes les dimensions d'un tableau doivent avoir une limite inférieure égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="9170d-485">All dimensions of an array must have a lower bound of zero.</span></span> <span data-ttu-id="9170d-486">L'exemple suivant crée un tableau non conforme à CLS avec une limite inférieure égale à un.</span><span class="sxs-lookup"><span data-stu-id="9170d-486">The following example creates a non-CLS-compliant array with a lower bound of one.</span></span> <span data-ttu-id="9170d-487">En dépit de la présence de l’attribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) , le compilateur ne détecte pas que le tableau retourné par la `Numbers.GetTenPrimes` méthode n’est pas conforme CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-487">Despite the presence of the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute, the compiler does not detect that the array returned by the `Numbers.GetTenPrimes` method is not CLS-compliant.</span></span>

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6);
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr;
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* <span data-ttu-id="9170d-488">Tous les éléments du tableau doivent se composer de types conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-488">All array elements must consist of CLS-compliant types.</span></span> <span data-ttu-id="9170d-489">L'exemple suivant définit deux méthodes qui retournent des tableaux non conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-489">The following example defines two methods that return non-CLS-compliant arrays.</span></span> <span data-ttu-id="9170d-490">La première retourne un tableau de valeurs [UInt32](xref:System.UInt32).</span><span class="sxs-lookup"><span data-stu-id="9170d-490">The first returns an array of [UInt32](xref:System.UInt32) values.</span></span> <span data-ttu-id="9170d-491">La deuxième retourne un tableau [Object](xref:System.Object) qui inclut les valeurs [Int32](xref:System.Int32) et `UInt32`.</span><span class="sxs-lookup"><span data-stu-id="9170d-491">The second returns an [Object](xref:System.Object) array that includes [Int32](xref:System.Int32) and `UInt32` values.</span></span> <span data-ttu-id="9170d-492">Bien que le compilateur identifie le premier tableau comme non conforme en raison de son type `UInt32`, il ne parvient pas à reconnaître que le second tableau inclut des éléments non conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-492">Although the compiler identifies the first array as non-compliant because of its `UInt32` type, it fails to recognize that the second array includes non-CLS-compliant elements.</span></span>

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```

* <span data-ttu-id="9170d-493">La résolution de surcharge pour les méthodes qui ont des paramètres de tableau repose sur le fait qu’il s’agit de tableaux et sur leur type d’élément.</span><span class="sxs-lookup"><span data-stu-id="9170d-493">Overload resolution for methods that have array parameters is based on the fact that they are arrays and on their element type.</span></span> <span data-ttu-id="9170d-494">C'est pourquoi la définition suivante d'une méthode `GetSquares` surchargée est conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-494">For this reason, the following definition of an overloaded `GetSquares` method is CLS-compliant.</span></span>

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]);
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr];

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr)))
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr)
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a><span data-ttu-id="9170d-495">Interfaces</span><span class="sxs-lookup"><span data-stu-id="9170d-495">Interfaces</span></span>

<span data-ttu-id="9170d-496">Les interfaces conformes à CLS peuvent définir des propriétés, des événements et des méthodes virtuelles (méthodes sans implémentation).</span><span class="sxs-lookup"><span data-stu-id="9170d-496">CLS-compliant interfaces can define properties, events, and virtual methods (methods with no implementation).</span></span> <span data-ttu-id="9170d-497">Une interface conforme à CLS ne peut avoir aucune des caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="9170d-497">A CLS-compliant interface cannot have any of the following:</span></span>

* <span data-ttu-id="9170d-498">Méthodes statiques ou champs statiques.</span><span class="sxs-lookup"><span data-stu-id="9170d-498">Static methods or static fields.</span></span> <span data-ttu-id="9170d-499">Le compilateur C# génère des erreurs de compilation si un membre statique est défini dans une interface.</span><span class="sxs-lookup"><span data-stu-id="9170d-499">The C# compiler generates compiler errors if you define a static member in an interface.</span></span>

* <span data-ttu-id="9170d-500">Champs.</span><span class="sxs-lookup"><span data-stu-id="9170d-500">Fields.</span></span> <span data-ttu-id="9170d-501">Le compilateur C# génère des erreurs de compilation si un champ est défini dans une interface.</span><span class="sxs-lookup"><span data-stu-id="9170d-501">The C# a compiler generates compiler errors if you define a field in an interface.</span></span>

* <span data-ttu-id="9170d-502">Méthodes qui ne sont pas conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-502">Methods that are not CLS-compliant.</span></span> <span data-ttu-id="9170d-503">Par exemple, la définition d'interface suivante inclut une méthode, `INumber.GetUnsigned`, qui est marquée comme non conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-503">For example, the following interface definition includes a method, `INumber.GetUnsigned`, that is marked as non-CLS-compliant.</span></span> <span data-ttu-id="9170d-504">Cet exemple génère un avertissement du compilateur.</span><span class="sxs-lookup"><span data-stu-id="9170d-504">This example generates a compiler warning.</span></span>

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a
    '    CLS-compliant interface.
    '
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  <span data-ttu-id="9170d-505">En raison de cette règle, pour implémenter des membres non conformes à CLS, il n'est pas nécessaire d'utiliser des types conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-505">Because of this rule, CLS-compliant types are not required to implement non-CLS-compliant members.</span></span> <span data-ttu-id="9170d-506">Si une infrastructure conforme à CLS expose une classe qui implémente une interface non conforme à CLS, elle doit également fournir des implémentations concrètes de tous les membres non conformes.</span><span class="sxs-lookup"><span data-stu-id="9170d-506">If a CLS-compliant framework does expose a class that implements a non-CLS compliant interface, it should also provide concrete implementations of all non-CLS-compliant members.</span></span>

<span data-ttu-id="9170d-507">Les compilateurs de langages conformes à CLS doivent également permettre à une classe de fournir des implémentations séparées des membres qui ont les mêmes nom et signature dans plusieurs interfaces.</span><span class="sxs-lookup"><span data-stu-id="9170d-507">CLS-compliant language compilers must also allow a class to provide separate implementations of members that have the same name and signature in multiple interfaces.</span></span> <span data-ttu-id="9170d-508">C# prend en charge des implémentations d’interface explicites pour fournir des implémentations différentes de méthodes portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="9170d-508">C# supports explicit interface implementations to provide different implementations of identically named methods.</span></span> <span data-ttu-id="9170d-509">L'exemple suivant illustre ce scénario en définissant une classe `Temperature` qui implémente les interfaces `ICelsius` et `IFahrenheit` en tant qu'implémentations d'interface explicites.</span><span class="sxs-lookup"><span data-stu-id="9170d-509">The following example illustrates this scenario by defining a `Temperature` class that implements the `ICelsius` and `IFahrenheit` interfaces as explicit interface implementations.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   }

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   }
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a><span data-ttu-id="9170d-510">Énumérations</span><span class="sxs-lookup"><span data-stu-id="9170d-510">Enumerations</span></span>

<span data-ttu-id="9170d-511">Les énumérations conformes à CLS doivent suivre ces règles :</span><span class="sxs-lookup"><span data-stu-id="9170d-511">CLS-compliant enumerations must follow these rules:</span></span>

* <span data-ttu-id="9170d-512">Le type sous-jacent de l’énumération doit être un entier conforme CLS intrinsèque ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32) ou [Int64](xref:System.Int64)).</span><span class="sxs-lookup"><span data-stu-id="9170d-512">The underlying type of the enumeration must be an intrinsic CLS-compliant integer ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), or [Int64](xref:System.Int64)).</span></span> <span data-ttu-id="9170d-513">Par exemple, le code suivant tente de définir une énumération dont le type sous-jacent est [UInt32](xref:System.UInt32) et génère un avertissement du compilateur.</span><span class="sxs-lookup"><span data-stu-id="9170d-513">For example, the following code tries to define an enumeration whose underlying type is [UInt32](xref:System.UInt32) and generates a compiler warning.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint {
        Unspecified = 0,
        XSmall = 1,
        Small = 2,
        Medium = 3,
        Large = 4,
        XLarge = 5
    };

    public class Clothing
    {
        public string Name;
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* <span data-ttu-id="9170d-514">Un type d'énumération doit avoir un champ d'instance unique nommé `Value__` qui est marqué avec l'attribut `FieldAttributes.RTSpecialName`.</span><span class="sxs-lookup"><span data-stu-id="9170d-514">An enumeration type must have a single instance field named `Value__` that is marked with the `FieldAttributes.RTSpecialName` attribute.</span></span> <span data-ttu-id="9170d-515">Cela vous permet de référencer implicitement la valeur du champ.</span><span class="sxs-lookup"><span data-stu-id="9170d-515">This enables you to reference the field value implicitly.</span></span>

* <span data-ttu-id="9170d-516">Une énumération inclut les champs statiques littéraux du même type que l'énumération elle-même.</span><span class="sxs-lookup"><span data-stu-id="9170d-516">An enumeration includes literal static fields whose types match the type of the enumeration itself.</span></span> <span data-ttu-id="9170d-517">Par exemple, si vous définissez une énumération `State` avec les valeurs `State.On` et `State.Off`, `State.On` et `State.Off` sont les deux champs statiques littéraux dont le type est `State`.</span><span class="sxs-lookup"><span data-stu-id="9170d-517">For example, if you define a `State` enumeration with values of `State.On` and `State.Off`, `State.On` and `State.Off` are both literal static fields whose type is `State`.</span></span>

* <span data-ttu-id="9170d-518">Il existe deux types d'énumérations :</span><span class="sxs-lookup"><span data-stu-id="9170d-518">There are two kinds of enumerations:</span></span>

  * <span data-ttu-id="9170d-519">Une énumération qui représente un jeu de valeurs entières nommées qui s'excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="9170d-519">An enumeration that represents a set of mutually exclusive, named integer values.</span></span> <span data-ttu-id="9170d-520">Ce type d’énumération est indiqué par l’absence de l’attribut personnalisé [System.FlagsAttribute](xref:System.FlagsAttribute).</span><span class="sxs-lookup"><span data-stu-id="9170d-520">This type of enumeration is indicated by the absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

  * <span data-ttu-id="9170d-521">Une énumération qui représente un jeu d'indicateurs binaires qui peuvent être combinés pour générer une valeur sans nom.</span><span class="sxs-lookup"><span data-stu-id="9170d-521">An enumeration that represents a set of bit flags that can combine to generate an unnamed value.</span></span> <span data-ttu-id="9170d-522">Ce type d’énumération est indiqué par la présence de l’attribut personnalisé [System.FlagsAttribute](xref:System.FlagsAttribute).</span><span class="sxs-lookup"><span data-stu-id="9170d-522">This type of enumeration is indicated by the presence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

<span data-ttu-id="9170d-523">Pour plus d’informations, consultez la documentation de la structure [Enum](xref:System.Enum).</span><span class="sxs-lookup"><span data-stu-id="9170d-523">For more information, see the documentation for the [Enum](xref:System.Enum) structure.</span></span>

* <span data-ttu-id="9170d-524">La valeur d'une énumération ne se limite pas à la plage de ses valeurs spécifiées.</span><span class="sxs-lookup"><span data-stu-id="9170d-524">The value of an enumeration is not limited to the range of its specified values.</span></span> <span data-ttu-id="9170d-525">En d'autres termes, la plage de valeurs d'une énumération est la plage de sa valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="9170d-525">In other words, the range of values in an enumeration is the range of its underlying value.</span></span> <span data-ttu-id="9170d-526">Vous pouvez utiliser la méthode `Enum.IsDefined` pour déterminer si une valeur spécifiée est membre d'une énumération.</span><span class="sxs-lookup"><span data-stu-id="9170d-526">You can use the `Enum.IsDefined` method to determine whether a specified value is a member of an enumeration.</span></span>

### <a name="type-members-in-general"></a><span data-ttu-id="9170d-527">Membres de types en général</span><span class="sxs-lookup"><span data-stu-id="9170d-527">Type members in general</span></span>

<span data-ttu-id="9170d-528">La spécification CLS (Common Language Specification) nécessite que tous les champs et toutes les méthodes soient accessibles en tant que membres d'une classe particulière.</span><span class="sxs-lookup"><span data-stu-id="9170d-528">The Common Language Specification requires all fields and methods to be accessed as members of a particular class.</span></span> <span data-ttu-id="9170d-529">Par conséquent, les méthodes et les champs statiques globaux (autrement dit, les méthodes ou les champs statiques définis en dehors d'un type) ne sont pas conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-529">Therefore, global static fields and methods (that is, static fields or methods that are defined apart from a type) are not CLS-compliant.</span></span> <span data-ttu-id="9170d-530">Si vous essayez d’inclure un champ global ou une méthode globale dans votre code source, le compilateur C# génère une erreur de compilateur.</span><span class="sxs-lookup"><span data-stu-id="9170d-530">If you try to include a global field or method in your source code, the C# compiler generates a compiler error.</span></span>

<span data-ttu-id="9170d-531">La spécification CLS (Common Language Specification) prend uniquement en charge la convention d'appel managée standard.</span><span class="sxs-lookup"><span data-stu-id="9170d-531">The Common Language Specification supports only the standard managed calling convention.</span></span> <span data-ttu-id="9170d-532">Elle ne prend pas en charge les conventions d'appel non managées ni les méthodes avec des listes d'arguments variables marquées avec le mot clé `varargs`.</span><span class="sxs-lookup"><span data-stu-id="9170d-532">It doesn't support unmanaged calling conventions and methods with variable argument lists marked with the `varargs` keyword.</span></span> <span data-ttu-id="9170d-533">Pour les listes d’arguments variables compatibles avec la convention d’appel managée standard, utilisez l’attribut [ParamArrayAttribute](xref:System.ParamArrayAttribute) ou l’implémentation de chaque langage, comme le mot clé `params` en C# et le mot clé `ParamArray` en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9170d-533">For variable argument lists that are compatible with the standard managed calling convention, use the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute or the individual language's implementation, such as the `params` keyword in C# and the `ParamArray` keyword in Visual Basic.</span></span>

### <a name="member-accessibility"></a><span data-ttu-id="9170d-534">Accessibilité des membres</span><span class="sxs-lookup"><span data-stu-id="9170d-534">Member accessibility</span></span>

<span data-ttu-id="9170d-535">Le remplacement d'un membre hérité ne peut pas modifier l'accessibilité de ce membre.</span><span class="sxs-lookup"><span data-stu-id="9170d-535">Overriding an inherited member cannot change the accessibility of that member.</span></span> <span data-ttu-id="9170d-536">Par exemple, une méthode publique dans une classe de base ne peut pas être remplacée par une méthode privée dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9170d-536">For example, a public method in a base class cannot be overridden by a private method in a derived class.</span></span> <span data-ttu-id="9170d-537">Il existe une exception : un membre `protected internal` (en C#) ou `Protected Friend` (en Visual Basic) dans un assembly qui est remplacé par un type dans un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="9170d-537">There is one exception: a `protected internal` (in C#) or `Protected Friend` (in Visual Basic) member in one assembly that is overridden by a type in a different assembly.</span></span>  <span data-ttu-id="9170d-538">Dans ce cas, l'accessibilité du remplacement est `Protected`.</span><span class="sxs-lookup"><span data-stu-id="9170d-538">In that case, the accessibility of the override is `Protected`.</span></span>

<span data-ttu-id="9170d-539">L’exemple suivant illustre l’erreur générée quand l’attribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) a la valeur `true`, et que `Person`, qui est une classe dérivée de `Animal`, tente de remplacer l’accessibilité publique de la propriété `Species` par une accessibilité privée.</span><span class="sxs-lookup"><span data-stu-id="9170d-539">The following example illustrates the error that is generated when the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is set to `true`, and `Person`, which is a class derived from `Animal`, tries to change the accessibility of the `Species` property from public to private.</span></span> <span data-ttu-id="9170d-540">L'exemple se compile correctement si son accessibilité devient publique.</span><span class="sxs-lookup"><span data-stu-id="9170d-540">The example compiles successfully if its accessibility is changed to public.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species
   {
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;
   }
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species
   {
      get { return base.Species; }
   }

   public override string ToString()
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species
   End Function
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
'
'         Private Overrides ReadOnly Property Species As String
```

<span data-ttu-id="9170d-541">Les types de la signature d'un membre doivent être accessibles chaque fois que ce membre est accessible.</span><span class="sxs-lookup"><span data-stu-id="9170d-541">Types in the signature of a member must be accessible whenever that member is accessible.</span></span> <span data-ttu-id="9170d-542">Par exemple, cela signifie qu’un membre public ne peut pas inclure un paramètre dont le type est privé, protégé ou interne.</span><span class="sxs-lookup"><span data-stu-id="9170d-542">For example, this means that a public member cannot include a parameter whose type is private, protected, or internal.</span></span> <span data-ttu-id="9170d-543">L'exemple suivant illustre l'erreur de compilateur obtenue lorsqu'un constructeur de classe `StringWrapper` expose une valeur d'énumération `StringOperationType` interne qui détermine comment une valeur de chaîne doit être encapsulée.</span><span class="sxs-lookup"><span data-stu-id="9170d-543">The following example illustrates the compiler error that results when a `StringWrapper` class constructor exposes an internal `StringOperationType` enumeration value that determines how a string value should be wrapped.</span></span>

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {
      if (type == StringOperationType.Normal) {
         useSB = false;
      }
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder()
         useSB = True
      End If
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a><span data-ttu-id="9170d-544">Types et membres génériques</span><span class="sxs-lookup"><span data-stu-id="9170d-544">Generic types and members</span></span>

<span data-ttu-id="9170d-545">Les types imbriqués ont toujours au moins autant de paramètres génériques que leur type englobant.</span><span class="sxs-lookup"><span data-stu-id="9170d-545">Nested types always have at least as many generic parameters as their enclosing type.</span></span> <span data-ttu-id="9170d-546">Ceux-ci correspondent par position aux paramètres génériques du type englobant.</span><span class="sxs-lookup"><span data-stu-id="9170d-546">These correspond by position to the generic parameters in the enclosing type.</span></span> <span data-ttu-id="9170d-547">Le type générique peut également inclure de nouveaux paramètres génériques.</span><span class="sxs-lookup"><span data-stu-id="9170d-547">The generic type can also include new generic parameters.</span></span>

<span data-ttu-id="9170d-548">La relation entre les paramètres de type générique d'un type conteneur et ses types imbriqués peut être masquée par la syntaxe des différents langages.</span><span class="sxs-lookup"><span data-stu-id="9170d-548">The relationship between the generic type parameters of a containing type and its nested types may be hidden by the syntax of individual languages.</span></span> <span data-ttu-id="9170d-549">Dans l'exemple suivant, un type générique `Outer<T>` contient deux classes imbriquées, `Inner1A` et `Inner1B<U>`.</span><span class="sxs-lookup"><span data-stu-id="9170d-549">In the following example, a generic type `Outer<T>` contains two nested classes, `Inner1A` and `Inner1B<U>`.</span></span> <span data-ttu-id="9170d-550">Les appels à la méthode `ToString`, dont chaque classe hérite de `Object.ToString`, indiquent que chaque classe imbriquée inclut les paramètres de type de sa classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="9170d-550">The calls to the `ToString` method, which each class inherits from `Object.ToString`, show that each nested class includes the type parameters of its containing class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

<span data-ttu-id="9170d-551">Les noms des types génériques sont encodés sous la forme *nom*'*n*, où *nom* est le nom du type, *\`* est un caractère littéral et *n* est le nombre de paramètres déclarés sur le type ou, pour les types génériques imbriqués, le nombre de paramètres de type récemment introduits.</span><span class="sxs-lookup"><span data-stu-id="9170d-551">Generic type names are encoded in the form *name*'*n*, where *name* is the type name, *\`* is a character literal, and *n* is the number of parameters declared on the type, or, for nested generic types, the number of newly introduced type parameters.</span></span> <span data-ttu-id="9170d-552">Cet encodage de noms de types génériques intéresse principalement les développeurs qui utilisent la réflexion pour accéder aux types génériques conformes à CLS dans une bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="9170d-552">This encoding of generic type names is primarily of interest to developers who use reflection to access CLS-complaint generic types in a library.</span></span>

<span data-ttu-id="9170d-553">Si les contraintes sont appliquées à un type générique, tous les types utilisés en tant que contraintes doivent également être conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-553">If constraints are applied to a generic type, any types used as constraints must also be CLS-compliant.</span></span> <span data-ttu-id="9170d-554">L'exemple suivant définit une classe nommée `BaseClass` qui n'est pas conforme à CLS et une classe générique nommée `BaseCollection` dont le paramètre de type doit dériver de `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="9170d-554">The following example defines a class named `BaseClass` that is not CLS-compliant and a generic class named `BaseCollection` whose type parameter must derive from `BaseClass`.</span></span> <span data-ttu-id="9170d-555">Toutefois, comme `BaseClass` n'est pas conforme à CLS, le compilateur émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="9170d-555">But because `BaseClass` is not CLS-compliant, the compiler emits a warning.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}

public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class

Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not
'    CLS-compliant.
'
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

<span data-ttu-id="9170d-556">Si un type générique est dérivé d'un type de base générique, il doit redéclarer toutes les contraintes pour s'assurer que les contraintes du type de base sont également satisfaites.</span><span class="sxs-lookup"><span data-stu-id="9170d-556">If a generic type is derived from a generic base type, it must redeclare any constraints so that it can guarantee that constraints on the base type are also satisfied.</span></span> <span data-ttu-id="9170d-557">L'exemple suivant définit un `Number<T>` qui peut représenter un type numérique.</span><span class="sxs-lookup"><span data-stu-id="9170d-557">The following example defines a `Number<T>` that can represent any numeric type.</span></span> <span data-ttu-id="9170d-558">Il définit également une classe `FloatingPoint<T>` qui représente une valeur à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="9170d-558">It also defines a `FloatingPoint<T>` class that represents a floating point value.</span></span> <span data-ttu-id="9170d-559">Toutefois, le code source ne se compile pas, car il n'applique pas la contrainte `Number<T>` (ce T doit être un type de valeur) à `FloatingPoint<T>`.</span><span class="sxs-lookup"><span data-stu-id="9170d-559">However, the source code fails to compile, because it does not apply the constraint on `Number<T>` (that T must be a value type) to `FloatingPoint<T>`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T>
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
// The attempt to compile the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
' The attempt to compile the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

<span data-ttu-id="9170d-560">L'exemple se compile correctement si la contrainte est ajoutée à la classe `FloatingPoint<T>`.</span><span class="sxs-lookup"><span data-stu-id="9170d-560">The example compiles successfully if the constraint is added to the `FloatingPoint<T>` class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
```

<span data-ttu-id="9170d-561">La spécification CLS (Common Language Specification) impose un modèle conservateur par instanciation pour les types imbriqués et les membres protégés.</span><span class="sxs-lookup"><span data-stu-id="9170d-561">The Common Language Specification imposes a conservative per-instantiation model for nested types and protected members.</span></span> <span data-ttu-id="9170d-562">Les types génériques ouverts ne peuvent pas exposer de champs ou de membres avec des signatures qui contiennent une instanciation spécifique d'un type générique imbriqué et protégé.</span><span class="sxs-lookup"><span data-stu-id="9170d-562">Open generic types cannot expose fields or members with signatures that contain a specific instantiation of a nested, protected generic type.</span></span> <span data-ttu-id="9170d-563">Les types non génériques qui étendent une instanciation spécifique d'une classe de base ou une interface générique ne peuvent pas exposer de champs ou de membres avec des signatures qui contiennent une instanciation différente d'un type générique imbriqué et protégé.</span><span class="sxs-lookup"><span data-stu-id="9170d-563">Non-generic types that extend a specific instantiation of a generic base class or interface cannot expose fields or members with signatures that contain a different instantiation of a nested, protected generic type.</span></span>

<span data-ttu-id="9170d-564">L’exemple suivant définit un type générique, `C1<T>`, et une classe protégée, `C1<T>.N`.</span><span class="sxs-lookup"><span data-stu-id="9170d-564">The following example defines a generic type, `C1<T>`, and a protected class, `C1<T>.N`.</span></span> <span data-ttu-id="9170d-565">`C1<T>` a deux méthodes : `M1` et `M2`.</span><span class="sxs-lookup"><span data-stu-id="9170d-565">`C1<T>` has two methods, `M1` and `M2`.</span></span> <span data-ttu-id="9170d-566">Toutefois, la méthode `M1` n’est pas conforme CLS, car elle essaie de retourner un objet `C1<int>.N` de `C1<T>`.</span><span class="sxs-lookup"><span data-stu-id="9170d-566">However, `M1` is not CLS-compliant because it tries to return a `C1<int>.N` object from `C1<T>`.</span></span> <span data-ttu-id="9170d-567">Une deuxième classe, `C2`, est dérivée de `C1<long>`.</span><span class="sxs-lookup"><span data-stu-id="9170d-567">A second class, `C2`, is derived from `C1<long>`.</span></span> <span data-ttu-id="9170d-568">Elle a deux méthodes, `M3` et `M4`.</span><span class="sxs-lookup"><span data-stu-id="9170d-568">It has two methods, `M3` and `M4`.</span></span> <span data-ttu-id="9170d-569">`M3`’est pas conforme CLS, car elle essaie de retourner un objet `C1<int>.N` d’une sous-classe de `C1<long>`.</span><span class="sxs-lookup"><span data-stu-id="9170d-569">`M3` is not CLS-compliant because it tries to return a `C1<int>.N` object from a subclass of `C1<long>`.</span></span> <span data-ttu-id="9170d-570">Les compilateurs de langage peuvent être encore plus restrictifs.</span><span class="sxs-lookup"><span data-stu-id="9170d-570">Language compilers can be even more restrictive.</span></span> <span data-ttu-id="9170d-571">Dans cet exemple, Visual Basic affiche une erreur lorsqu'il tente de compiler `M4`.</span><span class="sxs-lookup"><span data-stu-id="9170d-571">In this example, Visual Basic displays an error when it tries to compile `M4`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T>
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long>
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T)
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages

   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long)
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)
   End Sub
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace
'    '<Default>' through class 'C1'.
'
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because
'    it is 'Protected'.
'
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'
'                             ~~~~~~~~~~~~~~~~
'
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'
'       Protected Sub M4(n As C1(Of Long).N)
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a><span data-ttu-id="9170d-572">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="9170d-572">Constructors</span></span>

<span data-ttu-id="9170d-573">Les constructeurs des classes et structures conformes à CLS doivent suivre ces règles :</span><span class="sxs-lookup"><span data-stu-id="9170d-573">Constructors in CLS-compliant classes and structures must follow these rules:</span></span>

* <span data-ttu-id="9170d-574">Un constructeur d'une classe dérivée doit appeler le constructeur d'instance de sa classe de base avant d'accéder aux données d'instance héritées.</span><span class="sxs-lookup"><span data-stu-id="9170d-574">A constructor of a derived class must call the instance constructor of its base class before it accesses inherited instance data.</span></span> <span data-ttu-id="9170d-575">Cette spécification est due au fait que les constructeurs de classes de base ne sont pas hérités par leurs classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="9170d-575">This requirement is due to the fact that base class constructors are not inherited by their derived classes.</span></span> <span data-ttu-id="9170d-576">Cette règle ne s'applique pas aux structures, qui ne prennent pas en charge l'héritage direct.</span><span class="sxs-lookup"><span data-stu-id="9170d-576">This rule does not apply to structures, which do not support direct inheritance.</span></span>

  <span data-ttu-id="9170d-577">En général, les compilateurs appliquent cette règle indépendamment de la conformité CLS, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9170d-577">Typically, compilers enforce this rule independently of CLS compliance, as the following example shows.</span></span> <span data-ttu-id="9170d-578">Il crée une classe `Doctor` dérivée d'une classe `Person`, mais la classe `Doctor` ne parvient pas à appeler le constructeur de classe `Person` pour initialiser les champs d'instance hérités.</span><span class="sxs-lookup"><span data-stu-id="9170d-578">It creates a `Doctor` class that is derived from a `Person` class, but the `Doctor` class fails to call the `Person` class constructor to initialize inherited instance fields.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName
    {
        get { return fName; }
    }

    public string LastName
    {
        get { return lName; }
    }

    public string Id
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName,
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName,
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '
    '       Public Sub New()
    '                  ~~~
    ````

* <span data-ttu-id="9170d-579">Un constructeur d'objet ne peut être appelé que pour créer un objet.</span><span class="sxs-lookup"><span data-stu-id="9170d-579">An object constructor cannot be called except to create an object.</span></span> <span data-ttu-id="9170d-580">En outre, un objet ne peut pas être initialisé deux fois.</span><span class="sxs-lookup"><span data-stu-id="9170d-580">In addition, an object cannot be initialized twice.</span></span> <span data-ttu-id="9170d-581">Par exemple, cela signifie que `Object.MemberwiseClone` ne doit pas appeler de constructeurs.</span><span class="sxs-lookup"><span data-stu-id="9170d-581">For example, this means that `Object.MemberwiseClone` must not call constructors.</span></span>

### <a name="properties"></a><span data-ttu-id="9170d-582">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9170d-582">Properties</span></span>

<span data-ttu-id="9170d-583">Les propriétés dans les types conformes à CLS doivent suivre ces règles :</span><span class="sxs-lookup"><span data-stu-id="9170d-583">Properties in CLS-compliant types must follow these rules:</span></span>

* <span data-ttu-id="9170d-584">Une propriété doit posséder une méthode setter, getter ou les deux.</span><span class="sxs-lookup"><span data-stu-id="9170d-584">A property must have a setter, a getter, or both.</span></span> <span data-ttu-id="9170d-585">Dans un assembly, celles-ci sont implémentées comme des méthodes spéciales, ce qui signifie qu’elles apparaîtront comme des méthodes distinctes (l’accesseur Get est nommé `get` \_ *NomPropriété* et l’accesseur Set est `set` \_ *PropertyName*) marqué comme `SpecialName` dans les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9170d-585">In an assembly, these are implemented as special methods, which means that they will appear as separate methods (the getter is named `get`\_*propertyname* and the setter is `set`\_*propertyname*) marked as `SpecialName` in the assembly's metadata.</span></span> <span data-ttu-id="9170d-586">Le compilateur C# applique automatiquement cette règle sans qu’il soit nécessaire d’appliquer l’attribut <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9170d-586">The C# compiler enforces this rule automatically without the need to apply the <xref:System.CLSCompliantAttribute> attribute.</span></span>

* <span data-ttu-id="9170d-587">Le type d’une propriété correspond au type de retour de la méthode getter de la propriété et du dernier argument de la méthode setter.</span><span class="sxs-lookup"><span data-stu-id="9170d-587">A property's type is the return type of the property getter and the last argument of the setter.</span></span> <span data-ttu-id="9170d-588">Ces types doivent être conformes à CLS et les arguments ne peuvent pas être assignés à la propriété par référence (autrement dit, ils ne peuvent pas être des pointeurs managés).</span><span class="sxs-lookup"><span data-stu-id="9170d-588">These types must be CLS compliant, and arguments cannot be assigned to the property by reference (that is, they cannot be managed pointers).</span></span>

* <span data-ttu-id="9170d-589">Si une propriété possède une méthode getter et une méthode setter, elles doivent être toutes les deux virtuelles, statiques ou être toutes les deux des instances.</span><span class="sxs-lookup"><span data-stu-id="9170d-589">If a property has both a getter and a setter, they must both be virtual, both static, or both instance.</span></span> <span data-ttu-id="9170d-590">Le compilateur C# applique automatiquement cette règle par le biais de la syntaxe de définition de propriété.</span><span class="sxs-lookup"><span data-stu-id="9170d-590">The C# compiler automatically enforces this rule through property definition syntax.</span></span>

### <a name="events"></a><span data-ttu-id="9170d-591">Événements</span><span class="sxs-lookup"><span data-stu-id="9170d-591">Events</span></span>

<span data-ttu-id="9170d-592">Un événement est défini par son nom et son type.</span><span class="sxs-lookup"><span data-stu-id="9170d-592">An event is defined by its name and its type.</span></span> <span data-ttu-id="9170d-593">Le type d'événement est un délégué utilisé pour indiquer l'événement.</span><span class="sxs-lookup"><span data-stu-id="9170d-593">The event type is a delegate that is used to indicate the event.</span></span> <span data-ttu-id="9170d-594">Par exemple, l'événement `DbConnection.StateChange` est de type `StateChangeEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="9170d-594">For example, the `DbConnection.StateChange` event is of type `StateChangeEventHandler`.</span></span> <span data-ttu-id="9170d-595">Outre l'événement lui-même, trois méthodes avec des noms basés sur le nom de l'événement fournissent une implémentation de l'événement et sont marquées comme `SpecialName` dans les métadonnées de l'assembly :</span><span class="sxs-lookup"><span data-stu-id="9170d-595">In addition to the event itself, three methods with names based on the event name provide the event's implementation and are marked as `SpecialName` in the assembly's metadata:</span></span>

* <span data-ttu-id="9170d-596">Une méthode pour ajouter un gestionnaire d’événements, appelée `add`_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="9170d-596">A method for adding an event handler, named `add`_*EventName*.</span></span> <span data-ttu-id="9170d-597">Par exemple, la méthode d'abonnement aux événements pour l'événement `DbConnection.StateChange` est nommée `add_StateChange`.</span><span class="sxs-lookup"><span data-stu-id="9170d-597">For example, the event subscription method for the `DbConnection.StateChange` event is named `add_StateChange`.</span></span>

* <span data-ttu-id="9170d-598">Une méthode pour supprimer un gestionnaire d’événements, appelée `remove`_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="9170d-598">A method for removing an event handler, named `remove`_*EventName*.</span></span> <span data-ttu-id="9170d-599">Par exemple, la méthode de suppression pour l'événement `DbConnection.StateChange` est nommée `remove_StateChange`.</span><span class="sxs-lookup"><span data-stu-id="9170d-599">For example, the removal method for the `DbConnection.StateChange` event is named `remove_StateChange`.</span></span>

* <span data-ttu-id="9170d-600">Une méthode pour indiquer que l’événement s’est produit, nommée `raise`\_*NomÉvénement*.</span><span class="sxs-lookup"><span data-stu-id="9170d-600">A method for indicating that the event has occurred, named `raise`\_*EventName*.</span></span>

> [!NOTE]
> <span data-ttu-id="9170d-601">La plupart des règles de la spécification CLS concernant les événements sont implémentées par les compilateurs de langage et sont transparentes aux développeurs de composants.</span><span class="sxs-lookup"><span data-stu-id="9170d-601">Most of the Common Language Specification's rules regarding events are implemented by language compilers and are transparent to component developers.</span></span>

<span data-ttu-id="9170d-602">L'accessibilité des méthodes permettant d'ajouter, de supprimer et de déclencher un événement doit être identique.</span><span class="sxs-lookup"><span data-stu-id="9170d-602">The methods for adding, removing, and raising the event must have the same accessibility.</span></span> <span data-ttu-id="9170d-603">Les méthodes doivent également toutes être statiques, instanciées ou virtuelles.</span><span class="sxs-lookup"><span data-stu-id="9170d-603">They must also all be static, instance, or virtual.</span></span> <span data-ttu-id="9170d-604">Les méthodes d'ajout et de suppression d'un événement ont un paramètre dont le type est le type du délégué d'événement.</span><span class="sxs-lookup"><span data-stu-id="9170d-604">The methods for adding and removing an event have one parameter whose type is the event delegate type.</span></span> <span data-ttu-id="9170d-605">Les méthodes d'ajout et de suppression doivent être toutes les deux présentes ou absentes.</span><span class="sxs-lookup"><span data-stu-id="9170d-605">The add and remove methods must both be present or both be absent.</span></span>

<span data-ttu-id="9170d-606">L'exemple suivant définit une classe conforme à CLS nommée `Temperature` qui déclenche un événement `TemperatureChanged` si le changement de température entre deux lectures est égal ou supérieur à une valeur seuil.</span><span class="sxs-lookup"><span data-stu-id="9170d-606">The following example defines a CLS-compliant class named `Temperature` that raises a `TemperatureChanged` event if the change in temperature between two readings equals or exceeds a threshold value.</span></span> <span data-ttu-id="9170d-607">La classe `Temperature` définit explicitement une méthode `raise_TemperatureChanged` afin de pouvoir exécuter de manière sélective les gestionnaires d'événements.</span><span class="sxs-lookup"><span data-stu-id="9170d-607">The `Temperature` class explicitly defines a `raise_TemperatureChanged` method so that it can selectively execute event handlers.</span></span>

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp;
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   }

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   }

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance)
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return;

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub
End Class
```

### <a name="overloads"></a><span data-ttu-id="9170d-608">Surcharges</span><span class="sxs-lookup"><span data-stu-id="9170d-608">Overloads</span></span>

<span data-ttu-id="9170d-609">La spécification CLS impose les conditions suivantes aux membres surchargés :</span><span class="sxs-lookup"><span data-stu-id="9170d-609">The Common Language Specification imposes the following requirements on overloaded members:</span></span>

* <span data-ttu-id="9170d-610">Les membres peuvent être surchargés selon le nombre de paramètres et le type d'un paramètre.</span><span class="sxs-lookup"><span data-stu-id="9170d-610">Members can be overloaded based on the number of parameters and the type of any parameter.</span></span> <span data-ttu-id="9170d-611">La convention d’appel, le type de retour, les modificateurs personnalisés appliqués à la méthode ou à son paramètre et le fait que les paramètres soient transmis par valeur ou par référence ne sont pas pris en considération lors de la différenciation des surcharges.</span><span class="sxs-lookup"><span data-stu-id="9170d-611">Calling convention, return type, custom modifiers applied to the method or its parameter, and whether parameters are passed by value or by reference are not considered when differentiating between overloads.</span></span> <span data-ttu-id="9170d-612">Pour obtenir un exemple, consultez le code de l’exigence indiquant que les noms doivent être uniques dans une portée, dans la section [Conventions d’affectation de noms](#naming-conventions).</span><span class="sxs-lookup"><span data-stu-id="9170d-612">For an example, see the code for the requirement that names must be unique within a scope in the [Naming conventions](#naming-conventions) section.</span></span>

* <span data-ttu-id="9170d-613">Seules les propriétés et les méthodes peuvent être surchargées.</span><span class="sxs-lookup"><span data-stu-id="9170d-613">Only properties and methods can be overloaded.</span></span> <span data-ttu-id="9170d-614">Les champs et les événements ne peuvent pas être surchargés.</span><span class="sxs-lookup"><span data-stu-id="9170d-614">Fields and events cannot be overloaded.</span></span>

* <span data-ttu-id="9170d-615">Les méthodes génériques peuvent être surchargées selon le nombre de leurs paramètres génériques.</span><span class="sxs-lookup"><span data-stu-id="9170d-615">Generic methods can be overloaded based on the number of their generic parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="9170d-616">Les opérateurs `op_Explicit` et `op_Implicit` sont des exceptions à la règle indiquant que la valeur de retour n'est pas considérée comme faisant partie d'une signature de méthode pour la résolution de la surcharge.</span><span class="sxs-lookup"><span data-stu-id="9170d-616">The `op_Explicit` and `op_Implicit` operators are exceptions to the rule that return value is not considered part of a method signature for overload resolution.</span></span> <span data-ttu-id="9170d-617">Ces deux opérateurs peuvent être surchargés selon leurs paramètres et leur valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="9170d-617">These two operators can be overloaded based on both their parameters and their return value.</span></span>

### <a name="exceptions"></a><span data-ttu-id="9170d-618">Exceptions</span><span class="sxs-lookup"><span data-stu-id="9170d-618">Exceptions</span></span>

<span data-ttu-id="9170d-619">Les objets d’exception doivent dériver de [System.Exception](xref:System.Exception) ou d’un autre type dérivé de `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="9170d-619">Exception objects must derive from [System.Exception](xref:System.Exception) or from another type derived from `System.Exception`.</span></span> <span data-ttu-id="9170d-620">L'exemple suivant illustre l'erreur de compilateur obtenue lorsqu'une classe personnalisée nommée `ErrorClass` est utilisée pour la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="9170d-620">The following example illustrates the compiler error that results when a custom class named `ErrorClass` is used for exception handling.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

<span data-ttu-id="9170d-621">Pour corriger cette erreur, la classe `ErrorClass` doit hériter de `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="9170d-621">To correct this error, the `ErrorClass` class must inherit from `System.Exception`.</span></span> <span data-ttu-id="9170d-622">Par ailleurs, la propriété Message doit être remplacée.</span><span class="sxs-lookup"><span data-stu-id="9170d-622">In addition, the Message property must be overridden.</span></span> <span data-ttu-id="9170d-623">L'exemple suivant corrige ces erreurs pour définir une classe `ErrorClass` conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-623">The following example corrects these errors to define an `ErrorClass` class that is CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a><span data-ttu-id="9170d-624">Attributs</span><span class="sxs-lookup"><span data-stu-id="9170d-624">Attributes</span></span>

<span data-ttu-id="9170d-625">Dans les assemblys .NET Framework, les attributs personnalisés fournissent un mécanisme extensible pour stocker des attributs personnalisés et récupérer les métadonnées concernant la programmation des objets, tels que les assemblys, les types, les membres et les paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="9170d-625">In.NET Framework assemblies, custom attributes provide an extensible mechanism for storing custom attributes and retrieving metadata about programming objects, such as assemblies, types, members, and method parameters.</span></span> <span data-ttu-id="9170d-626">Les attributs personnalisés doivent dériver de [System.Attribute](xref:System.Attribute) ou d’un type dérivé de `System.Attribute`.</span><span class="sxs-lookup"><span data-stu-id="9170d-626">Custom attributes must derive from [System.Attribute](xref:System.Attribute) or from a type derived from `System.Attribute`.</span></span>

<span data-ttu-id="9170d-627">L'exemple suivant enfreint cette règle.</span><span class="sxs-lookup"><span data-stu-id="9170d-627">The following example violates this rule.</span></span> <span data-ttu-id="9170d-628">Il définit une classe `NumericAttribute` qui ne dérive pas de `System.Attribute`.</span><span class="sxs-lookup"><span data-stu-id="9170d-628">It defines a `NumericAttribute` class that does not derive from `System.Attribute`.</span></span> <span data-ttu-id="9170d-629">Une erreur du compilateur se produit uniquement lorsque l’attribut non conforme CLS est appliqué, et non lorsque la classe est définie.</span><span class="sxs-lookup"><span data-stu-id="9170d-629">A compiler error results only when the non-CLS-compliant attribute is applied, not when the class is defined.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)]
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it
'    does not inherit from 'System.Attribute'.
'
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

<span data-ttu-id="9170d-630">Le constructeur ou les propriétés d'un attribut conforme à CLS peuvent exposer uniquement les types suivants :</span><span class="sxs-lookup"><span data-stu-id="9170d-630">The constructor or the properties of a CLS-compliant attribute can expose only the following types:</span></span>

* [<span data-ttu-id="9170d-631">Booléen</span><span class="sxs-lookup"><span data-stu-id="9170d-631">Boolean</span></span>](xref:System.Boolean)

* [<span data-ttu-id="9170d-632">Poids</span><span class="sxs-lookup"><span data-stu-id="9170d-632">Byte</span></span>](xref:System.Byte)

* [<span data-ttu-id="9170d-633">Char</span><span class="sxs-lookup"><span data-stu-id="9170d-633">Char</span></span>](xref:System.Char)

* [<span data-ttu-id="9170d-634">Double</span><span class="sxs-lookup"><span data-stu-id="9170d-634">Double</span></span>](xref:System.Double)

* [<span data-ttu-id="9170d-635">Int16</span><span class="sxs-lookup"><span data-stu-id="9170d-635">Int16</span></span>](xref:System.Int16)

* [<span data-ttu-id="9170d-636">Int32</span><span class="sxs-lookup"><span data-stu-id="9170d-636">Int32</span></span>](xref:System.Int32)

* [<span data-ttu-id="9170d-637">Int64</span><span class="sxs-lookup"><span data-stu-id="9170d-637">Int64</span></span>](xref:System.Int64)

* [<span data-ttu-id="9170d-638">Unique</span><span class="sxs-lookup"><span data-stu-id="9170d-638">Single</span></span>](xref:System.Single)

* [<span data-ttu-id="9170d-639">Chaîne</span><span class="sxs-lookup"><span data-stu-id="9170d-639">String</span></span>](xref:System.String)

* [<span data-ttu-id="9170d-640">Type</span><span class="sxs-lookup"><span data-stu-id="9170d-640">Type</span></span>](xref:System.Type)

* <span data-ttu-id="9170d-641">Tout type d'énumération dont le type sous-jacent est `Byte`, `Int16`, `Int32` ou `Int64`.</span><span class="sxs-lookup"><span data-stu-id="9170d-641">Any enumeration type whose underlying type is `Byte`, `Int16`, `Int32`, or `Int64`.</span></span>

<span data-ttu-id="9170d-642">L’exemple suivant définit une classe `DescriptionAttribute` qui dérive de [Attribute](xref:System.Attribute).</span><span class="sxs-lookup"><span data-stu-id="9170d-642">The following example defines a `DescriptionAttribute` class that derives from [Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="9170d-643">Le constructeur de classe a un paramètre de type `Descriptor`, la classe n'est donc pas conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-643">The class constructor has a parameter of type `Descriptor`, so the class is not CLS-compliant.</span></span> <span data-ttu-id="9170d-644">Le compilateur C# émet un avertissement mais se compile correctement.</span><span class="sxs-lookup"><span data-stu-id="9170d-644">The C# compiler emits a warning but compiles successfully.</span></span>

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description;
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d;
   }

   public Descriptor Descriptor
   { get { return desc; } }
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType
   Public Description As String
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get
         Return desc
      End Get
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a><span data-ttu-id="9170d-645">Attribut CLSCompliantAttribute</span><span class="sxs-lookup"><span data-stu-id="9170d-645">The CLSCompliantAttribute attribute</span></span>

<span data-ttu-id="9170d-646">L’attribut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) permet d’indiquer si un élément de programme est conforme à la spécification CLS (Common Language Specification).</span><span class="sxs-lookup"><span data-stu-id="9170d-646">The [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is used to indicate whether a program element complies with the Common Language Specification.</span></span> <span data-ttu-id="9170d-647">Le constructeur `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` inclut un seul paramètre obligatoire, *isCompliant*, qui indique si l’élément de programme est conforme CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-647">The `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` constructor includes a single required parameter, *isCompliant*, that indicates whether the program element is CLS-compliant.</span></span>

<span data-ttu-id="9170d-648">Au moment de la compilation, le compilateur détecte les éléments non conformes qui sont présumés conformes à CLS et émet alors un avertissement.</span><span class="sxs-lookup"><span data-stu-id="9170d-648">At compile time, the compiler detects non-compliant elements that are presumed to be CLS-compliant and emits a warning.</span></span> <span data-ttu-id="9170d-649">Le compilateur n'émet pas d'avertissements pour les types ou les membres qui sont explicitement déclarés comme étant non conformes.</span><span class="sxs-lookup"><span data-stu-id="9170d-649">The compiler does not emit warnings for types or members that are explicitly declared to be non-compliant.</span></span>

<span data-ttu-id="9170d-650">Les développeurs de composants peuvent utiliser l'attribut `CLSCompliantAttribute` de deux façons :</span><span class="sxs-lookup"><span data-stu-id="9170d-650">Component developers can use the `CLSCompliantAttribute` attribute in two ways:</span></span>

* <span data-ttu-id="9170d-651">Pour définir les parties de l'interface publique exposées par un composant qui sont conformes à CLS et celles qui ne sont pas conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-651">To define the parts of the public interface exposed by a component that are CLS-compliant and the parts that are not CLS-compliant.</span></span> <span data-ttu-id="9170d-652">Lorsque l'attribut est utilisé pour marquer des éléments de programme particuliers comme étant conformes à CLS, son utilisation garantit que ces éléments sont accessibles à partir de tous les langages et outils qui ciblent le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9170d-652">When the attribute is used to mark particular program elements as CLS-compliant, its use guarantees that those elements are accessible from all languages and tools that target the .NET Framework.</span></span>

* <span data-ttu-id="9170d-653">Pour vérifier que l'interface publique de la bibliothèque de composants expose uniquement les éléments de programme conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-653">To ensure that the component library's public interface exposes only program elements that are CLS-compliant.</span></span> <span data-ttu-id="9170d-654">Si les éléments ne sont pas conformes à CLS, les compilateurs publieront généralement un avertissement.</span><span class="sxs-lookup"><span data-stu-id="9170d-654">If elements are not CLS-compliant, compilers will generally issue a warning.</span></span>

> [!WARNING]
> <span data-ttu-id="9170d-655">Dans certains cas, les compilateurs de langages imposent les règles conformes à CLS que l'attribut `CLSCompliantAttribute` soit utilisé ou non.</span><span class="sxs-lookup"><span data-stu-id="9170d-655">In some cases, language compilers enforce CLS-compliant rules regardless of whether the `CLSCompliantAttribute` attribute is used.</span></span> <span data-ttu-id="9170d-656">Par exemple, la définition d’un membre `*static` dans une interface est une infraction à une règle CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-656">For example, defining a `*static` member in an interface violates a CLS rule.</span></span> <span data-ttu-id="9170d-657">Toutefois, si vous définissez un membre `*static` dans une interface, le compilateur C# affiche un message d’erreur et ne compile pas l’application.</span><span class="sxs-lookup"><span data-stu-id="9170d-657">However, if you define a `*static` member in an interface, the C# compiler displays an error message and fails to compile the app.</span></span>

<span data-ttu-id="9170d-658">L’attribut `CLSCompliantAttribute` est marqué avec un attribut [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) qui a la valeur `AttributeTargets.All`.</span><span class="sxs-lookup"><span data-stu-id="9170d-658">The `CLSCompliantAttribute` attribute is marked with an [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) attribute that has a value of `AttributeTargets.All`.</span></span> <span data-ttu-id="9170d-659">Cette valeur permet d'appliquer l'attribut `CLSCompliantAttribute` à un élément de programme, notamment aux assemblys, modules, types (classes, structures, énumérations, interfaces et délégués), membres de types (constructeurs, méthodes, propriétés, champs et événements), paramètres, paramètres génériques et valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="9170d-659">This value allows you to apply the `CLSCompliantAttribute` attribute to any program element, including assemblies, modules, types (classes, structures, enumerations, interfaces, and delegates), type members (constructors, methods, properties, fields, and events), parameters, generic parameters, and return values.</span></span> <span data-ttu-id="9170d-660">Toutefois, dans la pratique, vous devez appliquer l'attribut uniquement aux assemblys, aux types et aux membres de types.</span><span class="sxs-lookup"><span data-stu-id="9170d-660">However, in practice, you should apply the attribute only to assemblies, types, and type members.</span></span> <span data-ttu-id="9170d-661">Sinon, les compilateurs ignorent l'attribut et continuent à générer des avertissements de compilateur lorsqu'ils rencontrent un paramètre non conforme, un paramètre générique ou une valeur de retour dans l'interface publique de votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="9170d-661">Otherwise, compilers ignore the attribute and continue to generate compiler warnings whenever they encounter a non-compliant parameter, generic parameter, or return value in your library's public interface.</span></span>

<span data-ttu-id="9170d-662">La valeur de l'attribut `CLSCompliantAttribute` est héritée par les éléments de programme contenus.</span><span class="sxs-lookup"><span data-stu-id="9170d-662">The value of the `CLSCompliantAttribute` attribute is inherited by contained program elements.</span></span> <span data-ttu-id="9170d-663">Par exemple, si un assembly est marqué comme étant conforme à CLS, ses types sont également conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-663">For example, if an assembly is marked as CLS-compliant, its types are also CLS-compliant.</span></span> <span data-ttu-id="9170d-664">Si un type est marqué comme étant conforme à CLS, ses membres et types imbriqués seront également conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-664">If a type is marked as CLS-compliant, its nested types and members are also CLS-compliant.</span></span>

<span data-ttu-id="9170d-665">Vous pouvez remplacer explicitement la conformité héritée en appliquant l'attribut `CLSCompliantAttribute` à un élément de programme contenu.</span><span class="sxs-lookup"><span data-stu-id="9170d-665">You can explicitly override the inherited compliance by applying the `CLSCompliantAttribute` attribute to a contained program element.</span></span> <span data-ttu-id="9170d-666">Par exemple, vous pouvez utiliser l’attribut `CLSCompliantAttribute` avec une valeur *isCompliant* égale à `false` pour définir un type non conforme dans un assembly conforme, et avec une valeur *isCompliant* égale à `true` pour définir un type conforme dans un assembly non conforme.</span><span class="sxs-lookup"><span data-stu-id="9170d-666">For example, you can use the `CLSCompliantAttribute` attribute with an *isCompliant* value of `false` to define a non-compliant type in a compliant assembly, and you can use the attribute with an *isCompliant* value of `true` to define a compliant type in a non-compliant assembly.</span></span> <span data-ttu-id="9170d-667">Vous pouvez également définir des membres non conformes dans un type conforme.</span><span class="sxs-lookup"><span data-stu-id="9170d-667">You can also define non-compliant members in a compliant type.</span></span> <span data-ttu-id="9170d-668">Toutefois, un type non conforme ne peut pas avoir de membres conformes, vous ne pouvez donc pas utiliser l’attribut avec une valeur *isCompliant* égale à `true` pour remplacer l’héritage d’un type non conforme.</span><span class="sxs-lookup"><span data-stu-id="9170d-668">However, a non-compliant type cannot have compliant members, so you cannot use the attribute with an *isCompliant* value of `true` to override inheritance from a non-compliant type.</span></span>

<span data-ttu-id="9170d-669">Lorsque vous développez des composants, vous devez toujours utiliser l'attribut `CLSCompliantAttribute` pour indiquer si votre assembly, ses types et ses membres sont conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-669">When you are developing components, you should always use the `CLSCompliantAttribute` attribute to indicate whether your assembly, its types, and its members are CLS-compliant.</span></span>

<span data-ttu-id="9170d-670">Pour créer des composants conformes à CLS :</span><span class="sxs-lookup"><span data-stu-id="9170d-670">To create CLS-compliant components:</span></span>

1. <span data-ttu-id="9170d-671">Utilisez `CLSCompliantAttribute` pour marquer votre assembly comme étant conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-671">Use the `CLSCompliantAttribute` to mark you assembly as CLS-compliant.</span></span>

2. <span data-ttu-id="9170d-672">Marquez les types exposés publiquement de l'assembly qui ne sont pas conformes à CLS comme non conformes.</span><span class="sxs-lookup"><span data-stu-id="9170d-672">Mark any publicly exposed types in the assembly that are not CLS-compliant as non-compliant.</span></span>

3. <span data-ttu-id="9170d-673">Marquez tous les membres exposés publiquement dans des types conformes à CLS comme non conformes.</span><span class="sxs-lookup"><span data-stu-id="9170d-673">Mark any publicly exposed members in CLS-compliant types as non-compliant.</span></span>

4. <span data-ttu-id="9170d-674">Fournissez une alternative conforme à CLS pour les membres non conformes.</span><span class="sxs-lookup"><span data-stu-id="9170d-674">Provide a CLS-compliant alternative for non-CLS-compliant members.</span></span>

<span data-ttu-id="9170d-675">Si vous avez correctement marqué tous vos types et membres non conformes, le compilateur ne doit émettre aucun avertissement de non-conformité.</span><span class="sxs-lookup"><span data-stu-id="9170d-675">If you've successfully marked all your non-compliant types and members, your compiler should not emit any non-compliance warnings.</span></span> <span data-ttu-id="9170d-676">Toutefois, vous devez indiquer quels membres ne sont pas conformes à CLS et répertorier leurs alternatives conformes à CLS dans votre documentation produit.</span><span class="sxs-lookup"><span data-stu-id="9170d-676">However, you should indicate which members are not CLS-compliant and list their CLS-compliant alternatives in your product documentation.</span></span>

<span data-ttu-id="9170d-677">L'exemple suivant utilise l'attribut `CLSCompliantAttribute` pour définir un assembly conforme à CLS et un type, `CharacterUtilities`, qui a deux membres non conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-677">The following example uses the `CLSCompliantAttribute` attribute to define a CLS-compliant assembly and a type, `CharacterUtilities`, that has two non-CLS-compliant members.</span></span> <span data-ttu-id="9170d-678">Les deux membres étant référencés avec l'attribut `CLSCompliant(false)`, le compilateur ne génère aucun avertissement.</span><span class="sxs-lookup"><span data-stu-id="9170d-678">Because both members are tagged with the `CLSCompliant(false)` attribute, the compiler produces no warnings.</span></span> <span data-ttu-id="9170d-679">La classe fournit également une alternative conforme à CLS pour les deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="9170d-679">The class also provides a CLS-compliant alternative for both methods.</span></span> <span data-ttu-id="9170d-680">Normalement, nous ajouterions seulement deux surcharges à la méthode `ToUTF16` pour fournir des alternatives conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-680">Ordinarily, we would just add two overloads to the `ToUTF16` method to provide CLS-compliant alternatives.</span></span> <span data-ttu-id="9170d-681">Toutefois, les méthodes ne pouvant pas être surchargées selon la valeur de retour, les noms des méthodes conformes à CLS sont différents des noms des méthodes non conformes.</span><span class="sxs-lookup"><span data-stu-id="9170d-681">However, because methods cannot be overloaded based on return value, the names of the CLS-compliant methods are different from the names of the non-compliant methods.</span></span>

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch);
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      }
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch)
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If
   End Function
End Class
```

<span data-ttu-id="9170d-682">Si vous développez une application plutôt qu'une bibliothèque (autrement dit, si vous n'exposez pas des types ou des membres qui peuvent être utilisés par d'autres développeurs d'applications), la conformité CLS des éléments de programme que votre application consomme n'a d'intérêt que si votre langage ne les prend pas en charge.</span><span class="sxs-lookup"><span data-stu-id="9170d-682">If you are developing an app rather than a library (that is, if you aren't exposing types or members that can be consumed by other app developers), the CLS compliance of the program elements that your app consumes are of interest only if your language does not support them.</span></span> <span data-ttu-id="9170d-683">Dans ce cas, votre compilateur de langage générera une erreur lorsque vous essaierez d'utiliser un élément non conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="9170d-683">In that case, your language compiler will generate an error when you try to use a non-CLS-compliant element.</span></span>

## <a name="cross-language-interoperability"></a><span data-ttu-id="9170d-684">Interopérabilité interlangage</span><span class="sxs-lookup"><span data-stu-id="9170d-684">Cross-language interoperability</span></span>

<span data-ttu-id="9170d-685">L'indépendance du langage a plusieurs significations possibles.</span><span class="sxs-lookup"><span data-stu-id="9170d-685">Language independence has a number of possible meanings.</span></span> <span data-ttu-id="9170d-686">Une des significations implique la consommation de façon transparente des types écrits dans un langage à partir d’une application écrite dans un autre langage.</span><span class="sxs-lookup"><span data-stu-id="9170d-686">One meaning involves seamlessly consuming types written in one language from an app written in another language.</span></span> <span data-ttu-id="9170d-687">Une deuxième signification, qui est le sujet de cet article, consiste à combiner du code écrit dans plusieurs langages dans un même assembly .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9170d-687">A second meaning, which is the focus of this article, involves combining code written in multiple languages into a single .NET Framework assembly.</span></span>

<span data-ttu-id="9170d-688">L'exemple suivant illustre l'interopérabilité interlangage en créant une bibliothèque de classes nommée Utilities.dll qui comprend deux classes, `NumericLib` et `StringLib`.</span><span class="sxs-lookup"><span data-stu-id="9170d-688">The following example illustrates cross-language interoperability by creating a class library named Utilities.dll that includes two classes, `NumericLib` and `StringLib`.</span></span> <span data-ttu-id="9170d-689">La classe `NumericLib` est écrite en C# et la classe `StringLib` est écrite en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9170d-689">The `NumericLib` class is written in C#, and the `StringLib` class is written in Visual Basic.</span></span> <span data-ttu-id="9170d-690">Voici le code source de `StringUtil.vb`, qui comprend un seul membre, `ToTitleCase`, dans sa classe `StringLib`.</span><span class="sxs-lookup"><span data-stu-id="9170d-690">Here's the source code for `StringUtil.vb`, which includes a single member, `ToTitleCase`, in its `StringLib` class.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String)

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split()
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "
         End If
      Next
      Return result
   End Function
End Module
```

<span data-ttu-id="9170d-691">Voici le code source de NumberUtil.cs, qui définit une classe `NumericLib` qui a deux membres, `IsEven` et `NearZero`.</span><span class="sxs-lookup"><span data-stu-id="9170d-691">Here's the source code for NumberUtil.cs, which defines a `NumericLib` class that has two members, `IsEven` and `NearZero`.</span></span>

```csharp
using System;

public static class NumericLib
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 ||
          number is Int32 ||
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001;
   }
}
```

<span data-ttu-id="9170d-692">Pour placer les deux classes dans un même assembly, vous devez les compiler dans des modules.</span><span class="sxs-lookup"><span data-stu-id="9170d-692">To package the two classes in a single assembly, you must compile them into modules.</span></span> <span data-ttu-id="9170d-693">Pour compiler le fichier de code source Visual Basic dans un module, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="9170d-693">To compile the Visual Basic source code file into a module, use this command:</span></span>

```console
vbc /t:module StringUtil.vb
```

<span data-ttu-id="9170d-694">Pour compiler le fichier de code source C# dans un module, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="9170d-694">To compile the C# source code file into a module, use this command:</span></span>

```console
csc /t:module NumberUtil.cs
```

<span data-ttu-id="9170d-695">Vous utilisez ensuite l’outil de liaison (Link.exe) pour compiler les deux modules en un assembly :</span><span class="sxs-lookup"><span data-stu-id="9170d-695">You then use the Link tool (Link.exe) to compile the two modules into an assembly:</span></span>

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

<span data-ttu-id="9170d-696">L'exemple suivant appelle ensuite les méthodes `NumericLib.NearZero` et `StringLib.ToTitleCase`.</span><span class="sxs-lookup"><span data-stu-id="9170d-696">The following example then calls the `NumericLib.NearZero` and `StringLib.ToTitleCase` methods.</span></span> <span data-ttu-id="9170d-697">Le code Visual Basic et le code C# peuvent accéder aux méthodes des deux classes.</span><span class="sxs-lookup"><span data-stu-id="9170d-697">Both the Visual Basic code and the C# code are able to access the methods in both classes.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

<span data-ttu-id="9170d-698">Pour compiler le code Visual Basic, utilisez cette commande :</span><span class="sxs-lookup"><span data-stu-id="9170d-698">To compile the Visual Basic code, use this command:</span></span>

```console
vbc example.vb /r:UtilityLib.dll
```

<span data-ttu-id="9170d-699">Pour compiler avec C#, changez le nom du compilateur vbc en csc et changez l’extension de fichier .vb en .cs :</span><span class="sxs-lookup"><span data-stu-id="9170d-699">To compile with C#, change the name of the compiler from vbc to csc, and change the file extension from .vb to .cs:</span></span>

```console
csc example.cs /r:UtilityLib.dll
```
