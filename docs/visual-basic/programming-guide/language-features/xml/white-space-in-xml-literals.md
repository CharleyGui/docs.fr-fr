---
title: Espaces blancs dans les littéraux XML
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: b3caf7ac052f3fed3fe5427da0cc96bbdd955ea6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360473"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="04822-102">Espaces blancs dans les littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04822-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="04822-103">Le compilateur Visual Basic incorpore uniquement les espaces significatifs d’un littéral XML lorsqu’il crée un [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objet.</span><span class="sxs-lookup"><span data-stu-id="04822-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="04822-104">Les caractères d’espace blanc non significatifs ne sont pas incorporés.</span><span class="sxs-lookup"><span data-stu-id="04822-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="04822-105">Espace blanc significatif et non significatif</span><span class="sxs-lookup"><span data-stu-id="04822-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="04822-106">Les caractères d’espace blanc dans les littéraux XML ne sont significatifs que dans trois domaines :</span><span class="sxs-lookup"><span data-stu-id="04822-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
- <span data-ttu-id="04822-107">Lorsqu’ils sont dans une valeur d’attribut.</span><span class="sxs-lookup"><span data-stu-id="04822-107">When they are in an attribute value.</span></span>  
  
- <span data-ttu-id="04822-108">Lorsqu’elles font partie du contenu textuel d’un élément et que le texte contient également d’autres caractères.</span><span class="sxs-lookup"><span data-stu-id="04822-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
- <span data-ttu-id="04822-109">Lorsqu’ils se trouvent dans une expression incorporée pour le contenu de texte d’un élément.</span><span class="sxs-lookup"><span data-stu-id="04822-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="04822-110">Sinon, le compilateur traite les caractères d’espace blanc comme non significatifs et n’inclut pas dans l' [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objet pour le littéral.</span><span class="sxs-lookup"><span data-stu-id="04822-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="04822-111">Pour inclure des espaces non significatifs dans un littéral XML, utilisez une expression incorporée qui contient un littéral de chaîne avec l’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="04822-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04822-112">Si l' `xml:space` attribut apparaît dans un littéral d’élément XML, le compilateur Visual Basic comprend l’attribut dans l' <xref:System.Xml.Linq.XElement> objet, mais l’ajout de cet attribut ne change pas la manière dont le compilateur traite les espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="04822-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="04822-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="04822-113">Examples</span></span>  
 <span data-ttu-id="04822-114">L’exemple suivant contient deux éléments XML, externes et internes.</span><span class="sxs-lookup"><span data-stu-id="04822-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="04822-115">Les deux éléments contiennent un espace blanc dans leur contenu de texte.</span><span class="sxs-lookup"><span data-stu-id="04822-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="04822-116">L’espace blanc dans l’élément externe est insignifiante, car il ne contient que des espaces blancs et un élément XML.</span><span class="sxs-lookup"><span data-stu-id="04822-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="04822-117">L’espace blanc dans l’élément interne est significatif, car il contient des espaces blancs et du texte.</span><span class="sxs-lookup"><span data-stu-id="04822-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="04822-118">Lors de l’exécution, ce code affiche le texte suivant.</span><span class="sxs-lookup"><span data-stu-id="04822-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04822-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04822-119">See also</span></span>

- [<span data-ttu-id="04822-120">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="04822-120">Creating XML in Visual Basic</span></span>](creating-xml.md)
