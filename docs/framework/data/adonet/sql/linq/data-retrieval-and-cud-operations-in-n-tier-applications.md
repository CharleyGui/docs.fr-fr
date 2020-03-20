---
title: Récupération de données et opérations CUD dans les applications multicouches (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: 5ab829993b8f8faa6dcb91d3f23e8442b8aa95bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148411"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>Récupération de données et opérations CUD dans les applications multicouches (LINQ to SQL)
Lorsque vous sérialisez des objets d'entité tels que Customers ou Orders vers un client sur un réseau, ces entités sont détachées de leur contexte de données. Le contexte de données ne suit plus leurs modifications ou leurs associations avec d'autres objets. Ceci ne constitue pas un problème tant que les clients lisent uniquement les données. Il est également relativement simple de permettre aux clients d'ajouter de nouvelles lignes à une base de données. Toutefois, si votre application nécessite que les clients puissent mettre à jour ou supprimer des données, vous devez attacher les entités à un nouveau contexte de données avant d'appeler <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>. De plus, si vous utilisez un contrôle d'accès concurrentiel optimiste avec les valeurs d'origine, vous aurez également besoin de trouver une manière de fournir à la base de données à la fois l'entité d'origine et l'entité modifiée. Les méthodes `Attach` sont fournies pour vous permettre de placer des entités dans un nouveau contexte de données après qu'elles ont été détachées.  
  
 Même si vous sérialisez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] des objets proxy à la place des entités, vous devez toujours <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>construire une entité sur la couche d’accès aux données (DAL), et l’attacher à un nouveau, afin de soumettre les données à la base de données.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]est complètement indifférent à la façon dont les entités sont sérialisées. Pour plus d’informations sur la façon d’utiliser les outils Object Relational Designer et SQLMetal pour générer des classes qui sont sérialisables en utilisant Windows Communication Foundation (WCF), voir [Comment: Rendre les entités sérialisables](how-to-make-entities-serializable.md).  
  
> [!NOTE]
> Appelez uniquement les méthodes `Attach` sur des entités nouvelles ou désérialisées. La seule manière de détacher une entité de son contexte de données d'origine est de la sérialiser. Si vous tentez d'attacher une entité détachée à un nouveau contexte de données et que cette entité comporte encore des chargeurs différés provenant de son contexte de données précédent, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] lèvera une exception. Une entité comportant des chargeurs différés provenant de deux contextes de données différents peut produire des résultats non désirés lorsque vous exécutez des opérations d'insertion, de mise à jour et de suppression sur cette entité. Pour plus d’informations sur les chargeurs différés, voir [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Récupération de données  
  
### <a name="client-method-call"></a>Appel de méthode client  
 Les exemples suivants montrent un appel de méthode d'exemple vers la couche Data Access à partir d'un client Windows Forms. Dans cet exemple, la couche Data Access est implémentée en tant que bibliothèque de services Windows :  
  
```vb  
Private Function GetProdsByCat_Click(ByVal sender As Object, ByVal e _  
    As EventArgs)  
  
    ' Create the WCF client proxy.  
    Dim proxy As New NorthwindServiceReference.Service1Client  
  
    ' Call the method on the service.  
    Dim products As NorthwindServiceReference.Product() = _  
        proxy.GetProductsByCategory(1)  
  
    ' If the database uses original values for concurrency checks,  
    ' the client needs to store them and pass them back to the  
    ' middle tier along with the new values when updating data.  
  
    For Each v As NorthwindClient1.NorthwindServiceReference.Product _  
        In products  
        ' Persist to a List(Of Product) declared at class scope.  
        ' Additional change-tracking logic is the responsibility  
        ' of the presentation tier and/or middle tier.  
        originalProducts.Add(v)  
    Next  
  
    ' (Not shown) Bind the products list to a control  
    ' and/or perform whatever processing is necessary.  
End Function  
```  
  
