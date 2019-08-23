---
title: Littéraux de commentaires XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 91369392f33f2a86a7a4cb5ffb3faa668c113348
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965410"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="d0b38-102">Littéraux de commentaires XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0b38-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="d0b38-103">Littéral représentant un <xref:System.Xml.Linq.XComment> objet.</span><span class="sxs-lookup"><span data-stu-id="d0b38-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0b38-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0b38-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="d0b38-105">Composants</span><span class="sxs-lookup"><span data-stu-id="d0b38-105">Parts</span></span>  
  
|<span data-ttu-id="d0b38-106">Terme</span><span class="sxs-lookup"><span data-stu-id="d0b38-106">Term</span></span>|<span data-ttu-id="d0b38-107">Définition</span><span class="sxs-lookup"><span data-stu-id="d0b38-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="d0b38-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="d0b38-108">Required.</span></span> <span data-ttu-id="d0b38-109">Indique le début du commentaire XML.</span><span class="sxs-lookup"><span data-stu-id="d0b38-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="d0b38-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="d0b38-110">Required.</span></span> <span data-ttu-id="d0b38-111">Texte à afficher dans le commentaire XML.</span><span class="sxs-lookup"><span data-stu-id="d0b38-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="d0b38-112">Ne peut pas contenir une série de deux traits d’Union (--) ou se terminer par un trait d’Union adjacent à la balise de fermeture.</span><span class="sxs-lookup"><span data-stu-id="d0b38-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="d0b38-113">Requis.</span><span class="sxs-lookup"><span data-stu-id="d0b38-113">Required.</span></span> <span data-ttu-id="d0b38-114">Désigne la fin du commentaire XML.</span><span class="sxs-lookup"><span data-stu-id="d0b38-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="d0b38-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d0b38-115">Return Value</span></span>  
 <span data-ttu-id="d0b38-116">Objet <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="d0b38-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0b38-117">Notes</span><span class="sxs-lookup"><span data-stu-id="d0b38-117">Remarks</span></span>  
 <span data-ttu-id="d0b38-118">Les littéraux de commentaire XML ne contiennent pas de contenu de document; elles contiennent des informations sur le document.</span><span class="sxs-lookup"><span data-stu-id="d0b38-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="d0b38-119">La section de commentaire XML se termine par la séquence «-->».</span><span class="sxs-lookup"><span data-stu-id="d0b38-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="d0b38-120">Cela implique les points suivants:</span><span class="sxs-lookup"><span data-stu-id="d0b38-120">This implies the following points:</span></span>  
  
- <span data-ttu-id="d0b38-121">Vous ne pouvez pas utiliser une expression incorporée dans un littéral de commentaire XML, car les délimiteurs d’expressions incorporées sont du contenu de commentaire XML valide.</span><span class="sxs-lookup"><span data-stu-id="d0b38-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="d0b38-122">Les sections de commentaires XML ne peuvent pas être `content` imbriquées, car ne peut pas contenir la valeur «-->».</span><span class="sxs-lookup"><span data-stu-id="d0b38-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="d0b38-123">Vous pouvez assigner un littéral de commentaire XML à une variable, ou vous pouvez l’inclure dans un littéral d’élément XML.</span><span class="sxs-lookup"><span data-stu-id="d0b38-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0b38-124">Un littéral XML peut s’étendre sur plusieurs lignes sans utiliser de caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="d0b38-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="d0b38-125">Cette fonctionnalité vous permet de copier le contenu d’un document XML et de le coller directement dans un programme de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d0b38-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="d0b38-126">Le compilateur Visual Basic convertit le littéral de commentaire XML en un appel <xref:System.Xml.Linq.XComment.%23ctor%2A> au constructeur.</span><span class="sxs-lookup"><span data-stu-id="d0b38-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0b38-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="d0b38-127">Example</span></span>  
 <span data-ttu-id="d0b38-128">L’exemple suivant crée un commentaire XML qui contient le texte «This is a comments».</span><span class="sxs-lookup"><span data-stu-id="d0b38-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="d0b38-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0b38-129">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="d0b38-130">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="d0b38-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="d0b38-131">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="d0b38-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="d0b38-132">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0b38-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
