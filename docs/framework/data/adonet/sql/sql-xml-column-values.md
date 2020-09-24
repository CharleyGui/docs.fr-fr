---
title: Valeurs des colonnes SQL XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: cd55e2263d4b71fe62910ac918e331ebe37833eb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177278"
---
# <a name="sql-xml-column-values"></a>Valeurs des colonnes SQL XML

SQL Server prend en charge le type de données `xml` et les développeurs peuvent extraire des ensembles de résultats incluant ce type à l’aide d’un comportement standard de la classe <xref:System.Data.SqlClient.SqlCommand>. Une colonne `xml` peut être récupérée comme n’importe quelle colonne (dans un <xref:System.Data.SqlClient.SqlDataReader>, par exemple), mais si vous souhaitez utiliser le contenu de la colonne au format XML, vous devez utiliser un <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Exemple  

 L’application console suivante sélectionne deux lignes contenant chacune une colonne `xml` dans la table **Sales.Store** de la base de données **AdventureWorks** pour une instance de <xref:System.Data.SqlClient.SqlDataReader>. Pour chaque ligne, la valeur de la colonne `xml` est lue à l’aide de la méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> de <xref:System.Data.SqlClient.SqlDataReader>. La valeur est stockée dans un <xref:System.Xml.XmlReader>. Notez que vous devez utiliser <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> plutôt que la méthode <xref:System.Data.IDataRecord.GetValue%2A> si vous souhaitez définir le contenu sur une variable <xref:System.Data.SqlTypes.SqlXml> ; <xref:System.Data.IDataRecord.GetValue%2A> renvoie la valeur de la colonne `xml` sous la forme d’une chaîne.  
  
> [!NOTE]
> L’exemple de base de données **AdventureWorks** n’est pas installé par défaut quand vous installez SQL Server. Vous pouvez l’installer en exécutant le programme d’installation de SQL Server.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.SqlTypes.SqlXml>
- [Données XML dans SQL Server](xml-data-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
