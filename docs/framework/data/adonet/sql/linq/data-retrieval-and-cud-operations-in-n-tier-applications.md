---
title: Récupération de données et opérations CUD dans les applications multicouches (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: 1bc97504b4dd053ce9ef747460a79865cbe836ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197415"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="25627-102">Récupération de données et opérations CUD dans les applications multicouches (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="25627-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>

<span data-ttu-id="25627-103">Lorsque vous sérialisez des objets d'entité tels que Customers ou Orders vers un client sur un réseau, ces entités sont détachées de leur contexte de données.</span><span class="sxs-lookup"><span data-stu-id="25627-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="25627-104">Le contexte de données ne suit plus leurs modifications ou leurs associations avec d'autres objets.</span><span class="sxs-lookup"><span data-stu-id="25627-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="25627-105">Ceci ne constitue pas un problème tant que les clients lisent uniquement les données.</span><span class="sxs-lookup"><span data-stu-id="25627-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="25627-106">Il est également relativement simple de permettre aux clients d'ajouter de nouvelles lignes à une base de données.</span><span class="sxs-lookup"><span data-stu-id="25627-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="25627-107">Toutefois, si votre application nécessite que les clients puissent mettre à jour ou supprimer des données, vous devez attacher les entités à un nouveau contexte de données avant d'appeler <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="25627-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="25627-108">De plus, si vous utilisez un contrôle d'accès concurrentiel optimiste avec les valeurs d'origine, vous aurez également besoin de trouver une manière de fournir à la base de données à la fois l'entité d'origine et l'entité modifiée.</span><span class="sxs-lookup"><span data-stu-id="25627-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="25627-109">Les méthodes `Attach` sont fournies pour vous permettre de placer des entités dans un nouveau contexte de données après qu'elles ont été détachées.</span><span class="sxs-lookup"><span data-stu-id="25627-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="25627-110">Même si vous sérialisez des objets proxy à la place des [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entités, vous devez toujours construire une entité sur la couche d’accès aux données (DAL) et l’attacher à une nouvelle <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> , afin d’envoyer les données à la base de données.</span><span class="sxs-lookup"><span data-stu-id="25627-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="25627-111">est totalement différent du mode de sérialisation des entités.</span><span class="sxs-lookup"><span data-stu-id="25627-111">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="25627-112">Pour plus d’informations sur l’utilisation des outils Concepteur Objet Relationnel et SQLMetal pour générer des classes qui sont sérialisables à l’aide de Windows Communication Foundation (WCF), consultez [Comment : rendre des entités sérialisables](how-to-make-entities-serializable.md).</span><span class="sxs-lookup"><span data-stu-id="25627-112">For more information about how to use the Object Relational Designer and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25627-113">Appelez uniquement les méthodes `Attach` sur des entités nouvelles ou désérialisées.</span><span class="sxs-lookup"><span data-stu-id="25627-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="25627-114">La seule manière de détacher une entité de son contexte de données d'origine est de la sérialiser.</span><span class="sxs-lookup"><span data-stu-id="25627-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="25627-115">Si vous tentez d'attacher une entité détachée à un nouveau contexte de données et que cette entité comporte encore des chargeurs différés provenant de son contexte de données précédent, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] lèvera une exception.</span><span class="sxs-lookup"><span data-stu-id="25627-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="25627-116">Une entité comportant des chargeurs différés provenant de deux contextes de données différents peut produire des résultats non désirés lorsque vous exécutez des opérations d'insertion, de mise à jour et de suppression sur cette entité.</span><span class="sxs-lookup"><span data-stu-id="25627-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="25627-117">Pour plus d’informations sur les chargeurs différés, consultez [différé et chargement immédiat](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="25627-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="25627-118">Récupération de données</span><span class="sxs-lookup"><span data-stu-id="25627-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="25627-119">Appel de méthode client</span><span class="sxs-lookup"><span data-stu-id="25627-119">Client Method Call</span></span>  

 <span data-ttu-id="25627-120">Les exemples suivants montrent un appel de méthode d'exemple vers la couche Data Access à partir d'un client Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="25627-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="25627-121">Dans cet exemple, la couche Data Access est implémentée en tant que bibliothèque de services Windows :</span><span class="sxs-lookup"><span data-stu-id="25627-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
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
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="25627-122">Implémentation de couche intermédiaire</span><span class="sxs-lookup"><span data-stu-id="25627-122">Middle Tier Implementation</span></span>  

 <span data-ttu-id="25627-123">L'exemple suivant montre une implémentation de la méthode d'interface sur la couche intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="25627-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="25627-124">Les deux points principaux à noter sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="25627-124">The following are the two main points to note:</span></span>  
  
- <span data-ttu-id="25627-125">Le <xref:System.Data.Linq.DataContext> est déclaré à la portée de la méthode.</span><span class="sxs-lookup"><span data-stu-id="25627-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
- <span data-ttu-id="25627-126">La méthode retourne une collection <xref:System.Collections.IEnumerable> des résultats réels.</span><span class="sxs-lookup"><span data-stu-id="25627-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="25627-127">Le sérialiseur exécutera la requête pour renvoyer les résultats au niveau client/à la couche Présentation.</span><span class="sxs-lookup"><span data-stu-id="25627-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="25627-128">Pour accéder localement aux résultats de la requête sur la couche intermédiaire, vous pouvez forcer l'exécution en appelant `ToList` ou `ToArray` sur la variable de requête.</span><span class="sxs-lookup"><span data-stu-id="25627-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="25627-129">Vous pouvez retourner ensuite cette liste ou ce tableau sous la forme de `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="25627-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
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
  
 <span data-ttu-id="25627-130">Une instance d'un contexte de données doit avoir une durée de vie d'une "unité de travail".</span><span class="sxs-lookup"><span data-stu-id="25627-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="25627-131">Dans un environnement faiblement couplé, une unité de travail est généralement petite, éventuellement une seule transaction optimiste, y compris un appel unique à `SubmitChanges`.</span><span class="sxs-lookup"><span data-stu-id="25627-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="25627-132">Par conséquent, le contexte de données est créé et supprimé à la portée de la méthode.</span><span class="sxs-lookup"><span data-stu-id="25627-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="25627-133">Si l'unité de travail inclut des appels à la logique de règles métier, vous souhaiterez généralement conserver l'instance `DataContext` pour cette opération entière.</span><span class="sxs-lookup"><span data-stu-id="25627-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="25627-134">Dans tous les cas, les instances `DataContext` ne sont pas conçues pour être gardées actives sur de longues périodes pour des nombres arbitraires de transactions.</span><span class="sxs-lookup"><span data-stu-id="25627-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="25627-135">Cette méthode retourne des objets Product, mais pas la collection des objets Order_Detail associés à chaque objet Product.</span><span class="sxs-lookup"><span data-stu-id="25627-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="25627-136">Utilisez l'objet <xref:System.Data.Linq.DataLoadOptions> pour modifier ce comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="25627-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="25627-137">Pour plus d’informations, consultez [Comment : contrôler la quantité de données liées récupérées](how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="25627-137">For more information, see [How to: Control How Much Related Data Is Retrieved](how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="25627-138">Insertion de données</span><span class="sxs-lookup"><span data-stu-id="25627-138">Inserting Data</span></span>  

 <span data-ttu-id="25627-139">Pour insérer un nouvel objet, la couche Présentation appelle simplement la méthode pertinente sur l'interface de couche intermédiaire et passe le nouvel objet à insérer.</span><span class="sxs-lookup"><span data-stu-id="25627-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="25627-140">Dans certains cas, il peut être plus efficace pour le client de passer seulement quelques valeurs et de laisser la couche intermédiaire générer l'objet complet.</span><span class="sxs-lookup"><span data-stu-id="25627-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="25627-141">Implémentation de couche intermédiaire</span><span class="sxs-lookup"><span data-stu-id="25627-141">Middle Tier Implementation</span></span>  

 <span data-ttu-id="25627-142">Sur la couche intermédiaire, un nouveau <xref:System.Data.Linq.DataContext> est créé, l'objet est joint au <xref:System.Data.Linq.DataContext> à l'aide de la méthode <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>, et l'objet est inséré lorsque <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est appelé.</span><span class="sxs-lookup"><span data-stu-id="25627-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="25627-143">Les exceptions, les rappels et les conditions d'erreur peuvent être traités exactement comme dans tout autre scénario de service Web.</span><span class="sxs-lookup"><span data-stu-id="25627-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
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
  
## <a name="deleting-data"></a><span data-ttu-id="25627-144">Suppression de données</span><span class="sxs-lookup"><span data-stu-id="25627-144">Deleting Data</span></span>  

 <span data-ttu-id="25627-145">Pour supprimer un objet existant de la base de données, la couche Présentation appelle la méthode pertinente sur l'interface de couche intermédiaire et passe sa copie qui inclut les valeurs initiales de l'objet à supprimer.</span><span class="sxs-lookup"><span data-stu-id="25627-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="25627-146">Les opérations de suppression impliquent des contrôles d'accès concurrentiel optimiste et l'objet à supprimer doit être préalablement attaché au nouveau contexte de données.</span><span class="sxs-lookup"><span data-stu-id="25627-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="25627-147">Dans cet exemple, le paramètre `Boolean` a la valeur `false` pour indiquer que l'objet n'a pas d'horodatage (RowVersion).</span><span class="sxs-lookup"><span data-stu-id="25627-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="25627-148">Si votre table de base de données génère des horodatages pour chaque enregistrement, les contrôles d'accès concurrentiel sont beaucoup plus simples, surtout pour le client.</span><span class="sxs-lookup"><span data-stu-id="25627-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="25627-149">Il suffit de passer l'objet d'origine ou l'objet modifié et d'affecter au paramètre `Boolean` la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="25627-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="25627-150">Dans tous les cas, sur la couche intermédiaire, il est généralement nécessaire d'intercepter <xref:System.Data.Linq.ChangeConflictException>.</span><span class="sxs-lookup"><span data-stu-id="25627-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="25627-151">Pour plus d’informations sur la gestion des conflits d’accès concurrentiel optimiste, consultez [accès concurrentiel optimiste : vue d’ensemble](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="25627-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="25627-152">Lorsque vous supprimez des entités qui ont des contraintes de clé étrangère sur les tables associées, vous devez d’abord supprimer tous les objets contenus dans ses collections <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="25627-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
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
  
## <a name="updating-data"></a><span data-ttu-id="25627-153">Mise à jour des données</span><span class="sxs-lookup"><span data-stu-id="25627-153">Updating Data</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="25627-154">prend en charge les modifications dans les scénarios suivants qui impliquent l'accès concurrentiel optimiste :</span><span class="sxs-lookup"><span data-stu-id="25627-154">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
- <span data-ttu-id="25627-155">accès concurrentiel optimiste basé sur les horodatages ou les nombres RowVersion ;</span><span class="sxs-lookup"><span data-stu-id="25627-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
- <span data-ttu-id="25627-156">accès concurrentiel optimiste basé sur les valeurs initiales d'un sous-ensemble de propriétés d'entité ;</span><span class="sxs-lookup"><span data-stu-id="25627-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
- <span data-ttu-id="25627-157">accès concurrentiel optimiste basé sur les entités initiales et modifiées complètes.</span><span class="sxs-lookup"><span data-stu-id="25627-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="25627-158">Vous pouvez également exécuter des mises à jour ou des suppressions sur une entité ainsi que ses relations, par exemple une entité Customer et une collection de ses objets Order associés.</span><span class="sxs-lookup"><span data-stu-id="25627-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="25627-159">Lorsque vous apportez sur le client des modifications à un graphe d’objets d’entité et leurs collections (`EntitySet`), enfants, et que les contrôles d’accès concurrentiel optimiste requièrent les valeurs d’origine, le client doit fournir ces valeurs d’origine pour chaque entité et objet <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="25627-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="25627-160">Si vous souhaitez permettre aux clients d'effectuer un ensemble de mises à jour, de suppressions et d'insertions connexes dans un appel de méthode unique, vous devez fournir au client une méthode pour indiquer le type d'opération à exécuter sur chaque entité.</span><span class="sxs-lookup"><span data-stu-id="25627-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="25627-161">Sur la couche intermédiaire, vous devez appeler ensuite la méthode <xref:System.Data.Linq.ITable.Attach%2A> appropriée, puis <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A> ou <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (sans `Attach`, pour les insertions) pour chaque entité avant d'appeler <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="25627-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="25627-162">Ne récupérez pas des données de base de données comme méthode pour obtenir des valeurs d'origine avant de tenter les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="25627-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="25627-163">Pour plus d’informations sur l’accès concurrentiel optimiste, consultez [accès concurrentiel optimiste : vue d’ensemble](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="25627-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="25627-164">Pour plus d’informations sur la résolution des conflits de modification de l’accès concurrentiel optimiste, consultez [Comment : gérer les conflits de modifications](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="25627-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="25627-165">Les exemples suivants illustrent chaque scénario :</span><span class="sxs-lookup"><span data-stu-id="25627-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="25627-166">Accès concurrentiel optimiste avec les horodatages</span><span class="sxs-lookup"><span data-stu-id="25627-166">Optimistic concurrency with timestamps</span></span>  
  
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
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="25627-167">Avec le sous-ensemble des valeurs d'origine</span><span class="sxs-lookup"><span data-stu-id="25627-167">With Subset of Original Values</span></span>  

 <span data-ttu-id="25627-168">Dans cette méthode, le client retourne l'objet sérialisé complet, ainsi que les valeurs à modifier.</span><span class="sxs-lookup"><span data-stu-id="25627-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
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
  
### <a name="with-complete-entities"></a><span data-ttu-id="25627-169">Avec les entités complètes</span><span class="sxs-lookup"><span data-stu-id="25627-169">With Complete Entities</span></span>  
  
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
  
 <span data-ttu-id="25627-170">Pour mettre à jour une collection, appelez <xref:System.Data.Linq.ITable.AttachAll%2A> au lieu de `Attach`.</span><span class="sxs-lookup"><span data-stu-id="25627-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="25627-171">Membres d'entité attendus</span><span class="sxs-lookup"><span data-stu-id="25627-171">Expected Entity Members</span></span>  

 <span data-ttu-id="25627-172">Comme indiqué précédemment, seuls certains membres de l'objet d'entité doivent être définis pour que vous puissiez appeler les méthodes `Attach`.</span><span class="sxs-lookup"><span data-stu-id="25627-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="25627-173">Les membres d'entité à définir doivent répondre aux critères suivants :</span><span class="sxs-lookup"><span data-stu-id="25627-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
- <span data-ttu-id="25627-174">faire partie de l'identité de l'entité ;</span><span class="sxs-lookup"><span data-stu-id="25627-174">Be part of the entity’s identity.</span></span>  
  
- <span data-ttu-id="25627-175">être modifiable ;</span><span class="sxs-lookup"><span data-stu-id="25627-175">Be expected to be modified.</span></span>  
  
- <span data-ttu-id="25627-176">être un horodatage ou avoir son attribut <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> défini à une valeur différente de `Never`.</span><span class="sxs-lookup"><span data-stu-id="25627-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="25627-177">Si une table utilise un horodatage ou un numéro de version pour un contrôle d'accès concurrentiel optimiste, vous devez définir ces membres avant d'appeler <xref:System.Data.Linq.ITable.Attach%2A>.</span><span class="sxs-lookup"><span data-stu-id="25627-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="25627-178">Un membre est dédié au contrôle de l'accès concurrentiel optimiste lorsque la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> a la valeur true sur cet attribut Column.</span><span class="sxs-lookup"><span data-stu-id="25627-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="25627-179">Toutes les mises à jour demandées seront soumises uniquement si les valeurs de numéro de version ou d'horodatage sont identiques dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="25627-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="25627-180">Un membre est également utilisé dans le contrôle d'accès concurrentiel optimiste, sauf si <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> pour le membre a la valeur `Never`.</span><span class="sxs-lookup"><span data-stu-id="25627-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="25627-181">La valeur par défaut est `Always` si aucune autre valeur n'est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="25627-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="25627-182">Si l'un de ces membres obligatoires est absent, une <xref:System.Data.Linq.ChangeConflictException> est levée durant <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Ligne introuvable ou modifiée").</span><span class="sxs-lookup"><span data-stu-id="25627-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="25627-183">State</span><span class="sxs-lookup"><span data-stu-id="25627-183">State</span></span>  

 <span data-ttu-id="25627-184">Une fois qu'un objet d'entité est attaché à l'instance <xref:System.Data.Linq.DataContext>, l'objet est considéré comme étant dans l'état `PossiblyModified`.</span><span class="sxs-lookup"><span data-stu-id="25627-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="25627-185">Vous pouvez imposer l'interprétation d'un objet attaché comme `Modified` de trois manières.</span><span class="sxs-lookup"><span data-stu-id="25627-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="25627-186">Attachez l'objet comme non modifié, puis modifiez directement les champs.</span><span class="sxs-lookup"><span data-stu-id="25627-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="25627-187">Attachez l'objet avec la surcharge <xref:System.Data.Linq.Table%601.Attach%2A> qui accepte les instances d'objet actuelles et initiales.</span><span class="sxs-lookup"><span data-stu-id="25627-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="25627-188">Ceci fournit au dispositif de suivi des modifications les valeurs anciennes et nouvelles afin qu'il détermine automatiquement les champs qui ont été modifiés.</span><span class="sxs-lookup"><span data-stu-id="25627-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="25627-189">Attachez l'objet avec la surcharge <xref:System.Data.Linq.Table%601.Attach%2A> qui accepte un deuxième paramètre Boolean (défini à true).</span><span class="sxs-lookup"><span data-stu-id="25627-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="25627-190">Ceci donnera au dispositif de suivi des modifications l'indication de considérer l'objet modifié sans avoir à fournir de valeurs d'origine.</span><span class="sxs-lookup"><span data-stu-id="25627-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="25627-191">Dans cette approche, l'objet doit avoir un champ de version/horodatage.</span><span class="sxs-lookup"><span data-stu-id="25627-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="25627-192">Pour plus d’informations, consultez [États des objets et suivi des modifications](object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="25627-192">For more information, see [Object States and Change-Tracking](object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="25627-193">Si un objet d'entité se produit déjà dans le cache d'ID avec la même identité que l'objet attaché, une <xref:System.Data.Linq.DuplicateKeyException> est levée.</span><span class="sxs-lookup"><span data-stu-id="25627-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="25627-194">Lorsque vous effectuez l'attachement avec un ensemble `IEnumerable` d'objets, une <xref:System.Data.Linq.DuplicateKeyException> est levée lorsqu'une clé déjà existante est présente.</span><span class="sxs-lookup"><span data-stu-id="25627-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="25627-195">Les objets restants ne sont pas attachés.</span><span class="sxs-lookup"><span data-stu-id="25627-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25627-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25627-196">See also</span></span>

- [<span data-ttu-id="25627-197">Applications multicouches et distantes avec LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="25627-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="25627-198">Informations générales</span><span class="sxs-lookup"><span data-stu-id="25627-198">Background Information</span></span>](background-information.md)
