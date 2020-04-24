---
title: Transformations XSLT sur différents magasins
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
ms.openlocfilehash: 490ac30a3e4f0c50cb5d011f1d583c6e5ce9e672
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709658"
---
# <a name="xslt-transformations-over-different-stores"></a>Transformations XSLT sur différents magasins
> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).  
  
 Les classes ADO.NET et XML du .NET Framework fournissent un modèle de programmation unifié pour accéder aux données. Ces données sont représentées à la fois comme des données XML (texte délimité par des étiquettes) et comme des données relationnelles (tableaux composés de lignes et de colonnes). Le code XML du .NET Framework lit les données XML à partir de tout flux de données dans des arborescences de nœuds DOM (Document Object Model), où les données sont accessibles par programmation, tandis qu’ADO.NET permet d’accéder à des données relationnelles et de les manipuler dans un objet <xref:System.Data.DataSet>.  
  
 Le DOM XML fournit l'accès aux données des documents XML et des classes supplémentaires pour lire et écrire des documents XML, ainsi que pour naviguer dans ceux-ci. Ces classes sont prises en charge dans l'espace de noms <xref:System.Xml> qui unifie également le DOM XML avec les services d'accès aux données fournis par ADO.NET. L'objet <xref:System.Xml.XmlDataDocument> fournit un accès relationnel aux données. L'objet <xref:System.Xml.XmlDataDocument> mappe les données XML à des données relationnelles dans un objet <xref:System.Data.DataSet> ADO.NET. Toute application .NET Framework peut utiliser les classes de l’espace de noms <xref:System.Xml> pour accéder à des documents XML et à des données relationnelles et les manipuler dans l’objet <xref:System.Xml.XmlDataDocument>. Cette implémentation prend en charge les architectures multicouches pour la collecte et la distribution de données. Pour plus d'informations, consultez [Intégration de XML aux données relationnelles et à ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Voir aussi

- [Implémentation du processeur XSLT par la classe XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
