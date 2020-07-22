---
title: Utilisation du CodeDOM
description: Utilisez le Code Document Object Model (CodeDOM), qui fournit des types représentant de nombreux types courants d’éléments de code source, pour assembler un graphique d’objet.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
ms.openlocfilehash: 476d8c18f386f889855c664147b1ee20995dc6f9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865214"
---
# <a name="using-the-codedom"></a><span data-ttu-id="4d956-103">Utilisation du CodeDOM</span><span class="sxs-lookup"><span data-stu-id="4d956-103">Using the CodeDOM</span></span>
<span data-ttu-id="4d956-104">CodeDOM fournit des types qui représentent de nombreux types courants d’éléments du code source.</span><span class="sxs-lookup"><span data-stu-id="4d956-104">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="4d956-105">Vous pouvez concevoir un programme qui génère un modèle de code source à l’aide d’éléments CodeDOM pour assembler un graphique d’objet.</span><span class="sxs-lookup"><span data-stu-id="4d956-105">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="4d956-106">Ce graphique d’objet peut être rendu sous forme de code source à l’aide d’un générateur de code CodeDOM pour un langage de programmation pris en charge.</span><span class="sxs-lookup"><span data-stu-id="4d956-106">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="4d956-107">CodeDOM permet également de compiler du code source dans un assembly binaire.</span><span class="sxs-lookup"><span data-stu-id="4d956-107">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="4d956-108">Voici quelques usages courants de CodeDOM :</span><span class="sxs-lookup"><span data-stu-id="4d956-108">Some common uses for the CodeDOM include:</span></span>  
  
