---
title: Sorties à partir de XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f51a657135d9e22d960743b428057e13c1b23804
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590362"
---
# <a name="outputs-from-an-xsltransform"></a>Sorties à partir de XslTransform
Dans la mesure où les feuilles de style peuvent déterminer le format de sortie à l'aide d'une instruction `<xsl:output>` avec l'attribut `method`, le tableau suivant décrit le format de sortie lors de l'utilisation de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> pour écrire la sortie, et le format de sortie est déclaré en tant qu'objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter>.  
  
> [!NOTE]
>  La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).  
  
 Dans la mesure où les feuilles de style peuvent déterminer le format de sortie à l'aide d'une instruction `<xsl:output>` avec l'attribut `method`, le tableau suivant décrit le format de sortie lors de l'utilisation de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> pour écrire la sortie, et le format de sortie est déclaré en tant qu'objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter>. Le tableau suivant décrit ce qui se produit lorsqu'un type de sortie est déclaré par la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> conjointement à l'utilisation d'une instruction `<xsl:output>` :  
  
|méthode \<xsl:output = > attribut|Format du résultat|  
|-----------------------------------------|-------------------|  
|method="xml"|XML|  
|method="html"|HTML|  
|method="text"|Texte|  
  
> [!NOTE]
>  Remarque : L’instruction `<xsl:output>` est ignorée quand la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter>.  
  
 Les attributs suivants sont pris en charge lorsque la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter> :  
  
- encoding*  
  
- omit-xml-declaration  
  
- autonomes  
  
- doctype-public  
  
- doctype-system  
  
- cdata-section-elements  
  
- indent  
  
    > [!NOTE]
    >  *l'attribut encoding est ignoré lorsque la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> envoie sa sortie à un objet <xref:System.IO.TextWriter>. La propriété encoding sur l'objet <xref:System.IO.TextWriter> est utilisée à la place.  
  
 Les attributs suivants sont ignorés lorsque la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.IO.Stream> :  
  
- version : la version est toujours 1.0 ;  
  
- media-type : le type de média.  
  
## <a name="escaping-special-characters"></a>Échappement de caractères spéciaux  
 La balise `<xsl:text disable-output-escaping>` est utilisée pour indiquer si des caractères spéciaux doivent ou non être placés dans une séquence d'échappement dans un formulaire XML (par exemple, en substituant `<&lt>` au symbole `"<"`) ou laissés tels quels. L'attribut `disable-output-escaping` est ignoré lors de la transformation en un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter> et n'a pas d'effet sur les caractères spéciaux.  
  
## <a name="see-also"></a>Voir aussi

- [Implémentation du processeur XSLT par la classe XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
