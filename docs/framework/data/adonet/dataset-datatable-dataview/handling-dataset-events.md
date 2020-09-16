---
title: Gestion des événements de DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 0f79b97b486bbc3e1150cd6aff8162d37134f62e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557994"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="a622a-102">Gestion des événements de DataSet</span><span class="sxs-lookup"><span data-stu-id="a622a-102">Handling DataSet Events</span></span>
<span data-ttu-id="a622a-103">L'objet <xref:System.Data.DataSet> fournit trois événements : <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>et <xref:System.Data.DataSet.MergeFailed>.</span><span class="sxs-lookup"><span data-stu-id="a622a-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="a622a-104">Événement MergeFailed</span><span class="sxs-lookup"><span data-stu-id="a622a-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="a622a-105">L'événement le plus couramment utilisé de l'objet `DataSet` est `MergeFailed`, qui se déclenche en cas de conflit au niveau du schéma des objets `DataSet` en cours de fusion.</span><span class="sxs-lookup"><span data-stu-id="a622a-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="a622a-106">Cela se produit lorsque des <xref:System.Data.DataRow> cible et source possèdent la même valeur de clé primaire et que la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="a622a-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="a622a-107">Par exemple, si les colonnes de clé primaire d'une table en cours de fusion sont identiques entre les tables des deux objets `DataSet` , une exception est levée et l'événement `MergeFailed` est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a622a-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="a622a-108">L'objet <xref:System.Data.MergeFailedEventArgs> passé à l'événement `MergeFailed` possède une propriété <xref:System.Data.MergeFailedEventArgs.Conflict%2A> qui identifie le conflit au niveau du schéma entre les deux objets `DataSet` et une propriété <xref:System.Data.MergeFailedEventArgs.Table%2A> qui identifie le nom de la table en conflit.</span><span class="sxs-lookup"><span data-stu-id="a622a-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="a622a-109">Le fragment de code ci-dessous montre comment ajouter un gestionnaire d'événements pour l'événement `MergeFailed` .</span><span class="sxs-lookup"><span data-stu-id="a622a-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a><span data-ttu-id="a622a-110">Événement Initialized</span><span class="sxs-lookup"><span data-stu-id="a622a-110">The Initialized Event</span></span>  
 <span data-ttu-id="a622a-111">L'événement <xref:System.Data.DataSet.Initialized> se produit après que le constructeur `DataSet` a initialisé une nouvelle instance du `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a622a-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="a622a-112">La propriété <xref:System.Data.DataSet.IsInitialized%2A> retourne `true` si le `DataSet` a terminé l'initialisation ; dans le cas contraire, elle retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="a622a-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="a622a-113">La méthode <xref:System.Data.DataSet.BeginInit%2A> , qui commence l'initialisation d'un `DataSet`, affecte à la propriété <xref:System.Data.DataSet.IsInitialized%2A> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="a622a-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="a622a-114">La méthode <xref:System.Data.DataSet.EndInit%2A> , qui termine l'initialisation du `DataSet`, lui affecte la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="a622a-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="a622a-115">Ces méthodes sont utilisées par l’environnement de conception de Visual Studio pour initialiser un `DataSet` qui est utilisé par un autre composant.</span><span class="sxs-lookup"><span data-stu-id="a622a-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="a622a-116">Vous ne les utiliserez pas couramment dans votre code.</span><span class="sxs-lookup"><span data-stu-id="a622a-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="a622a-117">Événement Disposed</span><span class="sxs-lookup"><span data-stu-id="a622a-117">The Disposed Event</span></span>  
 <span data-ttu-id="a622a-118">`DataSet` est dérivé de la classe <xref:System.ComponentModel.MarshalByValueComponent> , qui expose la méthode <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> et l'événement <xref:System.ComponentModel.MarshalByValueComponent.Disposed> .</span><span class="sxs-lookup"><span data-stu-id="a622a-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="a622a-119">L' <xref:System.ComponentModel.MarshalByValueComponent.Disposed> événement ajoute un gestionnaire d’événements pour écouter l’événement libéré sur le composant.</span><span class="sxs-lookup"><span data-stu-id="a622a-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="a622a-120">Vous pouvez utiliser l' <xref:System.ComponentModel.MarshalByValueComponent.Disposed> événement d’un `DataSet` si vous souhaitez exécuter du code lorsque la <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="a622a-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="a622a-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> Libère les ressources utilisées par le <xref:System.ComponentModel.MarshalByValueComponent> .</span><span class="sxs-lookup"><span data-stu-id="a622a-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a622a-122">Les `DataSet` `DataTable` objets et héritent de <xref:System.ComponentModel.MarshalByValueComponent> et prennent en charge l' <xref:System.Runtime.Serialization.ISerializable> interface pour la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="a622a-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="a622a-123">Ce sont les seuls objets ADO.NET qui peuvent être exécutés à distance.</span><span class="sxs-lookup"><span data-stu-id="a622a-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="a622a-124">Pour plus d’informations, consultez [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a622a-124">For more information, see [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span></span>  
  
 <span data-ttu-id="a622a-125">Pour plus d’informations sur les autres événements disponibles lors de l’utilisation d’un `DataSet` , consultez [gestion des événements DataTable](handling-datatable-events.md) et [gestion des événements DataAdapter](../handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="a622a-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](handling-datatable-events.md) and [Handling DataAdapter Events](../handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a622a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a622a-126">See also</span></span>

- [<span data-ttu-id="a622a-127">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="a622a-127">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="a622a-128">[Validation des données](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="a622a-128">[Validating Data](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span></span>
- [<span data-ttu-id="a622a-129">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a622a-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="a622a-130">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a622a-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
