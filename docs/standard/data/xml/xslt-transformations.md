---
title: Transformations XSLT
ms.date: 03/30/2017
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: 686b2d454eda99095bcb335c8b0edba9ecf2e304
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685056"
---
# <a name="xslt-transformations"></a><span data-ttu-id="0f77d-102">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="0f77d-102">XSLT Transformations</span></span>

<span data-ttu-id="0f77d-103">Les transformations XSLT (Extensible Stylesheet Language Transformation) ont pour but de transformer le contenu d'un document XML source en un autre document dont le format ou la structure diffère.</span><span class="sxs-lookup"><span data-stu-id="0f77d-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="0f77d-104">Par exemple, vous pouvez utiliser XSLT pour transformer un document XML en un document HTML pour une utilisation sur un site web ou en un document qui contient uniquement les champs requis par une application.</span><span class="sxs-lookup"><span data-stu-id="0f77d-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="0f77d-105">Ce processus de transformation est spécifié par la [recommandation du W3C sur XSLT (XSL Transformations) version 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="0f77d-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="0f77d-106">La classe <xref:System.Xml.Xsl.XslCompiledTransform> est le processeur XSLT dans .NET.</span><span class="sxs-lookup"><span data-stu-id="0f77d-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="0f77d-107">La classe <xref:System.Xml.Xsl.XslCompiledTransform> prend en charge la [recommandation du W3C sur XSLT 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="0f77d-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f77d-108">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="0f77d-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="0f77d-109">La classe <xref:System.Xml.Xsl.XslCompiledTransform> est une nouvelle implémentation du moteur XSLT.</span><span class="sxs-lookup"><span data-stu-id="0f77d-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="0f77d-110">Elle inclut des améliorations de performances et de nouvelles fonctions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0f77d-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="0f77d-111">La pratique recommandée consiste à créer des applications XSLT à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="0f77d-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f77d-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0f77d-112">In This Section</span></span>  

 [<span data-ttu-id="0f77d-113">Utilisation de la classe XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="0f77d-113">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="0f77d-114">Fournit des informations sur l'utilisation de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="0f77d-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="0f77d-115">Migration depuis la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="0f77d-115">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="0f77d-116">Explique comment migrer du code à partir de la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="0f77d-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="0f77d-117">XSLT Compiler (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="0f77d-117">XSLT Compiler (xsltc.exe)</span></span>](xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="0f77d-118">Fournit des informations sur l'utilisation de XSLT Compiler.</span><span class="sxs-lookup"><span data-stu-id="0f77d-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="0f77d-119">Transformations XSLT avec la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="0f77d-119">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="0f77d-120">Fournit des informations sur l'utilisation de la classe <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="0f77d-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0f77d-121">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="0f77d-121">Reference</span></span>  

 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="0f77d-122">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="0f77d-122">Related Sections</span></span>  

 [<span data-ttu-id="0f77d-123">Documents et données XML</span><span class="sxs-lookup"><span data-stu-id="0f77d-123">XML Documents and Data</span></span>](index.md)
