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
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="937c9-102">Implémentation de la logique métier (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="937c9-102">Implementing Business Logic (LINQ to SQL)</span></span>

<span data-ttu-id="937c9-103">Le terme "logique métier" utilisé dans cette rubrique désigne toutes les règles ou tests de validation personnalisés que vous appliquez aux données avant de les insérer, de les mettre à jour ou de les supprimer de la base de données.</span><span class="sxs-lookup"><span data-stu-id="937c9-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="937c9-104">La logique métier est parfois également désignée par le terme "règles métier" ou "logique de domaine".</span><span class="sxs-lookup"><span data-stu-id="937c9-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="937c9-105">Dans les applications multicouches, elle est généralement conçue comme une couche logique de manière à ce qu'elle puisse être modifiée indépendamment de la couche Présentation ou de la couche Data Access.</span><span class="sxs-lookup"><span data-stu-id="937c9-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="937c9-106">La logique métier peut être appelée par la couche Data Access avant ou après toute mise à jour, insertion ou suppression de données dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="937c9-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="937c9-107">La logique métier peut être aussi simple qu'une validation de schéma effectuée pour vérifier que le type du champ est compatible avec le type de la colonne de table.</span><span class="sxs-lookup"><span data-stu-id="937c9-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="937c9-108">Elle peut également être constituée d'un ensemble d'objets qui interagissent de manières arbitrairement complexes.</span><span class="sxs-lookup"><span data-stu-id="937c9-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="937c9-109">Les règles peuvent être implémentées comme des procédures stockées sur la base de données ou comme des objets en mémoire.</span><span class="sxs-lookup"><span data-stu-id="937c9-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="937c9-110">Toutefois, la logique métier est implémentée, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vous permet d’utiliser des classes partielles et des méthodes partielles pour séparer la logique métier du code d’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="937c9-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="937c9-111">Comment LINQ to SQL appelle votre logique métier</span><span class="sxs-lookup"><span data-stu-id="937c9-111">How LINQ to SQL Invokes Your Business Logic</span></span>  

 <span data-ttu-id="937c9-112">Lorsque vous générez une classe d’entité au moment du design, soit manuellement, soit à l’aide de Concepteur Objet Relationnel ou SQLMetal, elle est définie comme une classe partielle.</span><span class="sxs-lookup"><span data-stu-id="937c9-112">When you generate an entity class at design time, either manually or by using the Object Relational Designer or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="937c9-113">Cela signifie que, dans un fichier de code distinct, vous pouvez définir une autre partie de la classe d'entité qui contient votre logique métier personnalisée.</span><span class="sxs-lookup"><span data-stu-id="937c9-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="937c9-114">Lors de la compilation, les deux parties sont fusionnées en une classe unique.</span><span class="sxs-lookup"><span data-stu-id="937c9-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="937c9-115">Toutefois, si vous devez régénérer vos classes d’entité à l’aide de Concepteur Objet Relationnel ou SQLMetal, vous pouvez le faire et votre partie de la classe ne sera pas modifiée.</span><span class="sxs-lookup"><span data-stu-id="937c9-115">But if you have to regenerate your entity classes by using the Object Relational Designer or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="937c9-116">Les classes partielles qui définissent des entités et le <xref:System.Data.Linq.DataContext> contiennent des méthodes partielles.</span><span class="sxs-lookup"><span data-stu-id="937c9-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="937c9-117">Ce sont les points d'extensibilité que vous pouvez utiliser pour appliquer votre logique métier avant et après toute mise à jour, insertion ou suppression pour une entité ou une propriété d'entité.</span><span class="sxs-lookup"><span data-stu-id="937c9-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="937c9-118">Les méthodes partielles peuvent être comparées à des événements au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="937c9-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="937c9-119">Le générateur de code définit une signature de méthode et appelle les méthodes dans les accesseurs de propriété get et set, le constructeur `DataContext`, et dans certains cas en arrière-plan lorsque <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé.</span><span class="sxs-lookup"><span data-stu-id="937c9-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="937c9-120">Toutefois, si vous n'implémentez pas de méthode partielle particulière, toutes les références à celle-ci et la définition sont supprimées à la compilation.</span><span class="sxs-lookup"><span data-stu-id="937c9-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="937c9-121">Dans la définition d'implémentation que vous écrivez dans votre fichier de code distinct, vous pouvez exécuter toute logique personnalisée requise.</span><span class="sxs-lookup"><span data-stu-id="937c9-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="937c9-122">Vous pouvez utiliser votre classe partielle elle-même comme votre couche de domaine, ou vous pouvez l'appeler à partir de votre définition d'implémentation de la méthode partielle dans un objet ou des objets séparés.</span><span class="sxs-lookup"><span data-stu-id="937c9-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="937c9-123">Dans l'un et l'autre cas, votre logique métier est nettement séparée de votre code d'accès aux données et de votre code de couche Présentation.</span><span class="sxs-lookup"><span data-stu-id="937c9-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="937c9-124">Présentation détaillée des points d'extensibilité</span><span class="sxs-lookup"><span data-stu-id="937c9-124">A Closer Look at the Extensibility Points</span></span>  

 <span data-ttu-id="937c9-125">L’exemple suivant montre une partie du code généré par l’Concepteur Objet Relationnel pour la `DataContext` classe qui a deux tables : `Customers` et `Orders` .</span><span class="sxs-lookup"><span data-stu-id="937c9-125">The following example shows part of the code generated by the Object Relational Designer for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="937c9-126">Notez que les méthodes Insert, Update et Delete sont définies pour chaque table de la classe.</span><span class="sxs-lookup"><span data-stu-id="937c9-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="937c9-127">Si vous implémentez les méthodes Insert, Update et Delete dans votre classe partielle, le runtime [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] les appelle à la place de ses propres méthodes par défaut lorsque <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé.</span><span class="sxs-lookup"><span data-stu-id="937c9-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="937c9-128">Cela vous permet de substituer le comportement par défaut pour les opérations de création / lecture / mise à jour / suppression.</span><span class="sxs-lookup"><span data-stu-id="937c9-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="937c9-129">Pour plus d’informations, consultez [procédure pas à pas : personnalisation du comportement d’insertion, de mise à jour et de suppression de classes d’entité](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="937c9-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="937c9-130">La méthode `OnCreated` est appelée dans le constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="937c9-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="937c9-131">Les classes d'entité ont trois méthodes qui sont appelées par le runtime [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] lorsque l'entité est créée, chargée et validée (lorsque `SubmitChanges` est appelé).</span><span class="sxs-lookup"><span data-stu-id="937c9-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="937c9-132">Les classes d'entité ont également deux méthodes partielles pour chaque propriété, l'une est appelée avant que la propriété soit définie et l'autre après.</span><span class="sxs-lookup"><span data-stu-id="937c9-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="937c9-133">L'exemple de code suivant illustre quelques-unes des méthodes générées pour la classe `Customer` :</span><span class="sxs-lookup"><span data-stu-id="937c9-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="937c9-134">Les méthodes sont appelées dans l’accesseur set de propriété comme illustré dans l’exemple suivant pour la propriété `CustomerID` :</span><span class="sxs-lookup"><span data-stu-id="937c9-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="937c9-135">Dans votre partie de la classe, vous écrivez une définition d'implémentation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="937c9-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="937c9-136">Dans Visual Studio, après avoir tapé, `partial` vous verrez IntelliSense pour les définitions de méthode dans l’autre partie de la classe.</span><span class="sxs-lookup"><span data-stu-id="937c9-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="937c9-137">Pour plus d'informations sur l'ajout de la logique métier à votre application à l'aide des méthodes partielles, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="937c9-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="937c9-138">Guide pratique pour ajouter une validation à des classes d’entité</span><span class="sxs-lookup"><span data-stu-id="937c9-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="937c9-139">Procédure pas à pas : personnalisation du comportement d’insertion, de mise à jour et de suppression de classes d’entité</span><span class="sxs-lookup"><span data-stu-id="937c9-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="937c9-140">[Procédure pas à pas : ajout d’une validation à des classes d’entité](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="937c9-140">[Walkthrough: Adding Validation to Entity Classes](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="937c9-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="937c9-141">See also</span></span>

- [<span data-ttu-id="937c9-142">Classes et méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="937c9-142">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="937c9-143">Méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="937c9-143">Partial Methods</span></span>](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="937c9-144">LINQ to SQL Tools dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="937c9-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="937c9-145">SqlMetal.exe (outil de génération de code)</span><span class="sxs-lookup"><span data-stu-id="937c9-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
