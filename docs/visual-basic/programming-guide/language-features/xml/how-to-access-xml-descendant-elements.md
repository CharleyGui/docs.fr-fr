---
title: 'Comment : accéder à des éléments descendants XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: cc045114c67ee2917ef672e734bc852c40d408ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347155"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="7b9f0-102">Comment : accéder à des éléments descendants XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b9f0-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="7b9f0-103">Cet exemple montre comment utiliser une propriété d’axe descendant pour accéder à tous les éléments XML portant un nom spécifié et contenus sous un élément XML.</span><span class="sxs-lookup"><span data-stu-id="7b9f0-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="7b9f0-104">En particulier, elle utilise la propriété `Value` pour récupérer la valeur du premier élément de la collection que la propriété de l’axe descendant `name` retourne.</span><span class="sxs-lookup"><span data-stu-id="7b9f0-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="7b9f0-105">La `name` propriété d’axe descendant obtient tous les éléments nommés `name` qui sont contenus dans l’objet `contacts`.</span><span class="sxs-lookup"><span data-stu-id="7b9f0-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="7b9f0-106">Cet exemple utilise également la propriété d’axe descendant `phone` pour accéder à tous les descendants nommés `phone` qui sont contenus dans l’objet `contacts`.</span><span class="sxs-lookup"><span data-stu-id="7b9f0-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b9f0-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="7b9f0-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="7b9f0-108">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="7b9f0-108">Compile the code</span></span>  
 <span data-ttu-id="7b9f0-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="7b9f0-109">This example requires:</span></span>  
  
- <span data-ttu-id="7b9f0-110">une référence à l'espace de noms <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="7b9f0-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b9f0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b9f0-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7b9f0-112">Propriété d’axe descendant XML</span><span class="sxs-lookup"><span data-stu-id="7b9f0-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="7b9f0-113">Propriété de valeur XML</span><span class="sxs-lookup"><span data-stu-id="7b9f0-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="7b9f0-114">Accès au code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b9f0-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="7b9f0-115">XML</span><span class="sxs-lookup"><span data-stu-id="7b9f0-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
