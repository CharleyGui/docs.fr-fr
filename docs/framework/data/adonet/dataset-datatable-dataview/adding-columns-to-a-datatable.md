---
title: Ajout de colonnes à un DataTable
description: Un DataTable contient des objets DataColumn référencés par la propriété Columns de la table. Utilisez cet exemple de code pour ajouter des colonnes à une table dans ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 9d6d21696acd7a6b63cfd6d2ea7e906ec2acd7c9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286945"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="8620c-104">Ajout de colonnes à un DataTable</span><span class="sxs-lookup"><span data-stu-id="8620c-104">Adding Columns to a DataTable</span></span>
<span data-ttu-id="8620c-105">Un <xref:System.Data.DataTable> objet contient une collection d' <xref:System.Data.DataColumn> objets référencés par la propriété **Columns** de la table.</span><span class="sxs-lookup"><span data-stu-id="8620c-105">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="8620c-106">Cette collection de colonnes, ainsi que toute contrainte, définit le schéma, ou structure, de la table.</span><span class="sxs-lookup"><span data-stu-id="8620c-106">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="8620c-107">Vous créez des objets **DataColumn** dans une table en utilisant le constructeur **DataColumn** ou en appelant la méthode **Add** de la propriété **Columns** de la table, qui est un <xref:System.Data.DataColumnCollection> .</span><span class="sxs-lookup"><span data-stu-id="8620c-107">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="8620c-108">La méthode **Add** accepte les arguments facultatifs **ColumnName**, **DataType**et **expression** et crée un nouveau **DataColumn** en tant que membre de la collection.</span><span class="sxs-lookup"><span data-stu-id="8620c-108">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="8620c-109">Il accepte également un objet **DataColumn** existant, l’ajoute à la collection et retourne une référence au **DataColumn** ajouté, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="8620c-109">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="8620c-110">Étant donné que les objets **DataTable** ne sont pas spécifiques à une source de données, les types .NET Framework sont utilisés lors de la spécification du type de données d’un **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="8620c-110">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="8620c-111">L’exemple suivant ajoute quatre colonnes à un **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="8620c-111">The following example adds four columns to a **DataTable**.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 <span data-ttu-id="8620c-112">Dans l’exemple, remarquez que les propriétés de la colonne **CustID** sont définies de façon à ne pas autoriser les valeurs **DBNull** et à contraindre les valeurs à être uniques.</span><span class="sxs-lookup"><span data-stu-id="8620c-112">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="8620c-113">Toutefois, si vous définissez la colonne **CustID** comme colonne de clé primaire de la table, la propriété **AllowDBNull** prend automatiquement la valeur **false** et la propriété **unique** prend automatiquement la valeur **true**.</span><span class="sxs-lookup"><span data-stu-id="8620c-113">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="8620c-114">Pour plus d’informations, consultez [définition des clés primaires](defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="8620c-114">For more information, see [Defining Primary Keys](defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="8620c-115">Si un nom de colonne n’est pas fourni pour une colonne, la colonne reçoit un nom incrémentiel par défaut de colonne*N,* commençant par « Column1 », lorsqu’il est ajouté au **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="8620c-115">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="8620c-116">Nous vous recommandons d’éviter la Convention d’affectation de noms « column*N*» lorsque vous fournissez un nom de colonne, car le nom que vous fournissez peut être en conflit avec un nom de colonne par défaut existant dans le **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="8620c-116">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="8620c-117">Si le nom fourni existe déjà, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="8620c-117">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="8620c-118">Si vous utilisez <xref:System.Xml.Linq.XElement> en tant que <xref:System.Data.DataColumn.DataType%2A> d'un <xref:System.Data.DataColumn> dans <xref:System.Data.DataTable>, la sérialisation XML ne fonctionnera pas lors de la lecture dans les données.</span><span class="sxs-lookup"><span data-stu-id="8620c-118">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="8620c-119">Par exemple, si vous écrivez un <xref:System.Xml.XmlDocument> à l'aide de la méthode `DataTable.WriteXml`, lors de la sérialisation vers XML, un nœud parent supplémentaire est ajouté dans le <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="8620c-119">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="8620c-120">Pour contourner ce problème, utilisez le type <xref:System.Data.SqlTypes.SqlXml> à la place de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="8620c-120">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="8620c-121">`ReadXml` et `WriteXml` fonctionnent correctement avec <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="8620c-121">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8620c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8620c-122">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="8620c-123">Définition de schéma de DataTable</span><span class="sxs-lookup"><span data-stu-id="8620c-123">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="8620c-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="8620c-124">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="8620c-125">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8620c-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
