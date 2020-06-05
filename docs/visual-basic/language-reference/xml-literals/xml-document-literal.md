---
title: Littéral de document XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: 3a2182d2937827bc8dc45e22307a3668420261a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400200"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="f2f23-102">Littéral de document XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2f23-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="f2f23-103">Littéral représentant un <xref:System.Xml.Linq.XDocument> objet.</span><span class="sxs-lookup"><span data-stu-id="f2f23-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2f23-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="f2f23-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="f2f23-105">Parts</span></span>  
  
|<span data-ttu-id="f2f23-106">Terme</span><span class="sxs-lookup"><span data-stu-id="f2f23-106">Term</span></span>|<span data-ttu-id="f2f23-107">Définition</span><span class="sxs-lookup"><span data-stu-id="f2f23-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="f2f23-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f2f23-108">Optional.</span></span> <span data-ttu-id="f2f23-109">Texte littéral déclarant l’encodage utilisé par le document.</span><span class="sxs-lookup"><span data-stu-id="f2f23-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="f2f23-110">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f2f23-110">Optional.</span></span> <span data-ttu-id="f2f23-111">Texte littéral.</span><span class="sxs-lookup"><span data-stu-id="f2f23-111">Literal text.</span></span> <span data-ttu-id="f2f23-112">Doit être « oui » ou « non ».</span><span class="sxs-lookup"><span data-stu-id="f2f23-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="f2f23-113">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f2f23-113">Optional.</span></span> <span data-ttu-id="f2f23-114">Liste d’instructions de traitement XML et de commentaires XML.</span><span class="sxs-lookup"><span data-stu-id="f2f23-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="f2f23-115">Prend le format suivant :</span><span class="sxs-lookup"><span data-stu-id="f2f23-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="f2f23-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="f2f23-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="f2f23-117">Chaque `piComment` peut être l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f2f23-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="f2f23-118">-   [Littéral d’instruction de traitement XML](xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="f2f23-118">-   [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="f2f23-119">-   [Littéral de commentaire XML](xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="f2f23-119">-   [XML Comment Literal](xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="f2f23-120">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f2f23-120">Required.</span></span> <span data-ttu-id="f2f23-121">Élément racine du document.</span><span class="sxs-lookup"><span data-stu-id="f2f23-121">Root element of the document.</span></span> <span data-ttu-id="f2f23-122">Le format est l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f2f23-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="f2f23-123">[Littéral d’élément XML](xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="f2f23-123">[XML Element Literal](xml-element-literal.md).</span></span></li><li><span data-ttu-id="f2f23-124">Expression incorporée du formulaire `<%=` `elementExp` `%>` .</span><span class="sxs-lookup"><span data-stu-id="f2f23-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="f2f23-125">Le `elementExp` retourne l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f2f23-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="f2f23-126">Objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f2f23-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="f2f23-127">Collection qui contient un <xref:System.Xml.Linq.XElement> objet et un nombre quelconque d' <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment> objets et.</span><span class="sxs-lookup"><span data-stu-id="f2f23-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="f2f23-128">Pour plus d’informations, consultez [expressions incorporées en XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f2f23-128">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="f2f23-129">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f2f23-129">Return Value</span></span>  
 <span data-ttu-id="f2f23-130">Objet <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="f2f23-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2f23-131">Notes</span><span class="sxs-lookup"><span data-stu-id="f2f23-131">Remarks</span></span>  
 <span data-ttu-id="f2f23-132">Un littéral de document XML est identifié par la déclaration XML au début du littéral.</span><span class="sxs-lookup"><span data-stu-id="f2f23-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="f2f23-133">Bien que chaque littéral de document XML doive avoir un seul élément XML racine, il peut contenir un nombre quelconque d’instructions de traitement XML et de commentaires XML.</span><span class="sxs-lookup"><span data-stu-id="f2f23-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="f2f23-134">Un littéral de document XML ne peut pas apparaître dans un élément XML.</span><span class="sxs-lookup"><span data-stu-id="f2f23-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2f23-135">Un littéral XML peut s’étendre sur plusieurs lignes sans utiliser de caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="f2f23-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="f2f23-136">Cela vous permet de copier le contenu d’un document XML et de le coller directement dans un programme de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f2f23-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="f2f23-137">Le compilateur Visual Basic convertit le littéral de document XML en appels <xref:System.Xml.Linq.XDocument.%23ctor%2A> aux <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructeurs et.</span><span class="sxs-lookup"><span data-stu-id="f2f23-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2f23-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="f2f23-138">Example</span></span>  
 <span data-ttu-id="f2f23-139">L’exemple suivant crée un document XML qui a une déclaration XML, une instruction de traitement, un commentaire et un élément qui contient un autre élément.</span><span class="sxs-lookup"><span data-stu-id="f2f23-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="f2f23-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2f23-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="f2f23-141">Littéral d’instruction de traitement XML</span><span class="sxs-lookup"><span data-stu-id="f2f23-141">XML Processing Instruction Literal</span></span>](xml-processing-instruction-literal.md)
- [<span data-ttu-id="f2f23-142">Littéral de commentaires XML</span><span class="sxs-lookup"><span data-stu-id="f2f23-142">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="f2f23-143">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="f2f23-143">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="f2f23-144">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="f2f23-144">XML Literals</span></span>](index.md)
- [<span data-ttu-id="f2f23-145">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f2f23-145">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="f2f23-146">Expressions incorporées en XML</span><span class="sxs-lookup"><span data-stu-id="f2f23-146">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
