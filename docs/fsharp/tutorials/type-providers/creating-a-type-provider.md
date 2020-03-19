---
title: 'Tutorial: Créer un fournisseur de type'
description: Apprenez à créer vos propres fournisseurs de type F 3.0 en examinant plusieurs fournisseurs de type simple pour illustrer les concepts de base.
ms.date: 11/04/2019
ms.openlocfilehash: 3b8145d4c2d8bf96b6dcf66de02e9f2d83927d74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186121"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="93c0b-103">Tutorial: Créer un fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="93c0b-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="93c0b-104">Le mécanisme de fournisseur de type dans le cadre de la FMD est une partie importante de son soutien à la programmation riche en informations.</span><span class="sxs-lookup"><span data-stu-id="93c0b-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="93c0b-105">Ce tutoriel explique comment créer vos propres fournisseurs de type en vous promenant à travers le développement de plusieurs fournisseurs de type simple pour illustrer les concepts de base.</span><span class="sxs-lookup"><span data-stu-id="93c0b-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="93c0b-106">Pour plus d’informations sur le mécanisme de fournisseur de type dans F, voir [Fournisseurs de type](index.md).</span><span class="sxs-lookup"><span data-stu-id="93c0b-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="93c0b-107">L’écosystème FMD contient une gamme de fournisseurs de type pour les services de données Internet et d’entreprise couramment utilisés.</span><span class="sxs-lookup"><span data-stu-id="93c0b-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="93c0b-108">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="93c0b-108">For example:</span></span>

- <span data-ttu-id="93c0b-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) inclut les fournisseurs de type pour les formats de documents JSON, XML, CSV et HTML.</span><span class="sxs-lookup"><span data-stu-id="93c0b-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="93c0b-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) offre un accès fortement typé aux bases de données SQL par le biais d’une cartographie d’objets et de requêtes F-LINQ contre ces sources de données.</span><span class="sxs-lookup"><span data-stu-id="93c0b-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="93c0b-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) dispose d’un ensemble de fournisseurs de type pour l’intégration vérifiée en temps de compilation de T-SQL en F.</span><span class="sxs-lookup"><span data-stu-id="93c0b-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="93c0b-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) est un ancien ensemble de fournisseurs de type à utiliser uniquement avec la programmation cadre .NET pour accéder aux services de données SQL, Entity Framework, OData et WSDL.</span><span class="sxs-lookup"><span data-stu-id="93c0b-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="93c0b-113">Si nécessaire, vous pouvez créer des fournisseurs de type personnalisé, ou vous pouvez référencer les fournisseurs de type que d’autres ont créés.</span><span class="sxs-lookup"><span data-stu-id="93c0b-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="93c0b-114">Par exemple, votre organisation pourrait avoir un service de données qui fournit un nombre important et croissant d’ensembles de données nommés, chacun avec son propre schéma de données stables.</span><span class="sxs-lookup"><span data-stu-id="93c0b-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="93c0b-115">Vous pouvez créer un fournisseur de type qui lit les schémas et présente les ensembles de données actuels au programmeur d’une manière fortement tapée.</span><span class="sxs-lookup"><span data-stu-id="93c0b-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="93c0b-116">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="93c0b-116">Before You Start</span></span>

<span data-ttu-id="93c0b-117">Le mécanisme de fournisseur de type est principalement conçu pour injecter des espaces stables de données et d’information de service dans l’expérience de programmation de F.</span><span class="sxs-lookup"><span data-stu-id="93c0b-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="93c0b-118">Ce mécanisme n’est pas conçu pour injecter des espaces d’information dont le schéma change pendant l’exécution du programme d’une manière pertinente à la logique du programme.</span><span class="sxs-lookup"><span data-stu-id="93c0b-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="93c0b-119">En outre, le mécanisme n’est pas conçu pour la méta-programmation intra-langage, même si ce domaine contient quelques utilisations valides.</span><span class="sxs-lookup"><span data-stu-id="93c0b-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="93c0b-120">Vous ne devez utiliser ce mécanisme que si nécessaire et lorsque le développement d’un fournisseur de type donne une très grande valeur.</span><span class="sxs-lookup"><span data-stu-id="93c0b-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="93c0b-121">Vous devriez éviter d’écrire un fournisseur de type où un schéma n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="93c0b-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="93c0b-122">De même, vous devriez éviter d’écrire un fournisseur de type où une bibliothèque ordinaire (ou même existante) .NET suffirait.</span><span class="sxs-lookup"><span data-stu-id="93c0b-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="93c0b-123">Avant de commencer, vous pourriez poser les questions suivantes :</span><span class="sxs-lookup"><span data-stu-id="93c0b-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="93c0b-124">Avez-vous un schéma pour votre source d’information?</span><span class="sxs-lookup"><span data-stu-id="93c0b-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="93c0b-125">Dans l’affirmative, quelle est la cartographie dans le système de type F et NET ?</span><span class="sxs-lookup"><span data-stu-id="93c0b-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="93c0b-126">Pouvez-vous utiliser une API existante (dactylographié dynamiquement) comme point de départ pour votre mise en œuvre ?</span><span class="sxs-lookup"><span data-stu-id="93c0b-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="93c0b-127">Aurez-vous et votre organisation ont suffisamment d’utilisations du fournisseur de type pour le rendre utile à l’écriture?</span><span class="sxs-lookup"><span data-stu-id="93c0b-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="93c0b-128">Est-ce qu’une bibliothèque .NET normale répondrait à vos besoins?</span><span class="sxs-lookup"><span data-stu-id="93c0b-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="93c0b-129">Combien votre schéma va-t-il changer ?</span><span class="sxs-lookup"><span data-stu-id="93c0b-129">How much will your schema change?</span></span>

- <span data-ttu-id="93c0b-130">Va-t-il changer pendant le codage?</span><span class="sxs-lookup"><span data-stu-id="93c0b-130">Will it change during coding?</span></span>

- <span data-ttu-id="93c0b-131">Changera-t-il entre les sessions de codage ?</span><span class="sxs-lookup"><span data-stu-id="93c0b-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="93c0b-132">Cela changera-t-il pendant l’exécution du programme?</span><span class="sxs-lookup"><span data-stu-id="93c0b-132">Will it change during program execution?</span></span>

<span data-ttu-id="93c0b-133">Les fournisseurs de type sont les mieux adaptés aux situations où le schéma est stable au moment de l’exécution et pendant la durée de vie du code compilé.</span><span class="sxs-lookup"><span data-stu-id="93c0b-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="93c0b-134">Un fournisseur de type simple</span><span class="sxs-lookup"><span data-stu-id="93c0b-134">A Simple Type Provider</span></span>

