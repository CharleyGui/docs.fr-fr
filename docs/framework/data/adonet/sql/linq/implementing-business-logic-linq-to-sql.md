---
title: Implémentation de la logique métier (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 3d703f7a13f21947fb5d2b5adcac8ae4df6a1547
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158368"
---
# <a name="implementing-business-logic-linq-to-sql"></a>Implémentation de la logique métier (LINQ to SQL)

Le terme "logique métier" utilisé dans cette rubrique désigne toutes les règles ou tests de validation personnalisés que vous appliquez aux données avant de les insérer, de les mettre à jour ou de les supprimer de la base de données. La logique métier est parfois également désignée par le terme "règles métier" ou "logique de domaine". Dans les applications multicouches, elle est généralement conçue comme une couche logique de manière à ce qu'elle puisse être modifiée indépendamment de la couche Présentation ou de la couche Data Access. La logique métier peut être appelée par la couche Data Access avant ou après toute mise à jour, insertion ou suppression de données dans la base de données.  
  
 La logique métier peut être aussi simple qu'une validation de schéma effectuée pour vérifier que le type du champ est compatible avec le type de la colonne de table. Elle peut également être constituée d'un ensemble d'objets qui interagissent de manières arbitrairement complexes. Les règles peuvent être implémentées comme des procédures stockées sur la base de données ou comme des objets en mémoire. Toutefois, la logique métier est implémentée, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vous permet d’utiliser des classes partielles et des méthodes partielles pour séparer la logique métier du code d’accès aux données.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>Comment LINQ to SQL appelle votre logique métier  

 Lorsque vous générez une classe d’entité au moment du design, soit manuellement, soit à l’aide de Concepteur Objet Relationnel ou SQLMetal, elle est définie comme une classe partielle. Cela signifie que, dans un fichier de code distinct, vous pouvez définir une autre partie de la classe d'entité qui contient votre logique métier personnalisée. Lors de la compilation, les deux parties sont fusionnées en une classe unique. Toutefois, si vous devez régénérer vos classes d’entité à l’aide de Concepteur Objet Relationnel ou SQLMetal, vous pouvez le faire et votre partie de la classe ne sera pas modifiée.  
  
 Les classes partielles qui définissent des entités et le <xref:System.Data.Linq.DataContext> contiennent des méthodes partielles. Ce sont les points d'extensibilité que vous pouvez utiliser pour appliquer votre logique métier avant et après toute mise à jour, insertion ou suppression pour une entité ou une propriété d'entité. Les méthodes partielles peuvent être comparées à des événements au moment de la compilation. Le générateur de code définit une signature de méthode et appelle les méthodes dans les accesseurs de propriété get et set, le constructeur `DataContext`, et dans certains cas en arrière-plan lorsque <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé. Toutefois, si vous n'implémentez pas de méthode partielle particulière, toutes les références à celle-ci et la définition sont supprimées à la compilation.  
  
 Dans la définition d'implémentation que vous écrivez dans votre fichier de code distinct, vous pouvez exécuter toute logique personnalisée requise. Vous pouvez utiliser votre classe partielle elle-même comme votre couche de domaine, ou vous pouvez l'appeler à partir de votre définition d'implémentation de la méthode partielle dans un objet ou des objets séparés. Dans l'un et l'autre cas, votre logique métier est nettement séparée de votre code d'accès aux données et de votre code de couche Présentation.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Présentation détaillée des points d'extensibilité  

 L’exemple suivant montre une partie du code généré par l’Concepteur Objet Relationnel pour la `DataContext` classe qui a deux tables : `Customers` et `Orders` . Notez que les méthodes Insert, Update et Delete sont définies pour chaque table de la classe.  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 Si vous implémentez les méthodes Insert, Update et Delete dans votre classe partielle, le runtime [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] les appelle à la place de ses propres méthodes par défaut lorsque <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé. Cela vous permet de substituer le comportement par défaut pour les opérations de création / lecture / mise à jour / suppression. Pour plus d’informations, consultez [procédure pas à pas : personnalisation du comportement d’insertion, de mise à jour et de suppression de classes d’entité](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).  
  
 La méthode `OnCreated` est appelée dans le constructeur de classe.  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 Les classes d'entité ont trois méthodes qui sont appelées par le runtime [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] lorsque l'entité est créée, chargée et validée (lorsque `SubmitChanges` est appelé). Les classes d'entité ont également deux méthodes partielles pour chaque propriété, l'une est appelée avant que la propriété soit définie et l'autre après. L'exemple de code suivant illustre quelques-unes des méthodes générées pour la classe `Customer` :  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 Les méthodes sont appelées dans l’accesseur set de propriété comme illustré dans l’exemple suivant pour la propriété `CustomerID` :  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 Dans votre partie de la classe, vous écrivez une définition d'implémentation de la méthode. Dans Visual Studio, après avoir tapé, `partial` vous verrez IntelliSense pour les définitions de méthode dans l’autre partie de la classe.  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 Pour plus d'informations sur l'ajout de la logique métier à votre application à l'aide des méthodes partielles, consultez les rubriques suivantes :  
  
 [Guide pratique pour ajouter une validation à des classes d’entité](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [Procédure pas à pas : personnalisation du comportement d’insertion, de mise à jour et de suppression de classes d’entité](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [Procédure pas à pas : ajout d’une validation à des classes d’entité](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))  
  
## <a name="see-also"></a>Voir aussi

- [Classes et méthodes partielles](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [Méthodes partielles](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [LINQ to SQL Tools dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [SqlMetal.exe (outil de génération de code)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
