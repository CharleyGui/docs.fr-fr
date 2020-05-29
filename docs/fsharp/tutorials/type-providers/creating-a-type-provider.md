---
title: 'Didacticiel : créer un fournisseur de type'
description: 'Découvrez comment créer vos propres fournisseurs de type F # dans F # 3,0 en examinant plusieurs fournisseurs de types simples pour illustrer les concepts de base.'
ms.date: 11/04/2019
ms.openlocfilehash: 67ebd91007ff814370573ebc1a65b2c7a8399f7d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202130"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="900cf-103">Didacticiel : créer un fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="900cf-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="900cf-104">Le mécanisme du fournisseur de type en F # est une partie importante de la prise en charge de la programmation riche en informations.</span><span class="sxs-lookup"><span data-stu-id="900cf-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="900cf-105">Ce didacticiel explique comment créer vos propres fournisseurs de type en vous guidant tout au long du développement de plusieurs fournisseurs de types simples pour illustrer les concepts de base.</span><span class="sxs-lookup"><span data-stu-id="900cf-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="900cf-106">Pour plus d’informations sur le mécanisme du fournisseur de type en F #, consultez [fournisseurs de type](index.md).</span><span class="sxs-lookup"><span data-stu-id="900cf-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="900cf-107">L’écosystème F # contient une plage de fournisseurs de type pour les services de données Internet et d’entreprise couramment utilisés.</span><span class="sxs-lookup"><span data-stu-id="900cf-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="900cf-108">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="900cf-108">For example:</span></span>

