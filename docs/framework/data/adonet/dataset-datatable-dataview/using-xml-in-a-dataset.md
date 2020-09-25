---
title: Utilisation de XML dans un DataSet
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: e133da727887271af3bc5330a5779df4af58a37e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201185"
---
# <a name="using-xml-in-a-dataset"></a>Utilisation de XML dans un DataSet

Avec ADO.NET, vous pouvez remplir un objet <xref:System.Data.DataSet> à partir d'un flux ou d'un document XML. Vous pouvez utiliser le flux ou le document XML pour fournir à l'objet <xref:System.Data.DataSet> soit des données, soit des informations de schéma ou les deux à la fois. Les informations fournies à partir du flux ou du document XML peuvent être combinées aux données ou aux informations de schéma déjà présentes dans l'objet <xref:System.Data.DataSet>.  
  
 ADO.NET vous permet aussi de créer une représentation XML d'un objet <xref:System.Data.DataSet>, avec ou sans son schéma, afin de transporter l'objet <xref:System.Data.DataSet> sur HTTP en vue de son utilisation par une autre application ou une autre plateforme compatible XML. Dans la représentation XML d'un objet <xref:System.Data.DataSet>, les données sont écrites en XML et le schéma, s'il est inclus inline dans la représentation, est écrit en langage XSD (XML Schema Definition). XML et XSD proposent un format pratique pour le transfert du contenu d'un objet <xref:System.Data.DataSet> vers et à partir des clients distants.  
  
## <a name="in-this-section"></a>Dans cette section  

 [DiffGrams](diffgrams.md)  
 Fournit des informations sur le DiffGram, format XML utilisé pour lire et écrire le contenu d'un objet <xref:System.Data.DataSet>.  
  
 [Chargement d'un DataSet à partir de XML](loading-a-dataset-from-xml.md)  
 Présente les différentes possibilités à envisager pour le chargement du contenu d'un objet <xref:System.Data.DataSet> à partir d'un document XML.  
  
 [Écriture du contenu d'un DataSet comme données XML](writing-dataset-contents-as-xml-data.md)  
 Explique comment générer le contenu d'un objet <xref:System.Data.DataSet> sous forme de données XML et les différentes options de format XML que vous pouvez utiliser.  
  
 [Chargement des informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md)  
 Présente les méthodes <xref:System.Data.DataSet> utilisées pour charger le schéma d'un objet <xref:System.Data.DataSet> à partir de XML.  
  
 [Écriture des informations de schéma de DataSet comme XSD](writing-dataset-schema-information-as-xsd.md)  
 Présente les utilisations d'un schéma XML et explique comment en générer un à partir d'un objet <xref:System.Data.DataSet>.  
  
 [Synchronisation DataSet et XmlDataDocument](dataset-and-xmldatadocument-synchronization.md)  
 Présente la possibilité fournie par le .NET Framework d’obtenir un accès synchrone aux vues relationnelle et hiérarchique d’un même groupe de données, et explique comment créer une relation synchrone entre un objet <xref:System.Data.DataSet> et un objet <xref:System.Xml.XmlDataDocument>.  
  
 [Imbrication de DataRelations](nesting-datarelations.md)  
 Explique l'importance des objets <xref:System.Data.DataRelation> imbriqués lorsqu'il s'agit de représenter le contenu d'un objet <xref:System.Data.DataSet> sous forme de données XML, et décrit la façon de les créer.  
  
 [Dérivation de la structure relationnelle des DataSet à partir du schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Décrit la structure relationnelle, ou schéma, d'un objet <xref:System.Data.DataSet> créé à partir d'un schéma XML.  
  
 [Déduction de la structure relationnelle des DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md)  
 Décrit la structure relationnelle résultante, ou schéma, d'un objet <xref:System.Data.DataSet> créé par inférence à partir d'éléments XML.  
  
## <a name="related-sections"></a>Sections connexes  

 [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)  
 Décrit l'architecture et les composants d'ADO.NET ainsi que la façon de les utiliser pour accéder à des sources de données existantes et pour gérer des données d'application.  
  
## <a name="see-also"></a>Voir aussi

- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