```csharp  
private void GetProdsByCat_Click(object sender, EventArgs e)  
{  
    // Create the WCF client proxy.  
    NorthwindServiceReference.Service1Client proxy =
    new NorthwindClient.NorthwindServiceReference.Service1Client();  
  
    // Call the method on the service.  
    NorthwindServiceReference.Product[] products =
    proxy.GetProductsByCategory(1);  
  
    // If the database uses original values for concurrency checks,
    // the client needs to store them and pass them back to the
    // middle tier along with the new values when updating data.  
    foreach (var v in products)  
    {  
        // Persist to a list<Product> declared at class scope.  
        // Additional change-tracking logic is the responsibility  
        // of the presentation tier and/or middle tier.  
        originalProducts.Add(v);  
    }  
  
    // (Not shown) Bind the products list to a control  
    // and/or perform whatever processing is necessary.  
    }  
```  
  
### <a name="middle-tier-implementation"></a>Implémentation de couche intermédiaire  
 L'exemple suivant montre une implémentation de la méthode d'interface sur la couche intermédiaire. Les deux points principaux à noter sont les suivants :  
  
- Le <xref:System.Data.Linq.DataContext> est déclaré à la portée de la méthode.  
  
- La méthode retourne une collection <xref:System.Collections.IEnumerable> des résultats réels. Le sérialiseur exécutera la requête pour renvoyer les résultats au niveau client/à la couche Présentation. Pour accéder localement aux résultats de la requête sur la couche intermédiaire, vous pouvez forcer l'exécution en appelant `ToList` ou `ToArray` sur la variable de requête. Vous pouvez retourner ensuite cette liste ou ce tableau sous la forme de `IEnumerable`.  
  
```vb  
Public Function GetProductsByCategory(ByVal categoryID As Integer) _  
    As IEnumerable(Of Product)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    Dim productQuery = _  
    From prod In db.Products _  
    Where prod.CategoryID = categoryID _  
    Select prod  
  
    Return productQuery.AsEnumerable()  
  
End Function  
```  
  
```csharp  
public IEnumerable<Product> GetProductsByCategory(int categoryID)  
{  
    NorthwindClasses1DataContext db =
    new NorthwindClasses1DataContext(connectionString);  
  
    IEnumerable<Product> productQuery =  
    from prod in db.Products  
    where prod.CategoryID == categoryID  
    select prod;  
  
    return productQuery.AsEnumerable();
}  
```  
  
 Une instance d'un contexte de données doit avoir une durée de vie d'une "unité de travail". Dans un environnement faiblement couplé, une unité de travail est généralement petite, éventuellement une seule transaction optimiste, y compris un appel unique à `SubmitChanges`. Par conséquent, le contexte de données est créé et supprimé à la portée de la méthode. Si l'unité de travail inclut des appels à la logique de règles métier, vous souhaiterez généralement conserver l'instance `DataContext` pour cette opération entière. Dans tous les cas, les instances `DataContext` ne sont pas conçues pour être gardées actives sur de longues périodes pour des nombres arbitraires de transactions.  
  
 Cette méthode retourne des objets Product, mais pas la collection des objets Order_Detail associés à chaque objet Product. Utilisez l'objet <xref:System.Data.Linq.DataLoadOptions> pour modifier ce comportement par défaut. Pour plus d’informations, voir [comment : Contrôler la quantité de données connexes récupérées.](how-to-control-how-much-related-data-is-retrieved.md)  
  
## <a name="inserting-data"></a>Insertion de données  
 Pour insérer un nouvel objet, la couche Présentation appelle simplement la méthode pertinente sur l'interface de couche intermédiaire et passe le nouvel objet à insérer. Dans certains cas, il peut être plus efficace pour le client de passer seulement quelques valeurs et de laisser la couche intermédiaire générer l'objet complet.  
  
### <a name="middle-tier-implementation"></a>Implémentation de couche intermédiaire  
 Sur la couche intermédiaire, un nouveau <xref:System.Data.Linq.DataContext> est créé, l'objet est joint au <xref:System.Data.Linq.DataContext> à l'aide de la méthode <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>, et l'objet est inséré lorsque <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé. Les exceptions, les rappels et les conditions d'erreur peuvent être traités exactement comme dans tout autre scénario de service Web.  
  
