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
# <a name="handling-dataset-events"></a>Gestion des événements de DataSet
L'objet <xref:System.Data.DataSet> fournit trois événements : <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>et <xref:System.Data.DataSet.MergeFailed>.  
  
## <a name="the-mergefailed-event"></a>Événement MergeFailed  
 L'événement le plus couramment utilisé de l'objet `DataSet` est `MergeFailed`, qui se déclenche en cas de conflit au niveau du schéma des objets `DataSet` en cours de fusion. Cela se produit lorsque des <xref:System.Data.DataRow> cible et source possèdent la même valeur de clé primaire et que la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> a la valeur `true`. Par exemple, si les colonnes de clé primaire d'une table en cours de fusion sont identiques entre les tables des deux objets `DataSet` , une exception est levée et l'événement `MergeFailed` est déclenché. L'objet <xref:System.Data.MergeFailedEventArgs> passé à l'événement `MergeFailed` possède une propriété <xref:System.Data.MergeFailedEventArgs.Conflict%2A> qui identifie le conflit au niveau du schéma entre les deux objets `DataSet` et une propriété <xref:System.Data.MergeFailedEventArgs.Table%2A> qui identifie le nom de la table en conflit.  
  
 Le fragment de code ci-dessous montre comment ajouter un gestionnaire d'événements pour l'événement `MergeFailed` .  
  
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
  
## <a name="the-initialized-event"></a>Événement Initialized  
 L'événement <xref:System.Data.DataSet.Initialized> se produit après que le constructeur `DataSet` a initialisé une nouvelle instance du `DataSet`.  
  
 La propriété <xref:System.Data.DataSet.IsInitialized%2A> retourne `true` si le `DataSet` a terminé l'initialisation ; dans le cas contraire, elle retourne `false`. La méthode <xref:System.Data.DataSet.BeginInit%2A> , qui commence l'initialisation d'un `DataSet`, affecte à la propriété <xref:System.Data.DataSet.IsInitialized%2A> la valeur `false`. La méthode <xref:System.Data.DataSet.EndInit%2A> , qui termine l'initialisation du `DataSet`, lui affecte la valeur `true`. Ces méthodes sont utilisées par l’environnement de conception de Visual Studio pour initialiser un `DataSet` qui est utilisé par un autre composant. Vous ne les utiliserez pas couramment dans votre code.  
  
## <a name="the-disposed-event"></a>Événement Disposed  
 `DataSet` est dérivé de la classe <xref:System.ComponentModel.MarshalByValueComponent> , qui expose la méthode <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> et l'événement <xref:System.ComponentModel.MarshalByValueComponent.Disposed> . L' <xref:System.ComponentModel.MarshalByValueComponent.Disposed> événement ajoute un gestionnaire d’événements pour écouter l’événement libéré sur le composant. Vous pouvez utiliser l' <xref:System.ComponentModel.MarshalByValueComponent.Disposed> événement d’un `DataSet` si vous souhaitez exécuter du code lorsque la <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> méthode est appelée. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> Libère les ressources utilisées par le <xref:System.ComponentModel.MarshalByValueComponent> .  
  
> [!NOTE]
> Les `DataSet` `DataTable` objets et héritent de <xref:System.ComponentModel.MarshalByValueComponent> et prennent en charge l' <xref:System.Runtime.Serialization.ISerializable> interface pour la communication à distance. Ce sont les seuls objets ADO.NET qui peuvent être exécutés à distance. Pour plus d’informations, consultez [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).  
  
 Pour plus d’informations sur les autres événements disponibles lors de l’utilisation d’un `DataSet` , consultez [gestion des événements DataTable](handling-datatable-events.md) et [gestion des événements DataAdapter](../handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Voir aussi

- [DataSets, DataTables et DataViews](index.md)
- [Validation des données](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))
- [Extraction et modification de données dans ADO.NET](../retrieving-and-modifying-data.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
