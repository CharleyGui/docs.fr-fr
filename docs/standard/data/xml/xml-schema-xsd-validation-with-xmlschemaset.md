---
title: Validation de schéma XML (XSD) avec XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 34215c2b06db08a74b5b9c13589ac84f26a2ef8f
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158578"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="1b146-102">Validation de schéma XML (XSD) avec XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="1b146-102">XML schema (XSD) validation with XmlSchemaSet</span></span>

<span data-ttu-id="1b146-103">Les documents XML peuvent être validés par rapport à un schéma XSD (XML Schema Definition) dans un objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="1b146-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validate-xml-documents"></a><span data-ttu-id="1b146-104">Valider des documents XML</span><span class="sxs-lookup"><span data-stu-id="1b146-104">Validate XML documents</span></span>  
 <span data-ttu-id="1b146-105">Les documents XML sont validés par la méthode <xref:System.Xml.XmlReader.Create%2A> de la classe <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="1b146-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="1b146-106">Pour valider un document XML, vous construisez un objet <xref:System.Xml.XmlReaderSettings> qui contient un schéma de langage XSD (XML Schema Definition) permettant de valider le document XML.</span><span class="sxs-lookup"><span data-stu-id="1b146-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b146-107">L’espace de noms <xref:System.Xml.Schema> contient des méthodes d’extension qui facilitent la validation d’une arborescence XML par rapport à un fichier XSD en cas d’utilisation de [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) et [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1b146-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="1b146-108">Pour plus d’informations sur la validation de documents XML avec LINQ to XML, consultez [Comment valider à l’aide de XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) et [Comment : valider à l’aide de XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1b146-108">For more information on validating XML documents with LINQ to XML, see [How to validate using XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and [How to: Validate Using XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).</span></span>
  
 <span data-ttu-id="1b146-109">Vous pouvez ajouter un schéma individuel ou un jeu de schémas (sous forme de <xref:System.Xml.Schema.XmlSchemaSet>) à un <xref:System.Xml.Schema.XmlSchemaSet> en le passant en tant que paramètre à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="1b146-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="1b146-110">Lors de la validation d’un document, l’espace de noms cible du document doit correspondre à l’espace de noms cible du schéma dans le jeu de schémas.</span><span class="sxs-lookup"><span data-stu-id="1b146-110">When validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="1b146-111">Voici un exemple de document XML.</span><span class="sxs-lookup"><span data-stu-id="1b146-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="1b146-112">Voici le schéma qui valide l'exemple de document XML.</span><span class="sxs-lookup"><span data-stu-id="1b146-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="1b146-113">Dans l'exemple de code suivant, le schéma ci-dessus est ajouté à la propriété <xref:System.Xml.XmlReaderSettings.Schemas%2A> de l'objet  de l'objet <xref:System.Xml.XmlReaderSettings>.</span><span class="sxs-lookup"><span data-stu-id="1b146-113">In the code example that follows, the schema above is added to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="1b146-114">L'objet <xref:System.Xml.XmlReaderSettings> est passé sous forme de paramètre à la méthode <xref:System.Xml.XmlReader.Create%2A> de l'objet <xref:System.Xml.XmlReader> qui valide le document XML ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="1b146-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="1b146-115">La propriété <xref:System.Xml.XmlReaderSettings.ValidationType%2A> de l’objet <xref:System.Xml.XmlReaderSettings> est définie sur `Schema` pour effectuer la validation du document XML par la méthode <xref:System.Xml.XmlReader.Create%2A> de l’objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="1b146-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="1b146-116">Un objet <xref:System.Xml.Schema.ValidationEventHandler> est ajouté à l’objet <xref:System.Xml.XmlReaderSettings> pour gérer tous les événements <xref:System.Xml.Schema.XmlSeverityType.Warning> ou <xref:System.Xml.Schema.XmlSeverityType.Error> déclenchés par des erreurs trouvées lors du processus de validation du document et du schéma XML.</span><span class="sxs-lookup"><span data-stu-id="1b146-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example #1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1b146-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b146-117">See also</span></span>

- [<span data-ttu-id="1b146-118">XmlSchemaSet pour la compilation de schémas</span><span class="sxs-lookup"><span data-stu-id="1b146-118">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="1b146-119">Utilisation de schémas XML</span><span class="sxs-lookup"><span data-stu-id="1b146-119">Working with XML Schemas</span></span>](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
