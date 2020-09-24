---
title: Activation de MARS (Multiple Active Result Sets)
description: Découvrez comment activer ou désactiver MARS dans une chaîne de connexion, qui fonctionne avec SQL Server afin que vous puissiez exécuter plusieurs traitements sur une seule connexion dans ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 0c5b4043b389c7dde39a477f90e82bbf654331f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156249"
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="fd2b4-103">Activation de MARS (Multiple Active Result Sets)</span><span class="sxs-lookup"><span data-stu-id="fd2b4-103">Enabling Multiple Active Result Sets</span></span>

<span data-ttu-id="fd2b4-104">MARS (Multiple Active Result Sets) est une fonctionnalité qui opère avec SQL Server pour permettre l’exécution de plusieurs lots sur une seule connexion.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-104">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="fd2b4-105">Quand MARS est activé pour une utilisation avec SQL Server, chaque objet de commande utilisé ajoute une session à la connexion.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-105">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd2b4-106">Une session MARS unique ouvre une connexion logique que MARS doit utiliser, puis une connexion logique pour chaque commande active.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-106">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="fd2b4-107">Activation et désactivation de MARS dans la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="fd2b4-107">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd2b4-108">Les chaînes de connexion suivantes utilisent l’exemple de base de données **AdventureWorks** fourni avec SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-108">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="fd2b4-109">Les chaînes de connexion fournies supposent que la base de données est installée sur un serveur nommé MSSQL1.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-109">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="fd2b4-110">Modifiez la chaîne de connexion en fonction des besoins de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-110">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="fd2b4-111">La fonctionnalité MARS est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-111">The MARS feature is disabled by default.</span></span> <span data-ttu-id="fd2b4-112">Vous pouvez l’activer en ajoutant la paire de mots clés « MultipleActiveResultSets = True » à votre chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-112">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="fd2b4-113">« True » est la seule valeur valide pour l’activation de MARS.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-113">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="fd2b4-114">L’exemple suivant montre comment se connecter à une instance de SQL Server et spécifier que MARS doit être activé.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-114">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 <span data-ttu-id="fd2b4-115">Vous pouvez désactiver MARS en ajoutant la paire de mots clés « MultipleActiveResultSets = False » à votre chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-115">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="fd2b4-116">« False » est la seule valeur valide pour la désactivation de MARS.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-116">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="fd2b4-117">La chaîne de connexion suivante montre comment désactiver MARS.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-117">The following connection string demonstrates how to disable MARS.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="fd2b4-118">Considérations particulières en relation avec l'utilisation de MARS</span><span class="sxs-lookup"><span data-stu-id="fd2b4-118">Special Considerations When Using MARS</span></span>  

 <span data-ttu-id="fd2b4-119">En général, les applications existantes ne doivent pas être modifiées pour utiliser une connexion prenant en charge MARS.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-119">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="fd2b4-120">Toutefois, si vous souhaitez utiliser les fonctionnalités MARS dans vos applications, vous devez comprendre les considérations spéciales suivantes.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-120">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="fd2b4-121">Entrelacement d'instructions</span><span class="sxs-lookup"><span data-stu-id="fd2b4-121">Statement Interleaving</span></span>  

 <span data-ttu-id="fd2b4-122">Les opérations MARS s’exécutent de façon synchrone sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-122">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="fd2b4-123">L’entrelacement des instructions SELECT et BULK INSERT est autorisé.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-123">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="fd2b4-124">Toutefois, les instructions DML (Data Manipulation Language) et DDL (Data Definition Language) s’exécutent de manière atomique.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-124">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="fd2b4-125">Toutes les instructions tentant de s’exécuter pendant l’exécution d’un lot atomique sont bloquées.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-125">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="fd2b4-126">L’exécution en parallèle au niveau du serveur n’est pas une fonctionnalité MARS.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-126">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="fd2b4-127">Si deux lots sont soumis sous une connexion MARS, l’un d’eux contenant une instruction SELECT, l’autre contenant une instruction DML, l’instruction DML peut commencer l’exécution dans le cadre de l’exécution de l’instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-127">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="fd2b4-128">Toutefois, l’instruction DML doit s’exécuter jusqu’à la fin pour que l’instruction SELECT puisse progresser.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-128">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="fd2b4-129">Si les deux instructions s’exécutent sous la même transaction, toute modification apportée par une instruction DML après le début de l’exécution de l’instruction SELECT n’est pas visible pour l’opération de lecture.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-129">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="fd2b4-130">Une instruction WAITFOR à l’intérieur d’une instruction SELECT ne génère pas la transaction pendant qu’elle est en attente, c’est-à-dire, jusqu’à ce que la première ligne soit produite.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-130">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="fd2b4-131">Cela implique qu’aucun autre lot ne peut s’exécuter dans la même connexion pendant qu’une instruction WAITFOR est en attente.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-131">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="fd2b4-132">Cache de session MARS</span><span class="sxs-lookup"><span data-stu-id="fd2b4-132">MARS Session Cache</span></span>  

 <span data-ttu-id="fd2b4-133">Lorsqu’une connexion est ouverte avec MARS activée, une session logique est créée, ce qui ajoute une surcharge supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-133">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="fd2b4-134">Afin de minimiser la charge et d’améliorer les performances, **SqlClient** met en cache la session MARS à l’intérieur d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-134">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="fd2b4-135">Le cache contient au plus 10 sessions MARS.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-135">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="fd2b4-136">Cette valeur n'est pas ajustable par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-136">This value is not user adjustable.</span></span> <span data-ttu-id="fd2b4-137">Si la limite de session est atteinte, une nouvelle session est créée, aucune erreur n’est générée.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-137">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="fd2b4-138">Le cache et les sessions qu’il contient sont partagées par connexion ; elles ne sont pas partagées entre les connexions.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-138">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="fd2b4-139">Lorsqu’une session est mise en production, elle est retournée au pool, à moins que la limite supérieure du pool ne soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-139">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="fd2b4-140">Si le pool de caches est plein, la session est fermée.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-140">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="fd2b4-141">Les sessions MARS n’expirent pas.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-141">MARS sessions do not expire.</span></span> <span data-ttu-id="fd2b4-142">Elles sont nettoyées uniquement lorsque l’objet de connexion est supprimé.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-142">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="fd2b4-143">Le cache de session MARS n’est pas préchargé.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-143">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="fd2b4-144">Il est chargé, car l’application requiert plus de sessions.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-144">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="fd2b4-145">Cohérence de thread</span><span class="sxs-lookup"><span data-stu-id="fd2b4-145">Thread Safety</span></span>  

 <span data-ttu-id="fd2b4-146">Les opérations MARS ne sont pas thread-safe.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-146">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="fd2b4-147">Regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="fd2b4-147">Connection Pooling</span></span>  

 <span data-ttu-id="fd2b4-148">Les connexions compatibles MARS sont regroupées par pool comme n’importe quelle autre connexion.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-148">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="fd2b4-149">Si une application ouvre deux connexions, l’une avec MARS activée et l’autre avec MARS désactivée, les deux connexions se trouvent dans des pools distincts.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-149">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="fd2b4-150">Pour plus d’informations, consultez [Regroupement de connexions SQL Server (ADO.NET)](../sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="fd2b4-150">For more information, see [SQL Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="fd2b4-151">Environnement d'exécution par lots SQL Server</span><span class="sxs-lookup"><span data-stu-id="fd2b4-151">SQL Server Batch Execution Environment</span></span>  

 <span data-ttu-id="fd2b4-152">Lorsqu’une connexion est ouverte, un environnement par défaut est défini.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-152">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="fd2b4-153">Cet environnement est ensuite copié dans une session MARS logique.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-153">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="fd2b4-154">L’environnement d’exécution par lot comprend les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="fd2b4-154">The batch execution environment includes the following components:</span></span>  
  
- <span data-ttu-id="fd2b4-155">Définir les options (par exemple, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span><span class="sxs-lookup"><span data-stu-id="fd2b4-155">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
- <span data-ttu-id="fd2b4-156">Contexte de sécurité (rôle d’utilisateur/d’application)</span><span class="sxs-lookup"><span data-stu-id="fd2b4-156">Security context (user/application role)</span></span>  
  
- <span data-ttu-id="fd2b4-157">Contexte de la base de données (base de données actuelle)</span><span class="sxs-lookup"><span data-stu-id="fd2b4-157">Database context (current database)</span></span>  
  
- <span data-ttu-id="fd2b4-158">Variables d’état d’exécution (par exemple, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span><span class="sxs-lookup"><span data-stu-id="fd2b4-158">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
- <span data-ttu-id="fd2b4-159">Tables temporaires de niveau supérieur</span><span class="sxs-lookup"><span data-stu-id="fd2b4-159">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="fd2b4-160">Avec MARS, un environnement d’exécution par défaut est associé à une connexion.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-160">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="fd2b4-161">Chaque nouveau traitement dont l’exécution commence sous une connexion donnée reçoit une copie de l’environnement par défaut.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-161">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="fd2b4-162">Chaque fois que le code est exécuté sous un lot donné, toutes les modifications apportées à l’environnement sont étendues au lot spécifique.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-162">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="fd2b4-163">Une fois l’exécution achevée, les paramètres d’exécution sont copiés dans l’environnement par défaut.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-163">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="fd2b4-164">Dans le cas où un lot unique émet plusieurs commandes à exécuter de façon séquentielle sous la même transaction, les sémantiques sont les mêmes que celles exposées par les connexions impliquant des clients ou des serveurs dans les versions précédentes.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-164">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="fd2b4-165">Exécution en parallèle</span><span class="sxs-lookup"><span data-stu-id="fd2b4-165">Parallel Execution</span></span>  

 <span data-ttu-id="fd2b4-166">MARS n’est pas conçu pour supprimer toutes les exigences de connexions multiples dans une application.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-166">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="fd2b4-167">Si une application a besoin d’une véritable exécution parallèle des commandes sur un serveur, vous devez utiliser plusieurs connexions.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-167">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="fd2b4-168">Par exemple, considérez le scénario suivant.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-168">For example, consider the following scenario.</span></span> <span data-ttu-id="fd2b4-169">Deux objets de commande sont créés, l’un pour le traitement d’un jeu de résultats et l’autre pour la mise à jour des données ; ils partagent une connexion commune via MARS.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-169">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="fd2b4-170">Dans ce scénario, `Transaction`.`Commit`</span><span class="sxs-lookup"><span data-stu-id="fd2b4-170">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="fd2b4-171">échoue lors de la mise à jour jusqu’à ce que tous les résultats aient été lus sur le premier objet de commande, en générant l’exception suivante :</span><span class="sxs-lookup"><span data-stu-id="fd2b4-171">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="fd2b4-172">Message : Le contexte de transaction est utilisé par une autre session.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-172">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="fd2b4-173">Source : Fournisseur de données SqlClient .NET</span><span class="sxs-lookup"><span data-stu-id="fd2b4-173">Source: .NET SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="fd2b4-174">Attendu : (Null)</span><span class="sxs-lookup"><span data-stu-id="fd2b4-174">Expected: (null)</span></span>  
  
 <span data-ttu-id="fd2b4-175">Reçu : System.Data.SqlClient.SqlException</span><span class="sxs-lookup"><span data-stu-id="fd2b4-175">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="fd2b4-176">Trois options permettent de prendre en charge ce scénario :</span><span class="sxs-lookup"><span data-stu-id="fd2b4-176">There are three options for handling this scenario:</span></span>  
  
1. <span data-ttu-id="fd2b4-177">Démarrez la transaction après la création du lecteur, afin qu’il ne fasse pas partie de la transaction.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-177">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="fd2b4-178">Chaque mise à jour devient alors sa propre transaction.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-178">Every update then becomes its own transaction.</span></span>  
  
2. <span data-ttu-id="fd2b4-179">Validez tout le travail une fois le lecteur fermé.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-179">Commit all work after the reader is closed.</span></span> <span data-ttu-id="fd2b4-180">Cela peut entraîner un lot important de mises à jour.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-180">This has the potential for a substantial batch of updates.</span></span>  
  
3. <span data-ttu-id="fd2b4-181">N’utilisez pas MARS ; utilisez plutôt une connexion distincte pour chaque objet de commande comme avant MARS.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-181">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="fd2b4-182">Détection de la prise en charge de MARS</span><span class="sxs-lookup"><span data-stu-id="fd2b4-182">Detecting MARS Support</span></span>  

 <span data-ttu-id="fd2b4-183">Une application peut vérifier la prise en charge de MARS en lisant la valeur `SqlConnection.ServerVersion`.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-183">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="fd2b4-184">Le nombre majeur doit être 9 pour SQL Server 2005 et 10 pour SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="fd2b4-184">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd2b4-185">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd2b4-185">See also</span></span>

- [<span data-ttu-id="fd2b4-186">MARS (Multiple Active Result Sets)</span><span class="sxs-lookup"><span data-stu-id="fd2b4-186">Multiple Active Result Sets (MARS)</span></span>](multiple-active-result-sets-mars.md)
- [<span data-ttu-id="fd2b4-187">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fd2b4-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