- <span data-ttu-id="4d956-109">Génération d’un code modèle : génération du code pour ASP.NET, les proxies clients de services Web XML, les Assistants Code, les concepteurs ou d’autres mécanismes d’émission de code.</span><span class="sxs-lookup"><span data-stu-id="4d956-109">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
- <span data-ttu-id="4d956-110">Compilation dynamique : prise en charge de la compilation du code dans un ou plusieurs langages.</span><span class="sxs-lookup"><span data-stu-id="4d956-110">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="4d956-111">Génération d’un graphique CodeDOM</span><span class="sxs-lookup"><span data-stu-id="4d956-111">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="4d956-112">L’espace de noms <xref:System.CodeDom> fournit des classes représentant la structure logique du code source, indépendamment de la syntaxe d’un langage.</span><span class="sxs-lookup"><span data-stu-id="4d956-112">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="4d956-113">Structure d’un graphique CodeDOM</span><span class="sxs-lookup"><span data-stu-id="4d956-113">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="4d956-114">La structure d’un graphique CodeDOM est comparable à une arborescence de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="4d956-114">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="4d956-115">Le conteneur de niveau supérieur, ou conteneur racine, de chaque graphique CodeDOM compilable est un <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="4d956-115">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="4d956-116">Chaque élément de votre modèle de code source doit être lié au graphique par le biais d’une propriété d’un <xref:System.CodeDom.CodeObject> du graphique.</span><span class="sxs-lookup"><span data-stu-id="4d956-116">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="4d956-117">Génération d’un modèle de code source pour un exemple de programme Hello World</span><span class="sxs-lookup"><span data-stu-id="4d956-117">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="4d956-118">L’exemple ci-dessous montre comment générer un graphique d’objet CodeDOM représentant le code d’une application simple Hello World.</span><span class="sxs-lookup"><span data-stu-id="4d956-118">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="4d956-119">Pour obtenir le code source complet pour cet exemple, consultez la rubrique <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4d956-119">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="4d956-120">Création d’une unité de compilation</span><span class="sxs-lookup"><span data-stu-id="4d956-120">Creating a compile unit</span></span>  
 <span data-ttu-id="4d956-121">CodeDOM définit un objet appelé <xref:System.CodeDom.CodeCompileUnit> qui peut référencer un graphique d’objet CodeDOM modélisant le code source à compiler.</span><span class="sxs-lookup"><span data-stu-id="4d956-121">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="4d956-122">**CodeCompileUnit** a des propriétés pour le stockage des références aux attributs, espaces de noms et assemblys.</span><span class="sxs-lookup"><span data-stu-id="4d956-122">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="4d956-123">Les fournisseurs CodeDOM qui dérivent de la classe <xref:System.CodeDom.Compiler.CodeDomProvider> contiennent des méthodes qui traitent le graphique d’objet référencé par **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="4d956-123">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="4d956-124">Pour créer un graphique d’objet pour une application simple, vous devez assembler le modèle de code source et le référencer à partir de **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="4d956-124">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="4d956-125">Vous pouvez créer une unité de compilation avec la syntaxe illustrée dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4d956-125">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="4d956-126"><xref:System.CodeDom.CodeSnippetCompileUnit> peut contenir une section de code source qui figure déjà dans le langage cible, mais ne peut pas être rendue dans un autre langage.</span><span class="sxs-lookup"><span data-stu-id="4d956-126">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="4d956-127">Définition d’un espace de noms</span><span class="sxs-lookup"><span data-stu-id="4d956-127">Defining a namespace</span></span>  
 <span data-ttu-id="4d956-128">Pour définir un espace de noms, créez un <xref:System.CodeDom.CodeNamespace> et nommez-le en utilisant le constructeur approprié ou en définissant sa propriété **Name**.</span><span class="sxs-lookup"><span data-stu-id="4d956-128">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="4d956-129">Importation d’un espace de noms</span><span class="sxs-lookup"><span data-stu-id="4d956-129">Importing a namespace</span></span>  
 <span data-ttu-id="4d956-130">Pour ajouter une directive d’importation d’espace de noms à l’espace de noms, ajoutez un <xref:System.CodeDom.CodeNamespaceImport> qui spécifie l’espace de noms à importer dans la collection **CodeNamespace.Imports**.</span><span class="sxs-lookup"><span data-stu-id="4d956-130">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="4d956-131">Le code suivant ajoute une importation de l’espace de noms **System** à la collection **Imports** d’un **CodeNamespace** appelé `samples` :</span><span class="sxs-lookup"><span data-stu-id="4d956-131">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="4d956-132">Liaison d’éléments de code à l’intérieur du graphique d’objet</span><span class="sxs-lookup"><span data-stu-id="4d956-132">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="4d956-133">Tous les éléments de code qui forment un graphique CodeDOM doivent être liés au <xref:System.CodeDom.CodeCompileUnit> qui constitue l’élément racine de l’arborescence par une série de références entre des éléments directement référencés à partir des propriétés de l’objet racine du graphique.</span><span class="sxs-lookup"><span data-stu-id="4d956-133">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="4d956-134">Affectez un objet à une propriété d’un objet conteneur pour établir une référence à partir de cet objet.</span><span class="sxs-lookup"><span data-stu-id="4d956-134">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="4d956-135">L’instruction suivante ajoute le  **CodeNamespace**`samples` à la propriété de collection **Namespaces** du **CodeCompileUnit** racine.</span><span class="sxs-lookup"><span data-stu-id="4d956-135">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="4d956-136">Définition d’un type</span><span class="sxs-lookup"><span data-stu-id="4d956-136">Defining a type</span></span>  
 <span data-ttu-id="4d956-137">Pour déclarer une classe, une structure, une interface ou une énumération à l’aide de CodeDOM, créez un <xref:System.CodeDom.CodeTypeDeclaration> et nommez-le.</span><span class="sxs-lookup"><span data-stu-id="4d956-137">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="4d956-138">L’exemple suivant illustre cette opération à l’aide d’une surcharge de constructeur définissant la propriété **Name** :</span><span class="sxs-lookup"><span data-stu-id="4d956-138">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="4d956-139">Pour ajouter un type à un espace de noms, ajoutez un <xref:System.CodeDom.CodeTypeDeclaration> représentant ce type à la collection **Types** d’un **CodeNamespace**.</span><span class="sxs-lookup"><span data-stu-id="4d956-139">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="4d956-140">L’exemple suivant montre comment ajouter une classe nommée `class1` à un **CodeNamespace** nommé `samples` :</span><span class="sxs-lookup"><span data-stu-id="4d956-140">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="4d956-141">Ajout de membres de classe à une classe</span><span class="sxs-lookup"><span data-stu-id="4d956-141">Adding class members to a class</span></span>  
 <span data-ttu-id="4d956-142">L’espace de noms <xref:System.CodeDom> propose divers éléments que vous pouvez utiliser pour représenter des membres de classe.</span><span class="sxs-lookup"><span data-stu-id="4d956-142">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="4d956-143">Chaque membre de classe peut être ajouté à la collection **Members** d’un <xref:System.CodeDom.CodeTypeDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="4d956-143">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="4d956-144">Définition d’une méthode de point d’entrée de code pour un exécutable</span><span class="sxs-lookup"><span data-stu-id="4d956-144">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="4d956-145">Si vous créez le code d’un programme exécutable, il est nécessaire d’indiquer le point d’entrée du programme en créant un <xref:System.CodeDom.CodeEntryPointMethod> qui représente la méthode à laquelle doit commencer l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="4d956-145">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="4d956-146">L’exemple suivant montre comment définir une méthode de point d’entrée qui contient un <xref:System.CodeDom.CodeMethodInvokeExpression> qui appelle **System.Console.WriteLine** pour imprimer « Hello World! » :</span><span class="sxs-lookup"><span data-stu-id="4d956-146">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="4d956-147">L’instruction suivante ajoute la méthode de point d’entrée nommée `Start` à la collection **Members** de `class1` :</span><span class="sxs-lookup"><span data-stu-id="4d956-147">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="4d956-148">À présent, le <xref:System.CodeDom.CodeCompileUnit> nommé `compileUnit` contient le graphique CodeDOM d’un programme Hello World simple.</span><span class="sxs-lookup"><span data-stu-id="4d956-148">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="4d956-149">Pour plus d’informations sur la génération et la compilation de code à partir d’un graphique CodeDOM, consultez [Génération de code source et compilation d’un programme à partir d’un graphique CodeDOM](generating-and-compiling-source-code-from-a-codedom-graph.md).</span><span class="sxs-lookup"><span data-stu-id="4d956-149">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="4d956-150">Complément d’information sur la génération d’un graphique CodeDOM</span><span class="sxs-lookup"><span data-stu-id="4d956-150">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="4d956-151">CodeDOM prend en charge les nombreux types communs d’éléments de code présents dans les langages de programmation compatibles avec le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="4d956-151">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="4d956-152">CodeDOM n’a pas été conçu pour fournir des éléments représentant toutes les fonctionnalités de langage de programmation possibles.</span><span class="sxs-lookup"><span data-stu-id="4d956-152">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="4d956-153">Le code qui ne peut pas être facilement représenté à l’aide d’éléments CodeDOM peut être encapsulé dans un <xref:System.CodeDom.CodeSnippetExpression>, un <xref:System.CodeDom.CodeSnippetStatement>, un <xref:System.CodeDom.CodeSnippetTypeMember> ou un <xref:System.CodeDom.CodeSnippetCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="4d956-153">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="4d956-154">Toutefois, certains extraits de code ne peuvent pas être traduits automatiquement dans d’autres langages par CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="4d956-154">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="4d956-155">Pour plus d’informations sur chacun des types CodeDOM, consultez la documentation de référence pour l’espace de noms <xref:System.CodeDom>.</span><span class="sxs-lookup"><span data-stu-id="4d956-155">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="4d956-156">Pour obtenir un graphique permettant de retrouver rapidement l’élément CodeDOM à utiliser pour représenter un type d’élément de code particulier, consultez [Aide-mémoire de CodeDOM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4d956-156">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span></span>
