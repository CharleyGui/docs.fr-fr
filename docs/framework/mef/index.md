---
title: Managed Extensibility Framework (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
ms.openlocfilehash: 9a601ac860ac3bf81dd01980b020470d3323772f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181284"
---
# <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="028c6-102">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="028c6-102">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="028c6-103">Cette rubrique fournit une vue d'ensemble de Managed Extensibility Framework, qui a été introduit dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="028c6-103">This topic provides an overview of the Managed Extensibility Framework that was introduced in the .NET Framework 4.</span></span>

## <a name="what-is-mef"></a><span data-ttu-id="028c6-104">Présentation de MEF</span><span class="sxs-lookup"><span data-stu-id="028c6-104">What is MEF?</span></span>

<span data-ttu-id="028c6-105">Le Managed Extensibility Framework ou MEF est une bibliothèque pour la création d’applications légères et extensibles.</span><span class="sxs-lookup"><span data-stu-id="028c6-105">The Managed Extensibility Framework or MEF is a library for creating lightweight, and extensible applications.</span></span> <span data-ttu-id="028c6-106">Elle permet aux développeurs d'applications de découvrir et d'utiliser des extensions sans nécessiter de configuration particulière.</span><span class="sxs-lookup"><span data-stu-id="028c6-106">It allows application developers to discover and use extensions with no configuration required.</span></span> <span data-ttu-id="028c6-107">Elle permet également aux développeurs d'extensions d'encapsuler du code facilement tout en évitant les dépendances dures et fragiles.</span><span class="sxs-lookup"><span data-stu-id="028c6-107">It also lets extension developers easily encapsulate code and avoid fragile hard dependencies.</span></span> <span data-ttu-id="028c6-108">De plus, MEF permet de réutiliser des extensions dans une application, mais aussi d'une application à une autre.</span><span class="sxs-lookup"><span data-stu-id="028c6-108">MEF not only allows extensions to be reused within applications, but across applications as well.</span></span>

## <a name="the-problem-of-extensibility"></a><span data-ttu-id="028c6-109">Le problème d’extensibilité</span><span class="sxs-lookup"><span data-stu-id="028c6-109">The problem of extensibility</span></span>

<span data-ttu-id="028c6-110">Imaginez que vous êtes l'architecte d'une grande application devant fournir une prise en charge pour l'extensibilité.</span><span class="sxs-lookup"><span data-stu-id="028c6-110">Imagine that you are the architect of a large application that must provide support for extensibility.</span></span> <span data-ttu-id="028c6-111">Votre application doit inclure un nombre potentiellement important de petits composants qu'elle est censée créer et exécuter.</span><span class="sxs-lookup"><span data-stu-id="028c6-111">Your application has to include a potentially large number of smaller components, and is responsible for creating and running them.</span></span>

<span data-ttu-id="028c6-112">Face à ce problème, l'approche la plus simple consiste à inclure les composants sous forme de code source dans votre application et à les appeler directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="028c6-112">The simplest approach to the problem is to include the components as source code in your application, and call them directly from your code.</span></span> <span data-ttu-id="028c6-113">Cette approche comporte plusieurs inconvénients évidents.</span><span class="sxs-lookup"><span data-stu-id="028c6-113">This has a number of obvious drawbacks.</span></span> <span data-ttu-id="028c6-114">L'inconvénient majeur est que vous ne pouvez pas ajouter de nouveaux composants sans modifier le code source. Cette restriction est acceptable dans une application web par exemple, mais elle est rédhibitoire dans une application cliente.</span><span class="sxs-lookup"><span data-stu-id="028c6-114">Most importantly, you cannot add new components without modifying the source code, a restriction that might be acceptable in, for example, a Web application, but is unworkable in a client application.</span></span> <span data-ttu-id="028c6-115">Autre inconvénient tout aussi problématique, vous risquez de ne pas avoir accès au code source des composants développés par des tiers et, pour la même raison, vous ne pouvez pas leur permettre d'accéder aux vôtres.</span><span class="sxs-lookup"><span data-stu-id="028c6-115">Equally problematic, you may not have access to the source code for the components, because they might be developed by third parties, and for the same reason you cannot allow them to access yours.</span></span>

<span data-ttu-id="028c6-116">Il existe une approche un peu plus élaborée qui consiste à fournir une interface ou un point d'extension pour découpler l'application de ses composants.</span><span class="sxs-lookup"><span data-stu-id="028c6-116">A slightly more sophisticated approach would be to provide an extension point or interface, to permit decoupling between the application and its components.</span></span> <span data-ttu-id="028c6-117">Dans ce modèle, vous pouvez fournir une interface à implémenter par un composant, et une API pour lui permettre d'interagir avec votre application.</span><span class="sxs-lookup"><span data-stu-id="028c6-117">Under this model, you might provide an interface that a component can implement, and an API to enable it to interact with your application.</span></span> <span data-ttu-id="028c6-118">Si cette approche résout le problème de l'accès au code source, elle a d'autres inconvénients spécifiques.</span><span class="sxs-lookup"><span data-stu-id="028c6-118">This solves the problem of requiring source code access, but it still has its own difficulties.</span></span>

<span data-ttu-id="028c6-119">Comme l'application n'est pas en mesure de découvrir les composants elle-même, vous devez encore lui indiquer explicitement quels composants sont disponibles et doivent être chargés.</span><span class="sxs-lookup"><span data-stu-id="028c6-119">Because the application lacks any capacity for discovering components on its own, it must still be explicitly told which components are available and should be loaded.</span></span> <span data-ttu-id="028c6-120">Cela peut généralement se faire en inscrivant explicitement les composants disponibles dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="028c6-120">This is typically accomplished by explicitly registering the available components in a configuration file.</span></span> <span data-ttu-id="028c6-121">Cela implique de vérifier que les composants sont corrects, ce qui complique la maintenance, en particulier si la mise à jour doit normalement être effectuée par l'utilisateur final et non le développeur.</span><span class="sxs-lookup"><span data-stu-id="028c6-121">This means that assuring that the components are correct becomes a maintenance issue, particularly if it is the end user and not the developer who is expected to do the updating.</span></span>

<span data-ttu-id="028c6-122">De plus, les composants sont incapables de communiquer entre eux, sauf via les canaux rigides de l'application elle-même.</span><span class="sxs-lookup"><span data-stu-id="028c6-122">In addition, components are incapable of communicating with one another, except through the rigidly defined channels of the application itself.</span></span> <span data-ttu-id="028c6-123">Si l‘architecte de l‘application n‘a pas anticipé la nécessité d‘établir une communication spécifique, la communication est généralement impossible.</span><span class="sxs-lookup"><span data-stu-id="028c6-123">If the application architect has not anticipated the need for a particular communication, it is usually impossible.</span></span>

<span data-ttu-id="028c6-124">Enfin, les développeurs de composants doivent accepter la présence d'une dépendance dure sur l'assembly contenant l'interface qu'ils implémentent.</span><span class="sxs-lookup"><span data-stu-id="028c6-124">Finally, the component developers must accept a hard dependency on what assembly contains the interface they implement.</span></span> <span data-ttu-id="028c6-125">Cette dépendance rend compliquée l'utilisation d'un composant dans plusieurs applications et peut également poser des problèmes quand vous créez une infrastructure de tests pour les composants.</span><span class="sxs-lookup"><span data-stu-id="028c6-125">This makes it difficult for a component to be used in more than one application, and can also create problems when you create a test framework for components.</span></span>

## <a name="what-mef-provides"></a><span data-ttu-id="028c6-126">Ce qu’offre MEF</span><span class="sxs-lookup"><span data-stu-id="028c6-126">What MEF provides</span></span>

<span data-ttu-id="028c6-127">Au lieu de cette inscription explicite des composants disponibles, MEF permet leur découverte implicite par la *composition*.</span><span class="sxs-lookup"><span data-stu-id="028c6-127">Instead of this explicit registration of available components, MEF provides a way to discover them implicitly, via *composition*.</span></span> <span data-ttu-id="028c6-128">Un composant MEF, appelé *partie*, spécifie de manière déclarative à la fois ses dépendances (les *importations*) et les fonctionnalités (les *exportations*) qu’il rend disponibles.</span><span class="sxs-lookup"><span data-stu-id="028c6-128">A MEF component, called a *part*, declaratively specifies both its dependencies (known as *imports*) and what capabilities (known as *exports*) it makes available.</span></span> <span data-ttu-id="028c6-129">Lorsqu'une partie est créée, le moteur de composition MEF fournit à ses importations les éléments disponibles des autres parties.</span><span class="sxs-lookup"><span data-stu-id="028c6-129">When a part is created, the MEF composition engine satisfies its imports with what is available from other parts.</span></span>

<span data-ttu-id="028c6-130">Cette approche résout les problèmes abordés dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="028c6-130">This approach solves the problems discussed in the previous section.</span></span> <span data-ttu-id="028c6-131">Étant donné que les parties MEF spécifient leurs fonctionnalités de façon déclarative, elles sont détectables au moment de l'exécution, ce qui signifie qu'une application peut utiliser des parties sans avoir recours à des références codées en dur ni à des fichiers de configuration fragiles.</span><span class="sxs-lookup"><span data-stu-id="028c6-131">Because MEF parts declaratively specify their capabilities, they are discoverable at runtime, which means an application can make use of parts without either hard-coded references or fragile configuration files.</span></span> <span data-ttu-id="028c6-132">MEF permet aux applications de découvrir et d'examiner des parties grâce à leurs métadonnées, sans les instancier ni même charger leurs assemblys.</span><span class="sxs-lookup"><span data-stu-id="028c6-132">MEF allows applications to discover and examine parts by their metadata, without instantiating them or even loading their assemblies.</span></span> <span data-ttu-id="028c6-133">Par conséquent, il est inutile de spécifier avec précision quand et comment les extensions doivent être chargées.</span><span class="sxs-lookup"><span data-stu-id="028c6-133">As a result, there is no need to carefully specify when and how extensions should be loaded.</span></span>

<span data-ttu-id="028c6-134">En plus de spécifier les exportations qui lui sont fournies, une partie peut spécifier ses importations, qui seront remplies par d'autres parties.</span><span class="sxs-lookup"><span data-stu-id="028c6-134">In addition to its provided exports, a part can specify its imports, which will be filled by other parts.</span></span> <span data-ttu-id="028c6-135">Cela permet et facilite la communication entre les parties, tout en garantissant une bonne factorisation du code.</span><span class="sxs-lookup"><span data-stu-id="028c6-135">This makes communication among parts not only possible, but easy, and allows for good factoring of code.</span></span> <span data-ttu-id="028c6-136">Par exemple, les services communs à de nombreux composants peuvent être factorisés dans une partie distincte et être facilement modifiés ou remplacés.</span><span class="sxs-lookup"><span data-stu-id="028c6-136">For example, services common to many components can be factored into a separate part and easily modified or replaced.</span></span>

<span data-ttu-id="028c6-137">Étant donné que le modèle MEF n'a besoin d'aucune dépendance dure sur un assembly d'application particulier, il permet la réutilisation des extensions dans d'autres applications.</span><span class="sxs-lookup"><span data-stu-id="028c6-137">Because the MEF model requires no hard dependency on a particular application assembly, it allows extensions to be reused from application to application.</span></span> <span data-ttu-id="028c6-138">Cela facilite également le développement d’un atelier de test, indépendant de l’application, pour tester les composants d’extension.</span><span class="sxs-lookup"><span data-stu-id="028c6-138">This also makes it easy to develop a test harness, independent of the application, to test extension components.</span></span>

<span data-ttu-id="028c6-139">Une application extensible écrite à l'aide de MEF déclare une importation qui peut être remplie par les composants d'extension, et peut aussi déclarer des exportations pour exposer ses services aux extensions.</span><span class="sxs-lookup"><span data-stu-id="028c6-139">An extensible application written by using MEF declares an import that can be filled by extension components, and may also declare exports in order to expose application services to extensions.</span></span> <span data-ttu-id="028c6-140">Chaque composant d’extension déclare une exportation et éventuellement des importations.</span><span class="sxs-lookup"><span data-stu-id="028c6-140">Each extension component declares an export, and may also declare imports.</span></span> <span data-ttu-id="028c6-141">De cette façon, les composants d'extension eux-mêmes sont automatiquement extensibles.</span><span class="sxs-lookup"><span data-stu-id="028c6-141">In this way, extension components themselves are automatically extensible.</span></span>

## <a name="where-mef-is-available"></a><span data-ttu-id="028c6-142">Où MEF est disponible</span><span class="sxs-lookup"><span data-stu-id="028c6-142">Where MEF is available</span></span>

<span data-ttu-id="028c6-143">MEF fait partie intégrante de .NET Framework 4 et est disponible partout où le .NET Framework est utilisé.</span><span class="sxs-lookup"><span data-stu-id="028c6-143">MEF is an integral part of the .NET Framework 4, and is available wherever the .NET Framework is used.</span></span> <span data-ttu-id="028c6-144">Vous pouvez utiliser MEF dans vos applications clientes, si elles utilisent des Windows Forms, WPF ou une autre technologie, ou dans les applications serveur ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="028c6-144">You can use MEF in your client applications, whether they use Windows Forms, WPF, or any other technology, or in server applications that use ASP.NET.</span></span>

## <a name="mef-and-maf"></a><span data-ttu-id="028c6-145">MEF et MAF</span><span class="sxs-lookup"><span data-stu-id="028c6-145">MEF and MAF</span></span>

<span data-ttu-id="028c6-146">Les versions précédentes du .NET Framework ont introduit Managed Add-in Framework (MAF), une infrastructure conçue pour permettre aux applications d’isoler et de gérer des extensions.</span><span class="sxs-lookup"><span data-stu-id="028c6-146">Previous versions of the .NET Framework introduced the Managed Add-in Framework (MAF), designed to allow applications to isolate and manage extensions.</span></span> <span data-ttu-id="028c6-147">Le focus de MAF est légèrement plus général que MEF : MAF se concentre sur l’isolement des extensions et le chargement/déchargement des assemblys, tandis que le focus de MEF englobe la détectabilité, l’extensibilité et la portabilité.</span><span class="sxs-lookup"><span data-stu-id="028c6-147">The focus of MAF is slightly higher-level than MEF, concentrating on extension isolation and assembly loading and unloading, while MEF's focus is on discoverability, extensibility, and portability.</span></span> <span data-ttu-id="028c6-148">Les deux infrastructures interagissent de façon transparente et peuvent être utilisées par une même application.</span><span class="sxs-lookup"><span data-stu-id="028c6-148">The two frameworks interoperate smoothly, and a single application can take advantage of both.</span></span>

## <a name="simplecalculator-an-example-application"></a><span data-ttu-id="028c6-149">SimpleCalculator : exemple d’application</span><span class="sxs-lookup"><span data-stu-id="028c6-149">SimpleCalculator: An example application</span></span>

<span data-ttu-id="028c6-150">Le meilleur moyen de découvrir les possibilités de MEF consiste à créer une application MEF simple.</span><span class="sxs-lookup"><span data-stu-id="028c6-150">The simplest way to see what MEF can do is to build a simple MEF application.</span></span> <span data-ttu-id="028c6-151">Dans cet exemple, vous allez créer une calculatrice très simple nommée SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="028c6-151">In this example, you build a very simple calculator named SimpleCalculator.</span></span> <span data-ttu-id="028c6-152">L'objectif de SimpleCalculator est de créer une application console qui accepte des commandes arithmétiques de base (de type « 5 + 3 » ou « 6 - 2 ») et retourne des résultats corrects.</span><span class="sxs-lookup"><span data-stu-id="028c6-152">The goal of SimpleCalculator is to create a console application that accepts basic arithmetic commands, in the form "5+3" or "6-2", and returns the correct answers.</span></span> <span data-ttu-id="028c6-153">Grâce à MEF, vous pourrez ajouter de nouveaux opérateurs sans avoir à modifier le code de l'application.</span><span class="sxs-lookup"><span data-stu-id="028c6-153">Using MEF, you'll be able to add new operators without changing the application code.</span></span>

<span data-ttu-id="028c6-154">Pour télécharger le code complet de cet exemple, consultez l' [exemple SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span><span class="sxs-lookup"><span data-stu-id="028c6-154">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

> [!NOTE]
> <span data-ttu-id="028c6-155">L'objectif de SimpleCalculator est avant tout de montrer les concepts et la syntaxe de MEF, et non de fournir un scénario d'utilisation réaliste.</span><span class="sxs-lookup"><span data-stu-id="028c6-155">The purpose of SimpleCalculator is to demonstrate the concepts and syntax of MEF, rather than to necessarily provide a realistic scenario for its use.</span></span> <span data-ttu-id="028c6-156">La plupart des applications qui tirent le meilleur parti de MEF sont plus complexes que SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="028c6-156">Many of the applications that would benefit most from the power of MEF are more complex than SimpleCalculator.</span></span> <span data-ttu-id="028c6-157">Pour obtenir des exemples plus détaillés, consultez [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="028c6-157">For more extensive examples, see the [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) on GitHub.</span></span>

- <span data-ttu-id="028c6-158">Pour commencer, dans Visual Studio, créez un projet Application console et nommez-le `SimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="028c6-158">To start, in Visual Studio, create a new Console Application project and name it `SimpleCalculator`.</span></span>

- <span data-ttu-id="028c6-159">Ajoutez une référence à l' `System.ComponentModel.Composition` assembly où se trouve MEF.</span><span class="sxs-lookup"><span data-stu-id="028c6-159">Add a reference to the `System.ComponentModel.Composition` assembly, where MEF resides.</span></span>

- <span data-ttu-id="028c6-160">Ouvrez *Module1. vb* ou *Program.cs* et ajoutez `Imports` des `using` instructions ou `System.ComponentModel.Composition` pour `System.ComponentModel.Composition.Hosting`et.</span><span class="sxs-lookup"><span data-stu-id="028c6-160">Open *Module1.vb* or *Program.cs* and add `Imports` or `using` statements for `System.ComponentModel.Composition` and `System.ComponentModel.Composition.Hosting`.</span></span> <span data-ttu-id="028c6-161">Ces deux espaces de noms contiennent des types MEF dont vous avez besoin pour développer une application extensible.</span><span class="sxs-lookup"><span data-stu-id="028c6-161">These two namespaces contain MEF types you will need to develop an extensible application.</span></span>

- <span data-ttu-id="028c6-162">Si vous utilisez Visual Basic, ajoutez le mot clé `Public` dans la ligne qui déclare le module `Module1`.</span><span class="sxs-lookup"><span data-stu-id="028c6-162">If you're using Visual Basic, add the `Public` keyword to the line that declares the `Module1` module.</span></span>

## <a name="composition-container-and-catalogs"></a><span data-ttu-id="028c6-163">Catalogue et conteneur de composition</span><span class="sxs-lookup"><span data-stu-id="028c6-163">Composition container and catalogs</span></span>

<span data-ttu-id="028c6-164">Le cœur du modèle de composition MEF est le *conteneur de composition*, qui contient toutes les parties disponibles et exécute la composition.</span><span class="sxs-lookup"><span data-stu-id="028c6-164">The core of the MEF composition model is the *composition container*, which contains all the parts available and performs composition.</span></span> <span data-ttu-id="028c6-165">La composition est la correspondance entre les importations et les exportations.</span><span class="sxs-lookup"><span data-stu-id="028c6-165">Composition is the matching up of imports to exports.</span></span> <span data-ttu-id="028c6-166">Pour SimpleCalculator, vous allez utiliser <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, qui est le type de conteneur de composition le plus courant.</span><span class="sxs-lookup"><span data-stu-id="028c6-166">The most common type of composition container is <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, and you'll use this for SimpleCalculator.</span></span>

<span data-ttu-id="028c6-167">Si vous utilisez Visual Basic, ajoutez une classe publique nommée `Program` dans *Module1. vb*.</span><span class="sxs-lookup"><span data-stu-id="028c6-167">If you're using Visual Basic, add a public class named `Program` in *Module1.vb*.</span></span>

<span data-ttu-id="028c6-168">Ajoutez la ligne suivante à la `Program` classe dans *Module1. vb* ou *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="028c6-168">Add the following line to the `Program` class in *Module1.vb* or *Program.cs*:</span></span>

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

<span data-ttu-id="028c6-169">Pour découvrir les parties disponibles, les conteneurs de composition utilisent un *catalogue*.</span><span class="sxs-lookup"><span data-stu-id="028c6-169">In order to discover the parts available to it, the composition containers makes use of a *catalog*.</span></span> <span data-ttu-id="028c6-170">Un catalogue est un objet qui rend disponibles les parties découvertes dans une source.</span><span class="sxs-lookup"><span data-stu-id="028c6-170">A catalog is an object that makes available parts discovered from some source.</span></span> <span data-ttu-id="028c6-171">MEF propose des catalogues pour la découverte des parties dans un type, un assembly ou un répertoire fourni.</span><span class="sxs-lookup"><span data-stu-id="028c6-171">MEF provides catalogs to discover parts from a provided type, an assembly, or a directory.</span></span> <span data-ttu-id="028c6-172">Les développeurs d'applications peuvent facilement créer des catalogues pour découvrir des parties dans d'autres sources, telles qu'un service web.</span><span class="sxs-lookup"><span data-stu-id="028c6-172">Application developers can easily create new catalogs to discover parts from other sources, such as a Web service.</span></span>

<span data-ttu-id="028c6-173">Ajoutez le constructeur suivant à la classe `Program` :</span><span class="sxs-lookup"><span data-stu-id="028c6-173">Add the following constructor to the `Program` class:</span></span>

```vb
Public Sub New()
    ' An aggregate catalog that combines multiple catalogs.
     Dim catalog = New AggregateCatalog()

    ' Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    ' Create the CompositionContainer with the parts in the catalog.
    _container = New CompositionContainer(catalog)

    ' Fill the imports of this object.
    Try
        _container.ComposeParts(Me)
    Catch ex As CompositionException
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    // An aggregate catalog that combines multiple catalogs.
    var catalog = new AggregateCatalog();
    // Adds all the parts found in the same assembly as the Program class.
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    // Create the CompositionContainer with the parts in the catalog.
    _container = new CompositionContainer(catalog);

    // Fill the imports of this object.
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

<span data-ttu-id="028c6-174">L'appel à <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> indique au conteneur de composition qu'il doit composer un ensemble spécifique de parties (dans ce cas, l'instance actuelle de `Program`).</span><span class="sxs-lookup"><span data-stu-id="028c6-174">The call to <xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> tells the composition container to compose a specific set of parts, in this case the current instance of `Program`.</span></span> <span data-ttu-id="028c6-175">Toutefois, rien ne se produira à ce stade, puisque `Program` n'a pas d'importations à remplir.</span><span class="sxs-lookup"><span data-stu-id="028c6-175">At this point, however, nothing will happen, since `Program` has no imports to fill.</span></span>

## <a name="imports-and-exports-with-attributes"></a><span data-ttu-id="028c6-176">Importations et exportations avec des attributs</span><span class="sxs-lookup"><span data-stu-id="028c6-176">Imports and Exports with attributes</span></span>

<span data-ttu-id="028c6-177">Tout d'abord, `Program` doit importer une calculatrice.</span><span class="sxs-lookup"><span data-stu-id="028c6-177">First, you have `Program` import a calculator.</span></span> <span data-ttu-id="028c6-178">Cela permet de séparer les problèmes d'interface utilisateur, comme l'entrée et la sortie console qui iront dans `Program`, de la logique de la calculatrice.</span><span class="sxs-lookup"><span data-stu-id="028c6-178">This allows the separation of user interface concerns, such as the console input and output that will go into `Program`, from the logic of the calculator.</span></span>

<span data-ttu-id="028c6-179">Ajoutez le code suivant à la classe `Program` :</span><span class="sxs-lookup"><span data-stu-id="028c6-179">Add the following code to the `Program` class:</span></span>

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

<span data-ttu-id="028c6-180">Notez que la déclaration de l'objet `calculator` n'est pas inhabituelle, mais qu'elle est décorée avec l'attribut <xref:System.ComponentModel.Composition.ImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="028c6-180">Notice that the declaration of the `calculator` object is not unusual, but that it is decorated with the <xref:System.ComponentModel.Composition.ImportAttribute> attribute.</span></span> <span data-ttu-id="028c6-181">Cet attribut déclare qu'un élément est une importation, c'est-à-dire qu'il sera rempli par le moteur de composition quand l'objet sera composé.</span><span class="sxs-lookup"><span data-stu-id="028c6-181">This attribute declares something to be an import; that is, it will be filled by the composition engine when the object is composed.</span></span>

<span data-ttu-id="028c6-182">Chaque importation a un *contrat* qui détermine à quelles exportations elle doit être associée.</span><span class="sxs-lookup"><span data-stu-id="028c6-182">Every import has a *contract*, which determines what exports it will be matched with.</span></span> <span data-ttu-id="028c6-183">Le contrat peut être une chaîne explicitement spécifiée ou il peut être généré automatiquement par MEF à partir d'un type donné (dans ce cas, l'interface `ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="028c6-183">The contract can be an explicitly specified string, or it can be automatically generated by MEF from a given type, in this case the interface `ICalculator`.</span></span> <span data-ttu-id="028c6-184">Toute exportation déclarée avec un contrat correspondant effectuera cette importation.</span><span class="sxs-lookup"><span data-stu-id="028c6-184">Any export declared with a matching contract will fulfill this import.</span></span> <span data-ttu-id="028c6-185">Le type de l'objet `calculator` est ici `ICalculator`, mais ce n'est pas une obligation.</span><span class="sxs-lookup"><span data-stu-id="028c6-185">Note that while the type of the `calculator` object is in fact `ICalculator`, this is not required.</span></span> <span data-ttu-id="028c6-186">Le contrat est indépendant du type de l'objet d'importation.</span><span class="sxs-lookup"><span data-stu-id="028c6-186">The contract is independent from the type of the importing object.</span></span> <span data-ttu-id="028c6-187">(Dans ce cas, vous pouvez ignorer `typeof(ICalculator)`.</span><span class="sxs-lookup"><span data-stu-id="028c6-187">(In this case, you could leave out the `typeof(ICalculator)`.</span></span> <span data-ttu-id="028c6-188">MEF déduira automatiquement que le contrat est basé sur le type de l'importation, sauf si vous spécifiez un type explicitement.)</span><span class="sxs-lookup"><span data-stu-id="028c6-188">MEF will automatically assume the contract to be based on the type of the import unless you specify it explicitly.)</span></span>

<span data-ttu-id="028c6-189">Ajoutez cette interface très simple au module ou à l'espace de noms `SimpleCalculator` :</span><span class="sxs-lookup"><span data-stu-id="028c6-189">Add this very simple interface to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface ICalculator
    Function Calculate(input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

<span data-ttu-id="028c6-190">Vous venez de définir `ICalculator`, vous avez besoin maintenant d'une classe qui l'implémente.</span><span class="sxs-lookup"><span data-stu-id="028c6-190">Now that you have defined `ICalculator`, you need a class that implements it.</span></span> <span data-ttu-id="028c6-191">Ajoutez la classe suivante au module ou à l'espace de noms `SimpleCalculator` :</span><span class="sxs-lookup"><span data-stu-id="028c6-191">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

<span data-ttu-id="028c6-192">Voici l'exportation qui correspondra à l'importation dans `Program`.</span><span class="sxs-lookup"><span data-stu-id="028c6-192">Here is the export that will match the import in `Program`.</span></span> <span data-ttu-id="028c6-193">Pour que l'exportation corresponde à l'importation, l'exportation doit avoir le même contrat.</span><span class="sxs-lookup"><span data-stu-id="028c6-193">In order for the export to match the import, the export must have the same contract.</span></span> <span data-ttu-id="028c6-194">Une exportation avec un contrat basé sur `typeof(MySimpleCalculator)` engendrerait une incompatibilité, et l'importation ne serait pas remplie ; les contrats doivent correspondre exactement.</span><span class="sxs-lookup"><span data-stu-id="028c6-194">Exporting under a contract based on `typeof(MySimpleCalculator)` would produce a mismatch, and the import would not be filled; the contract needs to match exactly.</span></span>

<span data-ttu-id="028c6-195">Comme le conteneur de composition sera rempli avec toutes les parties disponibles dans cet assembly, la partie `MySimpleCalculator` sera disponible.</span><span class="sxs-lookup"><span data-stu-id="028c6-195">Since the composition container will be populated with all the parts available in this assembly, the `MySimpleCalculator` part will be available.</span></span> <span data-ttu-id="028c6-196">Quand le constructeur de `Program` exécutera la composition sur l'objet `Program`, son importation sera remplie avec un objet `MySimpleCalculator` qui sera créé à cet effet.</span><span class="sxs-lookup"><span data-stu-id="028c6-196">When the constructor for `Program` performs composition on the `Program` object, its import will be filled with a `MySimpleCalculator` object, which will be created for that purpose.</span></span>

<span data-ttu-id="028c6-197">La couche d'interface utilisateur (`Program`) n'a besoin d'aucune autre information.</span><span class="sxs-lookup"><span data-stu-id="028c6-197">The user interface layer (`Program`) does not need to know anything else.</span></span> <span data-ttu-id="028c6-198">Vous pouvez donc remplir le reste de la logique d'interface utilisateur dans la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="028c6-198">You can therefore fill in the rest of the user interface logic in the `Main` method.</span></span>

<span data-ttu-id="028c6-199">Ajoutez le code suivant à la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="028c6-199">Add the following code to the `Main` method:</span></span>

```vb
Sub Main()
    ' Composition is performed in the constructor.
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    // Composition is performed in the constructor.
    var p = new Program();
    string s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 <span data-ttu-id="028c6-200">Ce code lit simplement une ligne d'entrée et appelle la fonction `Calculate` de l'interface `ICalculator` dans le résultat, qu'il réécrit dans la console.</span><span class="sxs-lookup"><span data-stu-id="028c6-200">This code simply reads a line of input and calls the `Calculate` function of `ICalculator` on the result, which it writes back to the console.</span></span> <span data-ttu-id="028c6-201">C'est le seul code dont vous avez besoin dans `Program`.</span><span class="sxs-lookup"><span data-stu-id="028c6-201">That is all the code you need in `Program`.</span></span> <span data-ttu-id="028c6-202">Tout le reste du processus s'effectuera dans les parties.</span><span class="sxs-lookup"><span data-stu-id="028c6-202">All the rest of the work will happen in the parts.</span></span>

## <a name="further-imports-and-importmany"></a><span data-ttu-id="028c6-203">Importations supplémentaires et ImportMany</span><span class="sxs-lookup"><span data-stu-id="028c6-203">Further Imports and ImportMany</span></span>

<span data-ttu-id="028c6-204">Pour que SimpleCalculator soit extensible, il doit importer une liste d'opérations.</span><span class="sxs-lookup"><span data-stu-id="028c6-204">In order for SimpleCalculator to be extensible, it needs to import a list of operations.</span></span> <span data-ttu-id="028c6-205">Un attribut <xref:System.ComponentModel.Composition.ImportAttribute> standard est rempli par une seule exportation <xref:System.ComponentModel.Composition.ExportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="028c6-205">An ordinary <xref:System.ComponentModel.Composition.ImportAttribute> attribute is filled by one and only one <xref:System.ComponentModel.Composition.ExportAttribute>.</span></span> <span data-ttu-id="028c6-206">Si plusieurs exportations sont disponibles, le moteur de composition génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="028c6-206">If more than one is available, the composition engine produces an error.</span></span> <span data-ttu-id="028c6-207">Pour créer une importation qui peut être remplie par un nombre indéfini d'exportations, utilisez l'attribut <xref:System.ComponentModel.Composition.ImportManyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="028c6-207">To create an import that can be filled by any number of exports, you can use the <xref:System.ComponentModel.Composition.ImportManyAttribute> attribute.</span></span>

<span data-ttu-id="028c6-208">Ajoutez la propriété operations suivante à la classe `MySimpleCalculator` :</span><span class="sxs-lookup"><span data-stu-id="028c6-208">Add the following operations property to the `MySimpleCalculator` class:</span></span>

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

<span data-ttu-id="028c6-209"><xref:System.Lazy%602> est un type fourni par MEF pour contenir des références indirectes à des exportations.</span><span class="sxs-lookup"><span data-stu-id="028c6-209"><xref:System.Lazy%602> is a type provided by MEF to hold indirect references to exports.</span></span> <span data-ttu-id="028c6-210">Ici, en plus de l’objet exporté lui-même, vous obtenez des *métadonnées d’exportation*, ou des informations qui décrivent l’objet exporté.</span><span class="sxs-lookup"><span data-stu-id="028c6-210">Here, in addition to the exported object itself, you also get *export metadata*, or information that describes the exported object.</span></span> <span data-ttu-id="028c6-211">Chaque <xref:System.Lazy%602> contient un objet `IOperation` représentant une opération réelle et un objet `IOperationData` représentant ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="028c6-211">Each <xref:System.Lazy%602> contains an `IOperation` object, representing an actual operation, and an `IOperationData` object, representing its metadata.</span></span>

<span data-ttu-id="028c6-212">Ajoutez les interfaces simples suivantes au module ou à l'espace de noms `SimpleCalculator` :</span><span class="sxs-lookup"><span data-stu-id="028c6-212">Add the following simple interfaces to the module or `SimpleCalculator` namespace:</span></span>

```vb
Public Interface IOperation
    Function Operate(left As Integer, right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 <span data-ttu-id="028c6-213">Dans ce cas, les métadonnées pour chaque opération sont le symbole qui représente cette opération, tel que +,- \*,, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="028c6-213">In this case, the metadata for each operation is the symbol that represents that operation, such as +, -, \*, and so on.</span></span> <span data-ttu-id="028c6-214">Pour rendre l'addition disponible, ajoutez la classe suivante au module ou à l'espace de noms `SimpleCalculator` :</span><span class="sxs-lookup"><span data-stu-id="028c6-214">To make the addition operation available, add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

<span data-ttu-id="028c6-215">L'attribut <xref:System.ComponentModel.Composition.ExportAttribute> fonctionne comme auparavant.</span><span class="sxs-lookup"><span data-stu-id="028c6-215">The <xref:System.ComponentModel.Composition.ExportAttribute> attribute functions as it did before.</span></span> <span data-ttu-id="028c6-216">L'attribut <xref:System.ComponentModel.Composition.ExportMetadataAttribute> joint des métadonnées à cette exportation, sous la forme d'une paire nom-valeur.</span><span class="sxs-lookup"><span data-stu-id="028c6-216">The <xref:System.ComponentModel.Composition.ExportMetadataAttribute> attribute attaches metadata, in the form of a name-value pair, to that export.</span></span> <span data-ttu-id="028c6-217">La classe `Add` implémente `IOperation`, mais aucune classe implémentant `IOperationData` n'est explicitement définie.</span><span class="sxs-lookup"><span data-stu-id="028c6-217">While the `Add` class implements `IOperation`, a class that implements `IOperationData` is not explicitly defined.</span></span> <span data-ttu-id="028c6-218">En fait, MEF crée implicitement une classe en lui attribuant des propriétés basées sur les noms des métadonnées fournies.</span><span class="sxs-lookup"><span data-stu-id="028c6-218">Instead, a class is implicitly created by MEF with properties based on the names of the metadata provided.</span></span> <span data-ttu-id="028c6-219">(C'est l'une des différentes méthodes permettant d'accéder aux métadonnées dans MEF.)</span><span class="sxs-lookup"><span data-stu-id="028c6-219">(This is one of several ways to access metadata in MEF.)</span></span>

<span data-ttu-id="028c6-220">La composition dans MEF est *récursive*.</span><span class="sxs-lookup"><span data-stu-id="028c6-220">Composition in MEF is *recursive*.</span></span> <span data-ttu-id="028c6-221">Vous avez composé explicitement l'objet `Program`, qui a importé un `ICalculator` de type `MySimpleCalculator`.</span><span class="sxs-lookup"><span data-stu-id="028c6-221">You explicitly composed the `Program` object, which imported an `ICalculator` that turned out to be of type `MySimpleCalculator`.</span></span> <span data-ttu-id="028c6-222">Ensuite, `MySimpleCalculator` importe une collection d'objets `IOperation`. Cette importation sera remplie quand `MySimpleCalculator` sera créé, en même temps que les importations de `Program`.</span><span class="sxs-lookup"><span data-stu-id="028c6-222">`MySimpleCalculator`, in turn, imports a collection of `IOperation` objects, and that import will be filled when `MySimpleCalculator` is created, at the same time as the imports of `Program`.</span></span> <span data-ttu-id="028c6-223">Si la classe `Add` a déclaré une importation supplémentaire, celle-ci devra également être remplie, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="028c6-223">If the `Add` class declared a further import, that too would have to be filled, and so on.</span></span> <span data-ttu-id="028c6-224">Une importation non remplie provoque une erreur de composition.</span><span class="sxs-lookup"><span data-stu-id="028c6-224">Any import left unfilled results in a composition error.</span></span> <span data-ttu-id="028c6-225">(Toutefois, il est possible de déclarer que des importations sont facultatives ou de leur affecter des valeurs par défaut.)</span><span class="sxs-lookup"><span data-stu-id="028c6-225">(It is possible, however, to declare imports to be optional or to assign them default values.)</span></span>

## <a name="calculator-logic"></a><span data-ttu-id="028c6-226">Logique de la calculatrice</span><span class="sxs-lookup"><span data-stu-id="028c6-226">Calculator Logic</span></span>

<span data-ttu-id="028c6-227">Après avoir mis en place les différentes parties, il reste simplement à définir la logique de la calculatrice elle-même.</span><span class="sxs-lookup"><span data-stu-id="028c6-227">With these parts in place, all that remains is the calculator logic itself.</span></span> <span data-ttu-id="028c6-228">Ajoutez le code suivant à la classe `MySimpleCalculator` pour implémenter la méthode `Calculate` :</span><span class="sxs-lookup"><span data-stu-id="028c6-228">Add the following code in the `MySimpleCalculator` class to implement the `Calculate` method:</span></span>

```vb
Public Function Calculate(input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    ' Finds the operator.
    Dim fn = FindFirstNonDigit(input)
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        ' Separate out the operands.
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(string input)
{
    int left;
    int right;
    char operation;
    // Finds the operator.
    int fn = FindFirstNonDigit(input);
    if (fn < 0) return "Could not parse command.";

    try
    {
        // Separate out the operands.
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

<span data-ttu-id="028c6-229">Les étapes initiales analysent la chaîne d'entrée dans les opérandes de gauche et de droite, et un caractère d'opérateur.</span><span class="sxs-lookup"><span data-stu-id="028c6-229">The initial steps parse the input string into left and right operands and an operator character.</span></span> <span data-ttu-id="028c6-230">Dans la boucle `foreach`, chaque membre de la collection `operations` est examiné.</span><span class="sxs-lookup"><span data-stu-id="028c6-230">In the `foreach` loop, every member of the `operations` collection is examined.</span></span> <span data-ttu-id="028c6-231">Ces objets sont de type <xref:System.Lazy%602>, et leurs valeurs de métadonnées et d'objet exporté sont accessibles respectivement via la propriété <xref:System.Lazy%602.Metadata%2A> et la propriété <xref:System.Lazy%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="028c6-231">These objects are of type <xref:System.Lazy%602>, and their metadata values and exported object can be accessed with the <xref:System.Lazy%602.Metadata%2A> property and the <xref:System.Lazy%601.Value%2A> property respectively.</span></span> <span data-ttu-id="028c6-232">Dans ce cas, si la propriété `Symbol` découverte de l'objet `IOperationData` est une correspondance, la calculatrice appelle la méthode `Operate` de l'objet `IOperation` et retourne le résultat.</span><span class="sxs-lookup"><span data-stu-id="028c6-232">In this case, if the `Symbol` property of the `IOperationData` object is discovered to be a match, the calculator calls the `Operate` method of the `IOperation` object and returns the result.</span></span>

<span data-ttu-id="028c6-233">Pour terminer la calculatrice, vous devez également définir une méthode d'assistance qui retourne la position du premier caractère non numérique dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="028c6-233">To complete the calculator, you also need a helper method that returns the position of the first non-digit character in a string.</span></span> <span data-ttu-id="028c6-234">Ajoutez la méthode d'assistance suivante à la classe `MySimpleCalculator` :</span><span class="sxs-lookup"><span data-stu-id="028c6-234">Add the following helper method to the `MySimpleCalculator` class:</span></span>

```vb
Private Function FindFirstNonDigit(s As String) As Integer
    For i = 0 To s.Length - 1
        If Not Char.IsDigit(s(i)) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(string s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!Char.IsDigit(s[i])) return i;
    }
    return -1;
}
```

<span data-ttu-id="028c6-235">Vous devez maintenant être en mesure de compiler et d'exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="028c6-235">You should now be able to compile and run the project.</span></span> <span data-ttu-id="028c6-236">Dans Visual Basic, assurez-vous d'avoir ajouté le mot clé `Public` au module `Module1`.</span><span class="sxs-lookup"><span data-stu-id="028c6-236">In Visual Basic, make sure that you added the `Public` keyword to `Module1`.</span></span> <span data-ttu-id="028c6-237">Dans la fenêtre de console, tapez une addition, par exemple « 5 + 3 », et la calculatrice retourne le résultat.</span><span class="sxs-lookup"><span data-stu-id="028c6-237">In the console window, type an addition operation, such as "5+3", and the calculator returns the results.</span></span> <span data-ttu-id="028c6-238">L’utilisation d’un autre opérateur entraîne l’affichage du message</span><span class="sxs-lookup"><span data-stu-id="028c6-238">Any other operator results in the "Operation Not Found!"</span></span> <span data-ttu-id="028c6-239">.</span><span class="sxs-lookup"><span data-stu-id="028c6-239">message.</span></span>

## <a name="extending-simplecalculator-using-a-new-class"></a><span data-ttu-id="028c6-240">Extension de SimpleCalculator à l’aide d’une nouvelle classe</span><span class="sxs-lookup"><span data-stu-id="028c6-240">Extending SimpleCalculator using a new class</span></span>

<span data-ttu-id="028c6-241">La calculatrice fonctionne. Vous pouvez maintenant ajouter facilement une nouvelle opération.</span><span class="sxs-lookup"><span data-stu-id="028c6-241">Now that the calculator works, adding a new operation is easy.</span></span> <span data-ttu-id="028c6-242">Ajoutez la classe suivante au module ou à l'espace de noms `SimpleCalculator` :</span><span class="sxs-lookup"><span data-stu-id="028c6-242">Add the following class to the module or `SimpleCalculator` namespace:</span></span>

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

<span data-ttu-id="028c6-243">Compilez et exécutez le projet.</span><span class="sxs-lookup"><span data-stu-id="028c6-243">Compile and run the project.</span></span> <span data-ttu-id="028c6-244">Tapez une soustraction, par exemple « 5-3 ».</span><span class="sxs-lookup"><span data-stu-id="028c6-244">Type a subtraction operation, such as "5-3".</span></span> <span data-ttu-id="028c6-245">La calculatrice prend désormais en charge la soustraction ainsi que l'addition.</span><span class="sxs-lookup"><span data-stu-id="028c6-245">The calculator now supports subtraction as well as addition.</span></span>

## <a name="extending-simplecalculator-using-a-new-assembly"></a><span data-ttu-id="028c6-246">Extension de SimpleCalculator à l’aide d’un nouvel assembly</span><span class="sxs-lookup"><span data-stu-id="028c6-246">Extending SimpleCalculator using a new assembly</span></span>

<span data-ttu-id="028c6-247">L'ajout de classes au code source est une opération relativement simple, mais MEF permet de rechercher des parties en dehors de la source d'une application.</span><span class="sxs-lookup"><span data-stu-id="028c6-247">Adding classes to the source code is simple enough, but MEF provides the ability to look outside an application’s own source for parts.</span></span> <span data-ttu-id="028c6-248">Pour découvrir cette possibilité, vous devez modifier SimpleCalculator pour qu'il recherche des parties dans un répertoire et dans son propre assembly, en ajoutant un catalogue <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span><span class="sxs-lookup"><span data-stu-id="028c6-248">To demonstrate this, you will need to modify SimpleCalculator to search a directory, as well as its own assembly, for parts, by adding a <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>.</span></span>

<span data-ttu-id="028c6-249">Ajoutez un nouveau répertoire nommé `Extensions` au projet SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="028c6-249">Add a new directory named `Extensions` to the SimpleCalculator project.</span></span> <span data-ttu-id="028c6-250">Assurez-vous de l'ajouter au niveau du projet et pas au niveau de la solution.</span><span class="sxs-lookup"><span data-stu-id="028c6-250">Make sure to add it at the project level, and not at the solution level.</span></span> <span data-ttu-id="028c6-251">Ajoutez ensuite un nouveau projet de bibliothèque de classes, appelé `ExtendedOperations`, à la solution.</span><span class="sxs-lookup"><span data-stu-id="028c6-251">Then add a new Class Library project to the solution, named `ExtendedOperations`.</span></span> <span data-ttu-id="028c6-252">Le nouveau projet sera compilé dans un assembly distinct.</span><span class="sxs-lookup"><span data-stu-id="028c6-252">The new project will compile into a separate assembly.</span></span>

<span data-ttu-id="028c6-253">Ouvrez le concepteur de propriétés du projet pour le projet ExtendedOperations, puis cliquez sur l’onglet **compiler** ou **générer** . modifiez le chemin de sortie de la **génération** ou le **chemin de sortie** pour qu’il pointe vers le répertoire extensions dans le répertoire du projet SimpleCalculator (*.. \SimpleCalculator\Extensions\\*).</span><span class="sxs-lookup"><span data-stu-id="028c6-253">Open the Project Properties Designer for the ExtendedOperations project and click the **Compile** or **Build** tab. Change the **Build output path** or **Output path** to point to the Extensions directory in the SimpleCalculator project directory (*..\SimpleCalculator\Extensions\\*).</span></span>

 <span data-ttu-id="028c6-254">Dans *Module1. vb* ou *Program.cs*, ajoutez la ligne suivante au `Program` constructeur :</span><span class="sxs-lookup"><span data-stu-id="028c6-254">In *Module1.vb* or *Program.cs*, add the following line to the `Program` constructor:</span></span>

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

<span data-ttu-id="028c6-255">Remplacez le chemin d’accès de l’exemple par le chemin d’accès à votre répertoire Extensions.</span><span class="sxs-lookup"><span data-stu-id="028c6-255">Replace the example path with the path to your Extensions directory.</span></span> <span data-ttu-id="028c6-256">(Ce chemin d'accès absolu sert uniquement au débogage.</span><span class="sxs-lookup"><span data-stu-id="028c6-256">(This absolute path is for debugging purposes only.</span></span> <span data-ttu-id="028c6-257">Dans une application de production, vous utiliseriez un chemin d’accès relatif.) <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> Ajoute à présent toutes les parties trouvées dans les assemblys du répertoire extensions au conteneur de composition.</span><span class="sxs-lookup"><span data-stu-id="028c6-257">In a production application, you would use a relative path.) The <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> will now add any parts found in any assemblies in the Extensions directory to the composition container.</span></span>

<span data-ttu-id="028c6-258">Dans le projet ExtendedOperations, ajoutez des références à SimpleCalculator et à System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="028c6-258">In the ExtendedOperations project, add references to SimpleCalculator and System.ComponentModel.Composition.</span></span> <span data-ttu-id="028c6-259">Dans le fichier de classe ExtendedOperations, ajoutez une instruction `Imports` ou `using` pour System.ComponentModel.Composition.</span><span class="sxs-lookup"><span data-stu-id="028c6-259">In the ExtendedOperations class file, add an `Imports` or a `using` statement for System.ComponentModel.Composition.</span></span> <span data-ttu-id="028c6-260">Dans Visual Basic, ajoutez également une instruction `Imports` pour SimpleCalculator.</span><span class="sxs-lookup"><span data-stu-id="028c6-260">In Visual Basic, also add an `Imports` statement for SimpleCalculator.</span></span> <span data-ttu-id="028c6-261">Ajoutez ensuite la classe suivante au fichier de classe ExtendedOperations :</span><span class="sxs-lookup"><span data-stu-id="028c6-261">Then add the following class to the ExtendedOperations class file:</span></span>

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(left As Integer, right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

<span data-ttu-id="028c6-262">Notez que l'attribut <xref:System.ComponentModel.Composition.ExportAttribute> doit avoir le même type que <xref:System.ComponentModel.Composition.ImportAttribute> pour que le contrat corresponde.</span><span class="sxs-lookup"><span data-stu-id="028c6-262">Note that in order for the contract to match, the <xref:System.ComponentModel.Composition.ExportAttribute> attribute must have the same type as the <xref:System.ComponentModel.Composition.ImportAttribute>.</span></span>

<span data-ttu-id="028c6-263">Compilez et exécutez le projet.</span><span class="sxs-lookup"><span data-stu-id="028c6-263">Compile and run the project.</span></span> <span data-ttu-id="028c6-264">Testez le nouvel opérateur Mod (%).</span><span class="sxs-lookup"><span data-stu-id="028c6-264">Test the new Mod (%) operator.</span></span>

## <a name="conclusion"></a><span data-ttu-id="028c6-265">Conclusion</span><span class="sxs-lookup"><span data-stu-id="028c6-265">Conclusion</span></span>

<span data-ttu-id="028c6-266">Cette rubrique a couvert les concepts de base de MEF.</span><span class="sxs-lookup"><span data-stu-id="028c6-266">This topic covered the basic concepts of MEF.</span></span>

- <span data-ttu-id="028c6-267">Parties, catalogues et conteneur de composition</span><span class="sxs-lookup"><span data-stu-id="028c6-267">Parts, catalogs, and the composition container</span></span>

     <span data-ttu-id="028c6-268">Les parties et le conteneur de composition sont les blocs de construction élémentaires d'une application MEF.</span><span class="sxs-lookup"><span data-stu-id="028c6-268">Parts and the composition container are the basic building blocks of a MEF application.</span></span> <span data-ttu-id="028c6-269">Une partie est un objet qui importe ou exporte une valeur, y compris lui-même.</span><span class="sxs-lookup"><span data-stu-id="028c6-269">A part is any object that imports or exports a value, up to and including itself.</span></span> <span data-ttu-id="028c6-270">Un catalogue fournit une collection de parties disponibles dans une source donnée.</span><span class="sxs-lookup"><span data-stu-id="028c6-270">A catalog provides a collection of parts from a particular source.</span></span> <span data-ttu-id="028c6-271">Le conteneur de composition utilise les parties fournies par un catalogue pour exécuter la composition, la liaison d’importations à des exportations.</span><span class="sxs-lookup"><span data-stu-id="028c6-271">The composition container uses the parts provided by a catalog to perform composition, the binding of imports to exports.</span></span>

- <span data-ttu-id="028c6-272">Importations et exportations</span><span class="sxs-lookup"><span data-stu-id="028c6-272">Imports and exports</span></span>

     <span data-ttu-id="028c6-273">Les importations et les exportations sont un moyen de communication utilisé par les composants.</span><span class="sxs-lookup"><span data-stu-id="028c6-273">Imports and exports are the way by which components communicate.</span></span> <span data-ttu-id="028c6-274">Lors d'une importation, le composant spécifie qu'il a besoin d'une valeur ou d'un objet en particulier et, lors d'une exportation, il indique la disponibilité d'une valeur.</span><span class="sxs-lookup"><span data-stu-id="028c6-274">With an import, the component specifies a need for a particular value or object, and with an export it specifies the availability of a value.</span></span> <span data-ttu-id="028c6-275">Chaque importation est associée à une liste d'exportations par l'intermédiaire de son contrat.</span><span class="sxs-lookup"><span data-stu-id="028c6-275">Each import is matched with a list of exports by way of its contract.</span></span>

## <a name="next-steps"></a><span data-ttu-id="028c6-276">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="028c6-276">Next steps</span></span>

<span data-ttu-id="028c6-277">Pour télécharger le code complet de cet exemple, consultez l' [exemple SimpleCalculator (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span><span class="sxs-lookup"><span data-stu-id="028c6-277">To download the complete code for this example, see the [SimpleCalculator sample (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/simple-calculator-vb/).</span></span>

 <span data-ttu-id="028c6-278">Pour obtenir plus d’informations et des exemples de code, consultez [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span><span class="sxs-lookup"><span data-stu-id="028c6-278">For more information and code examples, see [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef).</span></span> <span data-ttu-id="028c6-279">Pour obtenir une liste des types MEF, consultez l'espace de noms <xref:System.ComponentModel.Composition?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="028c6-279">For a list of the MEF types, see the <xref:System.ComponentModel.Composition?displayProperty=nameWithType> namespace.</span></span>
