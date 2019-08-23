---
title: Valeurs des colonnes SQL XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 29e9ac5b95b62ef2a4467bf41484c3740d550abd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964950"
---
# <a name="sql-xml-column-values"></a>Valeurs des colonnes SQL XML
SQL Server prend en `xml` charge le type de données, et les développeurs peuvent récupérer des jeux de résultats incluant ce <xref:System.Data.SqlClient.SqlCommand> type à l’aide du comportement standard de la classe. Une colonne `xml` peut être extraite comme toute colonne (par exemple, dans un <xref:System.Data.SqlClient.SqlDataReader>) mais si vous souhaitez utiliser le contenu de la colonne comme XML, vous devez utiliser un <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Exemples  
 L’application console suivante sélectionne deux lignes, chacune contenant une `xml` colonne, à partir de la table **Sales. Store** de la base de <xref:System.Data.SqlClient.SqlDataReader> données **AdventureWorks** vers une instance. Pour chaque ligne, la valeur de la colonne `xml` est lue à l'aide de la méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> de <xref:System.Data.SqlClient.SqlDataReader>. La valeur est stockée dans un <xref:System.Xml.XmlReader>. Notez que vous devez utiliser la méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> plutôt que la méthode <xref:System.Data.IDataRecord.GetValue%2A> si vous souhaitez définir le contenu comme une variable <xref:System.Data.SqlTypes.SqlXml> ; <xref:System.Data.IDataRecord.GetValue%2A> retourne la valeur de la colonne `xml` comme chaîne.  
  
> [!NOTE]
> L’exemple de base de données **AdventureWorks** n’est pas installé par défaut lorsque vous installez SQL Server. Vous pouvez l'installer en exécutant l'Installation de SQL Server.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.SqlTypes.SqlXml>
- [Données XML dans SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
