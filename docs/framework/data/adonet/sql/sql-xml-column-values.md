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
# <a name="sql-xml-column-values"></a><span data-ttu-id="eac43-102">Valeurs des colonnes SQL XML</span><span class="sxs-lookup"><span data-stu-id="eac43-102">SQL XML Column Values</span></span>
<span data-ttu-id="eac43-103">SQL Server prend en `xml` charge le type de données, et les développeurs peuvent récupérer des jeux de résultats incluant ce <xref:System.Data.SqlClient.SqlCommand> type à l’aide du comportement standard de la classe.</span><span class="sxs-lookup"><span data-stu-id="eac43-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="eac43-104">Une colonne `xml` peut être extraite comme toute colonne (par exemple, dans un <xref:System.Data.SqlClient.SqlDataReader>) mais si vous souhaitez utiliser le contenu de la colonne comme XML, vous devez utiliser un <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="eac43-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eac43-105">Exemples</span><span class="sxs-lookup"><span data-stu-id="eac43-105">Example</span></span>  
 <span data-ttu-id="eac43-106">L’application console suivante sélectionne deux lignes, chacune contenant une `xml` colonne, à partir de la table **Sales. Store** de la base de <xref:System.Data.SqlClient.SqlDataReader> données **AdventureWorks** vers une instance.</span><span class="sxs-lookup"><span data-stu-id="eac43-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="eac43-107">Pour chaque ligne, la valeur de la colonne `xml` est lue à l'aide de la méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> de <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="eac43-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="eac43-108">La valeur est stockée dans un <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="eac43-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="eac43-109">Notez que vous devez utiliser la méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> plutôt que la méthode <xref:System.Data.IDataRecord.GetValue%2A> si vous souhaitez définir le contenu comme une variable <xref:System.Data.SqlTypes.SqlXml> ; <xref:System.Data.IDataRecord.GetValue%2A> retourne la valeur de la colonne `xml` comme chaîne.</span><span class="sxs-lookup"><span data-stu-id="eac43-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eac43-110">L’exemple de base de données **AdventureWorks** n’est pas installé par défaut lorsque vous installez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eac43-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="eac43-111">Vous pouvez l'installer en exécutant l'Installation de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eac43-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="eac43-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eac43-112">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="eac43-113">Données XML dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="eac43-113">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)
- [<span data-ttu-id="eac43-114">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="eac43-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
