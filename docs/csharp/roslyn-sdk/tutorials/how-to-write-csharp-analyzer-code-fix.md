---
title: 'Tutoriel : Écrire votre premier analyseur et correctif de code'
description: Ce tutoriel fournit des instructions détaillées pour générer un analyseur et un correctif de code à l’aide du SDK .NET Compiler (API Roslyn).
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: e79907f364939462b7d0d5814c4752be23bcfdf3
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381591"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="b0739-103">Tutoriel : Écrire votre premier analyseur et correctif de code</span><span class="sxs-lookup"><span data-stu-id="b0739-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="b0739-104">Le SDK .NET Compiler Platform fournit les outils nécessaires pour créer des avertissements personnalisés qui ciblent C# ou le code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b0739-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="b0739-105">Votre **analyseur** contient le code qui reconnaît les violations de votre règle.</span><span class="sxs-lookup"><span data-stu-id="b0739-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="b0739-106">Votre **correctif de code** contient le code qui résout la violation.</span><span class="sxs-lookup"><span data-stu-id="b0739-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="b0739-107">Les règles que vous implémentez peuvent aller de la structure du code au style de codage et aux conventions d’affectation de noms, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="b0739-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="b0739-108">.NET Compiler Platform fournit le framework permettant d’exécuter l’analyse alors que les développeurs écrivent du code, et toutes les fonctionnalités de l’IU Visual Studio pour corriger le code : afficher des tildes dans l’éditeur, renseigner la liste d’erreurs Visual Studio, créer des suggestions « ampoule » et afficher un aperçu détaillé des corrections suggérées.</span><span class="sxs-lookup"><span data-stu-id="b0739-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="b0739-109">Dans ce tutoriel, vous allez explorer la création d’un **analyseur** et d’un **correctif de code** associé à l’aide des API Roslyn.</span><span class="sxs-lookup"><span data-stu-id="b0739-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="b0739-110">Un analyseur consiste à effectuer une analyse du code source et signaler un problème à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b0739-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="b0739-111">Un analyseur peut également fournir un correctif de code qui représente une modification du code source de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b0739-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="b0739-112">Ce tutoriel crée un analyseur qui recherche des déclarations de variables locales qui pourraient être déclarées à l’aide du modificateur `const` mais qui ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="b0739-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="b0739-113">Le correctif de code associé modifie ces déclarations pour ajouter le modificateur `const`.</span><span class="sxs-lookup"><span data-stu-id="b0739-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0739-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="b0739-114">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b0739-115">Le modèle Visual Studio **Analyzer avec correction de code (.NET standard)** actuel contient un bogue connu et doit être corrigé dans Visual Studio 2019 version 16,7.</span><span class="sxs-lookup"><span data-stu-id="b0739-115">The current Visual Studio **Analyzer with code fix (.NET Standard)** template has a known bug in it and should be fixed in Visual Studio 2019 version 16.7.</span></span> <span data-ttu-id="b0739-116">Les projets dans le modèle ne se compilent pas, sauf si les modifications suivantes sont apportées :</span><span class="sxs-lookup"><span data-stu-id="b0739-116">The projects in the template will not compile unless the following changes are made:</span></span>
>
> 1. <span data-ttu-id="b0739-117">Sélectionnez les **Outils**  >  **options**outils  >  **Gestionnaire de package NuGet**  >  **sources du package**</span><span class="sxs-lookup"><span data-stu-id="b0739-117">Select **Tools** > **Options** > **NuGet Package Manager** > **Package Sources**</span></span>
>    - <span data-ttu-id="b0739-118">Sélectionnez le bouton plus (+) pour ajouter une nouvelle source :</span><span class="sxs-lookup"><span data-stu-id="b0739-118">Select the plus button, to add a new source:</span></span>
>    - <span data-ttu-id="b0739-119">Définir la **source** sur `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` et sélectionner **mettre à jour**</span><span class="sxs-lookup"><span data-stu-id="b0739-119">Set the **Source** to `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` and select **Update**</span></span>
> 1. <span data-ttu-id="b0739-120">Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **MakeConst. vsix** , puis sélectionnez **modifier le fichier projet** .</span><span class="sxs-lookup"><span data-stu-id="b0739-120">From the **Solution Explorer**, right-click on the **MakeConst.Vsix** project, and select **Edit Project File**</span></span>
>    - <span data-ttu-id="b0739-121">Mettez à jour le `<AssemblyName>` nœud pour ajouter le `.Visx` suffixe :</span><span class="sxs-lookup"><span data-stu-id="b0739-121">Update the `<AssemblyName>` node to add the `.Visx` suffix:</span></span>
>      - `<AssemblyName>MakeConst.Vsix</AssemblyName>`
>    - <span data-ttu-id="b0739-122">Mettez à jour le `<ProjectReference>` nœud sur la ligne 41 pour modifier la `TargetFramework` valeur :</span><span class="sxs-lookup"><span data-stu-id="b0739-122">Update the `<ProjectReference>` node on line 41 to alter the `TargetFramework` value:</span></span>
>      - `<ProjectReference Update="@(ProjectReference)" AdditionalProperties="TargetFramework=netstandard2.0" />`
> 1. <span data-ttu-id="b0739-123">Mettez à jour le fichier *MakeConstUnitTests.cs* dans le projet *MakeConst. test* :</span><span class="sxs-lookup"><span data-stu-id="b0739-123">Update the *MakeConstUnitTests.cs* file, in the *MakeConst.Test* project:</span></span>
>    - <span data-ttu-id="b0739-124">Remplacez la ligne 9 par ce qui suit, notez la modification de l’espace de noms :</span><span class="sxs-lookup"><span data-stu-id="b0739-124">Change line 9 to the following, notice namespace alteration:</span></span>
>      - `using Verify = Microsoft.CodeAnalysis.CSharp.Testing.MSTest.CodeFixVerifier<`
>    - <span data-ttu-id="b0739-125">Remplacez la ligne 24 par la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="b0739-125">Change line 24 to the following method:</span></span>
>      - `await Verify.VerifyAnalyzerAsync(test);`
>    - <span data-ttu-id="b0739-126">Remplacez la ligne 62 par la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="b0739-126">Change line 62 to the following method:</span></span>
>      - `await Verify.VerifyCodeFixAsync(test, expected, fixtest);`

