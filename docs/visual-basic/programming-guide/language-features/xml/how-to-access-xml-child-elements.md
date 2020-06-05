---
title: 'Comment : accéder à des éléments enfants XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 994249801eecc2984947efac9712df0047f076a4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392816"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="2e285-102">Comment : accéder à des éléments enfants XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e285-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="2e285-103">Cet exemple montre comment utiliser une propriété d’axe enfant pour accéder à tous les éléments enfants XML portant un nom spécifié dans un élément XML.</span><span class="sxs-lookup"><span data-stu-id="2e285-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="2e285-104">En particulier, elle utilise la <xref:System.Xml.Linq.XElement.Value%2A> propriété pour récupérer la valeur du premier élément de la collection retourné par la `name` propriété d’axe enfant.</span><span class="sxs-lookup"><span data-stu-id="2e285-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="2e285-105">La `name` propriété d’axe enfant obtient tous les éléments enfants nommés `phone` dans l' `contact` objet.</span><span class="sxs-lookup"><span data-stu-id="2e285-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="2e285-106">Cet exemple utilise également la `phone` propriété d’axe enfant pour accéder à tous les éléments enfants nommés `phone` qui sont contenus dans l' `contact` objet.</span><span class="sxs-lookup"><span data-stu-id="2e285-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e285-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="2e285-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="2e285-108">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="2e285-108">Compile the code</span></span>  
 <span data-ttu-id="2e285-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="2e285-109">This example requires:</span></span>  
  
- <span data-ttu-id="2e285-110">une référence à l'espace de noms <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="2e285-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e285-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e285-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2e285-112">XML Child Axis Property</span><span class="sxs-lookup"><span data-stu-id="2e285-112">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="2e285-113">Propriété de valeur XML</span><span class="sxs-lookup"><span data-stu-id="2e285-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="2e285-114">Accès au code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e285-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="2e285-115">XML</span><span class="sxs-lookup"><span data-stu-id="2e285-115">XML</span></span>](index.md)
