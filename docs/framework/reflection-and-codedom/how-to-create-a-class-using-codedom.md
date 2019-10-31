---
title: Guide pratique pour créer une classe à l’aide de CodeDOM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
ms.openlocfilehash: ff7c9d1593c8e75f9bcaeda6577c7cb941719749
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130204"
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="26ce0-102">Guide pratique pour créer une classe à l’aide de CodeDOM</span><span class="sxs-lookup"><span data-stu-id="26ce0-102">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="26ce0-103">Les procédures suivantes expliquent comment créer et compiler un graphique CodeDOM qui génère une classe contenant deux champs, trois propriétés, une méthode, un constructeur et un point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="26ce0-103">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1. <span data-ttu-id="26ce0-104">Créez une application console qui utilisera du code CodeDOM pour générer le code source pour une classe.</span><span class="sxs-lookup"><span data-stu-id="26ce0-104">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="26ce0-105">Dans cet exemple, la classe génératrice se nomme `Sample`, et le code généré est une classe nommée `CodeDOMCreatedClass` dans un fichier nommé SampleCode.</span><span class="sxs-lookup"><span data-stu-id="26ce0-105">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2. <span data-ttu-id="26ce0-106">Dans la classe génératrice, initialisez le graphique CodeDOM et utilisez des méthodes CodeDOM pour définir les membres, le constructeur et le point d’entrée (méthode `Main`) de la classe générée.</span><span class="sxs-lookup"><span data-stu-id="26ce0-106">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="26ce0-107">Dans cet exemple, la classe générée comporte deux champs, trois propriétés, un constructeur, une méthode et une méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="26ce0-107">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3. <span data-ttu-id="26ce0-108">Dans la classe génératrice, créez un fournisseur de code propre au langage, puis appelez ses méthodes <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> pour générer le code à partir du graphique.</span><span class="sxs-lookup"><span data-stu-id="26ce0-108">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4. <span data-ttu-id="26ce0-109">Compilez et exécutez l’application pour générer le code.</span><span class="sxs-lookup"><span data-stu-id="26ce0-109">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="26ce0-110">Dans cet exemple, le code généré se trouve dans un fichier nommé SampleCode.</span><span class="sxs-lookup"><span data-stu-id="26ce0-110">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="26ce0-111">Compilez et exécutez ce code pour voir l’exemple de sortie.</span><span class="sxs-lookup"><span data-stu-id="26ce0-111">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="26ce0-112">Pour créer l’application qui exécutera le code CodeDOM</span><span class="sxs-lookup"><span data-stu-id="26ce0-112">To create the application that will execute the CodeDOM code</span></span>  
  
- <span data-ttu-id="26ce0-113">Créez une classe d’application console pour contenir le code CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="26ce0-113">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="26ce0-114">Définissez les champs globaux qui doivent être utilisés dans la classe pour référencer l’assembly (<xref:System.CodeDom.CodeCompileUnit>) et la classe (<xref:System.CodeDom.CodeTypeDeclaration>), spécifiez le nom du fichier source généré, et déclarez la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="26ce0-114">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="26ce0-115">Pour initialiser le graphique CodeDOM</span><span class="sxs-lookup"><span data-stu-id="26ce0-115">To initialize the CodeDOM graph</span></span>  
  
- <span data-ttu-id="26ce0-116">Dans le constructeur de la classe d’application console, initialisez l’assembly et la classe, et ajoutez les déclarations appropriées au graphique CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="26ce0-116">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="26ce0-117">Pour ajouter des membres au graphique CodeDOM</span><span class="sxs-lookup"><span data-stu-id="26ce0-117">To add members to the CodeDOM graph</span></span>  
  
- <span data-ttu-id="26ce0-118">Ajoutez des champs au graphique CodeDOM en ajoutant des objets <xref:System.CodeDom.CodeMemberField> à la propriété <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> de la classe.</span><span class="sxs-lookup"><span data-stu-id="26ce0-118">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- <span data-ttu-id="26ce0-119">Ajoutez des propriétés au graphique CodeDOM en ajoutant des objets <xref:System.CodeDom.CodeMemberProperty> à la propriété <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> de la classe.</span><span class="sxs-lookup"><span data-stu-id="26ce0-119">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- <span data-ttu-id="26ce0-120">Ajoutez une méthode au graphique CodeDOM en ajoutant un objet <xref:System.CodeDom.CodeMemberMethod> à la propriété <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> de la classe.</span><span class="sxs-lookup"><span data-stu-id="26ce0-120">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- <span data-ttu-id="26ce0-121">Ajoutez un constructeur au graphique CodeDOM en ajoutant un objet <xref:System.CodeDom.CodeConstructor> à la propriété <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> de la classe.</span><span class="sxs-lookup"><span data-stu-id="26ce0-121">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- <span data-ttu-id="26ce0-122">Ajoutez un point d’entrée au graphique CodeDOM en ajoutant un objet <xref:System.CodeDom.CodeEntryPointMethod> à la propriété <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> de la classe.</span><span class="sxs-lookup"><span data-stu-id="26ce0-122">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="26ce0-123">Pour générer le code à partir du graphique CodeDOM</span><span class="sxs-lookup"><span data-stu-id="26ce0-123">To generate the code from the CodeDOM graph</span></span>  
  
- <span data-ttu-id="26ce0-124">Générez le code source à partir du graphique CodeDOM en appelant la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A>.</span><span class="sxs-lookup"><span data-stu-id="26ce0-124">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="26ce0-125">Pour créer le graphique et générer le code</span><span class="sxs-lookup"><span data-stu-id="26ce0-125">To create the graph and generate the code</span></span>  
  
1. <span data-ttu-id="26ce0-126">Ajoutez les méthodes créées aux étapes précédentes à la méthode `Main` définie lors de la première étape.</span><span class="sxs-lookup"><span data-stu-id="26ce0-126">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. <span data-ttu-id="26ce0-127">Compilez et exécutez la classe génératrice.</span><span class="sxs-lookup"><span data-stu-id="26ce0-127">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26ce0-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="26ce0-128">Example</span></span>  
 <span data-ttu-id="26ce0-129">L’exemple de code suivant montre le code des étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="26ce0-129">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="26ce0-130">Quand l’exemple précédent est compilé et exécuté, il génère le code source suivant.</span><span class="sxs-lookup"><span data-stu-id="26ce0-130">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="26ce0-131">Le code source généré produit la sortie suivante quand il est compilé et exécuté.</span><span class="sxs-lookup"><span data-stu-id="26ce0-131">The generated source code produces the following output when compiled and executed.</span></span>  
  
```output
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="26ce0-132">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="26ce0-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="26ce0-133">Cet exemple de code nécessite le jeu d’autorisations `FullTrust` pour s’exécuter correctement.</span><span class="sxs-lookup"><span data-stu-id="26ce0-133">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ce0-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26ce0-134">See also</span></span>

- [<span data-ttu-id="26ce0-135">Utilisation du CodeDOM</span><span class="sxs-lookup"><span data-stu-id="26ce0-135">Using the CodeDOM</span></span>](using-the-codedom.md)
- [<span data-ttu-id="26ce0-136">Génération et compilation du code source à partir d’un graphique CodeDOM</span><span class="sxs-lookup"><span data-stu-id="26ce0-136">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)