```vb  
' No call to Attach is necessary for inserts.  
Public Sub InsertOrder(ByVal o As Order)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    db.Orders.InsertOnSubmit(o)  
  
    ' Exception handling not shown.  
    db.SubmitChanges()  
  
End Sub  
```  
  
```csharp  
// No call to Attach is necessary for inserts.  
    public void InsertOrder(Order o)  
    {  
        NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
        db.Orders.InsertOnSubmit(o);  
  
        // Exception handling not shown.  
        db.SubmitChanges();  
    }  
```  
  
## <a name="deleting-data"></a>Suppression de données  
 Pour supprimer un objet existant de la base de données, la couche Présentation appelle la méthode pertinente sur l'interface de couche intermédiaire et passe sa copie qui inclut les valeurs initiales de l'objet à supprimer.  
  
 Les opérations de suppression impliquent des contrôles d'accès concurrentiel optimiste et l'objet à supprimer doit être préalablement attaché au nouveau contexte de données. Dans cet exemple, le paramètre `Boolean` a la valeur `false` pour indiquer que l'objet n'a pas d'horodatage (RowVersion). Si votre table de base de données génère des horodatages pour chaque enregistrement, les contrôles d'accès concurrentiel sont beaucoup plus simples, surtout pour le client. Il suffit de passer l'objet d'origine ou l'objet modifié et d'affecter au paramètre `Boolean` la valeur `true`. Dans tous les cas, sur la couche intermédiaire, il est généralement nécessaire d'intercepter <xref:System.Data.Linq.ChangeConflictException>. Pour plus d’informations sur la façon de gérer les conflits de concurrence optimiste, voir [Concordurrency Optimiste: Aperçu](optimistic-concurrency-overview.md).  
  
 Lorsque vous supprimez des entités qui ont des contraintes de clé étrangère sur les tables associées, vous devez d’abord supprimer tous les objets contenus dans ses collections <xref:System.Data.Linq.EntitySet%601>.  
  
```vb  
' Attach is necessary for deletes.  
Public Sub DeleteOrder(ByVal order As Order)  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
  
    db.Orders.Attach(order, False)  
    ' This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order)  
  
    Try  
        ' ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict)  
  
    Catch ex As ChangeConflictException  
        ' Get conflict information, and take actions  
        ' that are appropriate for your application.  
        ' See MSDN Article "How to: Manage Change  
        ' Conflicts (LINQ to SQL).  
  
    End Try  
End Sub  
```  
  
```csharp  
// Attach is necessary for deletes.  
public void DeleteOrder(Order order)  
{  
    NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
  
    db.Orders.Attach(order, false);  
    // This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order);  
    try  
    {  
        // ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict);  
    }  
    catch (ChangeConflictException e)  
    {  
       // Get conflict information, and take actions  
       // that are appropriate for your application.  
       // See MSDN Article How to: Manage Change Conflicts (LINQ to SQL).  
    }  
}  
```  
  
## <a name="updating-data"></a>Mise à jour des données  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prend en charge les modifications dans les scénarios suivants qui impliquent l'accès concurrentiel optimiste :  
  
- accès concurrentiel optimiste basé sur les horodatages ou les nombres RowVersion ;  
  
- accès concurrentiel optimiste basé sur les valeurs initiales d'un sous-ensemble de propriétés d'entité ;  
  
