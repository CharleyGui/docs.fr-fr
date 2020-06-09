---
title: Guide pratique pour créer un fichier de documentation XML à l’aide de CodeDOM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
ms.openlocfilehash: b9e11a51048733dbfc42ff9f575e18effc80db07
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596244"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="d6e35-102">Comment : créer un fichier de documentation XML à l’aide de CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d6e35-102">How to: Create an XML documentation file using CodeDOM</span></span>

<span data-ttu-id="d6e35-103">Vous pouvez utiliser CodeDOM pour créer du code qui génère de la documentation XML.</span><span class="sxs-lookup"><span data-stu-id="d6e35-103">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="d6e35-104">Le processus implique la création du graphique CodeDOM qui contient les commentaires de documentation XML, la génération du code et la compilation du code généré avec l’option du compilateur qui crée la sortie de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="d6e35-104">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
## <a name="create-a-codedom-graph"></a><span data-ttu-id="d6e35-105">Créer un graphique CodeDOM</span><span class="sxs-lookup"><span data-stu-id="d6e35-105">Create a CodeDOM graph</span></span>
  
1. <span data-ttu-id="d6e35-106">Créez un <xref:System.CodeDom.CodeCompileUnit> contenant le graphique CodeDOM pour l’exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="d6e35-106">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2. <span data-ttu-id="d6e35-107">Utilisez le constructeur <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> avec le paramètre `docComment` défini sur `true` pour créer les éléments et le texte de commentaires de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="d6e35-107">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="d6e35-108">Générer le code à partir de CodeCompileUnit</span><span class="sxs-lookup"><span data-stu-id="d6e35-108">Generate the code from the CodeCompileUnit</span></span>
  
1. <span data-ttu-id="d6e35-109">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> pour générer le code et créer un fichier source à compiler.</span><span class="sxs-lookup"><span data-stu-id="d6e35-109">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="d6e35-110">Compiler le code et générer le fichier de documentation</span><span class="sxs-lookup"><span data-stu-id="d6e35-110">Compile the code and generate the documentation file</span></span>
  
1. <span data-ttu-id="d6e35-111">Ajoutez l’option du compilateur **/doc** à la propriété <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> d’un objet <xref:System.CodeDom.Compiler.CompilerParameters> et passez l’objet à la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> pour créer le fichier de documentation XML quand le code est compilé.</span><span class="sxs-lookup"><span data-stu-id="d6e35-111">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="d6e35-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="d6e35-112">Example</span></span>

<span data-ttu-id="d6e35-113">L’exemple de code suivant crée un graphique CodeDOM avec des commentaires de documentation, génère un fichier de code à partir du graphique, compile le fichier et crée un fichier de documentation XML associé.</span><span class="sxs-lookup"><span data-stu-id="d6e35-113">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="d6e35-114">L’exemple de code crée la documentation XML suivante dans le fichier *HelloWorldDoc. xml* .</span><span class="sxs-lookup"><span data-stu-id="d6e35-114">The code example creates the following XML documentation in the *HelloWorldDoc.xml* file.</span></span>  
  
```xml  
<?xml version="1.0" ?>
<doc>  
  <assembly>  
    <name>HelloWorld</name>
  </assembly>  
  <members>  
    <member name="T:Samples.Class1">  
      <summary>  
        Create a Hello World application.
      </summary>
      <seealso cref="M:Samples.Class1.Main" />
    </member>  
    <member name="M:Samples.Class1.Main">  
      <summary>  
        Main method for HelloWorld application.
        <para>Add a new paragraph to the description.</para>
      </summary>  
    </member>  
  </members>  
</doc>  
```  
  
## <a name="compile-permissions"></a><span data-ttu-id="d6e35-115">Autorisations de compilation</span><span class="sxs-lookup"><span data-stu-id="d6e35-115">Compile permissions</span></span>
  
<span data-ttu-id="d6e35-116">Cet exemple de code nécessite le jeu d’autorisations `FullTrust` pour s’exécuter correctement.</span><span class="sxs-lookup"><span data-stu-id="d6e35-116">This code example requires the `FullTrust` permission set to execute successfully.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d6e35-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6e35-117">See also</span></span>

- [<span data-ttu-id="d6e35-118">Documenter votre code avec XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6e35-118">Document your code with XML (Visual Basic)</span></span>](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="d6e35-119">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="d6e35-119">XML documentation comments</span></span>](../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="d6e35-120">Documentation XML (C++)</span><span class="sxs-lookup"><span data-stu-id="d6e35-120">XML documentation (C++)</span></span>](/cpp/ide/xml-documentation-visual-cpp)
