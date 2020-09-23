---
title: 'Comment : accéder à des éléments descendants XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: dcbaf1f9022d86f40a90ef6a1e0033f627caeef2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058207"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="19a5e-102">Comment : accéder à des éléments descendants XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19a5e-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>

<span data-ttu-id="19a5e-103">Cet exemple montre comment utiliser une propriété d’axe descendant pour accéder à tous les éléments XML portant un nom spécifié et contenus sous un élément XML.</span><span class="sxs-lookup"><span data-stu-id="19a5e-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="19a5e-104">En particulier, elle utilise la `Value` propriété pour récupérer la valeur du premier élément de la collection que la propriété de l' `name` axe descendant retourne.</span><span class="sxs-lookup"><span data-stu-id="19a5e-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="19a5e-105">La `name` propriété d’axe descendant obtient tous les éléments nommés `name` qui sont contenus dans l' `contacts` objet.</span><span class="sxs-lookup"><span data-stu-id="19a5e-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="19a5e-106">Cet exemple utilise également la `phone` propriété de l’axe descendant pour accéder à tous les descendants nommés `phone` qui sont contenus dans l' `contacts` objet.</span><span class="sxs-lookup"><span data-stu-id="19a5e-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19a5e-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="19a5e-107">Example</span></span>  

 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="19a5e-108">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="19a5e-108">Compile the code</span></span>  

 <span data-ttu-id="19a5e-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="19a5e-109">This example requires:</span></span>  
  
- <span data-ttu-id="19a5e-110">une référence à l'espace de noms <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="19a5e-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19a5e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19a5e-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="19a5e-112">XML Descendant Axis Property</span><span class="sxs-lookup"><span data-stu-id="19a5e-112">XML Descendant Axis Property</span></span>](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="19a5e-113">Propriété de valeur XML</span><span class="sxs-lookup"><span data-stu-id="19a5e-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="19a5e-114">Accès au code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="19a5e-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="19a5e-115">XML</span><span class="sxs-lookup"><span data-stu-id="19a5e-115">XML</span></span>](index.md)
