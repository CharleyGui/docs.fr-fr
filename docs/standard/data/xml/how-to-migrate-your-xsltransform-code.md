---
title: 'Procédure : migrer votre code XslTransform'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7022a0f55cd7994141148bc6b2faefb10bfea416
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966978"
---
# <a name="how-to-migrate-your-xsltransform-code"></a><span data-ttu-id="c7445-102">Procédure : migrer votre code XslTransform</span><span class="sxs-lookup"><span data-stu-id="c7445-102">How to: Migrate Your XslTransform Code</span></span>
<span data-ttu-id="c7445-103">Les nouvelles classes XSLT ont été conçues pour être très semblables aux classes existantes.</span><span class="sxs-lookup"><span data-stu-id="c7445-103">The new XSLT classes have been designed to be very similar to the existing classes.</span></span> <span data-ttu-id="c7445-104">La classe <xref:System.Xml.Xsl.XslCompiledTransform> remplace la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class replaces the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="c7445-105">Les feuilles de style sont compilées à l'aide de la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7445-105">Style sheets are compiled using the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="c7445-106">Les transformations sont exécutées à l'aide de la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7445-106">Transforms are executed using the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="c7445-107">Les procédures suivantes illustrent des tâches XSLT communes et comparent le code des classes <xref:System.Xml.Xsl.XslTransform> et <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-107">The following procedures show common XSLT tasks, and compare the code using the <xref:System.Xml.Xsl.XslTransform> class versus the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a><span data-ttu-id="c7445-108">Pour transformer un fichier et l'envoyer à un URI</span><span class="sxs-lookup"><span data-stu-id="c7445-108">To transform a file and output to a URI</span></span>  
  
- <span data-ttu-id="c7445-109">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-109">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- <span data-ttu-id="c7445-110">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-110">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a><span data-ttu-id="c7445-111">Pour compiler une feuille de style et utiliser un programme de résolution avec des informations d'identification par défaut</span><span class="sxs-lookup"><span data-stu-id="c7445-111">To compile a style sheet and use a resolver with default credentials</span></span>  
  
- <span data-ttu-id="c7445-112">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-112">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- <span data-ttu-id="c7445-113">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-113">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="c7445-114">Pour utiliser un paramètre XSLT</span><span class="sxs-lookup"><span data-stu-id="c7445-114">To use an XSLT parameter</span></span>  
  
- <span data-ttu-id="c7445-115">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-115">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- <span data-ttu-id="c7445-116">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-116">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a><span data-ttu-id="c7445-117">Pour activer les scripts XSLT</span><span class="sxs-lookup"><span data-stu-id="c7445-117">To enable XSLT scripting</span></span>  
  
- <span data-ttu-id="c7445-118">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-118">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- <span data-ttu-id="c7445-119">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-119">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a><span data-ttu-id="c7445-120">Pour charger les résultats dans un objet DOM</span><span class="sxs-lookup"><span data-stu-id="c7445-120">To load the results into a DOM object</span></span>  
  
- <span data-ttu-id="c7445-121">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-121">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- <span data-ttu-id="c7445-122">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-122">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c7445-123">La classe <xref:System.Xml.Xsl.XslCompiledTransform> n'a pas de méthode permettant de retourner les résultats de la transformation XSLT sous la forme d'un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c7445-123">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have a method that returns the XSLT transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="c7445-124">Cependant, vous pouvez envoyer la sortie vers un fichier XML et charger le fichier XML dans un autre objet.</span><span class="sxs-lookup"><span data-stu-id="c7445-124">However, you can output to an XML file and load the XML file into another object.</span></span>  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a><span data-ttu-id="c7445-125">Pour envoyer les résultats vers un autre magasin de données</span><span class="sxs-lookup"><span data-stu-id="c7445-125">To stream the results into another data store</span></span>  
  
- <span data-ttu-id="c7445-126">Code utilisant la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-126">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- <span data-ttu-id="c7445-127">Code utilisant la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="c7445-127">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="c7445-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7445-128">See also</span></span>

- [<span data-ttu-id="c7445-129">Migration depuis la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="c7445-129">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [<span data-ttu-id="c7445-130">Utilisation de la classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="c7445-130">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
