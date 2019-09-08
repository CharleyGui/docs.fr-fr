---
title: SqlTypes et le DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: dea5a2017479443cb747d31e253c1c83585ddd09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791501"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="d95e9-102">SqlTypes et le DataSet</span><span class="sxs-lookup"><span data-stu-id="d95e9-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="d95e9-103">ADO.NET 2.0 a introduit une prise en charge de type avancée du `DataSet` via l'espace de noms <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="d95e9-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="d95e9-104">Les types dans <xref:System.Data.SqlTypes> sont conçus pour fournir des types de données avec les mêmes sémantiques et précision que les types de données dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d95e9-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="d95e9-105">Chaque type de données dans <xref:System.Data.SqlTypes> a un type de données équivalent dans SQL Server, avec la même représentation de données sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="d95e9-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="d95e9-106">L'utilisation de <xref:System.Data.SqlTypes> directement dans un <xref:System.Data.DataSet> offre plusieurs avantages lors de l'utilisation de types de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d95e9-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="d95e9-107"><xref:System.Data.SqlTypes> prend en charge la même sémantique que les types de données SQL Server natifs.</span><span class="sxs-lookup"><span data-stu-id="d95e9-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="d95e9-108">La spécification de l'un des <xref:System.Data.SqlTypes> dans la définition d'un <xref:System.Data.DataColumn> élimine la perte de précision qui peut résulter de la conversion des types de données décimales ou numériques en l'un des types de données Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d95e9-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d95e9-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="d95e9-109">Example</span></span>  
 <span data-ttu-id="d95e9-110">L'exemple suivant crée un objet <xref:System.Data.DataTable>, définissant de façon explicite les types de données <xref:System.Data.DataColumn> en utilisant des <xref:System.Data.SqlTypes> au lieu de types CLR.</span><span class="sxs-lookup"><span data-stu-id="d95e9-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="d95e9-111">Le code remplit l'objet <xref:System.Data.DataTable> à l'aide de données provenant de la table Sales.SalesOrderDetail de la base de données AdventureWorks dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d95e9-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="d95e9-112">La sortie affichée dans la fenêtre de console présente le type de données de chaque colonne et les valeurs extraites de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d95e9-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d95e9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d95e9-113">See also</span></span>

- [<span data-ttu-id="d95e9-114">Mappages de types de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="d95e9-114">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="d95e9-115">Configuration des paramètres et des types de données des paramètres</span><span class="sxs-lookup"><span data-stu-id="d95e9-115">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="d95e9-116">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d95e9-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