- <span data-ttu-id="900cf-109">[FSharp. Data](https://fsharp.github.io/FSharp.Data/) comprend des fournisseurs de type pour les formats de documents JSON, XML, CSV et html.</span><span class="sxs-lookup"><span data-stu-id="900cf-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="900cf-110">[SqlProvider](https://fsprojects.github.io/SQLProvider/) fournit un accès fortement typé aux bases de données SQL via un mappage d’objets et des requêtes LINQ F # sur ces sources de données.</span><span class="sxs-lookup"><span data-stu-id="900cf-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="900cf-111">[FSharp. Data. SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) possède un ensemble de fournisseurs de type pour l’incorporation activée de T-SQL au moment de la compilation en F #.</span><span class="sxs-lookup"><span data-stu-id="900cf-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="900cf-112">[FSharp. Data. TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) est un ancien ensemble de fournisseurs de type à utiliser uniquement avec .NET Framework programmation pour l’accès aux services de données SQL, Entity Framework, ODATA et WSDL.</span><span class="sxs-lookup"><span data-stu-id="900cf-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="900cf-113">Le cas échéant, vous pouvez créer des fournisseurs de type personnalisé, ou référencer des fournisseurs de type que d’autres ont créés.</span><span class="sxs-lookup"><span data-stu-id="900cf-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="900cf-114">Par exemple, votre organisation peut avoir un service de données qui fournit un nombre important et croissant de jeux de données nommés, chacun avec son propre schéma de données stable.</span><span class="sxs-lookup"><span data-stu-id="900cf-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="900cf-115">Vous pouvez créer un fournisseur de type qui lit les schémas et présente les jeux de données actuels au programmeur de manière fortement typée.</span><span class="sxs-lookup"><span data-stu-id="900cf-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="900cf-116">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="900cf-116">Before You Start</span></span>

<span data-ttu-id="900cf-117">Le mécanisme du fournisseur de type est principalement conçu pour injecter des données stables et des espaces d’informations de service dans l’expérience de programmation F #.</span><span class="sxs-lookup"><span data-stu-id="900cf-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="900cf-118">Ce mécanisme n’est pas conçu pour injecter des espaces d’information dont le schéma est modifié pendant l’exécution du programme, en ce qui concerne la logique du programme.</span><span class="sxs-lookup"><span data-stu-id="900cf-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="900cf-119">En outre, le mécanisme n’est pas conçu pour la méta-programmation intra-langage, même si ce domaine contient des utilisations valides.</span><span class="sxs-lookup"><span data-stu-id="900cf-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="900cf-120">Vous devez utiliser ce mécanisme uniquement lorsque cela est nécessaire et lorsque le développement d’un fournisseur de type produit une valeur très élevée.</span><span class="sxs-lookup"><span data-stu-id="900cf-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="900cf-121">Évitez d’écrire un fournisseur de type dans lequel un schéma n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="900cf-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="900cf-122">De même, vous devez éviter d’écrire un fournisseur de type dans lequel une bibliothèque .NET ordinaire (ou même une bibliothèque existante) suffirait.</span><span class="sxs-lookup"><span data-stu-id="900cf-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="900cf-123">Avant de commencer, vous pouvez poser les questions suivantes :</span><span class="sxs-lookup"><span data-stu-id="900cf-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="900cf-124">Disposez-vous d’un schéma pour votre source d’informations ?</span><span class="sxs-lookup"><span data-stu-id="900cf-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="900cf-125">Dans ce cas, qu’est-ce que le mappage dans le système de type F # et .NET ?</span><span class="sxs-lookup"><span data-stu-id="900cf-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="900cf-126">Pouvez-vous utiliser une API existante (de type dynamique) comme point de départ pour votre implémentation ?</span><span class="sxs-lookup"><span data-stu-id="900cf-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="900cf-127">Votre organisation et vous-même avez-vous des utilisations suffisantes du fournisseur de type pour que l’écriture soit utile ?</span><span class="sxs-lookup"><span data-stu-id="900cf-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="900cf-128">Une bibliothèque .NET normale répond-elle à vos besoins ?</span><span class="sxs-lookup"><span data-stu-id="900cf-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="900cf-129">Combien votre schéma sera-t-il modifié ?</span><span class="sxs-lookup"><span data-stu-id="900cf-129">How much will your schema change?</span></span>

- <span data-ttu-id="900cf-130">Va-t-il changer au cours du codage ?</span><span class="sxs-lookup"><span data-stu-id="900cf-130">Will it change during coding?</span></span>

- <span data-ttu-id="900cf-131">Sera-t-il modifié entre les sessions de codage ?</span><span class="sxs-lookup"><span data-stu-id="900cf-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="900cf-132">Va-t-il changer au cours de l’exécution du programme ?</span><span class="sxs-lookup"><span data-stu-id="900cf-132">Will it change during program execution?</span></span>

<span data-ttu-id="900cf-133">Les fournisseurs de type sont mieux adaptés aux situations où le schéma est stable au moment de l’exécution et Pendant la durée de vie du code compilé.</span><span class="sxs-lookup"><span data-stu-id="900cf-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="900cf-134">Un fournisseur de type simple</span><span class="sxs-lookup"><span data-stu-id="900cf-134">A Simple Type Provider</span></span>

<span data-ttu-id="900cf-135">Cet exemple est Samples. HelloWorldTypeProvider, de la même façon que les exemples du `examples` répertoire du [Kit de développement logiciel (SDK) du fournisseur de type F #](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="900cf-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="900cf-136">Le fournisseur met à disposition un « espace de type » qui contient 100 types effacés, comme le montre le code suivant en utilisant la syntaxe de signature F # et en omettant les détails pour tous les sauf `Type1` .</span><span class="sxs-lookup"><span data-stu-id="900cf-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="900cf-137">Pour plus d’informations sur les types effacés, consultez [Détails sur les types fournis effacés](#details-about-erased-provided-types) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="900cf-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="900cf-138">Notez que le jeu de types et de membres fourni est statiquement connu.</span><span class="sxs-lookup"><span data-stu-id="900cf-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="900cf-139">Cet exemple ne tire pas parti de la capacité des fournisseurs à fournir des types qui dépendent d’un schéma.</span><span class="sxs-lookup"><span data-stu-id="900cf-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="900cf-140">L’implémentation du fournisseur de type est présentée dans le code suivant, et les détails sont traités dans les sections ultérieures de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="900cf-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="900cf-141">Il peut y avoir des différences entre ce code et les exemples en ligne.</span><span class="sxs-lookup"><span data-stu-id="900cf-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="900cf-142">Pour utiliser ce fournisseur, ouvrez une instance distincte de Visual Studio, créez un script F #, puis ajoutez une référence au fournisseur à partir de votre script à l’aide de #r comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="900cf-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="900cf-143">Recherchez ensuite les types sous l' `Samples.HelloWorldTypeProvider` espace de noms généré par le fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="900cf-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="900cf-144">Avant de recompiler le fournisseur, assurez-vous que vous avez fermé toutes les instances de Visual Studio et F# Interactive qui utilisent la DLL du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="900cf-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="900cf-145">Sinon, une erreur de génération se produit, car la DLL de sortie est verrouillée.</span><span class="sxs-lookup"><span data-stu-id="900cf-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="900cf-146">Pour déboguer ce fournisseur à l’aide d’instructions print, créez un script qui expose un problème au fournisseur, puis utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="900cf-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="900cf-147">Pour déboguer ce fournisseur à l’aide de Visual Studio, ouvrez le Invite de commandes développeur pour Visual Studio avec les informations d’identification d’administration, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="900cf-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="900cf-148">Au lieu de cela, ouvrez Visual Studio, ouvrez le menu Déboguer, choisissez `Debug/Attach to process…` , puis attachez à un autre `devenv` processus dans lequel vous modifiez votre script.</span><span class="sxs-lookup"><span data-stu-id="900cf-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="900cf-149">À l’aide de cette méthode, vous pouvez cibler plus facilement une logique particulière dans le fournisseur de type en tapant de manière interactive des expressions dans la deuxième instance (avec IntelliSense complet et d’autres fonctionnalités).</span><span class="sxs-lookup"><span data-stu-id="900cf-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="900cf-150">Vous pouvez désactiver le débogage Uniquement mon code pour mieux identifier les erreurs dans le code généré.</span><span class="sxs-lookup"><span data-stu-id="900cf-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="900cf-151">Pour plus d’informations sur l’activation ou la désactivation de cette fonctionnalité, consultez [navigation dans le code avec le débogueur](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="900cf-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="900cf-152">En outre, vous pouvez également définir l’interception des exceptions de première chance en ouvrant le `Debug` menu, puis `Exceptions` en choisissant ou en appuyant sur les touches Ctrl + Alt + E pour ouvrir la `Exceptions` boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="900cf-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="900cf-153">Dans cette boîte de dialogue, sous `Common Language Runtime Exceptions` , activez la `Thrown` case à cocher.</span><span class="sxs-lookup"><span data-stu-id="900cf-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="900cf-154">Implémentation du fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="900cf-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="900cf-155">Cette section vous guide à travers les principales sections de l’implémentation du fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="900cf-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="900cf-156">Tout d’abord, vous définissez le type du fournisseur de type personnalisé lui-même :</span><span class="sxs-lookup"><span data-stu-id="900cf-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="900cf-157">Ce type doit être public, et vous devez le marquer avec l’attribut [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) afin que le compilateur reconnaisse le fournisseur de type lorsqu’un projet F # distinct référence l’assembly qui contient le type.</span><span class="sxs-lookup"><span data-stu-id="900cf-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="900cf-158">Le paramètre de *configuration* est facultatif et, le cas échéant, contient des informations de configuration contextuelle pour l’instance de fournisseur de type créée par le compilateur F #.</span><span class="sxs-lookup"><span data-stu-id="900cf-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="900cf-159">Ensuite, implémentez l’interface [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) .</span><span class="sxs-lookup"><span data-stu-id="900cf-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="900cf-160">Dans ce cas, vous utilisez le `TypeProviderForNamespaces` type de l' `ProvidedTypes` API comme type de base.</span><span class="sxs-lookup"><span data-stu-id="900cf-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="900cf-161">Ce type d’assistance peut fournir une collection finie d’espaces de noms fournis de façon dynamique, chacun d’entre eux contenant directement un nombre fini de types fixes et fournis de façon dynamique.</span><span class="sxs-lookup"><span data-stu-id="900cf-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="900cf-162">Dans ce contexte, le fournisseur génère des types de manière *dynamique* , même s’ils ne sont pas nécessaires ou utilisés.</span><span class="sxs-lookup"><span data-stu-id="900cf-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="900cf-163">Ensuite, définissez les valeurs privées locales qui spécifient l’espace de noms pour les types fournis et recherchez l’assembly du fournisseur de type lui-même.</span><span class="sxs-lookup"><span data-stu-id="900cf-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="900cf-164">Cet assembly est utilisé ultérieurement comme type de parent logique des types effacés fournis.</span><span class="sxs-lookup"><span data-stu-id="900cf-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="900cf-165">Ensuite, créez une fonction pour fournir chacun des types Type1... Type100.</span><span class="sxs-lookup"><span data-stu-id="900cf-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="900cf-166">Cette fonction est expliquée plus en détail plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="900cf-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="900cf-167">Ensuite, générez les types fournis par 100 :</span><span class="sxs-lookup"><span data-stu-id="900cf-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="900cf-168">Ensuite, ajoutez les types en tant qu’espace de noms fourni :</span><span class="sxs-lookup"><span data-stu-id="900cf-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="900cf-169">Enfin, ajoutez un attribut d’assembly qui indique que vous créez une DLL de fournisseur de type :</span><span class="sxs-lookup"><span data-stu-id="900cf-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="900cf-170">Fournir un type et ses membres</span><span class="sxs-lookup"><span data-stu-id="900cf-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="900cf-171">La `makeOneProvidedType` fonction effectue le véritable travail de fourniture de l’un des types.</span><span class="sxs-lookup"><span data-stu-id="900cf-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="900cf-172">Cette étape explique l’implémentation de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="900cf-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="900cf-173">Tout d’abord, créez le type fourni (par exemple, type1, lorsque n = 1 ou Type57, quand n = 57).</span><span class="sxs-lookup"><span data-stu-id="900cf-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="900cf-174">Notez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="900cf-174">You should note the following points:</span></span>

- <span data-ttu-id="900cf-175">Ce type fourni est effacé.</span><span class="sxs-lookup"><span data-stu-id="900cf-175">This provided type is erased.</span></span>  <span data-ttu-id="900cf-176">Étant donné que vous indiquez que le type `obj` de base est, les instances s’affichent en tant que valeurs de type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) dans le code compilé.</span><span class="sxs-lookup"><span data-stu-id="900cf-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="900cf-177">Lorsque vous spécifiez un type non imbriqué, vous devez spécifier l’assembly et l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="900cf-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="900cf-178">Pour les types effacés, l’assembly doit être l’assembly du fournisseur de type lui-même.</span><span class="sxs-lookup"><span data-stu-id="900cf-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="900cf-179">Ensuite, ajoutez la documentation XML au type.</span><span class="sxs-lookup"><span data-stu-id="900cf-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="900cf-180">Cette documentation est retardée, c’est-à-dire calculée à la demande si le compilateur hôte en a besoin.</span><span class="sxs-lookup"><span data-stu-id="900cf-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="900cf-181">Ensuite, vous ajoutez une propriété statique fournie au type :</span><span class="sxs-lookup"><span data-stu-id="900cf-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="900cf-182">L’obtention de cette propriété correspond toujours à la chaîne « Hello ! ».</span><span class="sxs-lookup"><span data-stu-id="900cf-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="900cf-183">Le `GetterCode` de la propriété utilise un quotation F #, qui représente le code généré par le compilateur hôte pour obtenir la propriété.</span><span class="sxs-lookup"><span data-stu-id="900cf-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="900cf-184">Pour plus d’informations sur les guillemets, consultez [Quotations de code (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="900cf-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="900cf-185">Ajoutez la documentation XML à la propriété.</span><span class="sxs-lookup"><span data-stu-id="900cf-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="900cf-186">Attachez à présent la propriété fournie au type fourni.</span><span class="sxs-lookup"><span data-stu-id="900cf-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="900cf-187">Vous devez attacher un membre fourni à un seul et unique type.</span><span class="sxs-lookup"><span data-stu-id="900cf-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="900cf-188">Dans le cas contraire, le membre ne sera jamais accessible.</span><span class="sxs-lookup"><span data-stu-id="900cf-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="900cf-189">Créez maintenant un constructeur fourni qui ne prend aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="900cf-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="900cf-190">`InvokeCode`Pour le constructeur retourne un quotation F #, qui représente le code que le compilateur hôte génère lorsque le constructeur est appelé.</span><span class="sxs-lookup"><span data-stu-id="900cf-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="900cf-191">Par exemple, vous pouvez utiliser le constructeur suivant :</span><span class="sxs-lookup"><span data-stu-id="900cf-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="900cf-192">Une instance du type fourni sera créée avec les données sous-jacentes « données de l’objet ».</span><span class="sxs-lookup"><span data-stu-id="900cf-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="900cf-193">Le code entre guillemets comprend une conversion en [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) , car ce type est l’effacement de ce type fourni (comme vous l’avez spécifié quand vous avez déclaré le type fourni).</span><span class="sxs-lookup"><span data-stu-id="900cf-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="900cf-194">Ajoutez la documentation XML au constructeur et ajoutez le constructeur fourni au type fourni :</span><span class="sxs-lookup"><span data-stu-id="900cf-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="900cf-195">Créez un deuxième constructeur fourni qui accepte un paramètre :</span><span class="sxs-lookup"><span data-stu-id="900cf-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="900cf-196">Le du `InvokeCode` constructeur retourne à nouveau un quotation F #, qui représente le code généré par le compilateur hôte pour un appel à la méthode.</span><span class="sxs-lookup"><span data-stu-id="900cf-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="900cf-197">Par exemple, vous pouvez utiliser le constructeur suivant :</span><span class="sxs-lookup"><span data-stu-id="900cf-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="900cf-198">Une instance du type fourni est créée avec les données sous-jacentes « dix ».</span><span class="sxs-lookup"><span data-stu-id="900cf-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="900cf-199">Vous avez peut-être déjà remarqué que la `InvokeCode` fonction retourne une quotation.</span><span class="sxs-lookup"><span data-stu-id="900cf-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="900cf-200">L’entrée de cette fonction est une liste d’expressions, une par paramètre de constructeur.</span><span class="sxs-lookup"><span data-stu-id="900cf-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="900cf-201">Dans ce cas, une expression qui représente la valeur d’un paramètre unique est disponible dans `args.[0]` .</span><span class="sxs-lookup"><span data-stu-id="900cf-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="900cf-202">Le code d’un appel au constructeur convertit la valeur de retour en type effacé `obj` .</span><span class="sxs-lookup"><span data-stu-id="900cf-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="900cf-203">Après avoir ajouté le deuxième constructeur fourni au type, vous créez une propriété d’instance fournie :</span><span class="sxs-lookup"><span data-stu-id="900cf-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="900cf-204">L’obtention de cette propriété retourne la longueur de la chaîne, qui est l’objet de représentation.</span><span class="sxs-lookup"><span data-stu-id="900cf-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="900cf-205">La `GetterCode` propriété retourne un quotation F # qui spécifie le code que le compilateur hôte génère pour recevoir la propriété.</span><span class="sxs-lookup"><span data-stu-id="900cf-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="900cf-206">Comme `InvokeCode` , la `GetterCode` fonction retourne une quotation.</span><span class="sxs-lookup"><span data-stu-id="900cf-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="900cf-207">Le compilateur hôte appelle cette fonction avec une liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="900cf-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="900cf-208">Dans ce cas, les arguments incluent uniquement l’expression unique qui représente l’instance sur laquelle l’accesseur Get est appelé, auquel vous pouvez accéder à l’aide de `args.[0]` .</span><span class="sxs-lookup"><span data-stu-id="900cf-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="900cf-209">L’implémentation de `GetterCode` , puis les épissures dans le devis de résultat au type effacé `obj` , et un cast est utilisé pour satisfaire le mécanisme du compilateur pour vérifier les types que l’objet est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="900cf-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="900cf-210">La partie suivante de `makeOneProvidedType` fournit une méthode d’instance avec un paramètre.</span><span class="sxs-lookup"><span data-stu-id="900cf-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="900cf-211">Enfin, créez un type imbriqué qui contient 100 propriétés imbriquées.</span><span class="sxs-lookup"><span data-stu-id="900cf-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="900cf-212">La création de ce type imbriqué et de ses propriétés est différée, c’est-à-dire calculée à la demande.</span><span class="sxs-lookup"><span data-stu-id="900cf-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="900cf-213">Détails sur les types fournis effacés</span><span class="sxs-lookup"><span data-stu-id="900cf-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="900cf-214">L’exemple de cette section fournit uniquement des *types fournis effacés*, qui sont particulièrement utiles dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="900cf-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="900cf-215">Lorsque vous écrivez un fournisseur pour un espace d’informations qui contient uniquement des données et des méthodes.</span><span class="sxs-lookup"><span data-stu-id="900cf-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="900cf-216">Lorsque vous écrivez un fournisseur dans lequel la sémantique de type Runtime exacte n’est pas essentielle pour une utilisation pratique de l’espace d’information.</span><span class="sxs-lookup"><span data-stu-id="900cf-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="900cf-217">Lorsque vous écrivez un fournisseur pour un espace d’informations tellement grand et interconnecté, il n’est techniquement pas possible de générer des types .NET réels pour l’espace d’information.</span><span class="sxs-lookup"><span data-stu-id="900cf-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="900cf-218">Dans cet exemple, chaque type fourni est effacé en type `obj` , et toutes les utilisations du type s’affichent en tant que type `obj` dans le code compilé.</span><span class="sxs-lookup"><span data-stu-id="900cf-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="900cf-219">En fait, les objets sous-jacents dans ces exemples sont des chaînes, mais le type apparaît comme `System.Object` dans le code compilé .net.</span><span class="sxs-lookup"><span data-stu-id="900cf-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="900cf-220">Comme pour toutes les utilisations de l’effacement de type, vous pouvez utiliser le boxing, l’unboxing et le cast explicites pour corrompre les types effacés.</span><span class="sxs-lookup"><span data-stu-id="900cf-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="900cf-221">Dans ce cas, une exception de cast non valide peut se produire lorsque l’objet est utilisé.</span><span class="sxs-lookup"><span data-stu-id="900cf-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="900cf-222">Un Runtime du fournisseur peut définir son propre type de représentation privée pour aider à se protéger contre les fausses représentations.</span><span class="sxs-lookup"><span data-stu-id="900cf-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="900cf-223">Vous ne pouvez pas définir de types effacés en F # lui-même.</span><span class="sxs-lookup"><span data-stu-id="900cf-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="900cf-224">Seuls les types fournis peuvent être effacés.</span><span class="sxs-lookup"><span data-stu-id="900cf-224">Only provided types may be erased.</span></span> <span data-ttu-id="900cf-225">Vous devez comprendre les ramifications, à la fois pratiques et sémantiques, de l’utilisation de types effacés pour votre fournisseur de type ou d’un fournisseur qui fournit des types effacés.</span><span class="sxs-lookup"><span data-stu-id="900cf-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="900cf-226">Un type effacé n’a pas de type .NET réel.</span><span class="sxs-lookup"><span data-stu-id="900cf-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="900cf-227">Par conséquent, vous ne pouvez pas faire de réflexion exacte sur le type et vous risquez de compromettre les types effacés si vous utilisez des casts de Runtime et d’autres techniques qui reposent sur la sémantique de type Runtime exacte.</span><span class="sxs-lookup"><span data-stu-id="900cf-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="900cf-228">La sous-version des types effacés aboutit souvent à des exceptions de conversion de type au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="900cf-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="900cf-229">Choix des représentations pour les types fournis effacés</span><span class="sxs-lookup"><span data-stu-id="900cf-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="900cf-230">Pour certaines utilisations de types fournis effacés, aucune représentation n’est requise.</span><span class="sxs-lookup"><span data-stu-id="900cf-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="900cf-231">Par exemple, le type fourni effacé peut contenir uniquement des propriétés et des membres statiques et aucun constructeur, et aucune méthode ou propriété ne retournerait une instance du type.</span><span class="sxs-lookup"><span data-stu-id="900cf-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="900cf-232">Si vous pouvez atteindre les instances d’un type fourni effacé, vous devez prendre en compte les questions suivantes :</span><span class="sxs-lookup"><span data-stu-id="900cf-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="900cf-233">**Qu’est-ce que l’effacement d’un type fourni ?**</span><span class="sxs-lookup"><span data-stu-id="900cf-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="900cf-234">L’effacement d’un type fourni est le mode d’affichage du type dans le code .NET compilé.</span><span class="sxs-lookup"><span data-stu-id="900cf-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="900cf-235">L’effacement d’un type de classe effacé fourni est toujours le premier type de base non effacé dans la chaîne d’héritage du type.</span><span class="sxs-lookup"><span data-stu-id="900cf-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="900cf-236">L’effacement d’un type d’interface effacé fourni est toujours `System.Object` .</span><span class="sxs-lookup"><span data-stu-id="900cf-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="900cf-237">**Quelles sont les représentations d’un type fourni ?**</span><span class="sxs-lookup"><span data-stu-id="900cf-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="900cf-238">L’ensemble d’objets possibles pour un type fourni effacé est appelé ses représentations.</span><span class="sxs-lookup"><span data-stu-id="900cf-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="900cf-239">Dans l’exemple de ce document, les représentations de tous les types fournis par l’effacement `Type1..Type100` sont toujours des objets String.</span><span class="sxs-lookup"><span data-stu-id="900cf-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="900cf-240">Toutes les représentations d’un type fourni doivent être compatibles avec l’effacement du type fourni.</span><span class="sxs-lookup"><span data-stu-id="900cf-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="900cf-241">(Sinon, soit le compilateur F # génère une erreur pour une utilisation du fournisseur de type, soit le code .NET non vérifiable non valide sera généré.</span><span class="sxs-lookup"><span data-stu-id="900cf-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="900cf-242">Un fournisseur de type n’est pas valide s’il retourne du code qui donne une représentation qui n’est pas valide.)</span><span class="sxs-lookup"><span data-stu-id="900cf-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="900cf-243">Vous pouvez choisir une représentation pour les objets fournis à l’aide de l’une des approches suivantes, qui sont très courantes :</span><span class="sxs-lookup"><span data-stu-id="900cf-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="900cf-244">Si vous fournissez simplement un wrapper fortement typé sur un type .NET existant, il est souvent judicieux que votre type efface ce type, utilise des instances de ce type comme représentations, ou les deux à la fois.</span><span class="sxs-lookup"><span data-stu-id="900cf-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="900cf-245">Cette approche est appropriée lorsque la plupart des méthodes existantes sur ce type ont toujours un sens quand vous utilisez la version fortement typée.</span><span class="sxs-lookup"><span data-stu-id="900cf-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="900cf-246">Si vous souhaitez créer une API qui diffère considérablement de toute API .NET existante, il est logique de créer des types au moment de l’exécution qui seront l’effacement de type et les représentations pour les types fournis.</span><span class="sxs-lookup"><span data-stu-id="900cf-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="900cf-247">L’exemple de ce document utilise des chaînes comme représentations des objets fournis.</span><span class="sxs-lookup"><span data-stu-id="900cf-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="900cf-248">Souvent, il peut être approprié d’utiliser d’autres objets pour les représentations.</span><span class="sxs-lookup"><span data-stu-id="900cf-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="900cf-249">Par exemple, vous pouvez utiliser un dictionnaire comme conteneur de propriétés :</span><span class="sxs-lookup"><span data-stu-id="900cf-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="900cf-250">Vous pouvez également définir un type dans votre fournisseur de type qui sera utilisé lors de l’exécution pour former la représentation, ainsi qu’une ou plusieurs opérations d’exécution :</span><span class="sxs-lookup"><span data-stu-id="900cf-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="900cf-251">Les membres fournis peuvent alors construire des instances de ce type d’objet :</span><span class="sxs-lookup"><span data-stu-id="900cf-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="900cf-252">Dans ce cas, vous pouvez (si vous le souhaitez) utiliser ce type comme effacement de type en spécifiant ce type comme lors de la `baseType` construction de `ProvidedTypeDefinition` :</span><span class="sxs-lookup"><span data-stu-id="900cf-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="900cf-253">Leçons clés</span><span class="sxs-lookup"><span data-stu-id="900cf-253">Key Lessons</span></span>

<span data-ttu-id="900cf-254">La section précédente a expliqué comment créer un fournisseur de type d’effacement simple qui fournit une plage de types, de propriétés et de méthodes.</span><span class="sxs-lookup"><span data-stu-id="900cf-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="900cf-255">Cette section a également expliqué le concept d’effacement de type, y compris certains avantages et inconvénients liés à la fourniture de types effacés à partir d’un fournisseur de type, et les représentations des types effacés.</span><span class="sxs-lookup"><span data-stu-id="900cf-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="900cf-256">Fournisseur de type qui utilise des paramètres statiques</span><span class="sxs-lookup"><span data-stu-id="900cf-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="900cf-257">La possibilité de paramétrer des fournisseurs de type par données statiques permet de nombreux scénarios intéressants, même si le fournisseur n’a pas besoin d’accéder à des données locales ou distantes.</span><span class="sxs-lookup"><span data-stu-id="900cf-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="900cf-258">Dans cette section, vous allez découvrir quelques techniques de base pour regrouper un tel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="900cf-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="900cf-259">Fournisseur d’expressions régulières vérifiées de type</span><span class="sxs-lookup"><span data-stu-id="900cf-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="900cf-260">Imaginez que vous souhaitiez implémenter un fournisseur de type pour les expressions régulières qui encapsule les <xref:System.Text.RegularExpressions.Regex> bibliothèques .net dans une interface qui fournit les garanties au moment de la compilation suivantes :</span><span class="sxs-lookup"><span data-stu-id="900cf-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="900cf-261">Vérification de la validité d’une expression régulière.</span><span class="sxs-lookup"><span data-stu-id="900cf-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="900cf-262">Fournir des propriétés nommées sur les correspondances basées sur tout nom de groupe dans l’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="900cf-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="900cf-263">Cette section vous montre comment utiliser des fournisseurs de type pour créer un `RegexTyped` type que le modèle d’expression régulière paramètrete pour offrir ces avantages.</span><span class="sxs-lookup"><span data-stu-id="900cf-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="900cf-264">Le compilateur signale une erreur si le modèle fourni n’est pas valide et que le fournisseur de type peut extraire les groupes du modèle afin que vous puissiez y accéder à l’aide des propriétés nommées sur les correspondances.</span><span class="sxs-lookup"><span data-stu-id="900cf-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="900cf-265">Quand vous concevez un fournisseur de type, vous devez prendre en compte la façon dont son API exposée doit s’afficher pour les utilisateurs finaux et comment cette conception sera traduite en code .NET.</span><span class="sxs-lookup"><span data-stu-id="900cf-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="900cf-266">L’exemple suivant montre comment utiliser une telle API pour récupérer les composants de l’indicatif de zone :</span><span class="sxs-lookup"><span data-stu-id="900cf-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="900cf-267">L’exemple suivant montre comment le fournisseur de type traduit ces appels :</span><span class="sxs-lookup"><span data-stu-id="900cf-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="900cf-268">Notez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="900cf-268">Note the following points:</span></span>

- <span data-ttu-id="900cf-269">Le type Regex standard représente le type paramétré `RegexTyped` .</span><span class="sxs-lookup"><span data-stu-id="900cf-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="900cf-270">Le `RegexTyped` constructeur entraîne un appel au constructeur Regex, en passant l’argument de type statique pour le modèle.</span><span class="sxs-lookup"><span data-stu-id="900cf-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="900cf-271">Les résultats de la `Match` méthode sont représentés par le <xref:System.Text.RegularExpressions.Match> type standard.</span><span class="sxs-lookup"><span data-stu-id="900cf-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="900cf-272">Chaque groupe nommé produit une propriété fournie et l’accès à la propriété entraîne l’utilisation d’un indexeur sur la collection d’une correspondance `Groups` .</span><span class="sxs-lookup"><span data-stu-id="900cf-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="900cf-273">Le code suivant est le cœur de la logique permettant d’implémenter un tel fournisseur, et cet exemple omet l’ajout de tous les membres au type fourni.</span><span class="sxs-lookup"><span data-stu-id="900cf-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="900cf-274">Pour plus d’informations sur chaque membre ajouté, consultez la section appropriée plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="900cf-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="900cf-275">Pour obtenir le code complet, téléchargez l’exemple à partir du [Pack d’exemples F # 3,0](https://archive.codeplex.com/?p=fsharp3sample) sur le site Web CodePlex.</span><span class="sxs-lookup"><span data-stu-id="900cf-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

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

<span data-ttu-id="900cf-276">Notez les points suivants :</span><span class="sxs-lookup"><span data-stu-id="900cf-276">Note the following points:</span></span>

- <span data-ttu-id="900cf-277">Le fournisseur de type accepte deux paramètres statiques : `pattern` , qui est obligatoire, et `options` , qui sont facultatifs (car une valeur par défaut est fournie).</span><span class="sxs-lookup"><span data-stu-id="900cf-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="900cf-278">Une fois les arguments statiques fournis, vous créez une instance de l’expression régulière.</span><span class="sxs-lookup"><span data-stu-id="900cf-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="900cf-279">Cette instance lèvera une exception si l’expression régulière est incorrecte, et cette erreur sera signalée aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="900cf-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="900cf-280">Dans le `DefineStaticParameters` rappel, vous définissez le type qui sera retourné une fois les arguments fournis.</span><span class="sxs-lookup"><span data-stu-id="900cf-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="900cf-281">Ce code affecte `HideObjectMethods` la valeur true pour que l’expérience IntelliSense reste rationalisée.</span><span class="sxs-lookup"><span data-stu-id="900cf-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="900cf-282">Cet attribut entraîne la `Equals` `GetHashCode` suppression des membres,, `Finalize` et `GetType` des listes IntelliSense pour un objet fourni.</span><span class="sxs-lookup"><span data-stu-id="900cf-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="900cf-283">Vous utilisez `obj` comme type de base de la méthode, mais vous utiliserez un `Regex` objet comme représentation d’exécution de ce type, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="900cf-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="900cf-284">L’appel au `Regex` constructeur lève une <xref:System.ArgumentException> lorsqu’une expression régulière n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="900cf-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="900cf-285">Le compilateur intercepte cette exception et signale un message d’erreur à l’utilisateur au moment de la compilation ou dans l’éditeur Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="900cf-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="900cf-286">Cette exception permet de valider des expressions régulières sans exécuter une application.</span><span class="sxs-lookup"><span data-stu-id="900cf-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="900cf-287">Le type défini ci-dessus n’est pas encore utile, car il ne contient aucune méthode ou propriété significative.</span><span class="sxs-lookup"><span data-stu-id="900cf-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="900cf-288">Tout d’abord, ajoutez une `IsMatch` méthode statique :</span><span class="sxs-lookup"><span data-stu-id="900cf-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="900cf-289">Le code précédent définit une méthode `IsMatch` , qui prend une chaîne comme entrée et retourne un `bool` .</span><span class="sxs-lookup"><span data-stu-id="900cf-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="900cf-290">La seule difficulté est l’utilisation de l' `args` argument dans la `InvokeCode` définition.</span><span class="sxs-lookup"><span data-stu-id="900cf-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="900cf-291">Dans cet exemple, `args` est une liste de devis qui représente les arguments de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="900cf-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="900cf-292">Si la méthode est une méthode d’instance, le premier argument représente l' `this` argument.</span><span class="sxs-lookup"><span data-stu-id="900cf-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="900cf-293">Toutefois, pour une méthode statique, les arguments sont tous uniquement les arguments explicites de la méthode.</span><span class="sxs-lookup"><span data-stu-id="900cf-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="900cf-294">Notez que le type de la valeur entre guillemets doit correspondre au type de retour spécifié (dans ce cas, `bool` ).</span><span class="sxs-lookup"><span data-stu-id="900cf-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="900cf-295">Notez également que ce code utilise la `AddXmlDoc` méthode pour s’assurer que la méthode fournie possède également une documentation utile, que vous pouvez fournir via IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="900cf-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="900cf-296">Ensuite, ajoutez une méthode de correspondance d’instance.</span><span class="sxs-lookup"><span data-stu-id="900cf-296">Next, add an instance Match method.</span></span> <span data-ttu-id="900cf-297">Toutefois, cette méthode doit retourner une valeur d’un `Match` type fourni afin que les groupes soient accessibles de manière fortement typée.</span><span class="sxs-lookup"><span data-stu-id="900cf-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="900cf-298">Par conséquent, vous devez d’abord déclarer le `Match` type.</span><span class="sxs-lookup"><span data-stu-id="900cf-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="900cf-299">Étant donné que ce type dépend du modèle qui a été fourni en tant qu’argument statique, ce type doit être imbriqué dans la définition de type paramétrable :</span><span class="sxs-lookup"><span data-stu-id="900cf-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="900cf-300">Vous ajoutez ensuite une propriété au type de correspondance pour chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="900cf-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="900cf-301">Au moment de l’exécution, une correspondance est représentée comme une <xref:System.Text.RegularExpressions.Match> valeur ; par conséquent, le devis qui définit la propriété doit utiliser la <xref:System.Text.RegularExpressions.Match.Groups> propriété indexée pour obtenir le groupe approprié.</span><span class="sxs-lookup"><span data-stu-id="900cf-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="900cf-302">Là encore, Notez que vous ajoutez la documentation XML à la propriété fournie.</span><span class="sxs-lookup"><span data-stu-id="900cf-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="900cf-303">Notez également qu’une propriété peut être lue si une `GetterCode` fonction est fournie et que la propriété peut être écrite si une `SetterCode` fonction est fournie, donc la propriété résultante est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="900cf-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="900cf-304">Vous pouvez maintenant créer une méthode d’instance qui retourne une valeur de ce `Match` type :</span><span class="sxs-lookup"><span data-stu-id="900cf-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="900cf-305">Étant donné que vous créez une méthode d’instance, `args.[0]` représente l' `RegexTyped` instance sur laquelle la méthode est appelée, et `args.[1]` est l’argument d’entrée.</span><span class="sxs-lookup"><span data-stu-id="900cf-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="900cf-306">Enfin, fournissez un constructeur afin que les instances du type fourni puissent être créées.</span><span class="sxs-lookup"><span data-stu-id="900cf-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="900cf-307">Le constructeur efface simplement la création d’une instance Regex .NET standard, qui est à nouveau boxed en objet, car `obj` est l’effacement du type fourni.</span><span class="sxs-lookup"><span data-stu-id="900cf-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="900cf-308">Avec cette modification, l’exemple d’utilisation d’API spécifié précédemment dans la rubrique fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="900cf-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="900cf-309">Le code suivant est complet et final :</span><span class="sxs-lookup"><span data-stu-id="900cf-309">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="900cf-310">Leçons clés</span><span class="sxs-lookup"><span data-stu-id="900cf-310">Key Lessons</span></span>

<span data-ttu-id="900cf-311">Cette section a expliqué comment créer un fournisseur de type qui fonctionne sur ses paramètres statiques.</span><span class="sxs-lookup"><span data-stu-id="900cf-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="900cf-312">Le fournisseur vérifie le paramètre statique et fournit des opérations en fonction de sa valeur.</span><span class="sxs-lookup"><span data-stu-id="900cf-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="900cf-313">Fournisseur de type qui est stocké par les données locales</span><span class="sxs-lookup"><span data-stu-id="900cf-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="900cf-314">Souvent, vous pouvez souhaiter que les fournisseurs de type présentent des API basées sur des paramètres statiques non seulement, mais également des informations sur des systèmes locaux ou distants.</span><span class="sxs-lookup"><span data-stu-id="900cf-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="900cf-315">Cette section traite des fournisseurs de type basés sur les données locales, tels que les fichiers de données locaux.</span><span class="sxs-lookup"><span data-stu-id="900cf-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="900cf-316">Fournisseur de fichiers CSV simple</span><span class="sxs-lookup"><span data-stu-id="900cf-316">Simple CSV File Provider</span></span>

<span data-ttu-id="900cf-317">En guise d’exemple simple, imaginez un fournisseur de type pour l’accès aux données scientifiques au format CSV (valeurs séparées par des virgules).</span><span class="sxs-lookup"><span data-stu-id="900cf-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="900cf-318">Cette section part du principe que les fichiers CSV contiennent une ligne d’en-tête suivie de données à virgule flottante, comme le montre le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="900cf-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="900cf-319">Distance (compteur)</span><span class="sxs-lookup"><span data-stu-id="900cf-319">Distance (meter)</span></span>|<span data-ttu-id="900cf-320">Heure (seconde)</span><span class="sxs-lookup"><span data-stu-id="900cf-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="900cf-321">50.0</span><span class="sxs-lookup"><span data-stu-id="900cf-321">50.0</span></span>|<span data-ttu-id="900cf-322">3.7</span><span class="sxs-lookup"><span data-stu-id="900cf-322">3.7</span></span>|
|<span data-ttu-id="900cf-323">100.0</span><span class="sxs-lookup"><span data-stu-id="900cf-323">100.0</span></span>|<span data-ttu-id="900cf-324">5.2</span><span class="sxs-lookup"><span data-stu-id="900cf-324">5.2</span></span>|
|<span data-ttu-id="900cf-325">150.0</span><span class="sxs-lookup"><span data-stu-id="900cf-325">150.0</span></span>|<span data-ttu-id="900cf-326">6.4</span><span class="sxs-lookup"><span data-stu-id="900cf-326">6.4</span></span>|

<span data-ttu-id="900cf-327">Cette section montre comment fournir un type que vous pouvez utiliser pour obtenir des lignes avec une `Distance` propriété de type `float<meter>` et une `Time` propriété de type `float<second>` .</span><span class="sxs-lookup"><span data-stu-id="900cf-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="900cf-328">Pour plus de simplicité, les hypothèses suivantes sont prises :</span><span class="sxs-lookup"><span data-stu-id="900cf-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="900cf-329">Les noms d’en-tête sont inférieurs à l’unité ou se présentent sous la forme « nom (unité) » et ne contiennent pas de virgules.</span><span class="sxs-lookup"><span data-stu-id="900cf-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="900cf-330">Les unités sont toutes des unités système internationales (SI), car le module [Microsoft. FSharp. Data. UnitSystems. si. UnitNames module (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) définit.</span><span class="sxs-lookup"><span data-stu-id="900cf-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="900cf-331">Les unités sont toutes simples (par exemple, les compteurs) au lieu de composent (par exemple, compteur/seconde).</span><span class="sxs-lookup"><span data-stu-id="900cf-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="900cf-332">Toutes les colonnes contiennent des données à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="900cf-332">All columns contain floating point data.</span></span>

<span data-ttu-id="900cf-333">Un fournisseur plus complet délibérera ces restrictions.</span><span class="sxs-lookup"><span data-stu-id="900cf-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="900cf-334">Là encore, la première étape consiste à réfléchir à l’aspect de l’API.</span><span class="sxs-lookup"><span data-stu-id="900cf-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="900cf-335">À partir d’un `info.csv` fichier avec le contenu de la table précédente (au format séparé par des virgules), les utilisateurs du fournisseur doivent être en mesure d’écrire du code qui ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="900cf-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="900cf-336">Dans ce cas, le compilateur doit convertir ces appels en un nom similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="900cf-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="900cf-337">La traduction optimale exige que le fournisseur de type définisse un `CsvFile` type réel dans l’assembly du fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="900cf-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="900cf-338">Les fournisseurs de type s’appuient souvent sur quelques types et méthodes d’assistance pour encapsuler la logique importante.</span><span class="sxs-lookup"><span data-stu-id="900cf-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="900cf-339">Étant donné que les mesures sont effacées au moment de l’exécution, vous pouvez utiliser `float[]` comme type effacé pour une ligne.</span><span class="sxs-lookup"><span data-stu-id="900cf-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="900cf-340">Le compilateur traitera différentes colonnes comme ayant différents types de mesures.</span><span class="sxs-lookup"><span data-stu-id="900cf-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="900cf-341">Par exemple, la première colonne de notre exemple est de type `float<meter>` , et la seconde a `float<second>` .</span><span class="sxs-lookup"><span data-stu-id="900cf-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="900cf-342">Toutefois, la représentation effacée peut rester assez simple.</span><span class="sxs-lookup"><span data-stu-id="900cf-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="900cf-343">Le code suivant illustre le cœur de l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="900cf-343">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="900cf-344">Notez les points suivants à propos de l’implémentation :</span><span class="sxs-lookup"><span data-stu-id="900cf-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="900cf-345">Les constructeurs surchargés autorisent le fichier d’origine ou celui qui a un schéma identique à lire.</span><span class="sxs-lookup"><span data-stu-id="900cf-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="900cf-346">Ce modèle est courant lorsque vous écrivez un fournisseur de type pour des sources de données locales ou distantes, et ce modèle permet d’utiliser un fichier local comme modèle pour les données distantes.</span><span class="sxs-lookup"><span data-stu-id="900cf-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="900cf-347">Vous pouvez utiliser la valeur [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) qui est passée au constructeur du fournisseur de type pour résoudre les noms de fichiers relatifs.</span><span class="sxs-lookup"><span data-stu-id="900cf-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="900cf-348">Vous pouvez utiliser la `AddDefinitionLocation` méthode pour définir l’emplacement des propriétés fournies.</span><span class="sxs-lookup"><span data-stu-id="900cf-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="900cf-349">Par conséquent, si vous utilisez `Go To Definition` sur une propriété fournie, le fichier CSV s’ouvre dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="900cf-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="900cf-350">Vous pouvez utiliser le `ProvidedMeasureBuilder` type pour rechercher les unités si et pour générer les types appropriés `float<_>` .</span><span class="sxs-lookup"><span data-stu-id="900cf-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="900cf-351">Leçons clés</span><span class="sxs-lookup"><span data-stu-id="900cf-351">Key Lessons</span></span>

<span data-ttu-id="900cf-352">Cette section a expliqué comment créer un fournisseur de type pour une source de données locale avec un schéma simple contenu dans la source de données elle-même.</span><span class="sxs-lookup"><span data-stu-id="900cf-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="900cf-353">Aller plus loin</span><span class="sxs-lookup"><span data-stu-id="900cf-353">Going Further</span></span>

<span data-ttu-id="900cf-354">Les sections suivantes incluent des suggestions pour une étude plus approfondie.</span><span class="sxs-lookup"><span data-stu-id="900cf-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="900cf-355">Examen du code compilé pour les types effacés</span><span class="sxs-lookup"><span data-stu-id="900cf-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="900cf-356">Pour vous donner une idée de la façon dont l’utilisation du fournisseur de type correspond au code émis, examinez la fonction suivante à l’aide du `HelloWorldTypeProvider` qui est utilisé précédemment dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="900cf-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="900cf-357">Voici une image du code obtenu décompilé à l’aide d’Ildasm. exe :</span><span class="sxs-lookup"><span data-stu-id="900cf-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="900cf-358">Comme le montre l’exemple, toutes les mentions du type `Type1` et de la `InstanceProperty` propriété ont été effacées, ce qui laisse uniquement les opérations sur les types de Runtime impliqués.</span><span class="sxs-lookup"><span data-stu-id="900cf-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="900cf-359">Conventions de conception et de nommage pour les fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="900cf-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="900cf-360">Respectez les conventions suivantes lors de la création de fournisseurs de type.</span><span class="sxs-lookup"><span data-stu-id="900cf-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="900cf-361">**Fournisseurs pour les protocoles de connectivité** En général, les noms de la plupart des dll de fournisseur pour les protocoles de connectivité de données et de services, tels que OData ou les connexions SQL, doivent se terminer par `TypeProvider` ou `TypeProviders` .</span><span class="sxs-lookup"><span data-stu-id="900cf-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="900cf-362">Par exemple, utilisez un nom de DLL qui ressemble à la chaîne suivante :</span><span class="sxs-lookup"><span data-stu-id="900cf-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="900cf-363">Assurez-vous que les types fournis sont membres de l’espace de noms correspondant et indiquez le protocole de connectivité que vous avez implémenté :</span><span class="sxs-lookup"><span data-stu-id="900cf-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="900cf-364">**Fournisseurs d’utilitaires pour le codage général**.</span><span class="sxs-lookup"><span data-stu-id="900cf-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="900cf-365">Pour un fournisseur de type utilitaire comme celui des expressions régulières, le fournisseur de type peut faire partie d’une bibliothèque de base, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="900cf-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="900cf-366">Dans ce cas, le type fourni apparaîtrait à un point approprié selon les conventions de conception .NET normales :</span><span class="sxs-lookup"><span data-stu-id="900cf-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="900cf-367">**Sources de données Singleton**.</span><span class="sxs-lookup"><span data-stu-id="900cf-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="900cf-368">Certains fournisseurs de type se connectent à une source de données dédiée unique et fournissent uniquement des données.</span><span class="sxs-lookup"><span data-stu-id="900cf-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="900cf-369">Dans ce cas, vous devez supprimer le `TypeProvider` suffixe et utiliser des conventions normales pour l’affectation de noms .net :</span><span class="sxs-lookup"><span data-stu-id="900cf-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="900cf-370">Pour plus d’informations, consultez la `GetConnection` Convention de conception décrite plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="900cf-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="900cf-371">Modèles de conception pour les fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="900cf-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="900cf-372">Les sections suivantes décrivent les modèles de conception que vous pouvez utiliser lors de la création de fournisseurs de type.</span><span class="sxs-lookup"><span data-stu-id="900cf-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="900cf-373">Modèle de conception GetConnection</span><span class="sxs-lookup"><span data-stu-id="900cf-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="900cf-374">La plupart des fournisseurs de type doivent être écrits pour utiliser le `GetConnection` modèle utilisé par les fournisseurs de type dans FSharp. Data. TypeProviders. dll, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="900cf-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="900cf-375">Fournisseurs de type avec des données et services distants</span><span class="sxs-lookup"><span data-stu-id="900cf-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="900cf-376">Avant de créer un fournisseur de type qui est associé à des données et des services distants, vous devez tenir compte d’une série de problèmes inhérents à la programmation connectée.</span><span class="sxs-lookup"><span data-stu-id="900cf-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="900cf-377">Ces problèmes incluent les considérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="900cf-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="900cf-378">mappage de schéma</span><span class="sxs-lookup"><span data-stu-id="900cf-378">schema mapping</span></span>

- <span data-ttu-id="900cf-379">activité et invalidation en présence d’une modification de schéma</span><span class="sxs-lookup"><span data-stu-id="900cf-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="900cf-380">mise en cache de schéma</span><span class="sxs-lookup"><span data-stu-id="900cf-380">schema caching</span></span>

- <span data-ttu-id="900cf-381">implémentations asynchrones d’opérations d’accès aux données</span><span class="sxs-lookup"><span data-stu-id="900cf-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="900cf-382">prise en charge des requêtes, y compris les requêtes LINQ</span><span class="sxs-lookup"><span data-stu-id="900cf-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="900cf-383">informations d’identification et authentification</span><span class="sxs-lookup"><span data-stu-id="900cf-383">credentials and authentication</span></span>

<span data-ttu-id="900cf-384">Cette rubrique n’explore pas ces problèmes plus en détail.</span><span class="sxs-lookup"><span data-stu-id="900cf-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="900cf-385">Techniques de création supplémentaires</span><span class="sxs-lookup"><span data-stu-id="900cf-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="900cf-386">Quand vous écrivez vos propres fournisseurs de type, vous souhaiterez peut-être utiliser les techniques supplémentaires suivantes.</span><span class="sxs-lookup"><span data-stu-id="900cf-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="900cf-387">Création de types et de membres à la demande</span><span class="sxs-lookup"><span data-stu-id="900cf-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="900cf-388">L’API ProvidedType a des versions retardées de AddMember.</span><span class="sxs-lookup"><span data-stu-id="900cf-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="900cf-389">Ces versions sont utilisées pour créer des espaces à la demande de types.</span><span class="sxs-lookup"><span data-stu-id="900cf-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="900cf-390">Fourniture de types de tableau et d’instanciations de types génériques</span><span class="sxs-lookup"><span data-stu-id="900cf-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="900cf-391">Vous faites des membres fournis (dont les signatures incluent des types tableau, des types ByRef et des instanciations de types génériques) à l’aide de la normale `MakeArrayType` , `MakePointerType` et `MakeGenericType` sur n’importe quelle instance de <xref:System.Type> , y compris `ProvidedTypeDefinitions` .</span><span class="sxs-lookup"><span data-stu-id="900cf-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="900cf-392">Dans certains cas, vous devrez peut-être utiliser le programme d’assistance dans `ProvidedTypeBuilder.MakeGenericType` .</span><span class="sxs-lookup"><span data-stu-id="900cf-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="900cf-393">Pour plus d’informations, consultez la [documentation du kit de développement logiciel du fournisseur de type](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) .</span><span class="sxs-lookup"><span data-stu-id="900cf-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="900cf-394">Fournir des annotations d’unité de mesure</span><span class="sxs-lookup"><span data-stu-id="900cf-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="900cf-395">L’API ProvidedTypes fournit des assistances pour fournir des annotations de mesure.</span><span class="sxs-lookup"><span data-stu-id="900cf-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="900cf-396">Par exemple, pour fournir le type `float<kg>` , utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="900cf-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="900cf-397">Pour fournir le type `Nullable<decimal<kg/m^2>>` , utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="900cf-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="900cf-398">Accès aux ressources de projet local ou de script local</span><span class="sxs-lookup"><span data-stu-id="900cf-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="900cf-399">Chaque instance d’un fournisseur de type peut recevoir une `TypeProviderConfig` valeur pendant la construction.</span><span class="sxs-lookup"><span data-stu-id="900cf-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="900cf-400">Cette valeur contient le « dossier de résolution » pour le fournisseur (autrement dit, le dossier du projet pour la compilation ou le répertoire qui contient un script), la liste des assemblys référencés et d’autres informations.</span><span class="sxs-lookup"><span data-stu-id="900cf-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="900cf-401">Invalidation</span><span class="sxs-lookup"><span data-stu-id="900cf-401">Invalidation</span></span>

<span data-ttu-id="900cf-402">Les fournisseurs peuvent déclencher des signaux d’invalidation pour notifier le service de langage F # que les hypothèses de schéma peuvent avoir changé.</span><span class="sxs-lookup"><span data-stu-id="900cf-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="900cf-403">Lorsque l’invalidation se produit, un typecheck est restauré si le fournisseur est hébergé dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="900cf-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="900cf-404">Ce signal sera ignoré lorsque le fournisseur est hébergé dans F# Interactive ou par le compilateur F # (FSC. exe).</span><span class="sxs-lookup"><span data-stu-id="900cf-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="900cf-405">Mise en cache des informations de schéma</span><span class="sxs-lookup"><span data-stu-id="900cf-405">Caching Schema Information</span></span>

<span data-ttu-id="900cf-406">Les fournisseurs doivent souvent mettre en cache l’accès aux informations de schéma.</span><span class="sxs-lookup"><span data-stu-id="900cf-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="900cf-407">Les données mises en cache doivent être stockées à l’aide d’un nom de fichier donné en tant que paramètre statique ou en tant que données utilisateur.</span><span class="sxs-lookup"><span data-stu-id="900cf-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="900cf-408">Un exemple de mise en cache de schéma est le `LocalSchemaFile` paramètre dans les fournisseurs de type dans l' `FSharp.Data.TypeProviders` assembly.</span><span class="sxs-lookup"><span data-stu-id="900cf-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="900cf-409">Dans l’implémentation de ces fournisseurs, ce paramètre statique indique au fournisseur de type d’utiliser les informations de schéma dans le fichier local spécifié au lieu d’accéder à la source de données sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="900cf-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="900cf-410">Pour utiliser les informations de schéma mises en cache, vous devez également définir le paramètre static `ForceUpdate` sur `false` .</span><span class="sxs-lookup"><span data-stu-id="900cf-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="900cf-411">Vous pouvez utiliser une technique similaire pour activer l’accès aux données en ligne et hors connexion.</span><span class="sxs-lookup"><span data-stu-id="900cf-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="900cf-412">Assembly de stockage</span><span class="sxs-lookup"><span data-stu-id="900cf-412">Backing Assembly</span></span>

<span data-ttu-id="900cf-413">Quand vous compilez un `.dll` `.exe` fichier ou, le fichier. dll de stockage des types générés est lié de manière statique à l’assembly résultant.</span><span class="sxs-lookup"><span data-stu-id="900cf-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="900cf-414">Ce lien est créé en copiant les définitions de type de langage intermédiaire (IL) et toutes les ressources managées à partir de l’assembly de stockage dans l’assembly final.</span><span class="sxs-lookup"><span data-stu-id="900cf-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="900cf-415">Lorsque vous utilisez F# Interactive, le fichier. dll de sauvegarde n’est pas copié et est chargé directement dans le processus de F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="900cf-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="900cf-416">Exceptions et diagnostics des fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="900cf-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="900cf-417">Toutes les utilisations de tous les membres des types fournis peuvent lever des exceptions.</span><span class="sxs-lookup"><span data-stu-id="900cf-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="900cf-418">Dans tous les cas, si un fournisseur de type lève une exception, le compilateur hôte attribut l’erreur à un fournisseur de type spécifique.</span><span class="sxs-lookup"><span data-stu-id="900cf-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="900cf-419">Les exceptions de fournisseur de type ne doivent jamais entraîner des erreurs internes du compilateur.</span><span class="sxs-lookup"><span data-stu-id="900cf-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="900cf-420">Les fournisseurs de type ne peuvent pas signaler d’avertissements.</span><span class="sxs-lookup"><span data-stu-id="900cf-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="900cf-421">Lorsqu’un fournisseur de type est hébergé dans le compilateur F #, un environnement de développement F #, ou F# Interactive, toutes les exceptions de ce fournisseur sont interceptées.</span><span class="sxs-lookup"><span data-stu-id="900cf-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="900cf-422">La propriété message est toujours le texte d’erreur et aucune trace de la pile ne s’affiche.</span><span class="sxs-lookup"><span data-stu-id="900cf-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="900cf-423">Si vous envisagez de lever une exception, vous pouvez lever les exemples suivants : `System.NotSupportedException` , `System.IO.IOException` , `System.Exception` .</span><span class="sxs-lookup"><span data-stu-id="900cf-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="900cf-424">Fourniture de types générés</span><span class="sxs-lookup"><span data-stu-id="900cf-424">Providing Generated Types</span></span>

<span data-ttu-id="900cf-425">Jusqu’à présent, ce document a expliqué comment fournir des types effacés.</span><span class="sxs-lookup"><span data-stu-id="900cf-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="900cf-426">Vous pouvez également utiliser le mécanisme du fournisseur de type en F # pour fournir des types générés, qui sont ajoutés en tant que définitions de type .NET réelles dans le programme des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="900cf-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="900cf-427">Vous devez faire référence aux types fournis générés à l’aide d’une définition de type.</span><span class="sxs-lookup"><span data-stu-id="900cf-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="900cf-428">Le code d’assistance ProvidedTypes-0,2 qui fait partie de la version F # 3,0 n’a qu’une prise en charge limitée pour la fourniture de types générés.</span><span class="sxs-lookup"><span data-stu-id="900cf-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="900cf-429">Les instructions suivantes doivent être vraies pour une définition de type générée :</span><span class="sxs-lookup"><span data-stu-id="900cf-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="900cf-430">`isErased` doit être défini sur `false`.</span><span class="sxs-lookup"><span data-stu-id="900cf-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="900cf-431">Le type généré doit être ajouté à un nouveau construit `ProvidedAssembly()` , qui représente un conteneur pour les fragments de code générés.</span><span class="sxs-lookup"><span data-stu-id="900cf-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="900cf-432">Le fournisseur doit avoir un assembly qui possède un fichier. dll .NET de sauvegarde réel avec un fichier. dll correspondant sur le disque.</span><span class="sxs-lookup"><span data-stu-id="900cf-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="900cf-433">Règles et limitations</span><span class="sxs-lookup"><span data-stu-id="900cf-433">Rules and Limitations</span></span>

<span data-ttu-id="900cf-434">Lorsque vous écrivez des fournisseurs de type, gardez à l’esprit les règles et limitations suivantes.</span><span class="sxs-lookup"><span data-stu-id="900cf-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="900cf-435">Les types fournis doivent être accessibles</span><span class="sxs-lookup"><span data-stu-id="900cf-435">Provided types must be reachable</span></span>

<span data-ttu-id="900cf-436">Tous les types fournis doivent être accessibles à partir des types non imbriqués.</span><span class="sxs-lookup"><span data-stu-id="900cf-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="900cf-437">Les types non imbriqués sont fournis dans l’appel au `TypeProviderForNamespaces` constructeur ou à un appel à `AddNamespace` .</span><span class="sxs-lookup"><span data-stu-id="900cf-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="900cf-438">Par exemple, si le fournisseur fournit un type `StaticClass.P : T` , vous devez vous assurer que T est un type non imbriqué ou imbriqué sous un.</span><span class="sxs-lookup"><span data-stu-id="900cf-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="900cf-439">Par exemple, certains fournisseurs ont une classe statique telle que `DataTypes` qui contient ces `T1, T2, T3, ...` types.</span><span class="sxs-lookup"><span data-stu-id="900cf-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="900cf-440">Dans le cas contraire, l’erreur indique qu’une référence au type T dans l’assembly A a été trouvée, mais que le type est introuvable dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="900cf-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="900cf-441">Si cette erreur s’affiche, vérifiez que tous vos sous-types sont accessibles à partir des types de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="900cf-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="900cf-442">Remarque : ces `T1, T2, T3...` types sont appelés types *à la volée* .</span><span class="sxs-lookup"><span data-stu-id="900cf-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="900cf-443">N’oubliez pas de les placer dans un espace de noms accessible ou un type parent.</span><span class="sxs-lookup"><span data-stu-id="900cf-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="900cf-444">Limitations du mécanisme du fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="900cf-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="900cf-445">Le mécanisme du fournisseur de type en F # présente les limitations suivantes :</span><span class="sxs-lookup"><span data-stu-id="900cf-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="900cf-446">L’infrastructure sous-jacente pour les fournisseurs de type en F # ne prend pas en charge les types génériques fournis ou les méthodes génériques fournies.</span><span class="sxs-lookup"><span data-stu-id="900cf-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="900cf-447">Le mécanisme ne prend pas en charge les types imbriqués avec des paramètres statiques.</span><span class="sxs-lookup"><span data-stu-id="900cf-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="900cf-448">Conseils de développement</span><span class="sxs-lookup"><span data-stu-id="900cf-448">Development Tips</span></span>

<span data-ttu-id="900cf-449">Les conseils suivants peuvent être utiles pendant le processus de développement :</span><span class="sxs-lookup"><span data-stu-id="900cf-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="900cf-450">Exécuter deux instances de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="900cf-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="900cf-451">Vous pouvez développer le fournisseur de type dans une instance et tester le fournisseur dans l’autre, car l’IDE de test prend un verrou sur le fichier. dll qui empêche le fournisseur de type d’être régénéré.</span><span class="sxs-lookup"><span data-stu-id="900cf-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="900cf-452">Par conséquent, vous devez fermer la deuxième instance de Visual Studio pendant que le fournisseur est créé dans la première instance, puis vous devez rouvrir la deuxième instance après la génération du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="900cf-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="900cf-453">Déboguer les fournisseurs de type à l’aide des appels de FSC. exe</span><span class="sxs-lookup"><span data-stu-id="900cf-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="900cf-454">Vous pouvez appeler des fournisseurs de type à l’aide des outils suivants :</span><span class="sxs-lookup"><span data-stu-id="900cf-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="900cf-455">FSC. exe (compilateur de ligne de commande F #)</span><span class="sxs-lookup"><span data-stu-id="900cf-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="900cf-456">FSI. exe (compilateur F# Interactive)</span><span class="sxs-lookup"><span data-stu-id="900cf-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="900cf-457">devenv. exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="900cf-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="900cf-458">Vous pouvez souvent déboguer les fournisseurs de type le plus facilement à l’aide de FSC. exe sur un fichier de script de test (par exemple, script. FSX).</span><span class="sxs-lookup"><span data-stu-id="900cf-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="900cf-459">Vous pouvez lancer un débogueur à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="900cf-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="900cf-460">Vous pouvez utiliser la journalisation de l’impression vers stdout.</span><span class="sxs-lookup"><span data-stu-id="900cf-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="900cf-461">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="900cf-461">See also</span></span>

- [<span data-ttu-id="900cf-462">Fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="900cf-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="900cf-463">Kit de développement logiciel du fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="900cf-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
