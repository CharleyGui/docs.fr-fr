---
title: 'Comment : incorporer des expressions dans des littéraux XML'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332939"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="0c306-102">Comment : incorporer des expressions dans des littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c306-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="0c306-103">Vous pouvez combiner des littéraux XML avec des expressions incorporées pour créer un document XML, un fragment ou un élément qui contient le contenu créé au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0c306-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="0c306-104">Les exemples suivants montrent comment utiliser des expressions incorporées pour remplir le contenu d’un élément, les attributs et les noms d’éléments au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0c306-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="0c306-105">La syntaxe d’une expression incorporée est `<%=` `exp` `%>`, qui est la même syntaxe que celle utilisée par ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0c306-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span></span> <span data-ttu-id="0c306-106">Pour plus d’informations, consultez [expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0c306-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="0c306-107">Vous pouvez également utiliser les API [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour créer des objets [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0c306-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="0c306-108">Pour plus d'informations, consultez <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="0c306-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0c306-109">Procédures</span><span class="sxs-lookup"><span data-stu-id="0c306-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="0c306-110">Pour insérer du texte en tant que contenu d’élément</span><span class="sxs-lookup"><span data-stu-id="0c306-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="0c306-111">L’exemple suivant montre comment insérer le texte contenu dans la variable `contactName` entre les éléments de nom d’ouverture et de fermeture.</span><span class="sxs-lookup"><span data-stu-id="0c306-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="0c306-112">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0c306-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="0c306-113">Pour insérer du texte en tant que valeur d’attribut</span><span class="sxs-lookup"><span data-stu-id="0c306-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="0c306-114">L’exemple suivant montre comment insérer le texte contenu dans la variable `phoneType` en tant que valeur de l’attribut `type`.</span><span class="sxs-lookup"><span data-stu-id="0c306-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="0c306-115">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0c306-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="0c306-116">Pour insérer du texte pour un nom d’élément</span><span class="sxs-lookup"><span data-stu-id="0c306-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="0c306-117">L’exemple suivant montre comment insérer le texte contenu dans la variable `elementName` comme nom d’un élément.</span><span class="sxs-lookup"><span data-stu-id="0c306-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="0c306-118">Lors de la création d’éléments à l’aide de cette technique, vous devez les fermer avec la balise \</>.</span><span class="sxs-lookup"><span data-stu-id="0c306-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="0c306-119">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0c306-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0c306-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c306-120">See also</span></span>

- [<span data-ttu-id="0c306-121">Guide pratique : créer des littéraux XML</span><span class="sxs-lookup"><span data-stu-id="0c306-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [<span data-ttu-id="0c306-122">Expressions incorporées en XML</span><span class="sxs-lookup"><span data-stu-id="0c306-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="0c306-123">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0c306-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="0c306-124">XML</span><span class="sxs-lookup"><span data-stu-id="0c306-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
