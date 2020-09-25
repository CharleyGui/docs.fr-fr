---
title: Création d'un DataTable
description: Apprenez à créer un DataTable dans ADO.NET, qui représente une table de données relationnelles en mémoire, à utiliser indépendamment ou par d’autres objets .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 75c9bcf0e0b6180030825b4d1e7dd9e1f9686712
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198637"
---
# <a name="creating-a-datatable"></a><span data-ttu-id="9b846-103">Création d'un DataTable</span><span class="sxs-lookup"><span data-stu-id="9b846-103">Creating a DataTable</span></span>

<span data-ttu-id="9b846-104">Un objet <xref:System.Data.DataTable>, qui représente une table de données relationnelles en mémoire, peut être créé et utilisé de façon indépendante. Il peut également être utilisé par d'autres objets .NET Framework, la plupart du temps comme membre d'un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="9b846-104">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="9b846-105">Vous pouvez créer un objet **DataTable** à l’aide du constructeur **DataTable** approprié.</span><span class="sxs-lookup"><span data-stu-id="9b846-105">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="9b846-106">Vous pouvez l’ajouter au **DataSet** à l’aide de la méthode **Add** pour l’ajouter à la collection **tables** de l’objet **DataTable** .</span><span class="sxs-lookup"><span data-stu-id="9b846-106">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="9b846-107">Vous pouvez également créer des objets **DataTable** dans un **DataSet** à l’aide des méthodes **Fill** ou **FillSchema** de l’objet **DataAdapter** , ou à partir d’un schéma XML prédéfini ou inféré à l’aide des méthodes **ReadXml**, **ReadXmlSchema**ou **InferXmlSchema** du **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="9b846-107">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="9b846-108">Notez qu’une fois que vous avez ajouté un **DataTable** comme membre de la collection **tables** d’un **DataSet**, vous ne pouvez pas l’ajouter à la collection de tables d’un autre **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="9b846-108">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="9b846-109">Quand vous créez un **DataTable**pour la première fois, il n’a pas de schéma (c’est-à-dire une structure).</span><span class="sxs-lookup"><span data-stu-id="9b846-109">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="9b846-110">Pour définir le schéma de la table, vous devez créer et ajouter des <xref:System.Data.DataColumn> objets à la collection **Columns** de la table.</span><span class="sxs-lookup"><span data-stu-id="9b846-110">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="9b846-111">Vous pouvez également définir une colonne de clé primaire pour la table et créer et ajouter des objets de **contrainte** à la collection **Constraints** de la table.</span><span class="sxs-lookup"><span data-stu-id="9b846-111">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="9b846-112">Après avoir défini le schéma d’un **DataTable**, vous pouvez ajouter des lignes de données à la table en ajoutant des objets **DataRow** à la collection **Rows** de la table.</span><span class="sxs-lookup"><span data-stu-id="9b846-112">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="9b846-113">Vous n’êtes pas obligé de fournir une valeur pour la <xref:System.Data.DataTable.TableName%2A> propriété lorsque vous créez un **DataTable**; vous pouvez spécifier la propriété à un autre moment, ou la conserver vide.</span><span class="sxs-lookup"><span data-stu-id="9b846-113">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="9b846-114">Toutefois, lorsque vous ajoutez une table sans valeur **TableName** à un **jeu de données**, la table reçoit un nom incrémentiel par défaut de table*N*, commençant par « table » pour Table0.</span><span class="sxs-lookup"><span data-stu-id="9b846-114">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b846-115">Nous vous recommandons d’éviter la Convention d’affectation de noms « table*N*» lorsque vous fournissez une valeur **TableName** , car le nom que vous fournissez peut être en conflit avec un nom de table par défaut existant dans le **jeu de données**.</span><span class="sxs-lookup"><span data-stu-id="9b846-115">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="9b846-116">Si le nom fourni existe déjà, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="9b846-116">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="9b846-117">L’exemple suivant crée une instance d’un objet **DataTable** et lui attribue le nom « Customers ».</span><span class="sxs-lookup"><span data-stu-id="9b846-117">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="9b846-118">L’exemple suivant crée une instance d’un **DataTable** en l’ajoutant à la collection **tables** d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="9b846-118">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b846-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b846-119">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [<span data-ttu-id="9b846-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="9b846-120">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="9b846-121">Remplissage d'un DataSet à partir d'un DataAdapter</span><span class="sxs-lookup"><span data-stu-id="9b846-121">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="9b846-122">Chargement d'un DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="9b846-122">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="9b846-123">Chargement des informations de schéma de DataSet à partir de XML</span><span class="sxs-lookup"><span data-stu-id="9b846-123">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="9b846-124">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b846-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
