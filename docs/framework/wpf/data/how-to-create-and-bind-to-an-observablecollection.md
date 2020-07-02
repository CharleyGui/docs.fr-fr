---
title: 'Comment : créer et effectuer une liaison à un ObservableCollection'
description: Découvrez comment créer et effectuer une liaison à une collection qui dérive de la classe ObservableCollection dans Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], ObservableCollection class
- notifications [WPF]
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
ms.openlocfilehash: 36e3d2d84aff0ab96c9b2914da28d4c968c32bac
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617867"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a><span data-ttu-id="c3683-103">Comment : créer et effectuer une liaison à un ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="c3683-103">How to: Create and Bind to an ObservableCollection</span></span>
<span data-ttu-id="c3683-104">Cet exemple montre comment créer et effectuer une liaison à une collection qui dérive de la <xref:System.Collections.ObjectModel.ObservableCollection%601> classe, qui est une classe de collection qui fournit des notifications lorsque des éléments sont ajoutés ou supprimés.</span><span class="sxs-lookup"><span data-stu-id="c3683-104">This example shows how to create and bind to a collection that derives from the <xref:System.Collections.ObjectModel.ObservableCollection%601> class, which is a collection class that provides notifications when items get added or removed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3683-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3683-105">Example</span></span>  
 <span data-ttu-id="c3683-106">L’exemple suivant illustre l’implémentation d’une collection `NameList` :</span><span class="sxs-lookup"><span data-stu-id="c3683-106">The following example shows the implementation of a `NameList` collection:</span></span>  
  
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
  
 <span data-ttu-id="c3683-107">Vous pouvez rendre la collection disponible pour la liaison de la même façon que vous le feriez avec d’autres objets common language runtime (CLR), comme décrit dans [rendre des données disponibles pour la liaison en XAML](how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="c3683-107">You can make the collection available for binding the same way you would with other common language runtime (CLR) objects, as described in [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span> <span data-ttu-id="c3683-108">Par exemple, vous pouvez instancier la collection en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et spécifier la collection en tant que ressource, comme indiqué ici :</span><span class="sxs-lookup"><span data-stu-id="c3683-108">For example, you can instantiate the collection in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and specify the collection as a resource, as shown here:</span></span>  
  
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
  
 <span data-ttu-id="c3683-109">Vous pouvez ensuite effectuer une liaison à la collection :</span><span class="sxs-lookup"><span data-stu-id="c3683-109">You can then bind to the collection:</span></span>  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 <span data-ttu-id="c3683-110">La définition de `NameItemTemplate` n’est pas indiquée ici.</span><span class="sxs-lookup"><span data-stu-id="c3683-110">The definition of `NameItemTemplate` is not shown here.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3683-111">Les objets de votre collection doivent satisfaire aux conditions décrites dans la [Vue d’ensemble des sources de liaison](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c3683-111">The objects in your collection must satisfy the requirements described in the [Binding Sources Overview](binding-sources-overview.md).</span></span> <span data-ttu-id="c3683-112">En particulier, si vous utilisez <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> (par exemple, vous souhaitez que votre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] se met à jour lorsque les propriétés sources changent dynamiquement), vous devez implémenter un mécanisme de notification de modification de propriété approprié, tel que l' <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span><span class="sxs-lookup"><span data-stu-id="c3683-112">In particular, if you are using <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> (for example, you want your [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to update when the source properties change dynamically), you must implement a suitable property changed notification mechanism such as the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span>  
  
 <span data-ttu-id="c3683-113">Pour plus d’informations, consultez la section « Liaisons de collections » de la [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c3683-113">For more information, see the Binding to Collections section in the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3683-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3683-114">See also</span></span>

- [<span data-ttu-id="c3683-115">Trier des données dans une vue</span><span class="sxs-lookup"><span data-stu-id="c3683-115">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="c3683-116">Filtrer des données dans une vue</span><span class="sxs-lookup"><span data-stu-id="c3683-116">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="c3683-117">Trier et regrouper des données à l’aide d’une vue en XAML</span><span class="sxs-lookup"><span data-stu-id="c3683-117">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="c3683-118">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="c3683-118">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c3683-119">Rubriques de procédures</span><span class="sxs-lookup"><span data-stu-id="c3683-119">How-to Topics</span></span>](data-binding-how-to-topics.md)