<span data-ttu-id="93c0b-135">Cet échantillon est Samples.HelloWorldTypeProvider, similaire `examples` aux échantillons dans le répertoire du fournisseur de [type F SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="93c0b-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="93c0b-136">Le fournisseur met à disposition un «espace de type» qui contient 100 types effacés, comme le montre `Type1`le code suivant en utilisant la syntaxe signature F et en omettant les détails pour tous sauf .</span><span class="sxs-lookup"><span data-stu-id="93c0b-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="93c0b-137">Pour plus d’informations sur les types effacés, voir [Détails sur les types fournis effacés](#details-about-erased-provided-types) plus tard dans ce sujet.</span><span class="sxs-lookup"><span data-stu-id="93c0b-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

```fsharp
namespace Samples.HelloWorldTypeProvider

type Type1 =
    /// This is a static property.
    static member StaticProperty : string

    /// This constructor takes no arguments.
    new : unit -> Type1

    /// This constructor takes one argument.
    new : data:string -> Type1

    /// This is an instance property.
    member InstanceProperty : int

    /// This is an instance method.
    member InstanceMethod : x:int -> char

    nested type NestedType =
        /// This is StaticProperty1 on NestedType.
        static member StaticProperty1 : string
        …
        /// This is StaticProperty100 on NestedType.
        static member StaticProperty100 : string

type Type2 =
…
…

type Type100 =
…
```

<span data-ttu-id="93c0b-138">Notez que l’ensemble des types et des membres fournis est connu de façon statique.</span><span class="sxs-lookup"><span data-stu-id="93c0b-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="93c0b-139">Cet exemple ne tire pas parti de la capacité des fournisseurs de fournir des types qui dépendent d’un schéma.</span><span class="sxs-lookup"><span data-stu-id="93c0b-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="93c0b-140">La mise en œuvre du fournisseur de type est décrite dans le code suivant, et les détails sont couverts dans les sections ultérieures de ce sujet.</span><span class="sxs-lookup"><span data-stu-id="93c0b-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="93c0b-141">Il peut y avoir des différences entre ce code et les échantillons en ligne.</span><span class="sxs-lookup"><span data-stu-id="93c0b-141">There may be differences between this code and the online samples.</span></span>

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open ProviderImplementation.ProvidedTypes
open FSharp.Core.CompilerServices
open FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =

  // Inheriting from this type provides implementations of ITypeProvider
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces(config)

  let namespaceName = "Samples.HelloWorldTypeProvider"
  let thisAssembly = Assembly.GetExecutingAssembly()

  // Make one provided type, called TypeN.
  let makeOneProvidedType (n:int) =
  …
  // Now generate 100 types
  let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]

  // And add them to the namespace
  do this.AddNamespace(namespaceName, types)

[<assembly:TypeProviderAssembly>]
do()
```

<span data-ttu-id="93c0b-142">Pour utiliser ce fournisseur, ouvrez une instance distincte de Visual Studio, créez un script F, puis ajoutez une référence au fournisseur de votre script en utilisant #r comme le code suivant l’indique :</span><span class="sxs-lookup"><span data-stu-id="93c0b-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

```fsharp
#r @".\bin\Debug\Samples.HelloWorldTypeProvider.dll"

let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")

let obj2 = Samples.HelloWorldTypeProvider.Type1("some other data")

obj1.InstanceProperty
obj2.InstanceProperty

[ for index in 0 .. obj1.InstanceProperty-1 -> obj1.InstanceMethod(index) ]
[ for index in 0 .. obj2.InstanceProperty-1 -> obj2.InstanceMethod(index) ]

let data1 = Samples.HelloWorldTypeProvider.Type1.NestedType.StaticProperty35
```

<span data-ttu-id="93c0b-143">Ensuite, recherchez les `Samples.HelloWorldTypeProvider` types sous l’espace nom que le fournisseur de type généré.</span><span class="sxs-lookup"><span data-stu-id="93c0b-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="93c0b-144">Avant de recomposer le fournisseur, assurez-vous d’avoir fermé toutes les instances de Visual Studio et de F Interactive qui utilisent le fournisseur DLL.</span><span class="sxs-lookup"><span data-stu-id="93c0b-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="93c0b-145">Dans le cas contraire, une erreur de construction se produira parce que la sortie DLL sera verrouillée.</span><span class="sxs-lookup"><span data-stu-id="93c0b-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="93c0b-146">Pour déboiffer ce fournisseur en utilisant des instructions imprimées, faire un script qui expose un problème avec le fournisseur, puis utiliser le code suivant:</span><span class="sxs-lookup"><span data-stu-id="93c0b-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="93c0b-147">Pour déboguer ce fournisseur en utilisant Visual Studio, ouvrez le Developer Command Prompt pour Visual Studio avec des informations administratives, et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="93c0b-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="93c0b-148">Comme alternative, ouvrez Visual Studio, ouvrez `Debug/Attach to process…`le menu Debug, choisissez et attachez-vous à un autre `devenv` processus où vous modifiez votre script.</span><span class="sxs-lookup"><span data-stu-id="93c0b-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="93c0b-149">En utilisant cette méthode, vous pouvez plus facilement cibler une logique particulière dans le fournisseur de type en tapant interactivement des expressions dans la deuxième instance (avec IntelliSense complet et d’autres fonctionnalités).</span><span class="sxs-lookup"><span data-stu-id="93c0b-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="93c0b-150">Vous pouvez désactiver Just My Code débogage pour mieux identifier les erreurs dans le code généré.</span><span class="sxs-lookup"><span data-stu-id="93c0b-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="93c0b-151">Pour plus d’informations sur la façon d’activer ou désactiver cette fonctionnalité, voir [Naviguer à travers code avec le Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="93c0b-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="93c0b-152">En outre, vous pouvez également définir la `Debug` capture d’exception de première chance en ouvrant le menu, puis en choisissant `Exceptions` ou en choisissant les clés Ctrl-Alt-E pour ouvrir la boîte de `Exceptions` dialogue.</span><span class="sxs-lookup"><span data-stu-id="93c0b-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="93c0b-153">Dans cette boîte de `Common Language Runtime Exceptions`dialogue, `Thrown` sous , sélectionnez la case à cocher.</span><span class="sxs-lookup"><span data-stu-id="93c0b-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="93c0b-154">Mise en œuvre du fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="93c0b-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="93c0b-155">Cette section vous guide à travers les principales sections de la mise en œuvre du fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="93c0b-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="93c0b-156">Tout d’abord, vous définissez le type pour le fournisseur de type personnalisé lui-même:</span><span class="sxs-lookup"><span data-stu-id="93c0b-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="93c0b-157">Ce type doit être public, et vous devez le marquer avec l’attribut [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) de sorte que le compilateur reconnaîtra le fournisseur de type lorsqu’un projet F distinct fait référence à l’assemblage qui contient le type.</span><span class="sxs-lookup"><span data-stu-id="93c0b-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="93c0b-158">Le paramètre *config* est facultatif et, s’il est présent, contient des informations de configuration contextuelle pour l’instance type fournisseur que le compilateur F crée.</span><span class="sxs-lookup"><span data-stu-id="93c0b-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="93c0b-159">Ensuite, vous implémentez l’interface [ITypeProvider.](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f)</span><span class="sxs-lookup"><span data-stu-id="93c0b-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="93c0b-160">Dans ce cas, `TypeProviderForNamespaces` vous utilisez `ProvidedTypes` le type de l’API comme type de base.</span><span class="sxs-lookup"><span data-stu-id="93c0b-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="93c0b-161">Ce type d’aide peut fournir une collection limitée d’espaces de nom avidement fournis, dont chacun contient directement un nombre fini de types fixes, avidement fournis.</span><span class="sxs-lookup"><span data-stu-id="93c0b-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="93c0b-162">Dans ce contexte, le fournisseur génère *avec empressement* des types même s’ils ne sont pas nécessaires ou utilisés.</span><span class="sxs-lookup"><span data-stu-id="93c0b-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="93c0b-163">Ensuite, définissez les valeurs privées locales qui spécifient l’espace de nom pour les types fournis, et trouvez l’assemblage du fournisseur de type lui-même.</span><span class="sxs-lookup"><span data-stu-id="93c0b-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="93c0b-164">Cet assemblage est utilisé plus tard comme le type parent logique des types effacés qui sont fournis.</span><span class="sxs-lookup"><span data-stu-id="93c0b-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="93c0b-165">Ensuite, créez une fonction pour fournir chacun des types Type1... Type100.</span><span class="sxs-lookup"><span data-stu-id="93c0b-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="93c0b-166">Cette fonction est expliquée plus en détail plus tard dans ce sujet.</span><span class="sxs-lookup"><span data-stu-id="93c0b-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="93c0b-167">Ensuite, générer les 100 types fournis:</span><span class="sxs-lookup"><span data-stu-id="93c0b-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="93c0b-168">Ensuite, ajoutez les types comme un espace de nom fourni:</span><span class="sxs-lookup"><span data-stu-id="93c0b-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="93c0b-169">Enfin, ajoutez un attribut d’assemblage qui indique que vous créez un fournisseur de type DLL :</span><span class="sxs-lookup"><span data-stu-id="93c0b-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="93c0b-170">Fournir un type et ses membres</span><span class="sxs-lookup"><span data-stu-id="93c0b-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="93c0b-171">La `makeOneProvidedType` fonction fait le vrai travail de fournir l’un des types.</span><span class="sxs-lookup"><span data-stu-id="93c0b-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="93c0b-172">Cette étape explique la mise en œuvre de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="93c0b-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="93c0b-173">Tout d’abord, créez le type fourni (par exemple, Type1, quand n 1, ou Type57, quand n 57).</span><span class="sxs-lookup"><span data-stu-id="93c0b-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="93c0b-174">Vous devez noter les points suivants :</span><span class="sxs-lookup"><span data-stu-id="93c0b-174">You should note the following points:</span></span>

- <span data-ttu-id="93c0b-175">Ce type fourni est effacé.</span><span class="sxs-lookup"><span data-stu-id="93c0b-175">This provided type is erased.</span></span>  <span data-ttu-id="93c0b-176">Parce que vous indiquez `obj`que le type de base est , les instances apparaîtront comme des valeurs de type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) dans le code compilé.</span><span class="sxs-lookup"><span data-stu-id="93c0b-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="93c0b-177">Lorsque vous spécifiez un type non imbriqué, vous devez spécifier l’espace de l’assemblage et du nom.</span><span class="sxs-lookup"><span data-stu-id="93c0b-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="93c0b-178">Pour les types effacés, l’assemblage doit être le type d’assemblage fournisseur lui-même.</span><span class="sxs-lookup"><span data-stu-id="93c0b-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="93c0b-179">Ensuite, ajoutez la documentation XML au type.</span><span class="sxs-lookup"><span data-stu-id="93c0b-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="93c0b-180">Cette documentation est retardée, c’est-à-dire calculée à la demande si le compilateur hôte en a besoin.</span><span class="sxs-lookup"><span data-stu-id="93c0b-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="93c0b-181">Ensuite, vous ajoutez une propriété statique fournie au type:</span><span class="sxs-lookup"><span data-stu-id="93c0b-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="93c0b-182">Obtenir cette propriété sera toujours évaluer à la chaîne "Bonjour!".</span><span class="sxs-lookup"><span data-stu-id="93c0b-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="93c0b-183">Le `GetterCode` pour la propriété utilise une citation F, qui représente le code que le compilateur hôte génère pour obtenir la propriété.</span><span class="sxs-lookup"><span data-stu-id="93c0b-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="93c0b-184">Pour plus d’informations sur les citations, voir [Citations de code (F)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="93c0b-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="93c0b-185">Ajoutez de la documentation XML à la propriété.</span><span class="sxs-lookup"><span data-stu-id="93c0b-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="93c0b-186">Attachez maintenant la propriété fournie au type fourni.</span><span class="sxs-lookup"><span data-stu-id="93c0b-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="93c0b-187">Vous devez joindre un membre fourni à un seul et unique type.</span><span class="sxs-lookup"><span data-stu-id="93c0b-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="93c0b-188">Sinon, le membre ne sera jamais accessible.</span><span class="sxs-lookup"><span data-stu-id="93c0b-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="93c0b-189">Maintenant, créez un constructeur fourni qui ne prend aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="93c0b-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="93c0b-190">Le `InvokeCode` constructeur renvoie une citation F, qui représente le code que le compilateur hôte génère lorsque le constructeur est appelé.</span><span class="sxs-lookup"><span data-stu-id="93c0b-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="93c0b-191">Par exemple, vous pouvez utiliser le constructeur suivant :</span><span class="sxs-lookup"><span data-stu-id="93c0b-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="93c0b-192">Une instance du type fourni sera créée avec des données sous-jacentes "Les données de l’objet".</span><span class="sxs-lookup"><span data-stu-id="93c0b-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="93c0b-193">Le code cité comprend une conversion en [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) parce que ce type est l’effacement de ce type fourni (comme vous l’avez précisé lorsque vous avez déclaré le type fourni).</span><span class="sxs-lookup"><span data-stu-id="93c0b-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="93c0b-194">Ajouter la documentation XML au constructeur et ajouter le constructeur fourni au type fourni :</span><span class="sxs-lookup"><span data-stu-id="93c0b-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="93c0b-195">Créez un deuxième constructeur fourni qui prend un paramètre :</span><span class="sxs-lookup"><span data-stu-id="93c0b-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="93c0b-196">Le `InvokeCode` pour le constructeur retourne à nouveau une citation F, qui représente le code que le compilateur hôte généré pour un appel à la méthode.</span><span class="sxs-lookup"><span data-stu-id="93c0b-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="93c0b-197">Par exemple, vous pouvez utiliser le constructeur suivant :</span><span class="sxs-lookup"><span data-stu-id="93c0b-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="93c0b-198">Une instance du type fourni est créée avec des données sous-jacentes "dix".</span><span class="sxs-lookup"><span data-stu-id="93c0b-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="93c0b-199">Vous avez peut-être `InvokeCode` déjà remarqué que la fonction renvoie une citation.</span><span class="sxs-lookup"><span data-stu-id="93c0b-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="93c0b-200">L’entrée à cette fonction est une liste d’expressions, une par paramètre constructeur.</span><span class="sxs-lookup"><span data-stu-id="93c0b-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="93c0b-201">Dans ce cas, une expression qui représente `args.[0]`la valeur de paramètre unique est disponible en .</span><span class="sxs-lookup"><span data-stu-id="93c0b-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="93c0b-202">Le code d’appel au constructeur contraigne la valeur `obj`de retour au type effacé .</span><span class="sxs-lookup"><span data-stu-id="93c0b-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="93c0b-203">Après avoir ajouté le deuxième constructeur fourni au type, vous créez une propriété d’instance fournie :</span><span class="sxs-lookup"><span data-stu-id="93c0b-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="93c0b-204">Obtenir cette propriété retournera la longueur de la chaîne, qui est l’objet de représentation.</span><span class="sxs-lookup"><span data-stu-id="93c0b-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="93c0b-205">La `GetterCode` propriété renvoie une citation de F qui spécifie le code que le compilateur hôte génère pour obtenir la propriété.</span><span class="sxs-lookup"><span data-stu-id="93c0b-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="93c0b-206">Comme, `InvokeCode` `GetterCode` la fonction renvoie une citation.</span><span class="sxs-lookup"><span data-stu-id="93c0b-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="93c0b-207">Le compilateur hôte appelle cette fonction avec une liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="93c0b-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="93c0b-208">Dans ce cas, les arguments comprennent juste l’expression unique qui représente l’instance sur `args.[0]`laquelle l’getter est appelé, que vous pouvez accéder en utilisant .</span><span class="sxs-lookup"><span data-stu-id="93c0b-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="93c0b-209">La mise `GetterCode` en œuvre des épissages dans `obj`la citation de résultat au type effacé, et un plâtre est utilisé pour satisfaire le mécanisme du compilateur pour vérifier les types que l’objet est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="93c0b-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="93c0b-210">La partie `makeOneProvidedType` suivante fournit une méthode d’instance avec un paramètre.</span><span class="sxs-lookup"><span data-stu-id="93c0b-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

```fsharp
let instanceMeth =
    ProvidedMethod(methodName = "InstanceMethod",
                   parameters = [ProvidedParameter("x",typeof<int>)],
                   returnType = typeof<char>,
                   invokeCode = (fun args ->
                       <@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

<span data-ttu-id="93c0b-211">Enfin, créez un type imbriqué qui contient 100 propriétés imbriquées.</span><span class="sxs-lookup"><span data-stu-id="93c0b-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="93c0b-212">La création de ce type imbriqué et de ses propriétés est retardée, c’est-à-dire calculée à la demande.</span><span class="sxs-lookup"><span data-stu-id="93c0b-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () ->
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () ->
    let staticPropsInNestedType =
      [
          for i in 1 .. 100 ->
              let valueOfTheProperty = "I am string "  + string i

              let p =
                ProvidedProperty(propertyName = "StaticProperty" + string i,
                  propertyType = typeof<string>,
                  isStatic = true,
                  getterCode= (fun args -> <@@ valueOfTheProperty @@>))

              p.AddXmlDocDelayed(fun () ->
                  sprintf "This is StaticProperty%d on NestedType" i)

              p
      ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="93c0b-213">Détails sur les types fournis effacés</span><span class="sxs-lookup"><span data-stu-id="93c0b-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="93c0b-214">L’exemple de cette section ne fournit que des *types effacés fournis,* qui sont particulièrement utiles dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="93c0b-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="93c0b-215">Lorsque vous écrivez un fournisseur pour un espace d’information qui ne contient que des données et des méthodes.</span><span class="sxs-lookup"><span data-stu-id="93c0b-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="93c0b-216">Lorsque vous écrivez un fournisseur où la sémantique précise de type runtime n’est pas essentielle pour une utilisation pratique de l’espace d’information.</span><span class="sxs-lookup"><span data-stu-id="93c0b-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="93c0b-217">Lorsque vous écrivez un fournisseur pour un espace d’information qui est si grand et interconnecté qu’il n’est pas techniquement possible de générer de vrais types .NET pour l’espace d’information.</span><span class="sxs-lookup"><span data-stu-id="93c0b-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="93c0b-218">Dans cet exemple, chaque type fourni `obj`est effacé au type, et `obj` toutes les utilisations du type apparaîtront comme type dans le code compilé.</span><span class="sxs-lookup"><span data-stu-id="93c0b-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="93c0b-219">En fait, les objets sous-jacents dans ces exemples sont des chaînes, mais le type apparaîtra comme `System.Object` dans le code compilé .NET.</span><span class="sxs-lookup"><span data-stu-id="93c0b-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="93c0b-220">Comme avec toutes les utilisations de l’effacement de type, vous pouvez utiliser la boxe explicite, le déballage, et le moulage pour subvertir les types effacés.</span><span class="sxs-lookup"><span data-stu-id="93c0b-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="93c0b-221">Dans ce cas, une exception de casting qui n’est pas valide peut en résulter lorsque l’objet est utilisé.</span><span class="sxs-lookup"><span data-stu-id="93c0b-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="93c0b-222">Un runtime fournisseur peut définir son propre type de représentation privée pour aider à se protéger contre les fausses représentations.</span><span class="sxs-lookup"><span data-stu-id="93c0b-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="93c0b-223">Vous ne pouvez pas définir les types effacés en F lui-même.</span><span class="sxs-lookup"><span data-stu-id="93c0b-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="93c0b-224">Seuls les types fournis peuvent être effacés.</span><span class="sxs-lookup"><span data-stu-id="93c0b-224">Only provided types may be erased.</span></span> <span data-ttu-id="93c0b-225">Vous devez comprendre les ramifications, pratiques et sémantiques, d’utiliser soit des types effacés pour votre fournisseur de type ou un fournisseur qui fournit des types effacés.</span><span class="sxs-lookup"><span data-stu-id="93c0b-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="93c0b-226">Un type effacé n’a pas de type .NET réel.</span><span class="sxs-lookup"><span data-stu-id="93c0b-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="93c0b-227">Par conséquent, vous ne pouvez pas faire une réflexion précise sur le type, et vous pourriez subvertir les types effacés si vous utilisez des moulages de temps d’exécution et d’autres techniques qui s’appuient sur la sémantique exacte de type runtime.</span><span class="sxs-lookup"><span data-stu-id="93c0b-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="93c0b-228">La subversion des types effacés entraîne souvent des exceptions de type de fonte au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="93c0b-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="93c0b-229">Choisir des représentations pour les types fournis effacés</span><span class="sxs-lookup"><span data-stu-id="93c0b-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="93c0b-230">Pour certaines utilisations de types fournis effacés, aucune représentation n’est requise.</span><span class="sxs-lookup"><span data-stu-id="93c0b-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="93c0b-231">Par exemple, le type effacé fourni ne peut contenir que des propriétés statiques et des membres et aucun constructeur, et aucune méthode ou propriété ne retournerait une instance du type.</span><span class="sxs-lookup"><span data-stu-id="93c0b-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="93c0b-232">Si vous pouvez joindre des instances d’un type fourni effacé, vous devez tenir compte des questions suivantes :</span><span class="sxs-lookup"><span data-stu-id="93c0b-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="93c0b-233">**Quelle est l’effacement d’un type fourni?**</span><span class="sxs-lookup"><span data-stu-id="93c0b-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="93c0b-234">L’effacement d’un type fourni est la façon dont le type apparaît dans le code .NET compilé.</span><span class="sxs-lookup"><span data-stu-id="93c0b-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="93c0b-235">L’effacement d’un type de classe effacé fourni est toujours le premier type de base non effacé dans la chaîne d’héritage du type.</span><span class="sxs-lookup"><span data-stu-id="93c0b-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="93c0b-236">L’effacement d’un type d’interface effacé fourni est toujours `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="93c0b-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="93c0b-237">**Quelles sont les représentations d’un type fourni?**</span><span class="sxs-lookup"><span data-stu-id="93c0b-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="93c0b-238">L’ensemble d’objets possibles pour un type à condition effacé est appelé ses représentations.</span><span class="sxs-lookup"><span data-stu-id="93c0b-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="93c0b-239">Dans l’exemple de ce document, les représentations `Type1..Type100` de tous les types effacés fournis sont toujours des objets en chaîne.</span><span class="sxs-lookup"><span data-stu-id="93c0b-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="93c0b-240">Toutes les représentations d’un type fourni doivent être compatibles avec l’effacement du type fourni.</span><span class="sxs-lookup"><span data-stu-id="93c0b-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="93c0b-241">(Sinon, soit le compilateur F donnera une erreur pour une utilisation du fournisseur de type, ou un code .NET invérifiable qui n’est pas valide sera généré.</span><span class="sxs-lookup"><span data-stu-id="93c0b-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="93c0b-242">Un fournisseur de type n’est pas valide s’il renvoie du code qui donne une représentation qui n’est pas valide.)</span><span class="sxs-lookup"><span data-stu-id="93c0b-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="93c0b-243">Vous pouvez choisir une représentation pour les objets fournis en utilisant l’une ou l’autre des approches suivantes, qui sont toutes deux très courantes :</span><span class="sxs-lookup"><span data-stu-id="93c0b-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="93c0b-244">Si vous fournissez simplement un emballage fortement tapé sur un type .NET existant, il est souvent logique pour votre type d’effacer à ce type, utiliser des instances de ce type comme représentations, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="93c0b-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="93c0b-245">Cette approche est appropriée lorsque la plupart des méthodes existantes sur ce type ont encore du sens lors de l’utilisation de la version fortement tapée.</span><span class="sxs-lookup"><span data-stu-id="93c0b-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="93c0b-246">Si vous voulez créer une API qui diffère considérablement de tout API .NET existant, il est logique de créer des types de temps d’exécution qui seront l’effacement de type et les représentations pour les types fournis.</span><span class="sxs-lookup"><span data-stu-id="93c0b-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="93c0b-247">L’exemple dans ce document utilise les chaînes comme représentations d’objets fournis.</span><span class="sxs-lookup"><span data-stu-id="93c0b-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="93c0b-248">Fréquemment, il peut être approprié d’utiliser d’autres objets pour des représentations.</span><span class="sxs-lookup"><span data-stu-id="93c0b-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="93c0b-249">Par exemple, vous pouvez utiliser un dictionnaire comme sac de propriété :</span><span class="sxs-lookup"><span data-stu-id="93c0b-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="93c0b-250">Comme alternative, vous pouvez définir un type dans votre fournisseur de type qui sera utilisé à l’heure d’exécution pour former la représentation, ainsi qu’une ou plusieurs opérations de temps d’exécution :</span><span class="sxs-lookup"><span data-stu-id="93c0b-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="93c0b-251">Les membres à condition de construire des instances de ce type d’objet :</span><span class="sxs-lookup"><span data-stu-id="93c0b-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="93c0b-252">Dans ce cas, vous pouvez (optionnellement) utiliser ce type comme effacement de type en spécifiant ce type comme lors de la `baseType` construction de la `ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="93c0b-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="93c0b-253">Leçons clés</span><span class="sxs-lookup"><span data-stu-id="93c0b-253">Key Lessons</span></span>

<span data-ttu-id="93c0b-254">La section précédente expliquait comment créer un simple fournisseur de type effacement qui fournit une gamme de types, de propriétés et de méthodes.</span><span class="sxs-lookup"><span data-stu-id="93c0b-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="93c0b-255">Cette section a également expliqué le concept d’effacement de type, y compris certains des avantages et des inconvénients de fournir des types effacés d’un fournisseur de type, et a discuté des représentations des types effacés.</span><span class="sxs-lookup"><span data-stu-id="93c0b-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="93c0b-256">Un fournisseur de type qui utilise des paramètres statiques</span><span class="sxs-lookup"><span data-stu-id="93c0b-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="93c0b-257">La possibilité de paramétriser les fournisseurs de type par des données statiques permet de nombreux scénarios intéressants, même dans les cas où le fournisseur n’a pas besoin d’accéder à des données locales ou distantes.</span><span class="sxs-lookup"><span data-stu-id="93c0b-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="93c0b-258">Dans cette section, vous apprendrez quelques techniques de base pour mettre sur pied un tel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="93c0b-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="93c0b-259">Type Vérifié Regex Fournisseur</span><span class="sxs-lookup"><span data-stu-id="93c0b-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="93c0b-260">Imaginez que vous souhaitez implémenter un fournisseur <xref:System.Text.RegularExpressions.Regex> de type pour les expressions régulières qui enveloppe les bibliothèques .NET dans une interface qui fournit les garanties suivantes de temps de compilation :</span><span class="sxs-lookup"><span data-stu-id="93c0b-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="93c0b-261">Vérifier si une expression régulière est valide.</span><span class="sxs-lookup"><span data-stu-id="93c0b-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="93c0b-262">Fournir des propriétés nommées sur les correspondances qui sont basées sur les noms de groupe dans l’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="93c0b-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="93c0b-263">Cette section vous montre comment utiliser `RegexTyped` des fournisseurs de type pour créer un type que le modèle d’expression régulière paramélise pour fournir ces avantages.</span><span class="sxs-lookup"><span data-stu-id="93c0b-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="93c0b-264">Le compilateur signalera une erreur si le modèle fourni n’est pas valide, et le fournisseur de type peut extraire les groupes du modèle afin que vous puissiez y accéder en utilisant des propriétés nommées sur les allumettes.</span><span class="sxs-lookup"><span data-stu-id="93c0b-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="93c0b-265">Lorsque vous concevez un fournisseur de type, vous devez considérer comment son API exposé devrait regarder aux utilisateurs finaux et comment cette conception se traduira par le code .NET.</span><span class="sxs-lookup"><span data-stu-id="93c0b-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="93c0b-266">L’exemple suivant montre comment utiliser une telle API pour obtenir les composants du code régional :</span><span class="sxs-lookup"><span data-stu-id="93c0b-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="93c0b-267">L’exemple suivant montre comment le fournisseur de type traduit ces appels :</span><span class="sxs-lookup"><span data-stu-id="93c0b-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="93c0b-268">Notez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="93c0b-268">Note the following points:</span></span>

- <span data-ttu-id="93c0b-269">Le type Regex standard `RegexTyped` représente le type paramétré.</span><span class="sxs-lookup"><span data-stu-id="93c0b-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="93c0b-270">Le `RegexTyped` constructeur donne lieu à un appel au constructeur Regex, en passant dans l’argument de type statique pour le modèle.</span><span class="sxs-lookup"><span data-stu-id="93c0b-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="93c0b-271">Les résultats `Match` de la méthode sont <xref:System.Text.RegularExpressions.Match> représentés par le type standard.</span><span class="sxs-lookup"><span data-stu-id="93c0b-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="93c0b-272">Chaque groupe désigné se traduit par une propriété fournie, et l’accès à `Groups` la propriété entraîne l’utilisation d’un indexer sur la collection d’un match.</span><span class="sxs-lookup"><span data-stu-id="93c0b-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="93c0b-273">Le code suivant est au cœur de la logique pour implémenter un tel fournisseur, et cet exemple omet l’ajout de tous les membres au type fourni.</span><span class="sxs-lookup"><span data-stu-id="93c0b-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="93c0b-274">Pour obtenir de l’information sur chaque membre ajouté, consultez la section appropriée plus tard dans ce sujet.</span><span class="sxs-lookup"><span data-stu-id="93c0b-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="93c0b-275">Pour le code complet, téléchargez l’échantillon à partir du [pack d’échantillons F 3.0](https://archive.codeplex.com/?p=fsharp3sample) sur le site Web de CodePlex.</span><span class="sxs-lookup"><span data-stu-id="93c0b-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

          match parameterValues with
          | [| :? string as pattern|] ->

            // Create an instance of the regular expression.
            //
            // This will fail with System.ArgumentException if the regular expression is not valid.
            // The exception will escape the type provider and be reported in client code.
            let r = System.Text.RegularExpressions.Regex(pattern)

            // Declare the typed regex provided type.
            // The type erasure of this type is 'obj', even though the representation will always be a Regex
            // This, combined with hiding the object methods, makes the IntelliSense experience simpler.
            let ty =
              ProvidedTypeDefinition(
                thisAssembly,
                rootNamespace,
                typeName,
                baseType = Some baseTy)

            ...

            ty
          | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

<span data-ttu-id="93c0b-276">Notez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="93c0b-276">Note the following points:</span></span>

- <span data-ttu-id="93c0b-277">Le fournisseur de type prend `pattern`deux paramètres statiques: `options`le , qui est obligatoire, et le , qui sont facultatifs (parce qu’une valeur par défaut est fournie).</span><span class="sxs-lookup"><span data-stu-id="93c0b-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="93c0b-278">Une fois les arguments statiques fournis, vous créez un exemple de l’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="93c0b-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="93c0b-279">Cette instance jettera une exception si le Regex est mal formé, et cette erreur sera signalée aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="93c0b-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="93c0b-280">Dans `DefineStaticParameters` le rappel, vous définissez le type qui sera retourné après que les arguments sont fournis.</span><span class="sxs-lookup"><span data-stu-id="93c0b-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="93c0b-281">Ce code `HideObjectMethods` s’établit à vrai afin que l’expérience IntelliSense reste rationalisée.</span><span class="sxs-lookup"><span data-stu-id="93c0b-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="93c0b-282">Cet attribut `Equals`provoque `GetHashCode` `Finalize`le `GetType` , , et les membres d’être supprimés à partir de listes IntelliSense pour un objet fourni.</span><span class="sxs-lookup"><span data-stu-id="93c0b-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="93c0b-283">Vous `obj` utilisez comme type de base de la `Regex` méthode, mais vous allez utiliser un objet comme la représentation en temps d’exécution de ce type, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="93c0b-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="93c0b-284">L’appel `Regex` au constructeur lance <xref:System.ArgumentException> un quand une expression régulière n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="93c0b-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="93c0b-285">Le compilateur saisit cette exception et signale un message d’erreur à l’utilisateur à l’heure de compilation ou dans l’éditeur Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93c0b-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="93c0b-286">Cette exception permet de valider les expressions régulières sans exécuter d’application.</span><span class="sxs-lookup"><span data-stu-id="93c0b-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="93c0b-287">Le type défini ci-dessus n’est pas encore utile parce qu’il ne contient pas de méthodes ou de propriétés significatives.</span><span class="sxs-lookup"><span data-stu-id="93c0b-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="93c0b-288">Tout d’abord, ajouter une méthode statique: `IsMatch`</span><span class="sxs-lookup"><span data-stu-id="93c0b-288">First, add a static `IsMatch` method:</span></span>

```fsharp
let isMatch =
    ProvidedMethod(
        methodName = "IsMatch",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = typeof<bool>,
        isStatic = true,
        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string."
ty.AddMember isMatch
```

<span data-ttu-id="93c0b-289">Le code précédent définit `IsMatch`une méthode , qui prend `bool`une chaîne comme entrée et renvoie un .</span><span class="sxs-lookup"><span data-stu-id="93c0b-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="93c0b-290">La seule partie délicate est `args` l’utilisation `InvokeCode` de l’argument dans la définition.</span><span class="sxs-lookup"><span data-stu-id="93c0b-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="93c0b-291">Dans cet `args` exemple, est une liste de citations qui représente les arguments à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="93c0b-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="93c0b-292">Si la méthode est une méthode d’instance, le premier argument représente l’argument. `this`</span><span class="sxs-lookup"><span data-stu-id="93c0b-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="93c0b-293">Cependant, pour une méthode statique, les arguments ne sont que les arguments explicites de la méthode.</span><span class="sxs-lookup"><span data-stu-id="93c0b-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="93c0b-294">Notez que le type de valeur citée doit correspondre au `bool`type de retour spécifié (dans ce cas, ).</span><span class="sxs-lookup"><span data-stu-id="93c0b-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="93c0b-295">Notez également que `AddXmlDoc` ce code utilise la méthode pour s’assurer que la méthode fournie dispose également d’une documentation utile, que vous pouvez fournir par IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="93c0b-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="93c0b-296">Ensuite, ajoutez une méthode de match d’instance.</span><span class="sxs-lookup"><span data-stu-id="93c0b-296">Next, add an instance Match method.</span></span> <span data-ttu-id="93c0b-297">Toutefois, cette méthode devrait retourner `Match` une valeur de type fourni afin que les groupes puissent être consultés d’une manière fortement tapée.</span><span class="sxs-lookup"><span data-stu-id="93c0b-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="93c0b-298">Ainsi, vous déclarez d’abord le `Match` type.</span><span class="sxs-lookup"><span data-stu-id="93c0b-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="93c0b-299">Étant donné que ce type dépend du modèle qui a été fourni comme argument statique, ce type doit être imbriqué dans la définition de type paramétré :</span><span class="sxs-lookup"><span data-stu-id="93c0b-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="93c0b-300">Vous ajoutez ensuite une propriété au type Match pour chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="93c0b-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="93c0b-301">Au moment de l’exécution, <xref:System.Text.RegularExpressions.Match> une correspondance est représentée comme une valeur, <xref:System.Text.RegularExpressions.Match.Groups> de sorte que la citation qui définit la propriété doit utiliser la propriété indexée pour obtenir le groupe concerné.</span><span class="sxs-lookup"><span data-stu-id="93c0b-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

```fsharp
for group in r.GetGroupNames() do
    // Ignore the group named 0, which represents all input.
    if group <> "0" then
    let prop =
      ProvidedProperty(
        propertyName = group,
        propertyType = typeof<Group>,
        getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
    matchTy.AddMember prop
```

<span data-ttu-id="93c0b-302">Encore une fois, notez que vous ajoutez la documentation XML à la propriété fournie.</span><span class="sxs-lookup"><span data-stu-id="93c0b-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="93c0b-303">Notez également qu’une propriété `GetterCode` peut être lue si une `SetterCode` fonction est fournie, et la propriété peut être écrite si une fonction est fournie, de sorte que la propriété résultante est lue seulement.</span><span class="sxs-lookup"><span data-stu-id="93c0b-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="93c0b-304">Maintenant, vous pouvez créer une méthode `Match` d’instance qui renvoie une valeur de ce type:</span><span class="sxs-lookup"><span data-stu-id="93c0b-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod =
    ProvidedMethod(
        methodName = "Match",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = matchTy,
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

ty.AddMember matchMeth
```

<span data-ttu-id="93c0b-305">Parce que vous créez `args.[0]` une `RegexTyped` méthode d’instance, représente l’instance sur laquelle la méthode est appelée, et `args.[1]` est l’argument de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="93c0b-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="93c0b-306">Enfin, fournir un constructeur afin que des instances du type fourni puissent être créées.</span><span class="sxs-lookup"><span data-stu-id="93c0b-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="93c0b-307">Le constructeur efface simplement à la création d’une instance standard .NET Regex, qui est à nouveau en boîte à un objet parce que `obj` c’est l’effacement du type fourni.</span><span class="sxs-lookup"><span data-stu-id="93c0b-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="93c0b-308">Avec ce changement, l’utilisation de l’API échantillon qui spécifié plus tôt dans le sujet fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="93c0b-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="93c0b-309">Le code suivant est complet et définitif :</span><span class="sxs-lookup"><span data-stu-id="93c0b-309">The following code is complete and final:</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types.
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams,
        instantiationFunction=(fun typeName parameterValues ->

            match parameterValues with
            | [| :? string as pattern|] ->

                // Create an instance of the regular expression.

                let r = System.Text.RegularExpressions.Regex(pattern)

                // Declare the typed regex provided type.

                let ty =
                    ProvidedTypeDefinition(
                        thisAssembly,
                        rootNamespace,
                        typeName,
                        baseType = Some baseTy)

                ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

                // Provide strongly typed version of Regex.IsMatch static method.
                let isMatch =
                    ProvidedMethod(
                        methodName = "IsMatch",
                        parameters = [ProvidedParameter("input", typeof<string>)],
                        returnType = typeof<bool>,
                        isStatic = true,
                        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>)

                isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

                ty.AddMember isMatch

                // Provided type for matches
                // Again, erase to obj even though the representation will always be a Match
                let matchTy =
                    ProvidedTypeDefinition(
                        "MatchType",
                        baseType = Some baseTy,
                        hideObjectMethods = true)

                // Nest the match type within parameterized Regex type.
                ty.AddMember matchTy

                // Add group properties to match type
                for group in r.GetGroupNames() do
                    // Ignore the group named 0, which represents all input.
                    if group <> "0" then
                        let prop =
                          ProvidedProperty(
                            propertyName = group,
                            propertyType = typeof<Group>,
                            getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
                        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
                        matchTy.AddMember(prop)

                // Provide strongly typed version of Regex.Match instance method.
                let matchMeth =
                  ProvidedMethod(
                    methodName = "Match",
                    parameters = [ProvidedParameter("input", typeof<string>)],
                    returnType = matchTy,
                    invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

                ty.AddMember matchMeth

                // Declare a constructor.
                let ctor =
                  ProvidedConstructor(
                    parameters = [],
                    invokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

                // Add documentation to the constructor.
                ctor.AddXmlDoc "Initializes a regular expression instance"

                ty.AddMember ctor

                ty
            | _ -> failwith "unexpected parameter values"))

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

### <a name="key-lessons"></a><span data-ttu-id="93c0b-310">Leçons clés</span><span class="sxs-lookup"><span data-stu-id="93c0b-310">Key Lessons</span></span>

<span data-ttu-id="93c0b-311">Cette section a expliqué comment créer un fournisseur de type qui fonctionne sur ses paramètres statiques.</span><span class="sxs-lookup"><span data-stu-id="93c0b-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="93c0b-312">Le fournisseur vérifie le paramètre statique et fournit des opérations en fonction de sa valeur.</span><span class="sxs-lookup"><span data-stu-id="93c0b-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="93c0b-313">Un fournisseur de type qui est soutenu par des données locales</span><span class="sxs-lookup"><span data-stu-id="93c0b-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="93c0b-314">Fréquemment, vous pouvez vouloir des fournisseurs de type pour présenter des API basées non seulement sur des paramètres statiques, mais aussi des informations provenant de systèmes locaux ou distants.</span><span class="sxs-lookup"><span data-stu-id="93c0b-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="93c0b-315">Cette section traite des fournisseurs de type qui sont basés sur des données locales, telles que les fichiers de données locaux.</span><span class="sxs-lookup"><span data-stu-id="93c0b-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="93c0b-316">Fournisseur de fichiers CSV simple</span><span class="sxs-lookup"><span data-stu-id="93c0b-316">Simple CSV File Provider</span></span>

<span data-ttu-id="93c0b-317">À titre d’exemple, considérez un fournisseur de type pour accéder aux données scientifiques dans le format Comma Separated Value (CSV).</span><span class="sxs-lookup"><span data-stu-id="93c0b-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="93c0b-318">Cette section suppose que les fichiers CSV contiennent une rangée d’en-têtes suivie de données de points flottants, comme l’illustre le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="93c0b-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="93c0b-319">Distance (mètre)</span><span class="sxs-lookup"><span data-stu-id="93c0b-319">Distance (meter)</span></span>|<span data-ttu-id="93c0b-320">Temps (deuxième)</span><span class="sxs-lookup"><span data-stu-id="93c0b-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="93c0b-321">50.0</span><span class="sxs-lookup"><span data-stu-id="93c0b-321">50.0</span></span>|<span data-ttu-id="93c0b-322">3.7</span><span class="sxs-lookup"><span data-stu-id="93c0b-322">3.7</span></span>|
|<span data-ttu-id="93c0b-323">100.0</span><span class="sxs-lookup"><span data-stu-id="93c0b-323">100.0</span></span>|<span data-ttu-id="93c0b-324">5.2</span><span class="sxs-lookup"><span data-stu-id="93c0b-324">5.2</span></span>|
|<span data-ttu-id="93c0b-325">150.0</span><span class="sxs-lookup"><span data-stu-id="93c0b-325">150.0</span></span>|<span data-ttu-id="93c0b-326">6.4</span><span class="sxs-lookup"><span data-stu-id="93c0b-326">6.4</span></span>|

<span data-ttu-id="93c0b-327">Cette section montre comment fournir un type que vous `Distance` pouvez utiliser `float<meter>` pour `Time` obtenir `float<second>`des rangées avec une propriété de type et une propriété de type .</span><span class="sxs-lookup"><span data-stu-id="93c0b-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="93c0b-328">Par souci de simplicité, les hypothèses suivantes sont faites :</span><span class="sxs-lookup"><span data-stu-id="93c0b-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="93c0b-329">Les noms d’en-tête sont soit unitaires ou ont le formulaire "Nom (unité)" et ne contiennent pas de virgules.</span><span class="sxs-lookup"><span data-stu-id="93c0b-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="93c0b-330">Les unités sont toutes des unités System International (SI) comme le définit le module [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) .</span><span class="sxs-lookup"><span data-stu-id="93c0b-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="93c0b-331">Les unités sont toutes simples (par exemple, compteur) plutôt que composé (par exemple, compteur /seconde).</span><span class="sxs-lookup"><span data-stu-id="93c0b-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="93c0b-332">Toutes les colonnes contiennent des données de points flottants.</span><span class="sxs-lookup"><span data-stu-id="93c0b-332">All columns contain floating point data.</span></span>

<span data-ttu-id="93c0b-333">Un fournisseur plus complet assouplirait ces restrictions.</span><span class="sxs-lookup"><span data-stu-id="93c0b-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="93c0b-334">Encore une fois, la première étape consiste à examiner à quoi devrait ressembler l’API.</span><span class="sxs-lookup"><span data-stu-id="93c0b-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="93c0b-335">Compte `info.csv` tenu d’un fichier avec le contenu du tableau précédent (en format virgule séparé), les utilisateurs du fournisseur doivent être en mesure d’écrire du code qui ressemble à l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="93c0b-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="93c0b-336">Dans ce cas, le compilateur devrait convertir ces appels en quelque chose comme l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="93c0b-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="93c0b-337">La traduction optimale exigera du fournisseur `CsvFile` de type qu’il définisse un type réel dans l’assemblage du fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="93c0b-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="93c0b-338">Les fournisseurs de type comptent souvent sur quelques types et méthodes d’aide pour envelopper la logique importante.</span><span class="sxs-lookup"><span data-stu-id="93c0b-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="93c0b-339">Parce que les mesures sont effacées `float[]` au moment de la course, vous pouvez utiliser un type effacé pour une rangée.</span><span class="sxs-lookup"><span data-stu-id="93c0b-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="93c0b-340">Le compilateur traitera différentes colonnes comme ayant différents types de mesure.</span><span class="sxs-lookup"><span data-stu-id="93c0b-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="93c0b-341">Par exemple, la première colonne `float<meter>`dans notre exemple `float<second>`a le type , et le second a .</span><span class="sxs-lookup"><span data-stu-id="93c0b-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="93c0b-342">Cependant, la représentation effacée peut rester assez simple.</span><span class="sxs-lookup"><span data-stu-id="93c0b-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="93c0b-343">Le code suivant montre le cœur de l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="93c0b-343">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data =
        seq {
            for line in File.ReadAllLines(filename) |> Seq.skip 1 ->
                line.Split(',') |> Array.map float
        }
        |> Seq.cache
    member _.Data = data

[<TypeProvider>]
type public MiniCsvProvider(cfg:TypeProviderConfig) as this =
    inherit TypeProviderForNamespaces(cfg)

    // Get the assembly and namespace used to house the provided types.
    let asm = System.Reflection.Assembly.GetExecutingAssembly()
    let ns = "Samples.FSharp.MiniCsvProvider"

    // Create the main provided type.
    let csvTy = ProvidedTypeDefinition(asm, ns, "MiniCsv", Some(typeof<obj>))

    // Parameterize the type by the file to use as a template.
    let filename = ProvidedStaticParameter("filename", typeof<string>)
    do csvTy.DefineStaticParameters([filename], fun tyName [| :? string as filename |] ->

        // Resolve the filename relative to the resolution folder.
        let resolvedFilename = Path.Combine(cfg.ResolutionFolder, filename)

        // Get the first line from the file.
        let headerLine = File.ReadLines(resolvedFilename) |> Seq.head

        // Define a provided type for each row, erasing to a float[].
        let rowTy = ProvidedTypeDefinition("Row", Some(typeof<float[]>))

        // Extract header names from the file, splitting on commas.
        // use Regex matching to get the position in the row at which the field occurs
        let headers = Regex.Matches(headerLine, "[^,]+")

        // Add one property per CSV field.
        for i in 0 .. headers.Count - 1 do
            let headerText = headers.[i].Value

            // Try to decompose this header into a name and unit.
            let fieldName, fieldTy =
                let m = Regex.Match(headerText, @"(?<field>.+) \((?<unit>.+)\)")
                if m.Success then

                    let unitName = m.Groups.["unit"].Value
                    let units = ProvidedMeasureBuilder.Default.SI unitName
                    m.Groups.["field"].Value, ProvidedMeasureBuilder.Default.AnnotateType(typeof<float>,[units])

                else
                    // no units, just treat it as a normal float
                    headerText, typeof<float>

            let prop =
                ProvidedProperty(fieldName, fieldTy,
                    getterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

            // Add metadata that defines the property's location in the referenced file.
            prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
            rowTy.AddMember(prop)

        // Define the provided type, erasing to CsvFile.
        let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

        // Add a parameterless constructor that loads the file that was used to define the schema.
        let ctor0 =
            ProvidedConstructor([],
                invokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
        ty.AddMember ctor0

        // Add a constructor that takes the file name to load.
        let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)],
            invokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
        ty.AddMember ctor1

        // Add a more strongly typed Data property, which uses the existing property at runtime.
        let prop =
            ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy),
                getterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
        ty.AddMember prop

        // Add the row type as a nested type.
        ty.AddMember rowTy
        ty)

    // Add the type to the namespace.
    do this.AddNamespace(ns, [csvTy])
```

<span data-ttu-id="93c0b-344">Notez les points suivants sur la mise en œuvre :</span><span class="sxs-lookup"><span data-stu-id="93c0b-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="93c0b-345">Les constructeurs surchargés permettent soit à l’ancien fichier, soit à un schéma identique d’être lu.</span><span class="sxs-lookup"><span data-stu-id="93c0b-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="93c0b-346">Ce modèle est courant lorsque vous écrivez un fournisseur de type pour les sources de données locales ou distantes, et ce modèle permet à un fichier local d’être utilisé comme modèle pour les données à distance.</span><span class="sxs-lookup"><span data-stu-id="93c0b-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="93c0b-347">Vous pouvez utiliser la valeur [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) qui est transmise au constructeur fournisseur de type pour résoudre les noms de fichiers relatifs.</span><span class="sxs-lookup"><span data-stu-id="93c0b-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="93c0b-348">Vous pouvez `AddDefinitionLocation` utiliser la méthode pour définir l’emplacement des propriétés fournies.</span><span class="sxs-lookup"><span data-stu-id="93c0b-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="93c0b-349">Par conséquent, `Go To Definition` si vous utilisez sur une propriété fournie, le fichier CSV s’ouvrira dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93c0b-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="93c0b-350">Vous pouvez `ProvidedMeasureBuilder` utiliser le type pour rechercher les `float<_>` unités SI et pour générer les types pertinents.</span><span class="sxs-lookup"><span data-stu-id="93c0b-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="93c0b-351">Leçons clés</span><span class="sxs-lookup"><span data-stu-id="93c0b-351">Key Lessons</span></span>

<span data-ttu-id="93c0b-352">Cette section a expliqué comment créer un fournisseur de type pour une source de données locale avec un schéma simple qui est contenu dans la source de données elle-même.</span><span class="sxs-lookup"><span data-stu-id="93c0b-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="93c0b-353">Aller plus loin</span><span class="sxs-lookup"><span data-stu-id="93c0b-353">Going Further</span></span>

<span data-ttu-id="93c0b-354">Les sections suivantes contiennent des suggestions pour une étude plus approfondie.</span><span class="sxs-lookup"><span data-stu-id="93c0b-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="93c0b-355">Un regard sur le code compilé pour les types effacés</span><span class="sxs-lookup"><span data-stu-id="93c0b-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="93c0b-356">Pour vous donner une idée de la façon dont l’utilisation du fournisseur de type correspond `HelloWorldTypeProvider` au code émis, regardez la fonction suivante en utilisant le qui est utilisé plus tôt dans ce sujet.</span><span class="sxs-lookup"><span data-stu-id="93c0b-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="93c0b-357">Voici une image du code résultant décomposé en utilisant ildasm.exe:</span><span class="sxs-lookup"><span data-stu-id="93c0b-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```il
.class public abstract auto ansi sealed Module1
extends [mscorlib]System.Object
{
.custom instance void [FSharp.Core]Microsoft.FSharp.Core.CompilationMappingAtt
ribute::.ctor(valuetype [FSharp.Core]Microsoft.FSharp.Core.SourceConstructFlags)
= ( 01 00 07 00 00 00 00 00 )
.method public static int32  function1() cil managed
{
// Code size       24 (0x18)
.maxstack  3
.locals init ([0] object obj1)
IL_0000:  nop
IL_0001:  ldstr      "some data"
IL_0006:  unbox.any  [mscorlib]System.Object
IL_000b:  stloc.0
IL_000c:  ldloc.0
IL_000d:  call       !!0 [FSharp.Core_2]Microsoft.FSharp.Core.LanguagePrimit
ives/IntrinsicFunctions::UnboxGeneric<string>(object)
IL_0012:  callvirt   instance int32 [mscorlib_3]System.String::get_Length()
IL_0017:  ret
} // end of method Module1::function1

} // end of class Module1
```

<span data-ttu-id="93c0b-358">Comme l’exemple le montre, `Type1` toutes `InstanceProperty` les mentions du type et de la propriété ont été effacées, ne laissant que des opérations sur les types de temps d’exécution impliqués.</span><span class="sxs-lookup"><span data-stu-id="93c0b-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="93c0b-359">Conventions de conception et de nomination pour les fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="93c0b-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="93c0b-360">Observez les conventions suivantes lors de la rédaction de fournisseurs de type.</span><span class="sxs-lookup"><span data-stu-id="93c0b-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="93c0b-361">**Fournisseurs de protocoles de connectivité** En général, les noms de la plupart des DLS fournisseurs pour les protocoles de `TypeProvider` connectivité `TypeProviders`des données et des services, tels que les connexions OData ou SQL, devraient se terminer ou .</span><span class="sxs-lookup"><span data-stu-id="93c0b-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="93c0b-362">Par exemple, utilisez un nom DLL qui ressemble à la chaîne suivante :</span><span class="sxs-lookup"><span data-stu-id="93c0b-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="93c0b-363">Assurez-vous que vos types fournis sont membres de l’espace nom correspondant et indiquez le protocole de connectivité que vous avez mis en œuvre :</span><span class="sxs-lookup"><span data-stu-id="93c0b-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="93c0b-364">**Fournisseurs de services publics pour le codage général**.</span><span class="sxs-lookup"><span data-stu-id="93c0b-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="93c0b-365">Pour un fournisseur de type utilitaire comme celui pour les expressions régulières, le fournisseur de type peut faire partie d’une bibliothèque de base, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="93c0b-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="93c0b-366">Dans ce cas, le type fourni apparaîtrait à un point approprié selon les conventions normales de conception .NET :</span><span class="sxs-lookup"><span data-stu-id="93c0b-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="93c0b-367">**Sources de données Singleton**.</span><span class="sxs-lookup"><span data-stu-id="93c0b-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="93c0b-368">Certains fournisseurs de type se connectent à une seule source de données dédiées et ne fournissent que des données.</span><span class="sxs-lookup"><span data-stu-id="93c0b-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="93c0b-369">Dans ce cas, vous `TypeProvider` devez laisser tomber le suffixe et utiliser des conventions normales pour .NET nommant:</span><span class="sxs-lookup"><span data-stu-id="93c0b-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="93c0b-370">Pour plus d’informations, voir la `GetConnection` convention de conception qui est décrite plus tard dans ce sujet.</span><span class="sxs-lookup"><span data-stu-id="93c0b-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="93c0b-371">Modèles de conception pour les fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="93c0b-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="93c0b-372">Les sections suivantes décrivent les modèles de conception que vous pouvez utiliser lors de la rédaction de fournisseurs de type.</span><span class="sxs-lookup"><span data-stu-id="93c0b-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="93c0b-373">Le modèle de conception GetConnection</span><span class="sxs-lookup"><span data-stu-id="93c0b-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="93c0b-374">La plupart des fournisseurs de `GetConnection` type doivent être écrits pour utiliser le modèle utilisé par les fournisseurs de type dans FSharp.Data.TypeProviders.dll, comme le montre l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="93c0b-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="93c0b-375">Fournisseurs de types soutenus par des données et des services à distance</span><span class="sxs-lookup"><span data-stu-id="93c0b-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="93c0b-376">Avant de créer un fournisseur de type qui est soutenu par des données et des services distants, vous devez tenir compte d’une gamme de questions inhérentes à la programmation connectée.</span><span class="sxs-lookup"><span data-stu-id="93c0b-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="93c0b-377">Ces questions comprennent les considérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="93c0b-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="93c0b-378">cartographie du schéma</span><span class="sxs-lookup"><span data-stu-id="93c0b-378">schema mapping</span></span>

- <span data-ttu-id="93c0b-379">la vivacité et l’invalidation en présence de changement de schéma</span><span class="sxs-lookup"><span data-stu-id="93c0b-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="93c0b-380">mise en cache de schémas</span><span class="sxs-lookup"><span data-stu-id="93c0b-380">schema caching</span></span>

- <span data-ttu-id="93c0b-381">mises en œuvre asynchrone des opérations d’accès aux données</span><span class="sxs-lookup"><span data-stu-id="93c0b-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="93c0b-382">demandes à l’appui, y compris les requêtes LINQ</span><span class="sxs-lookup"><span data-stu-id="93c0b-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="93c0b-383">informations d’identification et authentification</span><span class="sxs-lookup"><span data-stu-id="93c0b-383">credentials and authentication</span></span>

<span data-ttu-id="93c0b-384">Ce sujet n’explore pas ces questions plus loin.</span><span class="sxs-lookup"><span data-stu-id="93c0b-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="93c0b-385">Techniques d’auteur supplémentaires</span><span class="sxs-lookup"><span data-stu-id="93c0b-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="93c0b-386">Lorsque vous écrivez vos propres fournisseurs de type, vous pouvez utiliser les techniques supplémentaires suivantes.</span><span class="sxs-lookup"><span data-stu-id="93c0b-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="93c0b-387">Création de types et de membres à la demande</span><span class="sxs-lookup"><span data-stu-id="93c0b-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="93c0b-388">L’API ProvidedType a retardé les versions d’AddMember.</span><span class="sxs-lookup"><span data-stu-id="93c0b-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="93c0b-389">Ces versions sont utilisées pour créer des espaces à la demande de types.</span><span class="sxs-lookup"><span data-stu-id="93c0b-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="93c0b-390">Fournir des types de tableaux et des instantanéisissements de type génériques</span><span class="sxs-lookup"><span data-stu-id="93c0b-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="93c0b-391">Vous faites des membres fournis (dont les signatures comprennent les types de tableau, les `MakeArrayType` `MakePointerType`types `MakeGenericType` byref, <xref:System.Type>et `ProvidedTypeDefinitions`les instantanéiations des types génériques) en utilisant la normale , , et sur n’importe quel cas de , y compris .</span><span class="sxs-lookup"><span data-stu-id="93c0b-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="93c0b-392">Dans certains cas, vous devrez peut-être utiliser l’aide dans `ProvidedTypeBuilder.MakeGenericType`.</span><span class="sxs-lookup"><span data-stu-id="93c0b-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="93c0b-393">Consultez la [documentation SDK de Type Provider](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) pour plus de détails.</span><span class="sxs-lookup"><span data-stu-id="93c0b-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="93c0b-394">Fournir une unité d’annotations de mesure</span><span class="sxs-lookup"><span data-stu-id="93c0b-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="93c0b-395">L’API ProvidedTypes fournit des aides pour fournir des annotations de mesure.</span><span class="sxs-lookup"><span data-stu-id="93c0b-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="93c0b-396">Par exemple, pour `float<kg>`fournir le type, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="93c0b-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="93c0b-397">Pour fournir `Nullable<decimal<kg/m^2>>`le type, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="93c0b-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="93c0b-398">Accès aux ressources project-local ou script-local</span><span class="sxs-lookup"><span data-stu-id="93c0b-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="93c0b-399">Chaque instance d’un fournisseur `TypeProviderConfig` de type peut être donnée une valeur pendant la construction.</span><span class="sxs-lookup"><span data-stu-id="93c0b-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="93c0b-400">Cette valeur contient le « dossier de résolution » pour le fournisseur (c’est-à-dire le dossier de projet pour la compilation ou l’annuaire qui contient un script), la liste des assemblages référencés et d’autres informations.</span><span class="sxs-lookup"><span data-stu-id="93c0b-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="93c0b-401">Invalidation</span><span class="sxs-lookup"><span data-stu-id="93c0b-401">Invalidation</span></span>

<span data-ttu-id="93c0b-402">Les fournisseurs peuvent soulever des signaux d’invalidation pour aviser le service linguistique FD que les hypothèses de schéma peuvent avoir changé.</span><span class="sxs-lookup"><span data-stu-id="93c0b-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="93c0b-403">Lorsque l’invalidation se produit, un typecheck est refait si le fournisseur est hébergé dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93c0b-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="93c0b-404">Ce signal sera ignoré lorsque le fournisseur est hébergé dans F Interactive ou par le compilateur F (fsc.exe).</span><span class="sxs-lookup"><span data-stu-id="93c0b-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="93c0b-405">Caching Schema Informations</span><span class="sxs-lookup"><span data-stu-id="93c0b-405">Caching Schema Information</span></span>

<span data-ttu-id="93c0b-406">Les fournisseurs doivent souvent cacher l’accès à l’information sur les schémas.</span><span class="sxs-lookup"><span data-stu-id="93c0b-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="93c0b-407">Les données mises en cache doivent être stockées à l’aide d’un nom de fichier qui est donné sous forme de paramètre statique ou de données utilisateur.</span><span class="sxs-lookup"><span data-stu-id="93c0b-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="93c0b-408">Un exemple de mise en `LocalSchemaFile` cache de schéma `FSharp.Data.TypeProviders` est le paramètre dans les fournisseurs de type dans l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="93c0b-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="93c0b-409">Dans la mise en œuvre de ces fournisseurs, ce paramètre statique ordonne au fournisseur de type d’utiliser les informations schématiques dans le fichier local spécifié au lieu d’accéder à la source de données sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="93c0b-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="93c0b-410">Pour utiliser des informations de schéma mise en `ForceUpdate` `false`cache, vous devez également définir le paramètre statique à .</span><span class="sxs-lookup"><span data-stu-id="93c0b-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="93c0b-411">Vous pouvez utiliser une technique similaire pour activer l’accès aux données en ligne et hors ligne.</span><span class="sxs-lookup"><span data-stu-id="93c0b-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="93c0b-412">Assemblée de soutien</span><span class="sxs-lookup"><span data-stu-id="93c0b-412">Backing Assembly</span></span>

<span data-ttu-id="93c0b-413">Lorsque vous compilez `.exe` un ou un `.dll` fichier, le fichier support .dll pour les types générés est statiquement lié à l’assemblage résultant.</span><span class="sxs-lookup"><span data-stu-id="93c0b-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="93c0b-414">Ce lien est créé en copiant les définitions de type Langue intermédiaire (IL) et toutes les ressources gérées de l’assemblage de soutien à l’assemblage final.</span><span class="sxs-lookup"><span data-stu-id="93c0b-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="93c0b-415">Lorsque vous utilisez F Interactive, le fichier support .dll n’est pas copié et est plutôt chargé directement dans le processus interactif F.</span><span class="sxs-lookup"><span data-stu-id="93c0b-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="93c0b-416">Exceptions et diagnostics de la part des fournisseurs de types</span><span class="sxs-lookup"><span data-stu-id="93c0b-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="93c0b-417">Toutes les utilisations de tous les membres des types fournis peuvent jeter des exceptions.</span><span class="sxs-lookup"><span data-stu-id="93c0b-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="93c0b-418">Dans tous les cas, si un fournisseur de type lance une exception, le compilateur hôte attribue l’erreur à un fournisseur de type spécifique.</span><span class="sxs-lookup"><span data-stu-id="93c0b-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="93c0b-419">Les exceptions des fournisseurs de type ne devraient jamais entraîner d’erreurs internes de compilateur.</span><span class="sxs-lookup"><span data-stu-id="93c0b-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="93c0b-420">Les fournisseurs de type ne peuvent pas signaler les avertissements.</span><span class="sxs-lookup"><span data-stu-id="93c0b-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="93c0b-421">Lorsqu’un fournisseur de type est hébergé dans le compilateur F, un environnement de développement FMD ou F Interactive, toutes les exceptions de ce fournisseur sont prises.</span><span class="sxs-lookup"><span data-stu-id="93c0b-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="93c0b-422">La propriété Message est toujours le texte d’erreur, et aucune trace de pile n’apparaît.</span><span class="sxs-lookup"><span data-stu-id="93c0b-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="93c0b-423">Si vous allez jeter une exception, vous pouvez `System.NotSupportedException`jeter `System.IO.IOException` `System.Exception`les exemples suivants: , .</span><span class="sxs-lookup"><span data-stu-id="93c0b-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="93c0b-424">Fournir des types générés</span><span class="sxs-lookup"><span data-stu-id="93c0b-424">Providing Generated Types</span></span>

<span data-ttu-id="93c0b-425">Jusqu’à présent, ce document a expliqué comment fournir des types effacés.</span><span class="sxs-lookup"><span data-stu-id="93c0b-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="93c0b-426">Vous pouvez également utiliser le mécanisme de fournisseur de type dans F pour fournir les types générés, qui sont ajoutés comme définitions réelles de type .NET dans le programme des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="93c0b-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="93c0b-427">Vous devez vous référer aux types produits en utilisant une définition de type.</span><span class="sxs-lookup"><span data-stu-id="93c0b-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="93c0b-428">Le code d’assistance ProvidedTypes-0.2 qui fait partie de la version F 3.0 n’a qu’un soutien limité pour fournir des types générés.</span><span class="sxs-lookup"><span data-stu-id="93c0b-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="93c0b-429">Les énoncés suivants doivent être valables pour une définition de type générée :</span><span class="sxs-lookup"><span data-stu-id="93c0b-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="93c0b-430">`isErased` doit être défini sur `false`.</span><span class="sxs-lookup"><span data-stu-id="93c0b-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="93c0b-431">Le type généré doit être `ProvidedAssembly()`ajouté à un nouveau bâtiment, qui représente un conteneur pour les fragments de code générés.</span><span class="sxs-lookup"><span data-stu-id="93c0b-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="93c0b-432">Le fournisseur doit avoir un assemblage qui a un fichier support .NET .dll réel avec un fichier correspondant .dll sur le disque.</span><span class="sxs-lookup"><span data-stu-id="93c0b-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="93c0b-433">Règles et limites</span><span class="sxs-lookup"><span data-stu-id="93c0b-433">Rules and Limitations</span></span>

<span data-ttu-id="93c0b-434">Lorsque vous écrivez des fournisseurs de type, gardez à l’esprit les règles et les limitations suivantes.</span><span class="sxs-lookup"><span data-stu-id="93c0b-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="93c0b-435">À condition que les types soient accessibles</span><span class="sxs-lookup"><span data-stu-id="93c0b-435">Provided types must be reachable</span></span>

<span data-ttu-id="93c0b-436">Tous les types fournis doivent être accessibles à partir des types non imbriqués.</span><span class="sxs-lookup"><span data-stu-id="93c0b-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="93c0b-437">Les types non imbriqués sont `TypeProviderForNamespaces` donnés dans l’appel au constructeur ou un appel à `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="93c0b-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="93c0b-438">Par exemple, si le `StaticClass.P : T`fournisseur fournit un type, vous devez vous assurer que T est soit un type non imbriqué ou imbriqué sous un seul.</span><span class="sxs-lookup"><span data-stu-id="93c0b-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="93c0b-439">Par exemple, certains fournisseurs ont `DataTypes` une classe `T1, T2, T3, ...` statique comme celle qui contient ces types.</span><span class="sxs-lookup"><span data-stu-id="93c0b-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="93c0b-440">Sinon, l’erreur dit qu’une référence au type T dans l’assemblage A a été trouvée, mais le type n’a pas pu être trouvé dans cet assemblage.</span><span class="sxs-lookup"><span data-stu-id="93c0b-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="93c0b-441">Si cette erreur apparaît, vérifiez que tous vos sous-types peuvent être atteints à partir des types de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="93c0b-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="93c0b-442">Remarque : `T1, T2, T3...` Ces types sont appelés les types à *la volée.*</span><span class="sxs-lookup"><span data-stu-id="93c0b-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="93c0b-443">N’oubliez pas de les mettre dans un espace nom accessible ou un type de parent.</span><span class="sxs-lookup"><span data-stu-id="93c0b-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="93c0b-444">Limitations du mécanisme de fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="93c0b-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="93c0b-445">Le mécanisme de fournisseur de type dans le FMD a les limites suivantes :</span><span class="sxs-lookup"><span data-stu-id="93c0b-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="93c0b-446">L’infrastructure sous-jacente pour les fournisseurs de type dans F N’appuie pas les types génériques fournis ou fourni des méthodes génériques.</span><span class="sxs-lookup"><span data-stu-id="93c0b-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="93c0b-447">Le mécanisme ne prend pas en charge les types imbriqués avec des paramètres statiques.</span><span class="sxs-lookup"><span data-stu-id="93c0b-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="93c0b-448">Conseils de développement</span><span class="sxs-lookup"><span data-stu-id="93c0b-448">Development Tips</span></span>

<span data-ttu-id="93c0b-449">Vous trouverez peut-être les conseils suivants utiles pendant le processus de développement :</span><span class="sxs-lookup"><span data-stu-id="93c0b-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="93c0b-450">Exécuter deux instances de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="93c0b-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="93c0b-451">Vous pouvez développer le fournisseur de type dans un cas et tester le fournisseur dans l’autre parce que le test IDE prendra un verrou sur le fichier .dll qui empêche le fournisseur de type d’être reconstruit.</span><span class="sxs-lookup"><span data-stu-id="93c0b-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="93c0b-452">Ainsi, vous devez fermer la deuxième instance de Visual Studio pendant que le fournisseur est construit dans le premier cas, puis vous devez rouvrir la deuxième instance après la construction du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="93c0b-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="93c0b-453">Fournisseurs de type Debug en utilisant des invocations de fsc.exe</span><span class="sxs-lookup"><span data-stu-id="93c0b-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="93c0b-454">Vous pouvez invoquer des fournisseurs de type en utilisant les outils suivants :</span><span class="sxs-lookup"><span data-stu-id="93c0b-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="93c0b-455">fsc.exe (Compilateur de ligne de commande F)</span><span class="sxs-lookup"><span data-stu-id="93c0b-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="93c0b-456">fsi.exe (Compilateur interactif de F)</span><span class="sxs-lookup"><span data-stu-id="93c0b-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="93c0b-457">devenv.exe (Studio visuel)</span><span class="sxs-lookup"><span data-stu-id="93c0b-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="93c0b-458">Vous pouvez souvent déboquer les fournisseurs de type le plus facilement en utilisant fsc.exe sur un fichier de script de test (par exemple, script.fsx).</span><span class="sxs-lookup"><span data-stu-id="93c0b-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="93c0b-459">Vous pouvez lancer un débbugger à partir d’une invite de commande.</span><span class="sxs-lookup"><span data-stu-id="93c0b-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="93c0b-460">Vous pouvez utiliser l’enregistrement d’impression à stdout.</span><span class="sxs-lookup"><span data-stu-id="93c0b-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="93c0b-461">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93c0b-461">See also</span></span>

- [<span data-ttu-id="93c0b-462">Fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="93c0b-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="93c0b-463">Le fournisseur de type SDK</span><span class="sxs-lookup"><span data-stu-id="93c0b-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
