---
title: Transformations XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: 4bbecfbf1b163a9d7bfe6957806095b5b17fbab7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709632"
---
# <a name="xslt-transformations"></a>Transformations XSLT
Les transformations XSLT (Extensible Stylesheet Language Transformation) ont pour but de transformer le contenu d'un document XML source en un autre document dont le format ou la structure diffère. Par exemple, vous pouvez utiliser XSLT pour transformer un document XML en un document HTML pour une utilisation sur un site web ou en un document qui contient uniquement les champs requis par une application. Ce processus de transformation est spécifié par la [recommandation du W3C sur XSLT (XSL Transformations) version 1.0](https://www.w3.org/TR/xslt-10/).  
  
 La classe <xref:System.Xml.Xsl.XslCompiledTransform> est le processeur XSLT dans .NET. La classe <xref:System.Xml.Xsl.XslCompiledTransform> prend en charge la [recommandation du W3C sur XSLT 1.0](https://www.w3.org/TR/xslt-10/).  
  
> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le .NET Framework version 2.0. La classe <xref:System.Xml.Xsl.XslCompiledTransform> est une nouvelle implémentation du moteur XSLT. Elle inclut des améliorations de performances et de nouvelles fonctions de sécurité. La pratique recommandée consiste à créer des applications XSLT à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Utilisation de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 Fournit des informations sur l'utilisation de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 [Migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Explique comment migrer du code à partir de la classe <xref:System.Xml.Xsl.XslTransform>.  
  
 [XSLT Compiler (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 Fournit des informations sur l'utilisation de XSLT Compiler.  
  
 [Transformations XSLT avec la classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 Fournit des informations sur l'utilisation de la classe <xref:System.Xml.Xsl.XslTransform>.  
  
## <a name="reference"></a>Référence  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a>Sections connexes  
 [Documents et données XML](../../../../docs/standard/data/xml/index.md)
