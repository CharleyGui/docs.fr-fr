---
title: 'Procédure : transformer un fragment de nœud'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: f5eb8e7826dd132fd46f6f476335416e7dd03269
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722685"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="4cf61-102">Procédure : transformer un fragment de nœud</span><span class="sxs-lookup"><span data-stu-id="4cf61-102">How to: Transform a Node Fragment</span></span>

<span data-ttu-id="4cf61-103">Lorsque vous transformez des données contenues dans un objet <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XPath.XPathDocument>, les transformations XSLT s'appliquent à l'ensemble du document.</span><span class="sxs-lookup"><span data-stu-id="4cf61-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="4cf61-104">En d'autres termes, si vous passez dans un autre nœud que le nœud racine du document, cela n'empêche pas le processus de transformation d'accéder à tous les nœuds dans le document chargé.</span><span class="sxs-lookup"><span data-stu-id="4cf61-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="4cf61-105">Pour transformer un fragment de nœud, vous devez créer un objet séparé contenant uniquement le fragment de nœud et transmettre cet objet à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="4cf61-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="4cf61-106">Procédures</span><span class="sxs-lookup"><span data-stu-id="4cf61-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="4cf61-107">Pour transformer un fragment de nœud</span><span class="sxs-lookup"><span data-stu-id="4cf61-107">To transform a node fragment</span></span>  
  
1. <span data-ttu-id="4cf61-108">Créez un objet contenant le document source.</span><span class="sxs-lookup"><span data-stu-id="4cf61-108">Create an object containing the source document.</span></span>  
  
2. <span data-ttu-id="4cf61-109">Localisez le fragment de nœud que vous souhaitez transformer.</span><span class="sxs-lookup"><span data-stu-id="4cf61-109">Locate the node fragment you wish to transform.</span></span>  
  
3. <span data-ttu-id="4cf61-110">Créez un objet distinct contenant uniquement le fragment de nœud.</span><span class="sxs-lookup"><span data-stu-id="4cf61-110">Create separate object with just the node fragment.</span></span>  
  
4. <span data-ttu-id="4cf61-111">Transmettez le fragment de nœud à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="4cf61-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cf61-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="4cf61-112">Example</span></span>  

 <span data-ttu-id="4cf61-113">L'exemple suivant transforme un fragment de nœud et affiche les résultats sur la console.</span><span class="sxs-lookup"><span data-stu-id="4cf61-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="4cf61-114">Entrée</span><span class="sxs-lookup"><span data-stu-id="4cf61-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="4cf61-115">books.xml</span><span class="sxs-lookup"><span data-stu-id="4cf61-115">books.xml</span></span>  

 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="4cf61-116">single.xsl</span><span class="sxs-lookup"><span data-stu-id="4cf61-116">single.xsl</span></span>  

 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="4cf61-117">Sortie</span><span class="sxs-lookup"><span data-stu-id="4cf61-117">Output</span></span>  

 <span data-ttu-id="4cf61-118">Le titre du livre est The Confidence Man.</span><span class="sxs-lookup"><span data-stu-id="4cf61-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf61-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cf61-119">See also</span></span>

- [<span data-ttu-id="4cf61-120">Utilisation de la classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="4cf61-120">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)
