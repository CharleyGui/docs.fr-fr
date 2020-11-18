---
title: Utilisation de la classe XslCompiledTransform
ms.date: 03/30/2017
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: f2eae6f10cc2adf4628a0c2626617ef9a027c598
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821760"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="6c650-102">Utilisation de la classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="6c650-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="6c650-103">La classe <xref:System.Xml.Xsl.XslCompiledTransform> est le processeur XSLT dans Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c650-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="6c650-104">Cette classe est utilisée pour compiler des feuilles de style et exécuter des transformations XSLT.</span><span class="sxs-lookup"><span data-stu-id="6c650-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c650-105">Bien que les performances globales de la classe <xref:System.Xml.Xsl.XslCompiledTransform> soient meilleures que celles de la classe <xref:System.Xml.Xsl.XslTransform>, la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> de la classe <xref:System.Xml.Xsl.XslCompiledTransform> peut s'exécuter plus lentement que la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> de la classe <xref:System.Xml.Xsl.XslTransform> la première fois qu'elle est appelée pour une transformation.</span><span class="sxs-lookup"><span data-stu-id="6c650-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="6c650-106">C'est parce que le fichier XSLT doit être compilé avant d'être chargé.</span><span class="sxs-lookup"><span data-stu-id="6c650-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="6c650-107">Pour plus d'informations, consultez le billet de blog suivant : [XslCompiledTransform plus lent que XslTransform ?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform).</span><span class="sxs-lookup"><span data-stu-id="6c650-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c650-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6c650-108">In This Section</span></span>  
 [<span data-ttu-id="6c650-109">Entrées dans la classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="6c650-109">Inputs to the XslCompiledTransform Class</span></span>](inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="6c650-110">Décrit les options d'entrée XSLT disponibles.</span><span class="sxs-lookup"><span data-stu-id="6c650-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="6c650-111">Options de sortie de la classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="6c650-111">Output Options on the XslCompiledTransform Class</span></span>](output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="6c650-112">Décrit les options de sortie XSLT disponibles.</span><span class="sxs-lookup"><span data-stu-id="6c650-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="6c650-113">Résolution de ressources externes lors du traitement XSLT</span><span class="sxs-lookup"><span data-stu-id="6c650-113">Resolving External Resources During XSLT Processing</span></span>](resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="6c650-114">Présente l'utilisation de la classe <xref:System.Xml.XmlResolver> pour résoudre des ressources externes.</span><span class="sxs-lookup"><span data-stu-id="6c650-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="6c650-115">Extension de feuilles de style XSLT</span><span class="sxs-lookup"><span data-stu-id="6c650-115">Extending XSLT Style Sheets</span></span>](extending-xslt-style-sheets.md)  
 <span data-ttu-id="6c650-116">Présente la prise en charge des extensions XSLT.</span><span class="sxs-lookup"><span data-stu-id="6c650-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="6c650-117">Erreurs XSLT récupérables</span><span class="sxs-lookup"><span data-stu-id="6c650-117">Recoverable XSLT Errors</span></span>](recoverable-xslt-errors.md)|<span data-ttu-id="6c650-118">Répertorie chaque comportement discrétionnaire autorisé par la recommandation du World Wide Web Consortium (W3C) sur XSLT 1.0 et décrit la façon dont ces comportements sont gérés par la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="6c650-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="6c650-119">Procédure : transformer un fragment de nœud</span><span class="sxs-lookup"><span data-stu-id="6c650-119">How to: Transform a Node Fragment</span></span>](how-to-transform-a-node-fragment.md)|<span data-ttu-id="6c650-120">Décrit comment transformer un fragment de nœud.</span><span class="sxs-lookup"><span data-stu-id="6c650-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="6c650-121">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="6c650-121">Related Sections</span></span>  
 [<span data-ttu-id="6c650-122">Migration depuis la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="6c650-122">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="6c650-123">Explique comment migrer du code à partir de la classe <xref:System.Xml.Xsl.XslTransform></span><span class="sxs-lookup"><span data-stu-id="6c650-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c650-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c650-124">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
