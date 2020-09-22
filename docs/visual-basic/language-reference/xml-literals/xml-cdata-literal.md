---
title: Littéral CDATA XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 4447ad6cf0fb251b0d2d1387c109b06d32f69cb8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866098"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="06df7-102">Littéral CDATA XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06df7-102">XML CDATA Literal (Visual Basic)</span></span>

<span data-ttu-id="06df7-103">Littéral représentant un <xref:System.Xml.Linq.XCData> objet.</span><span class="sxs-lookup"><span data-stu-id="06df7-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06df7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06df7-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="06df7-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="06df7-105">Parts</span></span>  

 `<![CDATA[`  
 <span data-ttu-id="06df7-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="06df7-106">Required.</span></span> <span data-ttu-id="06df7-107">Indique le début de la section CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="06df7-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="06df7-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="06df7-108">Required.</span></span> <span data-ttu-id="06df7-109">Contenu de texte à afficher dans la section CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="06df7-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="06df7-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="06df7-110">Required.</span></span> <span data-ttu-id="06df7-111">Indique la fin de la section.</span><span class="sxs-lookup"><span data-stu-id="06df7-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06df7-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="06df7-112">Return Value</span></span>  

 <span data-ttu-id="06df7-113">Objet <xref:System.Xml.Linq.XCData>.</span><span class="sxs-lookup"><span data-stu-id="06df7-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06df7-114">Notes</span><span class="sxs-lookup"><span data-stu-id="06df7-114">Remarks</span></span>  

 <span data-ttu-id="06df7-115">Les sections CDATA XML contiennent du texte brut qui doit être inclus, mais pas analysé, avec le code XML qui le contient.</span><span class="sxs-lookup"><span data-stu-id="06df7-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="06df7-116">Une section CDATA XML peut contenir n’importe quel texte.</span><span class="sxs-lookup"><span data-stu-id="06df7-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="06df7-117">Cela comprend les caractères XML réservés.</span><span class="sxs-lookup"><span data-stu-id="06df7-117">This includes reserved XML characters.</span></span> <span data-ttu-id="06df7-118">La section CDATA XML se termine par la séquence « ]] > ».</span><span class="sxs-lookup"><span data-stu-id="06df7-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="06df7-119">Cela implique les points suivants :</span><span class="sxs-lookup"><span data-stu-id="06df7-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="06df7-120">Vous ne pouvez pas utiliser une expression incorporée dans un littéral CDATA XML, car les délimiteurs d’expressions incorporées sont du contenu CDATA XML valide.</span><span class="sxs-lookup"><span data-stu-id="06df7-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="06df7-121">Les sections CDATA XML ne peuvent pas être imbriquées, car `content` ne peut pas contenir la valeur "]] >".</span><span class="sxs-lookup"><span data-stu-id="06df7-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="06df7-122">Vous pouvez assigner un littéral CDATA XML à une variable ou l’inclure dans un littéral d’élément XML.</span><span class="sxs-lookup"><span data-stu-id="06df7-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06df7-123">Un littéral XML peut s’étendre sur plusieurs lignes, mais n’utilise pas de caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="06df7-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="06df7-124">Cela vous permet de copier le contenu d’un document XML et de le coller directement dans un programme de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="06df7-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="06df7-125">Le compilateur Visual Basic convertit le littéral CDATA XML en un appel au <xref:System.Xml.Linq.XCData.%23ctor%2A> constructeur.</span><span class="sxs-lookup"><span data-stu-id="06df7-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06df7-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="06df7-126">Example</span></span>  

 <span data-ttu-id="06df7-127">L’exemple suivant crée une section CDATA qui contient le texte « peut contenir des \<XML> balises littérales ».</span><span class="sxs-lookup"><span data-stu-id="06df7-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="06df7-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06df7-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="06df7-129">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="06df7-129">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="06df7-130">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="06df7-130">XML Literals</span></span>](index.md)
- [<span data-ttu-id="06df7-131">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06df7-131">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
