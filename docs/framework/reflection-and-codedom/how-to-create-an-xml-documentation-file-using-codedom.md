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
ms.openlocfilehash: a0ccb469a43c3a21a76eaf24fa7ce7b490dd5c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180520"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Guide pratique pour créer un fichier de documentation XML à l’aide de CodeDOM
Vous pouvez utiliser CodeDOM pour créer du code qui génère de la documentation XML. Le processus implique la création du graphique CodeDOM qui contient les commentaires de documentation XML, la génération du code et la compilation du code généré avec l’option du compilateur qui crée la sortie de documentation XML.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>Pour créer un graphique CodeDOM qui contient des commentaires de documentation XML  
  
1. Créez un <xref:System.CodeDom.CodeCompileUnit> contenant le graphique CodeDOM pour l’exemple d’application.  
  
2. Utilisez le constructeur <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> avec le paramètre `docComment` défini sur `true` pour créer les éléments et le texte de commentaires de documentation XML.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>Pour générer le code à partir de CodeCompileUnit  
  
1. Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> pour générer le code et créer un fichier source à compiler.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Pour compiler le code et générer le fichier de documentation  
  
1. Ajoutez l’option du compilateur **/doc** à la propriété <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> d’un objet <xref:System.CodeDom.Compiler.CompilerParameters> et passez l’objet à la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> pour créer le fichier de documentation XML quand le code est compilé.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant crée un graphique CodeDOM avec des commentaires de documentation, génère un fichier de code à partir du graphique, compile le fichier et crée un fichier de documentation XML associé.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 L’exemple de code crée la documentation XML suivante dans le fichier HelloWorldDoc.xml.  
  
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
        <seealso cref="M:Samples.Class1.Main" />
      </summary>  
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
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Cet exemple de code nécessite le jeu d’autorisations `FullTrust` pour s’exécuter correctement.  
  
## <a name="see-also"></a>Voir aussi

- [Documentation de votre code avec le langage XML](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Commentaires de documentation XML](../../csharp/programming-guide/xmldoc/index.md)
- [Documentation XML](/cpp/ide/xml-documentation-visual-cpp)
