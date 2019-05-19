---
title: Intégration de System.Transactions à SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 09fcf3f1a7e58a4bd8c2c6b0d25c24f32ea5ec5e
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880594"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="f7ab9-102">Intégration de System.Transactions à SQL Server</span><span class="sxs-lookup"><span data-stu-id="f7ab9-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="f7ab9-103">Le .NET Framework version 2.0 a introduit une infrastructure de transaction qui est accessible via la <xref:System.Transactions> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-103">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="f7ab9-104">Cette infrastructure expose des transactions d’une manière qui est entièrement intégré dans le .NET Framework, notamment ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-104">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="f7ab9-105">Outre les améliorations de programmabilité, <xref:System.Transactions> et ADO.NET peuvent collaborer pour coordonner les optimisations lorsque vous travaillez avec des transactions.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-105">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="f7ab9-106">Une transaction susceptible d'être promue est une transaction légère (locale) qui peut être promue automatiquement en une transaction entièrement distribuée en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="f7ab9-107">En commençant par ADO.NET 2.0, <xref:System.Data.SqlClient> prend en charge les transactions pouvant être promues lorsque vous travaillez avec SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-107">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="f7ab9-108">Une transaction pouvant être promue n'invoque pas la charge supplémentaire d'une transaction distribuée à moins qu'elle ne soit requise.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="f7ab9-109">Transactions pouvant être promues sont automatiques et ne requièrent aucune intervention du développeur.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="f7ab9-110">Transactions pouvant être promues sont disponibles uniquement lorsque vous utilisez le fournisseur de données .NET Framework pour SQL Server (`SqlClient`) avec SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-110">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="f7ab9-111">Création de transactions pouvant être promues</span><span class="sxs-lookup"><span data-stu-id="f7ab9-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="f7ab9-112">Le fournisseur .NET Framework pour SQL Server prend en charge les transactions pouvant être promues, qui sont gérées via les classes dans le .NET Framework <xref:System.Transactions> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-112">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="f7ab9-113">Les transactions pouvant être promues optimisent les transactions distribuées en différant la création d'une transaction distribuée jusqu'à ce qu'elle soit nécessaire.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="f7ab9-114">Si un seul gestionnaire de ressources est requis, aucune transaction distribuée n'a lieu.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7ab9-115">Dans un scénario de niveau de confiance partiel, l'objet <xref:System.Transactions.DistributedTransactionPermission> est requis lorsqu'une transaction est promue en transaction distribuée.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="f7ab9-116">Scénarios de transaction pouvant être promue</span><span class="sxs-lookup"><span data-stu-id="f7ab9-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="f7ab9-117">Les transactions distribuées consomment généralement une partie importante des ressources système, car elles sont gérées par Microsoft Distributed Transaction Coordinator (MS DTC), qui intègre tous les gestionnaires de ressources auxquels la transaction accède.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="f7ab9-118">Une transaction pouvant être promue est une forme spéciale d’un <xref:System.Transactions> transaction qui délègue efficacement le travail à une simple transaction SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="f7ab9-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, et SQL Server coordonner le travail impliqué dans la gestion de la transaction, la promotion à une transaction entièrement distribuée en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="f7ab9-120">L'avantage de l'utilisation de transactions pouvant être promues réside dans le fait que, quand une connexion est ouverte à l'aide d'une transaction <xref:System.Transactions.TransactionScope> active alors qu'aucune autre connexion n'est ouverte, la transaction est validée comme transaction légère, au lieu de générer la charge supplémentaire d'une transaction entièrement distribuée.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="f7ab9-121">Mots clés des chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="f7ab9-121">Connection String Keywords</span></span>  
 <span data-ttu-id="f7ab9-122">La propriété <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> prend en charge un mot clé, `Enlist`, qui indique si <xref:System.Data.SqlClient> détecte des contextes transactionnels et inscrit automatiquement la connexion dans une transaction distribuée.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="f7ab9-123">Si `Enlist=true`, la connexion est automatiquement inscrite dans le contexte de transaction actuel du thread qui s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="f7ab9-124">Si `Enlist=false`, la connexion `SqlClient` n'interagit pas avec une transaction distribuée.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="f7ab9-125">La valeur par défaut de `Enlist` est true.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="f7ab9-126">Si `Enlist` n'est pas spécifié dans la chaîne de connexion, la connexion est automatiquement inscrite dans une transaction distribuée détectée lors de l'ouverture de la connexion.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="f7ab9-127">Les mots clés `Transaction Binding` d'une chaîne de connexion <xref:System.Data.SqlClient.SqlConnection> contrôlent l'association de la connexion à une transaction `System.Transactions` inscrite.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="f7ab9-128">Il est également possible d'utiliser la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> d'un objet <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="f7ab9-129">Le tableau suivant décrit les valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="f7ab9-130">Mot clé</span><span class="sxs-lookup"><span data-stu-id="f7ab9-130">Keyword</span></span>|<span data-ttu-id="f7ab9-131">Description</span><span class="sxs-lookup"><span data-stu-id="f7ab9-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7ab9-132">Implicit Unbind</span><span class="sxs-lookup"><span data-stu-id="f7ab9-132">Implicit Unbind</span></span>|<span data-ttu-id="f7ab9-133">Valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-133">The default.</span></span> <span data-ttu-id="f7ab9-134">La connexion se détache de la transaction une fois cette dernière terminée et revient au mode de validation automatique.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="f7ab9-135">Explicit Unbind</span><span class="sxs-lookup"><span data-stu-id="f7ab9-135">Explicit Unbind</span></span>|<span data-ttu-id="f7ab9-136">La connexion reste attachée à la transaction jusqu'à la fermeture de cette dernière.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="f7ab9-137">La connexion échoue si la transaction associée n'est pas active ou ne correspond pas à la propriété <xref:System.Transactions.Transaction.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="f7ab9-138">Utilisation de TransactionScope</span><span class="sxs-lookup"><span data-stu-id="f7ab9-138">Using TransactionScope</span></span>  
 <span data-ttu-id="f7ab9-139">La classe <xref:System.Transactions.TransactionScope> rend un bloc de code transactionnel en inscrivant implicitement des connexions dans une transaction distribuée.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="f7ab9-140">Vous devez appeler la méthode <xref:System.Transactions.TransactionScope.Complete%2A> à la fin du bloc <xref:System.Transactions.TransactionScope> avant de le quitter.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="f7ab9-141">Le fait de quitter le bloc invoque la méthode <xref:System.Transactions.TransactionScope.Dispose%2A> .</span><span class="sxs-lookup"><span data-stu-id="f7ab9-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="f7ab9-142">Si une exception a été levée qui a pour effet que le code sorte de la portée, la transaction est considérée comme abandonnée.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="f7ab9-143">Il est recommandé d'utiliser un bloc `using` pour s'assurer que la méthode <xref:System.Transactions.TransactionScope.Dispose%2A> est appelée sur l'objet <xref:System.Transactions.TransactionScope> en cas de sortie du bloc using.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="f7ab9-144">La non-validation ou la non-restauration des transactions en attente peut considérablement nuire aux performances, le délai d'attente par défaut de l'objet <xref:System.Transactions.TransactionScope> étant d'une minute.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="f7ab9-145">Si vous n'utilisez pas d'instruction `using` , vous devez effectuer tout le travail dans un bloc `Try` et appeler explicitement la méthode <xref:System.Transactions.TransactionScope.Dispose%2A> dans le bloc `Finally` .</span><span class="sxs-lookup"><span data-stu-id="f7ab9-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="f7ab9-146">Si une exception est levée dans l'objet <xref:System.Transactions.TransactionScope>, la transaction est marquée comme incohérente et est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="f7ab9-147">Elle sera annulée lors de la suppression du <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="f7ab9-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="f7ab9-148">Si aucune exception n'est levée, les transactions participantes sont validées.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7ab9-149">La classe `TransactionScope` crée une transaction dont la propriété <xref:System.Transactions.Transaction.IsolationLevel%2A> a par défaut la valeur `Serializable` .</span><span class="sxs-lookup"><span data-stu-id="f7ab9-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="f7ab9-150">En fonction de votre application, vous devez envisager d'abaisser le niveau d'isolation afin d'éviter une contention élevée dans votre application.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7ab9-151">Il est recommandé de n'effectuer des mises à jour, des insertions et des suppressions que dans des transactions distribuées car ces opérations consomment des ressources de base de données importantes.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="f7ab9-152">Les instructions select risquent de verrouiller inutilement les ressources de base de données ; dans certains cas, vous pouvez être amené à utiliser des transactions pour effectuer des sélections.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="f7ab9-153">Tout travail autre qu'un travail de base de données doit être réalisé en dehors de la transaction, à moins qu'il n'implique d'autres gestionnaires de ressources.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="f7ab9-154">Bien qu'une exception dans la transaction empêche la validation de celle-ci, la classe <xref:System.Transactions.TransactionScope> n'a aucune disposition pour annuler les modifications que votre code a apportées en dehors de la transaction proprement dite.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="f7ab9-155">Pour intervenir lors de l'annulation de la transaction, vous devez écrire votre propre implémentation de l'interface <xref:System.Transactions.IEnlistmentNotification> et vous inscrire explicitement dans la transaction.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7ab9-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="f7ab9-156">Example</span></span>  
 <span data-ttu-id="f7ab9-157">L'utilisation de l'espace de noms <xref:System.Transactions> exige que vous disposiez d'une référence à System.Transactions.dll.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="f7ab9-158">La fonction suivante montre comment créer une transaction pouvant être promue en relation avec deux instances différentes de SQL Server, représentées par deux objets <xref:System.Data.SqlClient.SqlConnection> différents, enveloppés dans un bloc <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="f7ab9-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="f7ab9-159">Le code crée le bloc <xref:System.Transactions.TransactionScope> avec une instruction `using` et ouvre la première connexion qui l'inscrit automatiquement dans le <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="f7ab9-160">La transaction est initialement inscrite comme transaction légère, pas comme transaction entièrement distribuée.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="f7ab9-161">La seconde connexion est inscrite dans l'objet <xref:System.Transactions.TransactionScope> uniquement si la commande dans la première connexion ne lève pas une exception.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="f7ab9-162">Une fois la seconde connexion ouverte, la transaction est automatiquement promue en transaction entièrement distribuée.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="f7ab9-163">La méthode <xref:System.Transactions.TransactionScope.Complete%2A> est appelée, ce qui valide la transaction uniquement si aucune exception n'a été levée.</span><span class="sxs-lookup"><span data-stu-id="f7ab9-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="f7ab9-164">Si une exception a été levée dans le bloc <xref:System.Transactions.TransactionScope> , la méthode `Complete` n'est pas appelée et la transaction distribuée est annulée lors de la suppression de l'objet <xref:System.Transactions.TransactionScope> à la fin de son bloc `using` .</span><span class="sxs-lookup"><span data-stu-id="f7ab9-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can   
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the   
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2   
                // only when there is a chance that the transaction can commit.     
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not   
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can   
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the   
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2   
                ' only when there is a chance that the transaction can commit.     
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will   
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7ab9-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7ab9-165">See also</span></span>

- [<span data-ttu-id="f7ab9-166">Transactions et accès concurrentiel</span><span class="sxs-lookup"><span data-stu-id="f7ab9-166">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [<span data-ttu-id="f7ab9-167">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="f7ab9-167">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
