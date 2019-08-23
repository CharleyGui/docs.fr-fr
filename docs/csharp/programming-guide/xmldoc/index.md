---
title: Commentaires de documentation XML - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: 8f75783f004f3667644a126930fbfbca4acb0787
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921690"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="2eba4-102">Commentaires de documentation XML (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2eba4-102">XML Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="2eba4-103">Dans Visual C #, vous pouvez créer de la documentation de votre code en incluant des éléments XML dans des champs de commentaire spéciaux (indiqués par trois barres obliques) dans le code source, juste avant le bloc de code auquel les commentaires font référence, par exemple :</span><span class="sxs-lookup"><span data-stu-id="2eba4-103">In Visual C# you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example:</span></span>  
  
```csharp  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass {}  
```  
  
 <span data-ttu-id="2eba4-104">Quand vous utilisez l’option [/doc](../../language-reference/compiler-options/doc-compiler-option.md) pour compiler, le compilateur recherche toutes les balises XML dans le code source et crée un fichier de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="2eba4-104">When you compile with the [/doc](../../language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="2eba4-105">Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="2eba4-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="2eba4-106">Pour faire référence à des éléments XML (par exemple, votre fonction traite des éléments XML spécifiques que vous souhaitez décrire dans un commentaire de documentation XML), vous pouvez utiliser le mécanisme de citation standard (`<` et `>`).</span><span class="sxs-lookup"><span data-stu-id="2eba4-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="2eba4-107">Pour faire référence aux identificateurs génériques dans les éléments de référence de code (`cref`), vous pouvez utiliser des caractères d’échappement (par exemple, `cref="List&lt;T&gt;"`) ou des accolades (`cref="List{T}"`).</span><span class="sxs-lookup"><span data-stu-id="2eba4-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="2eba4-108">En tant que cas particulier, le compilateur analyse les accolades comme des crochets pointus pour rendre le commentaire de documentation moins fastidieux à créer lorsqu'il s'agit de faire référence aux identificateurs génériques.</span><span class="sxs-lookup"><span data-stu-id="2eba4-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2eba4-109">Les commentaires de documentation XML ne sont pas des métadonnées. Ils ne sont pas inclus dans l'assembly compilé et ne sont donc pas accessibles par réflexion.</span><span class="sxs-lookup"><span data-stu-id="2eba4-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2eba4-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2eba4-110">In This Section</span></span>  
  
- [<span data-ttu-id="2eba4-111">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="2eba4-111">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)  
  
- [<span data-ttu-id="2eba4-112">Traitement du fichier XML</span><span class="sxs-lookup"><span data-stu-id="2eba4-112">Processing the XML File</span></span>](./processing-the-xml-file.md)  
  
- [<span data-ttu-id="2eba4-113">Délimiteurs pour les balises de documentation</span><span class="sxs-lookup"><span data-stu-id="2eba4-113">Delimiters for Documentation Tags</span></span>](./delimiters-for-documentation-tags.md)  
  
- [<span data-ttu-id="2eba4-114">Guide pratique pour utiliser les fonctionnalités de la documentation XML</span><span class="sxs-lookup"><span data-stu-id="2eba4-114">How to: Use the XML Documentation Features</span></span>](./how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a><span data-ttu-id="2eba4-115">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="2eba4-115">Related Sections</span></span>  
 <span data-ttu-id="2eba4-116">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="2eba4-116">For more information, see:</span></span>  
  
- [<span data-ttu-id="2eba4-117">/doc (Traiter les commentaires de documentation)</span><span class="sxs-lookup"><span data-stu-id="2eba4-117">/doc (Process Documentation Comments)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="2eba4-118">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="2eba4-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2eba4-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2eba4-119">See also</span></span>

- [<span data-ttu-id="2eba4-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="2eba4-120">C# Programming Guide</span></span>](../index.md)
