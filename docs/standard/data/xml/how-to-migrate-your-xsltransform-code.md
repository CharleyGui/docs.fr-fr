---
title: 'Procédure : migrer votre code XslTransform'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
ms.openlocfilehash: 2bc5cbc1b0857a82d3b0a11f05a4eb5756724546
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710841"
---
# <a name="how-to-migrate-your-xsltransform-code"></a><span data-ttu-id="03f03-102">Procédure : migrer votre code XslTransform</span><span class="sxs-lookup"><span data-stu-id="03f03-102">How to: Migrate Your XslTransform Code</span></span>
<span data-ttu-id="03f03-103">Les nouvelles classes XSLT ont été conçues pour être très semblables aux classes existantes.</span><span class="sxs-lookup"><span data-stu-id="03f03-103">The new XSLT classes have been designed to be very similar to the existing classes.</span></span> <span data-ttu-id="03f03-104">La classe <xref:System.Xml.Xsl.XslCompiledTransform> remplace la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class replaces the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="03f03-105">Les feuilles de style sont compilées à l'aide de la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="03f03-105">Style sheets are compiled using the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="03f03-106">Les transformations sont exécutées à l'aide de la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="03f03-106">Transforms are executed using the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="03f03-107">Les procédures suivantes illustrent des tâches XSLT communes et comparent le code des classes <xref:System.Xml.Xsl.XslTransform> et <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-107">The following procedures show common XSLT tasks, and compare the code using the <xref:System.Xml.Xsl.XslTransform> class versus the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a><span data-ttu-id="03f03-108">Pour transformer un fichier et l'envoyer à un URI</span><span class="sxs-lookup"><span data-stu-id="03f03-108">To transform a file and output to a URI</span></span>  
  
- <span data-ttu-id="03f03-109">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-109">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- <span data-ttu-id="03f03-110">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-110">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a><span data-ttu-id="03f03-111">Pour compiler une feuille de style et utiliser un programme de résolution avec des informations d'identification par défaut</span><span class="sxs-lookup"><span data-stu-id="03f03-111">To compile a style sheet and use a resolver with default credentials</span></span>  
  
- <span data-ttu-id="03f03-112">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-112">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- <span data-ttu-id="03f03-113">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-113">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="03f03-114">Pour utiliser un paramètre XSLT</span><span class="sxs-lookup"><span data-stu-id="03f03-114">To use an XSLT parameter</span></span>  
  
- <span data-ttu-id="03f03-115">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-115">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- <span data-ttu-id="03f03-116">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-116">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a><span data-ttu-id="03f03-117">Pour activer les scripts XSLT</span><span class="sxs-lookup"><span data-stu-id="03f03-117">To enable XSLT scripting</span></span>  
  
- <span data-ttu-id="03f03-118">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-118">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- <span data-ttu-id="03f03-119">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-119">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a><span data-ttu-id="03f03-120">Pour charger les résultats dans un objet DOM</span><span class="sxs-lookup"><span data-stu-id="03f03-120">To load the results into a DOM object</span></span>  
  
- <span data-ttu-id="03f03-121">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-121">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- <span data-ttu-id="03f03-122">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-122">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="03f03-123">La classe <xref:System.Xml.Xsl.XslCompiledTransform> n'a pas de méthode permettant de retourner les résultats de la transformation XSLT sous la forme d'un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="03f03-123">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have a method that returns the XSLT transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="03f03-124">Cependant, vous pouvez envoyer la sortie vers un fichier XML et charger le fichier XML dans un autre objet.</span><span class="sxs-lookup"><span data-stu-id="03f03-124">However, you can output to an XML file and load the XML file into another object.</span></span>  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a><span data-ttu-id="03f03-125">Pour envoyer les résultats vers un autre magasin de données</span><span class="sxs-lookup"><span data-stu-id="03f03-125">To stream the results into another data store</span></span>  
  
- <span data-ttu-id="03f03-126">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-126">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- <span data-ttu-id="03f03-127">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="03f03-127">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="03f03-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03f03-128">See also</span></span>

- [<span data-ttu-id="03f03-129">Migration depuis la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="03f03-129">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [<span data-ttu-id="03f03-130">Utilisation de la classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="03f03-130">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
