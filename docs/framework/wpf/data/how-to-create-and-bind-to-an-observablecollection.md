---
title: 'Procédure : Créer et effectuer une liaison à un ObservableCollection'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], ObservableCollection class
- notifications [WPF]
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
ms.openlocfilehash: 8db9f2051a0401e01f233f9c959e015eb657bdac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965478"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a>Procédure : Créer et effectuer une liaison à un ObservableCollection
Cet exemple montre comment créer et effectuer une liaison à une collection qui dérive de <xref:System.Collections.ObjectModel.ObservableCollection%601> la classe, qui est une classe de collection qui fournit des notifications lorsque des éléments sont ajoutés ou supprimés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’implémentation d’une collection `NameList` :  
  
```csharp  
public class NameList : ObservableCollection<PersonName>  
{  
    public NameList() : base()  
    {  
        Add(new PersonName("Willa", "Cather"));  
        Add(new PersonName("Isak", "Dinesen"));  
        Add(new PersonName("Victor", "Hugo"));  
        Add(new PersonName("Jules", "Verne"));  
    }  
  }  
  
  public class PersonName  
  {  
      private string firstName;  
      private string lastName;  
  
      public PersonName(string first, string last)  
      {  
          this.firstName = first;  
          this.lastName = last;  
      }  
  
      public string FirstName  
      {  
          get { return firstName; }  
          set { firstName = value; }  
      }  
  
      public string LastName  
      {  
          get { return lastName; }  
          set { lastName = value; }  
      }  
  }  
```  
  
```vb  
Public Class NameList  
    Inherits ObservableCollection(Of PersonName)  
  
    ' Methods  
    Public Sub New()  
        MyBase.Add(New PersonName("Willa", "Cather"))  
        MyBase.Add(New PersonName("Isak", "Dinesen"))  
        MyBase.Add(New PersonName("Victor", "Hugo"))  
        MyBase.Add(New PersonName("Jules", "Verne"))  
    End Sub  
  
End Class  
  
Public Class PersonName  
    ' Methods  
    Public Sub New(ByVal first As String, ByVal last As String)  
        Me._firstName = first  
        Me._lastName = last  
    End Sub  
  
    ' Properties  
    Public Property FirstName() As String  
        Get  
            Return Me._firstName  
        End Get  
        Set(ByVal value As String)  
            Me._firstName = value  
        End Set  
    End Property  
  
    Public Property LastName() As String  
        Get  
            Return Me._lastName  
        End Get  
        Set(ByVal value As String)  
            Me._lastName = value  
        End Set  
    End Property  
  
    ' Fields  
    Private _firstName As String  
    Private _lastName As String  
End Class  
```  
  
 Vous pouvez rendre la collection disponible pour la liaison de la même façon que vous le feriez avec d’autres objets common language runtime (CLR), comme décrit dans [rendre des données disponibles pour la liaison en XAML](how-to-make-data-available-for-binding-in-xaml.md). Par exemple, vous pouvez instancier la collection en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et spécifier la collection en tant que ressource, comme indiqué ici :  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:c="clr-namespace:SDKSample"  
  x:Class="SDKSample.Window1"  
  Width="400"  
  Height="280"  
  Title="MultiBinding Sample">  
  
  <Window.Resources>  
    <c:NameList x:Key="NameListData"/>  
  
...  
  
</Window.Resources>  
```  
  
 Vous pouvez ensuite effectuer une liaison à la collection :  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 La définition de `NameItemTemplate` n’est pas indiquée ici.  
  
> [!NOTE]
> Les objets de votre collection doivent satisfaire aux conditions décrites dans la [Vue d’ensemble des sources de liaison](binding-sources-overview.md). En particulier, si vous utilisez <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> (par exemple, vous souhaitez que votre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se met à jour lorsque les propriétés sources changent dynamiquement), vous devez implémenter un mécanisme de notification de modification de propriété approprié, tel que le <xref:System.ComponentModel.INotifyPropertyChanged>interface.  
  
 Pour plus d’informations, consultez la section « Liaisons de collections » de la [Vue d’ensemble de la liaison de données](data-binding-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Trier des données dans une vue](how-to-sort-data-in-a-view.md)
- [Filtrer les données d’une vue](how-to-filter-data-in-a-view.md)
- [Trier et grouper des données à l'aide d'une vue en XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Vue d’ensemble de la liaison de données](data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
