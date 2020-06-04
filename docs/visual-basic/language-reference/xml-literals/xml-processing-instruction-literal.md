---
title: Littéral d’instruction de traitement XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 9bd1781e01bc4cbf1ce5da8c454ab2f5a679aead
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400174"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="55ce6-102">Littéral d'instruction de traitement XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55ce6-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="55ce6-103">Littéral représentant un <xref:System.Xml.Linq.XProcessingInstruction> objet.</span><span class="sxs-lookup"><span data-stu-id="55ce6-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55ce6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55ce6-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="55ce6-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="55ce6-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="55ce6-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="55ce6-106">Required.</span></span> <span data-ttu-id="55ce6-107">Indique le début du littéral d’instruction de traitement XML.</span><span class="sxs-lookup"><span data-stu-id="55ce6-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="55ce6-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="55ce6-108">Required.</span></span> <span data-ttu-id="55ce6-109">Nom indiquant l’application ciblée par l’instruction de traitement.</span><span class="sxs-lookup"><span data-stu-id="55ce6-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="55ce6-110">Ne peut pas commencer par « XML » ou « XML ».</span><span class="sxs-lookup"><span data-stu-id="55ce6-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="55ce6-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="55ce6-111">Optional.</span></span> <span data-ttu-id="55ce6-112">Chaîne indiquant comment l’application ciblée par `piName` doit traiter le document XML.</span><span class="sxs-lookup"><span data-stu-id="55ce6-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="55ce6-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="55ce6-113">Required.</span></span> <span data-ttu-id="55ce6-114">Indique la fin de l’instruction de traitement.</span><span class="sxs-lookup"><span data-stu-id="55ce6-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55ce6-115">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="55ce6-115">Return Value</span></span>  
 <span data-ttu-id="55ce6-116">Objet <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="55ce6-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55ce6-117">Notes</span><span class="sxs-lookup"><span data-stu-id="55ce6-117">Remarks</span></span>  
 <span data-ttu-id="55ce6-118">Les littéraux d’instruction de traitement XML indiquent comment les applications doivent traiter un document XML.</span><span class="sxs-lookup"><span data-stu-id="55ce6-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="55ce6-119">Quand une application charge un document XML, l’application peut vérifier les instructions de traitement XML pour déterminer comment traiter le document.</span><span class="sxs-lookup"><span data-stu-id="55ce6-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="55ce6-120">L’application interprète la signification de `piName` et `piData` .</span><span class="sxs-lookup"><span data-stu-id="55ce6-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="55ce6-121">Le littéral de document XML utilise une syntaxe similaire à celle de l’instruction de traitement XML.</span><span class="sxs-lookup"><span data-stu-id="55ce6-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="55ce6-122">Pour plus d’informations, consultez [littéral de document XML](xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="55ce6-122">For more information, see [XML Document Literal](xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55ce6-123">L' `piName` élément ne peut pas commencer par les chaînes « XML » ou « XML », car la spécification xml 1,0 réserve ces identificateurs.</span><span class="sxs-lookup"><span data-stu-id="55ce6-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="55ce6-124">Vous pouvez assigner un littéral d’instruction de traitement XML à une variable ou l’inclure dans un littéral de document XML.</span><span class="sxs-lookup"><span data-stu-id="55ce6-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55ce6-125">Un littéral XML peut s’étendre sur plusieurs lignes sans avoir besoin de caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="55ce6-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="55ce6-126">Cela vous permet de copier le contenu d’un document XML et de le coller directement dans un programme de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="55ce6-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="55ce6-127">Le compilateur Visual Basic convertit le littéral d’instruction de traitement XML en un appel au <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructeur.</span><span class="sxs-lookup"><span data-stu-id="55ce6-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55ce6-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="55ce6-128">Example</span></span>  
 <span data-ttu-id="55ce6-129">L’exemple suivant crée une instruction de traitement identifiant une feuille de style pour un document XML.</span><span class="sxs-lookup"><span data-stu-id="55ce6-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="55ce6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55ce6-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="55ce6-131">Littéral de document XML</span><span class="sxs-lookup"><span data-stu-id="55ce6-131">XML Document Literal</span></span>](xml-document-literal.md)
- [<span data-ttu-id="55ce6-132">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="55ce6-132">XML Literals</span></span>](index.md)
- [<span data-ttu-id="55ce6-133">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55ce6-133">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