- [<span data-ttu-id="b0739-127">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b0739-127">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="b0739-128">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="b0739-128">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="b0739-129">Vous devez installer le kit de **développement logiciel (SDK) .NET Compiler Platform** via le Visual Studio installer :</span><span class="sxs-lookup"><span data-stu-id="b0739-129">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="b0739-130">Il existe plusieurs étapes pour créer et valider votre analyseur :</span><span class="sxs-lookup"><span data-stu-id="b0739-130">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="b0739-131">Créez la solution.</span><span class="sxs-lookup"><span data-stu-id="b0739-131">Create the solution.</span></span>
1. <span data-ttu-id="b0739-132">Enregistrez le nom de l’analyseur et sa description.</span><span class="sxs-lookup"><span data-stu-id="b0739-132">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="b0739-133">Créez un rapport sur les avertissements et les recommandations de l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="b0739-133">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="b0739-134">Implémentez le correctif de code pour accepter les recommandations.</span><span class="sxs-lookup"><span data-stu-id="b0739-134">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="b0739-135">Améliorez l’analyse par le biais de tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="b0739-135">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="b0739-136">Explorer le modèle d’analyseur</span><span class="sxs-lookup"><span data-stu-id="b0739-136">Explore the analyzer template</span></span>

<span data-ttu-id="b0739-137">Votre analyseur signale à l’utilisateur les déclarations de variables locales qui peuvent être converties en constantes locales.</span><span class="sxs-lookup"><span data-stu-id="b0739-137">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="b0739-138">Considérons par exemple le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b0739-138">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="b0739-139">Dans le code ci-dessus, une valeur constante est attribuée à `x` et n’est jamais modifiée.</span><span class="sxs-lookup"><span data-stu-id="b0739-139">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="b0739-140">Elle peut être déclarée à l’aide du modificateur `const` :</span><span class="sxs-lookup"><span data-stu-id="b0739-140">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="b0739-141">L’analyse pour déterminer si une variable peut être déclarée constante est impliquée, nécessitant une analyse syntaxique, une analyse constante de l’expression de l’initialiseur et une analyse du flux de données pour s’assurer que la variable n’est jamais accessible en écriture.</span><span class="sxs-lookup"><span data-stu-id="b0739-141">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="b0739-142">.NET Compiler Platform fournit les API qui simplifient l’exécution de cette analyse.</span><span class="sxs-lookup"><span data-stu-id="b0739-142">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="b0739-143">La première étape consiste à créer un nouveau projet C# **Analyseur avec correctif de code**.</span><span class="sxs-lookup"><span data-stu-id="b0739-143">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="b0739-144">Dans Visual Studio, choisissez **Fichier > Nouveau > Projet...** pour afficher la boîte de dialogue Nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="b0739-144">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="b0739-145">Sous **Visual C# > Extensibilité**, choisissez **Analyseur avec correctif de code (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="b0739-145">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="b0739-146">Nommez votre projet « **MakeConst** », puis cliquez sur OK.</span><span class="sxs-lookup"><span data-stu-id="b0739-146">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="b0739-147">Le modèle Analyseur avec correctif de code crée trois projets : un contient l’analyseur et le correctif de code, le second est un projet de test unitaire et le troisième est le projet VSIX.</span><span class="sxs-lookup"><span data-stu-id="b0739-147">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="b0739-148">Le projet de démarrage par défaut est le projet VSIX.</span><span class="sxs-lookup"><span data-stu-id="b0739-148">The default startup project is the VSIX project.</span></span> <span data-ttu-id="b0739-149">Appuyez sur <kbd>F5</kbd> pour démarrer le projet VSIX.</span><span class="sxs-lookup"><span data-stu-id="b0739-149">Press <kbd>F5</kbd> to start the VSIX project.</span></span> <span data-ttu-id="b0739-150">Ceci démarre une deuxième instance de Visual Studio qui a chargé votre nouvel analyseur.</span><span class="sxs-lookup"><span data-stu-id="b0739-150">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="b0739-151">Lorsque vous exécutez votre analyseur, vous démarrez une deuxième copie de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0739-151">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="b0739-152">Cette deuxième copie utilise un hive de Registre différent pour stocker les paramètres.</span><span class="sxs-lookup"><span data-stu-id="b0739-152">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="b0739-153">Cela vous permet de différencier les paramètres Visual dans les deux copies de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0739-153">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="b0739-154">Vous pouvez choisir un autre thème pour l’exécution expérimentale de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0739-154">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="b0739-155">En outre, ne rendez pas vos paramètres itinérants et ne vous connectez pas à votre compte Visual Studio à l’aide de l’exécution expérimentale de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0739-155">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="b0739-156">Cela permet de conserver les paramètres différents.</span><span class="sxs-lookup"><span data-stu-id="b0739-156">That keeps the settings different.</span></span>

<span data-ttu-id="b0739-157">Dans la deuxième instance de Visual Studio que vous venez de démarrer, créez un projet d’application console C# (.NET Core ou .NET Framework projet fonctionne, les analyseurs fonctionnent au niveau de la source.) Placez le curseur sur le jeton avec un soulignement ondulé et le texte d’avertissement fourni par un analyseur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="b0739-157">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="b0739-158">Le modèle crée un analyseur qui émet un avertissement sur chaque déclaration de type dont le nom de type contient des lettres minuscules, comme indiqué dans la figure suivante :</span><span class="sxs-lookup"><span data-stu-id="b0739-158">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Avertissement de l’analyseur](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="b0739-160">Le modèle fournit également un correctif de code qui modifie n’importe quel nom de type contenant des caractères minuscules en majuscules.</span><span class="sxs-lookup"><span data-stu-id="b0739-160">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="b0739-161">Vous pouvez cliquer sur l’ampoule affichée avec l’avertissement pour voir les modifications suggérées.</span><span class="sxs-lookup"><span data-stu-id="b0739-161">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="b0739-162">Le fait d’accepter les modifications suggérées met à jour le nom de type et toutes les références à ce type dans la solution.</span><span class="sxs-lookup"><span data-stu-id="b0739-162">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="b0739-163">Maintenant que vous avez vu l’analyseur initial en action, fermez la deuxième instance de Visual Studio et revenez à votre projet d’analyseur.</span><span class="sxs-lookup"><span data-stu-id="b0739-163">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="b0739-164">Vous n’êtes pas obligé de démarrer une deuxième copie de Visual Studio et de créer un nouveau code pour tester chaque modification de votre analyseur.</span><span class="sxs-lookup"><span data-stu-id="b0739-164">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="b0739-165">Le modèle crée également un projet de test unitaire pour vous.</span><span class="sxs-lookup"><span data-stu-id="b0739-165">The template also creates a unit test project for you.</span></span> <span data-ttu-id="b0739-166">Ce projet contient deux tests.</span><span class="sxs-lookup"><span data-stu-id="b0739-166">That project contains two tests.</span></span> <span data-ttu-id="b0739-167">`TestMethod1` montre le format classique d’un test qui analyse le code sans déclencher un diagnostic.</span><span class="sxs-lookup"><span data-stu-id="b0739-167">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="b0739-168">`TestMethod2` montre le format d’un test qui déclenche un diagnostic, puis applique un correctif de code proposé.</span><span class="sxs-lookup"><span data-stu-id="b0739-168">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="b0739-169">À mesure que vous générez votre analyseur et votre correctif de code, vous écrirez des tests pour des structures de codes différentes afin de vérifier votre travail.</span><span class="sxs-lookup"><span data-stu-id="b0739-169">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="b0739-170">Les tests unitaires pour les analyseurs sont beaucoup plus rapides que de les tester de manière interactive avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0739-170">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="b0739-171">Les tests unitaires d’analyseur sont un excellent outil lorsque vous savez quelles constructions de code doivent et ne doivent pas déclencher votre analyseur.</span><span class="sxs-lookup"><span data-stu-id="b0739-171">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="b0739-172">Le chargement de votre analyseur dans une autre copie de Visual Studio est un excellent outil pour explorer et rechercher des constructions auxquelles vous n’avez peut-être pas encore pensé.</span><span class="sxs-lookup"><span data-stu-id="b0739-172">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="b0739-173">Créer des enregistrements d’analyseur</span><span class="sxs-lookup"><span data-stu-id="b0739-173">Create analyzer registrations</span></span>

<span data-ttu-id="b0739-174">Le modèle crée la classe `DiagnosticAnalyzer` initiale, dans le fichier **MakeConstAnalyzer.cs**.</span><span class="sxs-lookup"><span data-stu-id="b0739-174">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="b0739-175">Cet analyseur initial montre deux propriétés importantes de chaque analyseur.</span><span class="sxs-lookup"><span data-stu-id="b0739-175">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="b0739-176">Chaque analyseur de diagnostic doit fournir un attribut `[DiagnosticAnalyzer]` qui décrit le langage sur lequel il opère.</span><span class="sxs-lookup"><span data-stu-id="b0739-176">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="b0739-177">Chaque analyseur de diagnostic doit dériver de la classe <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer>.</span><span class="sxs-lookup"><span data-stu-id="b0739-177">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="b0739-178">Le modèle montre également les fonctionnalités de base qui font partie de n’importe quel analyseur :</span><span class="sxs-lookup"><span data-stu-id="b0739-178">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="b0739-179">Enregistrer les actions.</span><span class="sxs-lookup"><span data-stu-id="b0739-179">Register actions.</span></span> <span data-ttu-id="b0739-180">Les actions représentent les modifications de code qui doivent déclencher votre analyseur pour qu’il examine les violations dans le code.</span><span class="sxs-lookup"><span data-stu-id="b0739-180">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="b0739-181">Lorsque Visual Studio détecte des modifications de code qui correspondent à une action enregistré, il appelle la méthode enregistrée de votre analyseur.</span><span class="sxs-lookup"><span data-stu-id="b0739-181">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="b0739-182">Créer des diagnostics.</span><span class="sxs-lookup"><span data-stu-id="b0739-182">Create diagnostics.</span></span> <span data-ttu-id="b0739-183">Quand votre analyseur détecte une violation, il crée un objet de diagnostic que Visual Studio utilise pour informer l’utilisateur de la violation.</span><span class="sxs-lookup"><span data-stu-id="b0739-183">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="b0739-184">Vous enregistrez des actions dans votre substitution de la méthode <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b0739-184">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b0739-185">Dans ce tutoriel, vous allez consulter des **nœuds de syntaxe** pour rechercher des déclarations locales et voir lesquelles ont des valeurs constantes.</span><span class="sxs-lookup"><span data-stu-id="b0739-185">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="b0739-186">Si une déclaration peut être une constante, votre analyseur crée et signale un diagnostic.</span><span class="sxs-lookup"><span data-stu-id="b0739-186">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="b0739-187">La première étape consiste à mettre à jour les constantes d’inscription et la méthode `Initialize` pour que ces constantes indiquent votre analyseur « Make Const ».</span><span class="sxs-lookup"><span data-stu-id="b0739-187">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="b0739-188">La plupart des constantes de chaîne est définie dans le fichier de ressources de chaîne.</span><span class="sxs-lookup"><span data-stu-id="b0739-188">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="b0739-189">Cette pratique facilite la localisation.</span><span class="sxs-lookup"><span data-stu-id="b0739-189">You should follow that practice for easier localization.</span></span> <span data-ttu-id="b0739-190">Ouvrez le fichier **Resources.resx** pour le projet d’analyseur **MakeConst**.</span><span class="sxs-lookup"><span data-stu-id="b0739-190">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="b0739-191">Cela affiche l’éditeur de ressources.</span><span class="sxs-lookup"><span data-stu-id="b0739-191">This displays the resource editor.</span></span> <span data-ttu-id="b0739-192">Mettez à jour les ressources de chaîne comme suit :</span><span class="sxs-lookup"><span data-stu-id="b0739-192">Update the string resources as follows:</span></span>

- <span data-ttu-id="b0739-193">Remplacez `AnalyzerTitle` par « Variable can be made constant » (La variable peut être rendue constante).</span><span class="sxs-lookup"><span data-stu-id="b0739-193">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="b0739-194">Remplacez `AnalyzerMessageFormat` par « Can be made constant » (Peut être rendu constant).</span><span class="sxs-lookup"><span data-stu-id="b0739-194">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="b0739-195">Remplacez `AnalyzerDescription` par « Make constant » (Rendre constant).</span><span class="sxs-lookup"><span data-stu-id="b0739-195">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="b0739-196">Modifiez aussi le menu déroulant **Modificateur d’accès** sur `public`.</span><span class="sxs-lookup"><span data-stu-id="b0739-196">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="b0739-197">Ainsi, ces constantes sont plus faciles à utiliser dans les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="b0739-197">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="b0739-198">Lorsque vous avez terminé, l’éditeur de ressources doit apparaître comme le montre l’illustration suivante :</span><span class="sxs-lookup"><span data-stu-id="b0739-198">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Mettre à jour les ressources de chaîne](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="b0739-200">Les modifications restantes ont lieu dans le fichier de l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="b0739-200">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="b0739-201">Ouvrez **MakeConstAnalyzer.cs** dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0739-201">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="b0739-202">Modifiez l’action enregistrée d’une action qui agit sur les symboles à une action qui agit sur la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="b0739-202">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="b0739-203">Dans la méthode `MakeConstAnalyzerAnalyzer.Initialize`, recherchez la ligne qui enregistre l’action sur les symboles :</span><span class="sxs-lookup"><span data-stu-id="b0739-203">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="b0739-204">Remplacez-la par la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="b0739-204">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="b0739-205">Après cette modification, vous pouvez supprimer la méthode `AnalyzeSymbol`.</span><span class="sxs-lookup"><span data-stu-id="b0739-205">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="b0739-206">Cet outil examine <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, et non les instructions <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b0739-206">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="b0739-207">Notez que `AnalyzeNode` est souligné par des traits ondulés rouges.</span><span class="sxs-lookup"><span data-stu-id="b0739-207">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="b0739-208">Le code que vous venez d’ajouter référence une méthode `AnalyzeNode` qui n’a pas été déclarée.</span><span class="sxs-lookup"><span data-stu-id="b0739-208">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="b0739-209">Déclarez cette méthode en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b0739-209">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="b0739-210">Remplacez `Category` par « Usage » (Utilisation) dans **MakeConstAnalyzer.cs** comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b0739-210">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="b0739-211">Rechercher des déclarations locales qui pourraient être constantes</span><span class="sxs-lookup"><span data-stu-id="b0739-211">Find local declarations that could be const</span></span>

<span data-ttu-id="b0739-212">Il est temps d’écrire la première version de la méthode `AnalyzeNode`.</span><span class="sxs-lookup"><span data-stu-id="b0739-212">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="b0739-213">Elle doit rechercher une déclaration locale unique qui peut être `const` mais ne l’est pas, comme le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b0739-213">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="b0739-214">La première étape consiste à rechercher les déclarations locales.</span><span class="sxs-lookup"><span data-stu-id="b0739-214">The first step is to find local declarations.</span></span> <span data-ttu-id="b0739-215">Ajoutez le code suivant à `AnalyzeNode` dans **MakeConstAnalyzer.cs** :</span><span class="sxs-lookup"><span data-stu-id="b0739-215">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="b0739-216">Ce cast réussit toujours, car votre analyseur a enregistré les modifications apportées aux déclarations locales, et uniquement les déclarations locales.</span><span class="sxs-lookup"><span data-stu-id="b0739-216">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="b0739-217">Aucun autre type de nœud ne déclenche un appel à votre méthode `AnalyzeNode`.</span><span class="sxs-lookup"><span data-stu-id="b0739-217">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="b0739-218">Ensuite, vérifiez la présence de modificateurs `const` dans la déclaration.</span><span class="sxs-lookup"><span data-stu-id="b0739-218">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="b0739-219">Si vous en trouvez, retournez immédiatement.</span><span class="sxs-lookup"><span data-stu-id="b0739-219">If you find them, return immediately.</span></span> <span data-ttu-id="b0739-220">Le code suivant recherche les modificateurs `const` sur la déclaration locale :</span><span class="sxs-lookup"><span data-stu-id="b0739-220">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="b0739-221">Enfin, vous devez vérifier que la variable peut être `const`.</span><span class="sxs-lookup"><span data-stu-id="b0739-221">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="b0739-222">Cela signifie de s’assurer qu’elle n’est jamais assignée après son initialisation.</span><span class="sxs-lookup"><span data-stu-id="b0739-222">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="b0739-223">Vous allez effectuer une analyse sémantique à l’aide de <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span><span class="sxs-lookup"><span data-stu-id="b0739-223">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="b0739-224">Vous utilisez l’argument `context` pour déterminer si la déclaration de variable locale peut être rendue `const`.</span><span class="sxs-lookup"><span data-stu-id="b0739-224">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="b0739-225">Un <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> représente toutes les informations sémantiques dans un fichier source unique.</span><span class="sxs-lookup"><span data-stu-id="b0739-225">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents all of semantic information in a single source file.</span></span> <span data-ttu-id="b0739-226">Vous pouvez en apprendre plus dans l’article qui traite des [modèles sémantiques](../work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="b0739-226">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="b0739-227">Vous allez utiliser <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> pour effectuer une analyse de flux de données sur l’instruction de déclaration locale.</span><span class="sxs-lookup"><span data-stu-id="b0739-227">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="b0739-228">Ensuite, vous utilisez les résultats de cette analyse de flux de données pour vous assurer que la variable locale n’est pas écrite avec une nouvelle valeur ailleurs.</span><span class="sxs-lookup"><span data-stu-id="b0739-228">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="b0739-229">Appelez la méthode d’extension <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> pour récupérer <xref:Microsoft.CodeAnalysis.ILocalSymbol> pour la variable et vérifiez qu’il n’est pas contenu avec la collection <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> de l’analyse de flux de données.</span><span class="sxs-lookup"><span data-stu-id="b0739-229">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="b0739-230">Ajoutez le code suivant à la fin de la méthode `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="b0739-230">Add the following code to the end of the `AnalyzeNode` method:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="b0739-231">Le code qui vient d’être ajouté garantit que la variable n’est pas modifiée et peut par conséquent devenir `const`.</span><span class="sxs-lookup"><span data-stu-id="b0739-231">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="b0739-232">Il est temps de générer le diagnostic.</span><span class="sxs-lookup"><span data-stu-id="b0739-232">It's time to raise the diagnostic.</span></span> <span data-ttu-id="b0739-233">Ajoutez le code suivant comme dernière ligne dans `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="b0739-233">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="b0739-234">Vous pouvez vérifier votre progression en appuyant sur <kbd>F5</kbd> pour exécuter votre analyseur.</span><span class="sxs-lookup"><span data-stu-id="b0739-234">You can check your progress by pressing <kbd>F5</kbd> to run your analyzer.</span></span> <span data-ttu-id="b0739-235">Vous pouvez charger l’application console que vous avez créée précédemment et ajouter le code de test suivant :</span><span class="sxs-lookup"><span data-stu-id="b0739-235">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="b0739-236">L’ampoule doit apparaître et votre analyseur doit signaler un diagnostic.</span><span class="sxs-lookup"><span data-stu-id="b0739-236">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="b0739-237">Toutefois, l’ampoule utilise toujours le correctif de code généré par le modèle et vous indique qu’il peut être converti en majuscules.</span><span class="sxs-lookup"><span data-stu-id="b0739-237">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="b0739-238">La section suivante explique comment écrire le correctif de code.</span><span class="sxs-lookup"><span data-stu-id="b0739-238">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="b0739-239">Écrire le correctif de code</span><span class="sxs-lookup"><span data-stu-id="b0739-239">Write the code fix</span></span>

<span data-ttu-id="b0739-240">Un analyseur peut fournir un ou plusieurs correctifs de code.</span><span class="sxs-lookup"><span data-stu-id="b0739-240">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="b0739-241">Un correctif de code définit une modification qui traite le problème signalé.</span><span class="sxs-lookup"><span data-stu-id="b0739-241">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="b0739-242">Pour l’analyseur que vous avez créé, vous pouvez fournir un correctif de code qui insère le mot clé const :</span><span class="sxs-lookup"><span data-stu-id="b0739-242">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="b0739-243">L’utilisateur le choisit à partir de l’IU ampoule dans l’éditeur et Visual Studio modifie le code.</span><span class="sxs-lookup"><span data-stu-id="b0739-243">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="b0739-244">Ouvrez le fichier **MakeConstCodeFixProvider.cs** ajouté par le modèle.</span><span class="sxs-lookup"><span data-stu-id="b0739-244">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="b0739-245">Ce correctif de code est déjà associé à l’ID de diagnostic produit par votre analyseur de diagnostic, mais il n’implémente pas encore la transformation de code adéquate.</span><span class="sxs-lookup"><span data-stu-id="b0739-245">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="b0739-246">Tout d’abord, vous devez supprimer une partie du code du modèle.</span><span class="sxs-lookup"><span data-stu-id="b0739-246">First you should remove some of the template code.</span></span> <span data-ttu-id="b0739-247">Remplacez la chaîne de titre par « Make constant » :</span><span class="sxs-lookup"><span data-stu-id="b0739-247">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="b0739-248">Ensuite, supprimez la méthode `MakeUppercaseAsync`.</span><span class="sxs-lookup"><span data-stu-id="b0739-248">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="b0739-249">Elle n’est plus applicable.</span><span class="sxs-lookup"><span data-stu-id="b0739-249">It no longer applies.</span></span>

<span data-ttu-id="b0739-250">Tous les fournisseurs de correctif de code dérivent de <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span><span class="sxs-lookup"><span data-stu-id="b0739-250">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="b0739-251">Ils substituent tous <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> pour signaler les correctifs de code disponibles.</span><span class="sxs-lookup"><span data-stu-id="b0739-251">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="b0739-252">Dans `RegisterCodeFixesAsync`, remplacez le type de nœud ancêtre que vous recherchez par <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> pour faire correspondre le diagnostic :</span><span class="sxs-lookup"><span data-stu-id="b0739-252">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="b0739-253">Ensuite, modifiez la dernière ligne pour enregistrer un correctif de code.</span><span class="sxs-lookup"><span data-stu-id="b0739-253">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="b0739-254">Votre correctif crée un nouveau document obtenu en ajoutant le modificateur `const` à une déclaration existante :</span><span class="sxs-lookup"><span data-stu-id="b0739-254">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="b0739-255">Notez les traits de soulignement ondulés rouges dans le code que vous venez d’ajouter sur le symbole `MakeConstAsync`.</span><span class="sxs-lookup"><span data-stu-id="b0739-255">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="b0739-256">Ajoutez une déclaration pour `MakeConstAsync` comme le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b0739-256">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="b0739-257">Votre nouvelle méthode `MakeConstAsync` transformera <xref:Microsoft.CodeAnalysis.Document> qui représente le fichier source de l’utilisateur en un nouveau <xref:Microsoft.CodeAnalysis.Document> qui contient à présent une déclaration `const`.</span><span class="sxs-lookup"><span data-stu-id="b0739-257">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="b0739-258">Vous créez un nouveau jeton de mot clé `const` à insérer au début de l’instruction de déclaration.</span><span class="sxs-lookup"><span data-stu-id="b0739-258">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="b0739-259">Veillez tout d’abord à supprimer les trivia de début dans le premier jeton de l’instruction de déclaration et à les associer au jeton `const`.</span><span class="sxs-lookup"><span data-stu-id="b0739-259">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="b0739-260">Ajoutez le code suivant à la méthode `MakeConstAsync` :</span><span class="sxs-lookup"><span data-stu-id="b0739-260">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="b0739-261">Ensuite, ajoutez le jeton `const` dans la déclaration à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="b0739-261">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="b0739-262">Ensuite, mettez en forme la nouvelle déclaration en fonction des règles de mise en forme en C#.</span><span class="sxs-lookup"><span data-stu-id="b0739-262">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="b0739-263">La mise en forme de vos modifications pour correspondre au code existant crée une meilleure expérience.</span><span class="sxs-lookup"><span data-stu-id="b0739-263">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="b0739-264">Ajoutez l’instruction suivante immédiatement après le code existant :</span><span class="sxs-lookup"><span data-stu-id="b0739-264">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="b0739-265">Un nouvel espace de noms est requis pour ce code.</span><span class="sxs-lookup"><span data-stu-id="b0739-265">A new namespace is required for this code.</span></span> <span data-ttu-id="b0739-266">Ajoutez la directive `using` suivante en haut du fichier :</span><span class="sxs-lookup"><span data-stu-id="b0739-266">Add the following `using` directive to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="b0739-267">L’étape finale consiste à apporter votre modification.</span><span class="sxs-lookup"><span data-stu-id="b0739-267">The final step is to make your edit.</span></span> <span data-ttu-id="b0739-268">Ce processus comprend trois étapes :</span><span class="sxs-lookup"><span data-stu-id="b0739-268">There are three steps to this process:</span></span>

1. <span data-ttu-id="b0739-269">Obtenir un handle pour le document existant.</span><span class="sxs-lookup"><span data-stu-id="b0739-269">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="b0739-270">Créer un document en remplaçant la déclaration existante par la nouvelle déclaration.</span><span class="sxs-lookup"><span data-stu-id="b0739-270">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="b0739-271">Retourner le nouveau document.</span><span class="sxs-lookup"><span data-stu-id="b0739-271">Return the new document.</span></span>

<span data-ttu-id="b0739-272">Ajoutez le code suivant à la fin de la méthode `MakeConstAsync` :</span><span class="sxs-lookup"><span data-stu-id="b0739-272">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="b0739-273">Votre correctif de code est prêt à être testé.</span><span class="sxs-lookup"><span data-stu-id="b0739-273">Your code fix is ready to try.</span></span>  <span data-ttu-id="b0739-274">Appuyez sur <kbd>F5</kbd> pour exécuter le projet de l’analyseur dans une seconde instance de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0739-274">Press <kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="b0739-275">Dans la deuxième instance de Visual Studio, créez un projet Application console C# et ajoutez quelques déclarations de variables locales initialisées avec des valeurs constantes à la méthode Main.</span><span class="sxs-lookup"><span data-stu-id="b0739-275">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="b0739-276">Vous verrez que ces éléments sont signalés en tant qu’avertissements comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b0739-276">You'll see that they are reported as warnings as below.</span></span>

![Avertissements Can make const](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="b0739-278">Vous avez bien progressé.</span><span class="sxs-lookup"><span data-stu-id="b0739-278">You've made a lot of progress.</span></span> <span data-ttu-id="b0739-279">Des traits de soulignement ondulés s’affichent sous les déclarations qui peuvent devenir `const`.</span><span class="sxs-lookup"><span data-stu-id="b0739-279">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="b0739-280">Mais il reste encore du travail.</span><span class="sxs-lookup"><span data-stu-id="b0739-280">But there is still work to do.</span></span> <span data-ttu-id="b0739-281">Cela fonctionne si vous ajoutez `const` aux déclarations qui commencent par `i`, puis `j` et enfin `k`.</span><span class="sxs-lookup"><span data-stu-id="b0739-281">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="b0739-282">Mais, si le modificateur `const` est ajouté dans un autre ordre, en commençant par `k`, l’analyseur crée des erreurs : `k` ne peut pas être déclaré `const`, sauf si `i` et `j` sont tous deux déjà `const`.</span><span class="sxs-lookup"><span data-stu-id="b0739-282">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="b0739-283">Vous devez effectuer d’autres analyses afin de vous assurer que vous gérez les différentes façons dont les variables peuvent être déclarées et initialisées.</span><span class="sxs-lookup"><span data-stu-id="b0739-283">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="b0739-284">Générer des tests pilotés par les données</span><span class="sxs-lookup"><span data-stu-id="b0739-284">Build data driven tests</span></span>

<span data-ttu-id="b0739-285">Votre analyseur et votre correctif de code travaillent sur un cas simple d’une déclaration unique qui peut être devenir constante.</span><span class="sxs-lookup"><span data-stu-id="b0739-285">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="b0739-286">Il existe de nombreuses instructions de déclaration possibles où cette implémentation commet des erreurs.</span><span class="sxs-lookup"><span data-stu-id="b0739-286">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="b0739-287">Vous allez traiter ces cas en travaillant avec la bibliothèque de tests unitaires écrite par le modèle.</span><span class="sxs-lookup"><span data-stu-id="b0739-287">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="b0739-288">C’est beaucoup plus rapide que d’ouvrir plusieurs fois une deuxième copie de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0739-288">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="b0739-289">Ouvrez le fichier **MakeConstUnitTests.cs** dans le projet de test unitaire.</span><span class="sxs-lookup"><span data-stu-id="b0739-289">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="b0739-290">Le modèle a créé deux tests qui suivent les deux modèles courants pour un test unitaire d’analyseur et de correctif de code.</span><span class="sxs-lookup"><span data-stu-id="b0739-290">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="b0739-291">`TestMethod1` montre le modèle pour un test qui garantit que l’analyseur ne signale pas un diagnostic lorsqu’il ne le devrait pas.</span><span class="sxs-lookup"><span data-stu-id="b0739-291">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="b0739-292">`TestMethod2` montre le modèle pour créer un rapport de diagnostic et exécuter le correctif de code.</span><span class="sxs-lookup"><span data-stu-id="b0739-292">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="b0739-293">Le code de presque chaque test pour votre analyseur suit un de ces deux modèles.</span><span class="sxs-lookup"><span data-stu-id="b0739-293">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="b0739-294">Pour la première étape, vous pouvez revoir ces tests en tant que tests pilotés par les données.</span><span class="sxs-lookup"><span data-stu-id="b0739-294">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="b0739-295">Ensuite, il sera facile de créer de nouveaux tests en ajoutant de nouvelles constantes de chaîne pour représenter les différentes entrées de test.</span><span class="sxs-lookup"><span data-stu-id="b0739-295">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="b0739-296">Pour plus d’efficacité, la première étape consiste à refactoriser les deux tests en tests pilotés par des données.</span><span class="sxs-lookup"><span data-stu-id="b0739-296">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="b0739-297">Ensuite, il vous suffit de définir quelques constantes de chaîne pour chaque nouveau test.</span><span class="sxs-lookup"><span data-stu-id="b0739-297">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="b0739-298">Pendant la refactorisation, renommez les deux méthodes avec des noms plus performants.</span><span class="sxs-lookup"><span data-stu-id="b0739-298">While you are refactoring, rename both methods to better names.</span></span> <span data-ttu-id="b0739-299">Remplacez `TestMethod1` par ce test qui garantit qu’aucun diagnostic n’est déclenché :</span><span class="sxs-lookup"><span data-stu-id="b0739-299">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="b0739-300">Vous pouvez créer une nouvelle ligne de données pour ce test en définissant un fragment de code qui ne doit pas entraîner votre diagnostic à déclencher un avertissement.</span><span class="sxs-lookup"><span data-stu-id="b0739-300">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="b0739-301">Cette surcharge de passes `VerifyCSharpDiagnostic` lorsqu’il n’y a aucun diagnostic déclenché pour le fragment de code source.</span><span class="sxs-lookup"><span data-stu-id="b0739-301">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="b0739-302">Ensuite, remplacez `TestMethod2` par ce test qui garantit qu’un diagnostic est déclenché et un correctif de code appliqué pour le fragment de code source :</span><span class="sxs-lookup"><span data-stu-id="b0739-302">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

<span data-ttu-id="b0739-303">Le code précédent a apporté également quelques modifications au code qui génère le résultat de diagnostic attendu.</span><span class="sxs-lookup"><span data-stu-id="b0739-303">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="b0739-304">Il utilise les constantes publiques enregistrées dans l’analyseur `MakeConst`.</span><span class="sxs-lookup"><span data-stu-id="b0739-304">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="b0739-305">En outre, il utilise deux constantes de chaîne pour la source d’entrée et corrigée.</span><span class="sxs-lookup"><span data-stu-id="b0739-305">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="b0739-306">Ajoutez les constantes de chaîne suivantes à la classe `UnitTest` :</span><span class="sxs-lookup"><span data-stu-id="b0739-306">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="b0739-307">Exécutez ces deux tests pour vous assurer qu’ils réussissent.</span><span class="sxs-lookup"><span data-stu-id="b0739-307">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="b0739-308">Dans Visual Studio, ouvrez **l’Explorateur de tests** en sélectionnant **Test** > **Windows** > **Explorateur de tests**.</span><span class="sxs-lookup"><span data-stu-id="b0739-308">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span> <span data-ttu-id="b0739-309">Sélectionnez ensuite le lien **exécuter tout** .</span><span class="sxs-lookup"><span data-stu-id="b0739-309">Then select the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="b0739-310">Créer des tests pour les déclarations valides</span><span class="sxs-lookup"><span data-stu-id="b0739-310">Create tests for valid declarations</span></span>

<span data-ttu-id="b0739-311">En règle générale, les analyseurs doivent s’arrêter aussi rapidement que possible, en effectuant un minimum de travail.</span><span class="sxs-lookup"><span data-stu-id="b0739-311">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="b0739-312">Visual Studio appelle les analyseurs enregistrés lorsque l’utilisateur modifie le code.</span><span class="sxs-lookup"><span data-stu-id="b0739-312">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="b0739-313">La réactivité est essentielle.</span><span class="sxs-lookup"><span data-stu-id="b0739-313">Responsiveness is a key requirement.</span></span> <span data-ttu-id="b0739-314">Il existe plusieurs cas de test pour le code qui ne doivent pas déclencher votre diagnostic.</span><span class="sxs-lookup"><span data-stu-id="b0739-314">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="b0739-315">Votre analyseur a déjà géré l’un de ces tests, le cas où une variable est assignée après avoir été initialisée.</span><span class="sxs-lookup"><span data-stu-id="b0739-315">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="b0739-316">Ajoutez la constante de chaîne suivante à vos tests pour représenter ce cas :</span><span class="sxs-lookup"><span data-stu-id="b0739-316">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="b0739-317">Ensuite, ajoutez une ligne de données pour ce test, comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="b0739-317">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="b0739-318">Ce test réussit également.</span><span class="sxs-lookup"><span data-stu-id="b0739-318">This test passes as well.</span></span> <span data-ttu-id="b0739-319">Ensuite, ajoutez des constantes pour les conditions que vous n’avez pas encore gérées :</span><span class="sxs-lookup"><span data-stu-id="b0739-319">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="b0739-320">Déclarations qui sont déjà `const`, car elles sont déjà constantes :</span><span class="sxs-lookup"><span data-stu-id="b0739-320">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="b0739-321">Déclarations sans initialiseur, car il n’existe aucune valeur à utiliser :</span><span class="sxs-lookup"><span data-stu-id="b0739-321">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="b0739-322">Déclarations où l’initialiseur n’est pas une constante, car elles ne peuvent pas être des constantes de compilation :</span><span class="sxs-lookup"><span data-stu-id="b0739-322">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="b0739-323">Cela peut être encore plus compliqué, car C# accepte que plusieurs déclarations forment une seule instruction.</span><span class="sxs-lookup"><span data-stu-id="b0739-323">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="b0739-324">Prenez en compte la constante de chaîne de cas de test suivante :</span><span class="sxs-lookup"><span data-stu-id="b0739-324">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="b0739-325">La variable `i` peut devenir constante, mais la variable `j` ne le peut pas.</span><span class="sxs-lookup"><span data-stu-id="b0739-325">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="b0739-326">Par conséquent, cette instruction ne peut pas devenir une déclaration constante.</span><span class="sxs-lookup"><span data-stu-id="b0739-326">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="b0739-327">Ajouter les déclarations `DataRow` pour tous ces tests :</span><span class="sxs-lookup"><span data-stu-id="b0739-327">Add the `DataRow` declarations for all these tests:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="b0739-328">Réexécutez vos tests, et vous verrez ces nouveaux cas de test échouent.</span><span class="sxs-lookup"><span data-stu-id="b0739-328">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="b0739-329">Mettre à jour votre analyseur afin d’ignorer les déclarations correctes</span><span class="sxs-lookup"><span data-stu-id="b0739-329">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="b0739-330">Vous avez besoin de certaines améliorations dans la méthode `AnalyzeNode` de votre analyseur pour éliminer le code correspondant à ces conditions.</span><span class="sxs-lookup"><span data-stu-id="b0739-330">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="b0739-331">Ce sont toutes des conditions associées, donc des modifications similaires résoudront toutes ces conditions.</span><span class="sxs-lookup"><span data-stu-id="b0739-331">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="b0739-332">Dans `AnalyzeNode`, effectuez les changements suivants :</span><span class="sxs-lookup"><span data-stu-id="b0739-332">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="b0739-333">Votre analyse sémantique a examiné une déclaration de variable unique.</span><span class="sxs-lookup"><span data-stu-id="b0739-333">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="b0739-334">Ce code doit se trouver dans une boucle `foreach` qui examine toutes les variables déclarées dans la même instruction.</span><span class="sxs-lookup"><span data-stu-id="b0739-334">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="b0739-335">Chaque variable déclarée doit avoir un initialiseur.</span><span class="sxs-lookup"><span data-stu-id="b0739-335">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="b0739-336">L’initialiseur de chaque variable déclarée doit être une constante de compilation.</span><span class="sxs-lookup"><span data-stu-id="b0739-336">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="b0739-337">Dans votre méthode `AnalyzeNode`, remplacez l’analyse sémantique d’origine :</span><span class="sxs-lookup"><span data-stu-id="b0739-337">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="b0739-338">par l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="b0739-338">with the following code snippet:</span></span>

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

<span data-ttu-id="b0739-339">La première boucle `foreach` examine chaque déclaration de variable à l’aide de l’analyse syntaxique.</span><span class="sxs-lookup"><span data-stu-id="b0739-339">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="b0739-340">La première vérification garantit que la variable a un initialiseur.</span><span class="sxs-lookup"><span data-stu-id="b0739-340">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="b0739-341">La deuxième vérification garantit que l’initialiseur est une constante.</span><span class="sxs-lookup"><span data-stu-id="b0739-341">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="b0739-342">La deuxième boucle contient l’analyse sémantique d’origine.</span><span class="sxs-lookup"><span data-stu-id="b0739-342">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="b0739-343">Les vérifications sémantiques sont dans une boucle distincte, car elles ont un impact plus important sur les performances.</span><span class="sxs-lookup"><span data-stu-id="b0739-343">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="b0739-344">Réexécutez vos tests. Ils doivent tous réussir.</span><span class="sxs-lookup"><span data-stu-id="b0739-344">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="b0739-345">Ajouter la touche finale</span><span class="sxs-lookup"><span data-stu-id="b0739-345">Add the final polish</span></span>

<span data-ttu-id="b0739-346">Vous avez presque terminé.</span><span class="sxs-lookup"><span data-stu-id="b0739-346">You're almost done.</span></span> <span data-ttu-id="b0739-347">Il existe quelques conditions de plus que votre analyseur doit gérer.</span><span class="sxs-lookup"><span data-stu-id="b0739-347">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="b0739-348">Visual Studio appelle les analyseurs lorsque l’utilisateur écrit du code.</span><span class="sxs-lookup"><span data-stu-id="b0739-348">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="b0739-349">Souvent, votre analyseur sera appelé lorsque du code ne se compile pas.</span><span class="sxs-lookup"><span data-stu-id="b0739-349">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="b0739-350">La méthode `AnalyzeNode` de votre analyseur de diagnostic ne vérifie pas si la valeur de constante est convertible en type de variable.</span><span class="sxs-lookup"><span data-stu-id="b0739-350">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="b0739-351">Par conséquent, l’implémentation actuelle convertit sans problème une déclaration incorrecte comme int i = « abc » en une constante locale.</span><span class="sxs-lookup"><span data-stu-id="b0739-351">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="b0739-352">Ajoutez une constante de chaîne source pour cette condition :</span><span class="sxs-lookup"><span data-stu-id="b0739-352">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="b0739-353">En outre, les types de référence ne sont pas gérés correctement.</span><span class="sxs-lookup"><span data-stu-id="b0739-353">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="b0739-354">La seule valeur de constante autorisée pour un type de référence est `null`, sauf dans le cas de <xref:System.String?displayProperty=nameWithType>, qui autorise des littéraux de chaîne.</span><span class="sxs-lookup"><span data-stu-id="b0739-354">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="b0739-355">En d’autres termes, `const string s = "abc"` est légal, mais pas `const object s = "abc"`.</span><span class="sxs-lookup"><span data-stu-id="b0739-355">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="b0739-356">Cet extrait de code vérifie cette condition :</span><span class="sxs-lookup"><span data-stu-id="b0739-356">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="b0739-357">Pour être exhaustif, vous devez ajouter un autre test afin de vous assurer que vous pouvez créer une déclaration de constante pour une chaîne.</span><span class="sxs-lookup"><span data-stu-id="b0739-357">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="b0739-358">L’extrait de code suivant définit le code qui déclenche le diagnostic et le code une fois que le correctif a été appliqué :</span><span class="sxs-lookup"><span data-stu-id="b0739-358">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="b0739-359">Enfin, si une variable est déclarée avec le mot clé `var`, le correctif de code fait la mauvaise chose et génère une déclaration `const var`, qui n’est pas prise en charge par le langage C#.</span><span class="sxs-lookup"><span data-stu-id="b0739-359">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="b0739-360">Pour corriger ce bogue, le correctif de code doit remplacer le mot clé `var` par le nom du type déduit :</span><span class="sxs-lookup"><span data-stu-id="b0739-360">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="b0739-361">Ces modifications mettent à jour les déclarations de ligne de données pour les deux tests.</span><span class="sxs-lookup"><span data-stu-id="b0739-361">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="b0739-362">Le code suivant montre ces tests avec tous les attributs de ligne de données :</span><span class="sxs-lookup"><span data-stu-id="b0739-362">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="b0739-363">Heureusement, tous les bogues ci-dessus peuvent être gérés à l’aide des mêmes techniques que celles que vous venez d’apprendre.</span><span class="sxs-lookup"><span data-stu-id="b0739-363">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="b0739-364">Pour corriger le premier bogue, commencez par ouvrir **DiagnosticAnalyzer.cs** et recherchez la boucle foreach où chacun des initialiseurs de la déclaration locale est vérifié pour s’assurer que des valeurs constantes leur sont attribués.</span><span class="sxs-lookup"><span data-stu-id="b0739-364">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="b0739-365">Immédiatement _avant_ la première boucle foreach, appelez `context.SemanticModel.GetTypeInfo()` pour récupérer des informations détaillées sur le type déclaré de la déclaration locale :</span><span class="sxs-lookup"><span data-stu-id="b0739-365">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="b0739-366">Ensuite, dans votre boucle `foreach`, vérifiez chaque initialiseur pour vous assurer qu’il peut être converti dans le type de variable.</span><span class="sxs-lookup"><span data-stu-id="b0739-366">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="b0739-367">Ajoutez la vérification suivante après avoir vérifié que l’initialiseur est une constante :</span><span class="sxs-lookup"><span data-stu-id="b0739-367">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="b0739-368">La modification suivante s’appuie sur la précédente.</span><span class="sxs-lookup"><span data-stu-id="b0739-368">The next change builds upon the last one.</span></span> <span data-ttu-id="b0739-369">Avant l’accolade fermante de la première boucle foreach, ajoutez le code suivant pour vérifier le type de la déclaration locale si la constante est une chaîne ou une valeur null.</span><span class="sxs-lookup"><span data-stu-id="b0739-369">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

<span data-ttu-id="b0739-370">Vous devez écrire un peu plus de code dans votre fournisseur de correctifs de code pour remplacer le `var` mot clé par le nom de type correct.</span><span class="sxs-lookup"><span data-stu-id="b0739-370">You must write a bit more code in your code fix provider to replace the `var` keyword with the correct type name.</span></span> <span data-ttu-id="b0739-371">Revenez dans **CodeFixProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="b0739-371">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="b0739-372">Le code que vous ajouterez effectue les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="b0739-372">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="b0739-373">Vérifiez si la déclaration est une déclaration `var`, et dans ce cas :</span><span class="sxs-lookup"><span data-stu-id="b0739-373">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="b0739-374">Créez un nouveau type pour le type déduit.</span><span class="sxs-lookup"><span data-stu-id="b0739-374">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="b0739-375">Assurez-vous que la déclaration de type n’est pas un alias.</span><span class="sxs-lookup"><span data-stu-id="b0739-375">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="b0739-376">Le cas échéant, il est permis de déclarer `const var`.</span><span class="sxs-lookup"><span data-stu-id="b0739-376">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="b0739-377">Assurez-vous que `var` n’est pas un nom de type dans ce programme.</span><span class="sxs-lookup"><span data-stu-id="b0739-377">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="b0739-378">(Dans ce cas, `const var` est autorisé).</span><span class="sxs-lookup"><span data-stu-id="b0739-378">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="b0739-379">Simplifier le nom de type complet</span><span class="sxs-lookup"><span data-stu-id="b0739-379">Simplify the full type name</span></span>

<span data-ttu-id="b0739-380">On dirait que beaucoup de code est nécessaire pour cela.</span><span class="sxs-lookup"><span data-stu-id="b0739-380">That sounds like a lot of code.</span></span> <span data-ttu-id="b0739-381">Ce n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="b0739-381">It's not.</span></span> <span data-ttu-id="b0739-382">Remplacez la ligne qui déclare et initialise `newLocal` par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b0739-382">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="b0739-383">Il se place immédiatement après l’initialisation de `newModifiers` :</span><span class="sxs-lookup"><span data-stu-id="b0739-383">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="b0739-384">Vous devez ajouter une `using` directive pour utiliser le <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type :</span><span class="sxs-lookup"><span data-stu-id="b0739-384">You'll need to add one `using` directive to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="b0739-385">Exécutez vos tests. Ils doivent tous réussir.</span><span class="sxs-lookup"><span data-stu-id="b0739-385">Run your tests, and they should all pass.</span></span> <span data-ttu-id="b0739-386">Félicitez-vous en exécutant votre analyseur terminé.</span><span class="sxs-lookup"><span data-stu-id="b0739-386">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="b0739-387">Appuyez sur <kbd>CTRL</kbd> + <kbd>F5</kbd> pour exécuter le projet de l’analyseur dans une seconde instance de Visual Studio avec l’extension de prévisualisation Roslyn chargée.</span><span class="sxs-lookup"><span data-stu-id="b0739-387">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="b0739-388">Dans la deuxième instance de Visual Studio, créez un projet Application console C# et ajoutez `int x = "abc";` à la méthode Main.</span><span class="sxs-lookup"><span data-stu-id="b0739-388">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="b0739-389">Grâce à la correction du premier bogue, aucun avertissement ne doit être signalé pour cette déclaration de variable locale (même s’il existe une erreur du compilateur comme prévu).</span><span class="sxs-lookup"><span data-stu-id="b0739-389">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="b0739-390">Ensuite, ajoutez `object s = "abc";` à la méthode Main.</span><span class="sxs-lookup"><span data-stu-id="b0739-390">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="b0739-391">En raison de la correction du deuxième bogue, aucun avertissement ne doit être signalé.</span><span class="sxs-lookup"><span data-stu-id="b0739-391">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="b0739-392">Enfin, ajoutez une autre variable locale qui utilise le mot clé `var`.</span><span class="sxs-lookup"><span data-stu-id="b0739-392">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="b0739-393">Un avertissement est signalé et une suggestion apparaît en dessous à gauche.</span><span class="sxs-lookup"><span data-stu-id="b0739-393">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="b0739-394">Déplacez le signe insertion de l’éditeur sur le soulignement ondulé et appuyez sur <kbd>CTRL</kbd> + <kbd>.</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b0739-394">Move the editor caret over the squiggly underline and press <kbd>Ctrl</kbd>+<kbd>.</kbd>.</span></span> <span data-ttu-id="b0739-395">pour afficher le correctif de code suggéré.</span><span class="sxs-lookup"><span data-stu-id="b0739-395">to display the suggested code fix.</span></span> <span data-ttu-id="b0739-396">Après avoir sélectionné votre correctif de code, Notez que le `var` mot clé est désormais géré correctement.</span><span class="sxs-lookup"><span data-stu-id="b0739-396">Upon selecting your code fix, note that the `var` keyword is now handled correctly.</span></span>

<span data-ttu-id="b0739-397">Enfin, ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b0739-397">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="b0739-398">Après ces modifications, vous obtenez des traits de soulignement ondulés rouges uniquement sur les deux premières variables.</span><span class="sxs-lookup"><span data-stu-id="b0739-398">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="b0739-399">Ajoutez `const` à `i` et à `j`, et vous obtenez un nouvel avertissement sur `k`, car cet élément peut désormais devenir `const`.</span><span class="sxs-lookup"><span data-stu-id="b0739-399">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="b0739-400">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="b0739-400">Congratulations!</span></span> <span data-ttu-id="b0739-401">Vous avez créé votre première extension .NET Compiler Platform qui effectue une analyse de code à la volée pour détecter un problème et fournit une solution rapide pour résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="b0739-401">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="b0739-402">Tout au long du processus, vous avez découvert la plupart des API de code qui font partie du SDK .NET Compiler Platform (API Roslyn).</span><span class="sxs-lookup"><span data-stu-id="b0739-402">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="b0739-403">Vous pouvez comparer votre travail avec [l’exemple terminé](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) dans notre référentiel GitHub d’exemples.</span><span class="sxs-lookup"><span data-stu-id="b0739-403">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="b0739-404">Autres ressources</span><span class="sxs-lookup"><span data-stu-id="b0739-404">Other resources</span></span>

- [<span data-ttu-id="b0739-405">Bien démarrer avec l’analyse de la syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0739-405">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="b0739-406">Bien démarrer avec l’analyse sémantique</span><span class="sxs-lookup"><span data-stu-id="b0739-406">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