- accès concurrentiel optimiste basé sur les entités initiales et modifiées complètes.  
  
 Vous pouvez également exécuter des mises à jour ou des suppressions sur une entité ainsi que ses relations, par exemple une entité Customer et une collection de ses objets Order associés. Lorsque vous apportez sur le client des modifications à un graphe d’objets d’entité et leurs collections (`EntitySet`), enfants, et que les contrôles d’accès concurrentiel optimiste requièrent les valeurs d’origine, le client doit fournir ces valeurs d’origine pour chaque entité et objet <xref:System.Data.Linq.EntitySet%601>. Si vous souhaitez permettre aux clients d'effectuer un ensemble de mises à jour, de suppressions et d'insertions connexes dans un appel de méthode unique, vous devez fournir au client une méthode pour indiquer le type d'opération à exécuter sur chaque entité. Sur la couche intermédiaire, vous devez appeler ensuite la méthode <xref:System.Data.Linq.ITable.Attach%2A> appropriée, puis <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A> ou <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (sans `Attach`, pour les insertions) pour chaque entité avant d'appeler <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Ne récupérez pas des données de base de données comme méthode pour obtenir des valeurs d'origine avant de tenter les mises à jour.  
  
 Pour plus d’informations sur la concurrence optimiste, voir [Concordurrency Optimiste: Aperçu](optimistic-concurrency-overview.md). Pour obtenir des informations détaillées sur la résolution des conflits optimistes de changement de concurrence, voir [Comment : Gérer les conflits de changement](how-to-manage-change-conflicts.md).  
  
 Les exemples suivants illustrent chaque scénario :  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Accès concurrentiel optimiste avec les horodatages  
  
```vb  
' Assume that "customer" has been sent by client.  
' Attach with "true" to say this is a modified entity  
' and it can be checked for optimistic concurrency  
' because it has a column that is marked with the  
' "RowVersion" attribute.  
  
db.Customers.Attach(customer, True)  
  
Try  
    ' Optional: Specify a ConflictMode value  
    ' in call to SubmitChanges.  
    db.SubmitChanges()  
Catch ex As ChangeConflictException  
    ' Handle conflict based on options provided.  
    ' See MSDN article "How to: Manage Change  
    ' Conflicts (LINQ to SQL)".  
End Try  
```  
  
```csharp  
// Assume that "customer" has been sent by client.  
// Attach with "true" to say this is a modified entity  
// and it can be checked for optimistic concurrency because  
//  it has a column that is marked with "RowVersion" attribute  
db.Customers.Attach(customer, true)  
try  
{  
    // Optional: Specify a ConflictMode value  
    // in call to SubmitChanges.  
    db.SubmitChanges();  
}  
catch(ChangeConflictException e)  
{  
    // Handle conflict based on options provided  
    // See MSDN article How to: Manage Change Conflicts (LINQ to SQL).  
}  
```  
  
### <a name="with-subset-of-original-values"></a>Avec le sous-ensemble des valeurs d'origine  
 Dans cette méthode, le client retourne l'objet sérialisé complet, ainsi que les valeurs à modifier.  
  
```vb  
Public Sub UpdateProductInventory(ByVal p As Product, ByVal _  
    unitsInStock As Short?, ByVal unitsOnOrder As Short?)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        ' p is the original unmodified product  
        ' that was obtained from the database.  
        ' The client kept a copy and returns it now.  
        db.Products.Attach(p, False)  
  
        ' Now that the original values are in the data context,  
        ' apply the changes.  
        p.UnitsInStock = unitsInStock  
        p.UnitsOnOrder = unitsOnOrder  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle conflict based on options provided.  
            ' See MSDN article "How to: Manage Change Conflicts  
            ' (LINQ to SQL)".  
        End Try  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInventory(Product p, short? unitsInStock, short? unitsOnOrder)  
{  
    using (NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString))  
    {  
        // p is the original unmodified product  
        // that was obtained from the database.  
        // The client kept a copy and returns it now.  
        db.Products.Attach(p, false);  
  
        // Now that the original values are in the data context, apply the changes.  
        p.UnitsInStock = unitsInStock;  
        p.UnitsOnOrder = unitsOnOrder;  
        try  
        {  
             // Optional: Specify a ConflictMode value  
             // in call to SubmitChanges.  
             db.SubmitChanges();  
        }  
        catch (ChangeConflictException e)  
        {  
            // Handle conflict based on provided options.  
            // See MSDN article How to: Manage Change Conflicts  
            // (LINQ to SQL).  
        }  
    }  
}  
```  
  
### <a name="with-complete-entities"></a>Avec les entités complètes  
  
