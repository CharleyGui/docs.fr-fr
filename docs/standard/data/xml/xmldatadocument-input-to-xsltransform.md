---
title: Entrée XmlDataDocument dans XslTransform
ms.date: 03/30/2017
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
ms.openlocfilehash: 96ce5176b83a6dfcb9af29b55f4e5052915dba93
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721944"
---
# <a name="xmldatadocument-input-to-xsltransform"></a>Entrée XmlDataDocument dans XslTransform

> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](migrating-from-the-xsltransform-class.md).  
  
 Microsoft .NET Framework implémente le modèle DOM (Document Object Model) XML pour fournir l’accès aux données des documents XML et des classes supplémentaires pour lire et écrire des documents XML, ainsi que pour naviguer dans ceux-ci. La classe <xref:System.Xml.XmlDataDocument>, située dans l'espace de noms <xref:System.Xml>, fournit un accès relationnel aux données grâce à sa capacité de synchronisation avec les données relationnelles contenues dans le <xref:System.Data.DataSet>. Vous pouvez afficher et manipuler simultanément un document XML structuré par l'intermédiaire de la représentation relationnelle de l'objet <xref:System.Data.DataSet> ou manipuler le document XML semi-structuré par l'intermédiaire de la représentation DOM de l'objet <xref:System.Xml.XmlDataDocument>. C'est pourquoi l'objet <xref:System.Xml.XmlDataDocument> dépasse les limites des mondes XML et relationnels.  
  
 Si les données sont stockées dans une structure relationnelle et que vous souhaitez qu'elles soient une entrée dans une transformation XSLT, vous pouvez charger les données relationnelles dans un objet <xref:System.Data.DataSet> et les associer à l'objet <xref:System.Xml.XmlDataDocument>. L'objet <xref:System.Xml.XPath.XPathNavigator>, l'entrée dans l'objet <xref:System.Xml.Xsl.XslTransform>, est implémenté sur l'objet <xref:System.Xml.XmlDataDocument> à l'aide de l'interface <xref:System.Xml.XPath.IXPathNavigable>. En prenant des données relationnelles, en les chargeant dans un objet <xref:System.Data.DataSet> et en utilisant la synchronisation dans l'objet <xref:System.Xml.XmlDataDocument>, il est à présent possible d'effectuer des transformations XSLT sur des données relationnelles.  
  
 Pour plus d'informations sur l'application d'une transformation aux données relationnelles, consultez [Application d'une transformation XSLT à un DataSet](../../../framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDataDocument>
- [Synchronisation DataSet et XmlDataDocument](../../../framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [Transformations XSLT avec la classe XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Implémentation du processeur XSLT par la classe XslTransform](xsltransform-class-implements-the-xslt-processor.md)
- [XPathNavigator dans les transformations](xpathnavigator-in-transformations.md)
- [XPathNodeIterator dans les transformations](xpathnodeiterator-in-transformations.md)
- [Entrée XPathDocument dans XslTransform](xpathdocument-input-to-xsltransform.md)
- [Entrée XmlDocument dans XslTransform](xmldocument-input-to-xsltransform.md)
