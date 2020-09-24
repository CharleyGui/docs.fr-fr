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
# <a name="sql-xml-column-values"></a><span data-ttu-id="e33d7-102">Valeurs des colonnes SQL XML</span><span class="sxs-lookup"><span data-stu-id="e33d7-102">SQL XML Column Values</span></span>

<span data-ttu-id="e33d7-103">SQL Server prend en charge le type de données `xml` et les développeurs peuvent extraire des ensembles de résultats incluant ce type à l’aide d’un comportement standard de la classe <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="e33d7-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="e33d7-104">Une colonne `xml` peut être récupérée comme n’importe quelle colonne (dans un <xref:System.Data.SqlClient.SqlDataReader>, par exemple), mais si vous souhaitez utiliser le contenu de la colonne au format XML, vous devez utiliser un <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="e33d7-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e33d7-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="e33d7-105">Example</span></span>  

 <span data-ttu-id="e33d7-106">L’application console suivante sélectionne deux lignes contenant chacune une colonne `xml` dans la table **Sales.Store** de la base de données **AdventureWorks** pour une instance de <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="e33d7-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="e33d7-107">Pour chaque ligne, la valeur de la colonne `xml` est lue à l’aide de la méthode <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> de <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="e33d7-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="e33d7-108">La valeur est stockée dans un <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="e33d7-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="e33d7-109">Notez que vous devez utiliser <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> plutôt que la méthode <xref:System.Data.IDataRecord.GetValue%2A> si vous souhaitez définir le contenu sur une variable <xref:System.Data.SqlTypes.SqlXml> ; <xref:System.Data.IDataRecord.GetValue%2A> renvoie la valeur de la colonne `xml` sous la forme d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e33d7-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e33d7-110">L’exemple de base de données **AdventureWorks** n’est pas installé par défaut quand vous installez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e33d7-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="e33d7-111">Vous pouvez l’installer en exécutant le programme d’installation de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e33d7-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e33d7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e33d7-112">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="e33d7-113">Données XML dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="e33d7-113">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)
- [<span data-ttu-id="e33d7-114">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e33d7-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