```vb  
Public Sub UpdateProductInfo(ByVal newProd As Product, ByVal _  
    originalProd As Product)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        db.Products.Attach(newProd, originalProd)  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle potential change conflicgt in whatever way  
            ' is appropriate for your application.  
            ' For more information, see the MSDN article  
            ' "How to: Manage Change Conflicts (LINQ to  
            ' SQL)".  
        End Try  
  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInfo(Product newProd, Product originalProd)  
{  
     using (NorthwindClasses1DataContext db = new  
        NorthwindClasses1DataContext(connectionString))  
     {  
         db.Products.Attach(newProd, originalProd);  
         try  
         {  
               // Optional: Specify a ConflictMode value  
               // in call to SubmitChanges.  
               db.SubmitChanges();  
         }  
        catch (ChangeConflictException e)  
        {  
            // Handle potential change conflict in whatever way  
            // is appropriate for your application.  
            // For more information, see the MSDN article  
            // How to: Manage Change Conflicts (LINQ to SQL)/  
        }
    }  
}  
```  
  
 Pour mettre à jour une collection, appelez <xref:System.Data.Linq.ITable.AttachAll%2A> au lieu de `Attach`.  
  
### <a name="expected-entity-members"></a>Membres d'entité attendus  
 Comme indiqué précédemment, seuls certains membres de l'objet d'entité doivent être définis pour que vous puissiez appeler les méthodes `Attach`. Les membres d'entité à définir doivent répondre aux critères suivants :  
  
- faire partie de l'identité de l'entité ;  
  
- être modifiable ;  
  
- être un horodatage ou avoir son attribut <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> défini à une valeur différente de `Never`.  
  
 Si une table utilise un horodatage ou un numéro de version pour un contrôle d'accès concurrentiel optimiste, vous devez définir ces membres avant d'appeler <xref:System.Data.Linq.ITable.Attach%2A>. Un membre est dédié au contrôle de l'accès concurrentiel optimiste lorsque la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> a la valeur true sur cet attribut Column. Toutes les mises à jour demandées seront soumises uniquement si les valeurs de numéro de version ou d'horodatage sont identiques dans la base de données.  
  
 Un membre est également utilisé dans le contrôle d'accès concurrentiel optimiste, sauf si <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> pour le membre a la valeur `Never`. La valeur par défaut est `Always` si aucune autre valeur n'est spécifiée.  
  
 Si l'un de ces membres obligatoires est absent, une <xref:System.Data.Linq.ChangeConflictException> est levée durant <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Ligne introuvable ou modifiée").  
  
### <a name="state"></a>State  
 Une fois qu'un objet d'entité est attaché à l'instance <xref:System.Data.Linq.DataContext>, l'objet est considéré comme étant dans l'état `PossiblyModified`. Vous pouvez imposer l'interprétation d'un objet attaché comme `Modified` de trois manières.  
  
1. Attachez l'objet comme non modifié, puis modifiez directement les champs.  
  
2. Attachez l'objet avec la surcharge <xref:System.Data.Linq.Table%601.Attach%2A> qui accepte les instances d'objet actuelles et initiales. Ceci fournit au dispositif de suivi des modifications les valeurs anciennes et nouvelles afin qu'il détermine automatiquement les champs qui ont été modifiés.  
  
3. Attachez l'objet avec la surcharge <xref:System.Data.Linq.Table%601.Attach%2A> qui accepte un deuxième paramètre Boolean (défini à true). Ceci donnera au dispositif de suivi des modifications l'indication de considérer l'objet modifié sans avoir à fournir de valeurs d'origine. Dans cette approche, l'objet doit avoir un champ de version/horodatage.  
  
 Pour plus d’informations, voir [Object States et Change-Tracking](object-states-and-change-tracking.md).  
  
 Si un objet d'entité se produit déjà dans le cache d'ID avec la même identité que l'objet attaché, une <xref:System.Data.Linq.DuplicateKeyException> est levée.  
  
 Lorsque vous effectuez l'attachement avec un ensemble `IEnumerable` d'objets, une <xref:System.Data.Linq.DuplicateKeyException> est levée lorsqu'une clé déjà existante est présente. Les objets restants ne sont pas attachés.  
  
## <a name="see-also"></a>Voir aussi

- [Applications multicouches et distantes avec LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
- [Informations de base](background-information.md)
