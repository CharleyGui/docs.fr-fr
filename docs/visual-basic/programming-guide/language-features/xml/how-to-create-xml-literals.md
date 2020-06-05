---
title: 'Comment : créer des littéraux XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 61b138c0851c747ed30eedc10cb882cc3b03c4d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392608"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="74f3d-102">Comment : créer des littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74f3d-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="74f3d-103">Vous pouvez créer un document XML, un fragment ou un élément directement dans le code à l’aide d’un littéral XML.</span><span class="sxs-lookup"><span data-stu-id="74f3d-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="74f3d-104">Les exemples de cette rubrique montrent comment créer un élément XML qui a trois éléments enfants et comment créer un document XML.</span><span class="sxs-lookup"><span data-stu-id="74f3d-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="74f3d-105">Vous pouvez également utiliser les [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API pour créer des [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objets.</span><span class="sxs-lookup"><span data-stu-id="74f3d-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="74f3d-106">Pour plus d’informations, consultez <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="74f3d-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="74f3d-107">Pour créer un élément XML</span><span class="sxs-lookup"><span data-stu-id="74f3d-107">To create an XML element</span></span>  
  
- <span data-ttu-id="74f3d-108">Créez le XML inline à l’aide de la syntaxe de littéral XML, qui est la même que la syntaxe XML réelle.</span><span class="sxs-lookup"><span data-stu-id="74f3d-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="74f3d-109">Exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="74f3d-109">Run the code.</span></span> <span data-ttu-id="74f3d-110">Le résultat de ce code est le suivant :</span><span class="sxs-lookup"><span data-stu-id="74f3d-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="74f3d-111">Pour créer un document XML</span><span class="sxs-lookup"><span data-stu-id="74f3d-111">To create an XML document</span></span>  
  
- <span data-ttu-id="74f3d-112">Créez le document XML en ligne.</span><span class="sxs-lookup"><span data-stu-id="74f3d-112">Create the XML document inline.</span></span> <span data-ttu-id="74f3d-113">Le code suivant crée un document XML qui a une syntaxe littérale, une déclaration XML, une instruction de traitement, un commentaire et un élément qui contient un autre élément.</span><span class="sxs-lookup"><span data-stu-id="74f3d-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="74f3d-114">Exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="74f3d-114">Run the code.</span></span> <span data-ttu-id="74f3d-115">Le résultat de ce code est le suivant :</span><span class="sxs-lookup"><span data-stu-id="74f3d-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="74f3d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74f3d-116">See also</span></span>

- [<span data-ttu-id="74f3d-117">XML</span><span class="sxs-lookup"><span data-stu-id="74f3d-117">XML</span></span>](index.md)
- [<span data-ttu-id="74f3d-118">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="74f3d-118">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="74f3d-119">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="74f3d-119">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="74f3d-120">Littéral de document XML</span><span class="sxs-lookup"><span data-stu-id="74f3d-120">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
