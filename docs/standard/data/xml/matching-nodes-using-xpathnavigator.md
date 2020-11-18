---
title: Mise en correspondance de nœuds avec XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: e7e9d63ed4b24eb0e594c464038590aa9dc99910
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822527"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="f848c-102">Mise en correspondance de nœuds avec XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f848c-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="f848c-103">La classe <xref:System.Xml.XPath.XPathNavigator> fournit la méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> permettant de déterminer si un nœud correspond à une expression XPath.</span><span class="sxs-lookup"><span data-stu-id="f848c-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="f848c-104">La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> prend une expression XPath comme entrée et retourne un objet <xref:System.Boolean> indiquant si le nœud actuel correspond à l’expression XPath donnée ou à l’objet <xref:System.Xml.XPath.XPathExpression> compilé donné.</span><span class="sxs-lookup"><span data-stu-id="f848c-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="f848c-105">Mise en correspondance de nœuds</span><span class="sxs-lookup"><span data-stu-id="f848c-105">Matching Nodes</span></span>  
 <span data-ttu-id="f848c-106">La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retourne `true` si le nœud actuel correspond à l’expression XPath spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f848c-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="f848c-107">Par exemple, dans le code suivant, la méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retournera `true` si le nœud actuel est l'élément `b` et si l'élément `b` a un attribut `c`.</span><span class="sxs-lookup"><span data-stu-id="f848c-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f848c-108">La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> ne modifie pas l'état de l'objet <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f848c-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a><span data-ttu-id="f848c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f848c-109">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f848c-110">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="f848c-110">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f848c-111">Sélection de données XML à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f848c-111">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f848c-112">Évaluation d’expressions XPath à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f848c-112">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="f848c-113">Types de nœuds reconnus avec les requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="f848c-113">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="f848c-114">Requêtes et espaces de noms XPath</span><span class="sxs-lookup"><span data-stu-id="f848c-114">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="f848c-115">Expressions XPath compilées</span><span class="sxs-lookup"><span data-stu-id="f848c-115">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
