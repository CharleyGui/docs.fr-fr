---
title: Accès concurrentiel optimiste
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: 681044a9d905f052516ba240e25ffff84928e58e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166636"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="d3a60-102">Accès concurrentiel optimiste</span><span class="sxs-lookup"><span data-stu-id="d3a60-102">Optimistic Concurrency</span></span>

<span data-ttu-id="d3a60-103">Dans un environnement multi-utilisateur, il existe deux modèles pour la mise à jour de données dans une base de données : l'accès simultané optimiste et l'accès simultané pessimiste.</span><span class="sxs-lookup"><span data-stu-id="d3a60-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="d3a60-104">L'objet <xref:System.Data.DataSet> est conçu pour privilégier l'utilisation de l'accès simultané optimiste pour les activités longues, comme lors de la communication à distance de données ou de l'interaction avec ces dernières.</span><span class="sxs-lookup"><span data-stu-id="d3a60-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="d3a60-105">L'accès simultané pessimiste implique le verrouillage de lignes à la source de données pour empêcher que d'autres utilisateurs modifient des données d'une manière affectant l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="d3a60-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="d3a60-106">Dans un modèle pessimiste, lorsqu'un utilisateur effectue une action entraînant l'application d'un verrou, les autres utilisateurs ne peuvent pas effectuer d'actions qui créeraient un conflit avec le verrou tant que le propriétaire de ce dernier ne l'a pas libéré.</span><span class="sxs-lookup"><span data-stu-id="d3a60-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="d3a60-107">Ce modèle est principalement utilisé dans les environnements où les conflits relatifs aux données sont fréquents, de sorte que le coût de la protection des données par verrous est inférieur à celui de la restauration des transactions en cas de conflits d’accès simultané.</span><span class="sxs-lookup"><span data-stu-id="d3a60-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="d3a60-108">Par conséquent, dans un modèle d'accès simultané pessimiste, un utilisateur qui met à jour une ligne crée un verrou.</span><span class="sxs-lookup"><span data-stu-id="d3a60-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="d3a60-109">Jusqu'à ce que cet utilisateur ait terminé sa mise à jour et libéré le verrou, personne d'autre ne peut modifier cette ligne.</span><span class="sxs-lookup"><span data-stu-id="d3a60-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="d3a60-110">C'est pourquoi il est préférable d'implémenter l'accès simultané pessimiste lorsque les temps de verrouillage sont courts, comme c'est le cas pour le traitement d'enregistrements par programme.</span><span class="sxs-lookup"><span data-stu-id="d3a60-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="d3a60-111">L'accès simultané pessimiste ne constitue pas la solution la plus adaptée lorsque des utilisateurs interagissent avec les données, ce qui entraîne le verrouillage d'enregistrements pendant des laps de temps relativement longs.</span><span class="sxs-lookup"><span data-stu-id="d3a60-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3a60-112">Si vous devez mettre à jour plusieurs lignes en une même opération, la création d’une transaction constitue une option plus adaptée que l’utilisation du verrouillage pessimiste.</span><span class="sxs-lookup"><span data-stu-id="d3a60-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="d3a60-113">Au contraire, les utilisateurs qui ont recours à un accès simultané optimiste ne verrouillent pas une ligne lorsqu'ils la lisent.</span><span class="sxs-lookup"><span data-stu-id="d3a60-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="d3a60-114">Lorsqu'un utilisateur souhaite mettre à jour une ligne, l'application doit déterminer si un autre utilisateur a modifié cette ligne depuis sa dernière lecture.</span><span class="sxs-lookup"><span data-stu-id="d3a60-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="d3a60-115">L'accès simultané optimiste est généralement utilisé dans les environnements où les conflits relatifs aux données sont rares.</span><span class="sxs-lookup"><span data-stu-id="d3a60-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="d3a60-116">L'accès simultané optimiste améliore les performances, dans la mesure où aucun verrouillage des enregistrements n'est requis et où le verrouillage d'enregistrements nécessite des ressources serveur supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="d3a60-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="d3a60-117">Il faut également savoir que la gestion des verrous d'enregistrements requiert une connexion permanente au serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="d3a60-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="d3a60-118">Parce que ce n'est pas le cas dans un modèle d'accès simultané optimiste, les connexions au serveur sont disponibles pour traiter plus rapidement un nombre important de clients.</span><span class="sxs-lookup"><span data-stu-id="d3a60-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="d3a60-119">Dans un modèle d'accès simultané optimiste, une violation est réputée avoir eu lieu si, après réception par un utilisateur d'une valeur provenant de la base de données, un autre utilisateur modifie cette valeur avant que le premier n'ait tenté de le faire.</span><span class="sxs-lookup"><span data-stu-id="d3a60-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="d3a60-120">La manière dont le serveur résout une violation de l'accès simultané est bien illustrée par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d3a60-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="d3a60-121">Les tableaux ci-après suivent un exemple d'accès simultané optimiste.</span><span class="sxs-lookup"><span data-stu-id="d3a60-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="d3a60-122">À 13h00, l'utilisateur 1 lit une ligne de la base de données contenant les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3a60-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="d3a60-123">**CustID     LastName     FirstName**</span><span class="sxs-lookup"><span data-stu-id="d3a60-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="d3a60-124">101          Smith             Bob</span><span class="sxs-lookup"><span data-stu-id="d3a60-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="d3a60-125">Nom de la colonne</span><span class="sxs-lookup"><span data-stu-id="d3a60-125">Column name</span></span>|<span data-ttu-id="d3a60-126">Valeur d'origine</span><span class="sxs-lookup"><span data-stu-id="d3a60-126">Original value</span></span>|<span data-ttu-id="d3a60-127">Valeur actuelle</span><span class="sxs-lookup"><span data-stu-id="d3a60-127">Current value</span></span>|<span data-ttu-id="d3a60-128">Valeur dans la base de données</span><span class="sxs-lookup"><span data-stu-id="d3a60-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d3a60-129">CustID</span><span class="sxs-lookup"><span data-stu-id="d3a60-129">CustID</span></span>|<span data-ttu-id="d3a60-130">101</span><span class="sxs-lookup"><span data-stu-id="d3a60-130">101</span></span>|<span data-ttu-id="d3a60-131">101</span><span class="sxs-lookup"><span data-stu-id="d3a60-131">101</span></span>|<span data-ttu-id="d3a60-132">101</span><span class="sxs-lookup"><span data-stu-id="d3a60-132">101</span></span>|  
|<span data-ttu-id="d3a60-133">LastName</span><span class="sxs-lookup"><span data-stu-id="d3a60-133">LastName</span></span>|<span data-ttu-id="d3a60-134">Smith</span><span class="sxs-lookup"><span data-stu-id="d3a60-134">Smith</span></span>|<span data-ttu-id="d3a60-135">Smith</span><span class="sxs-lookup"><span data-stu-id="d3a60-135">Smith</span></span>|<span data-ttu-id="d3a60-136">Smith</span><span class="sxs-lookup"><span data-stu-id="d3a60-136">Smith</span></span>|  
|<span data-ttu-id="d3a60-137">FirstName</span><span class="sxs-lookup"><span data-stu-id="d3a60-137">FirstName</span></span>|<span data-ttu-id="d3a60-138">Bob</span><span class="sxs-lookup"><span data-stu-id="d3a60-138">Bob</span></span>|<span data-ttu-id="d3a60-139">Bob</span><span class="sxs-lookup"><span data-stu-id="d3a60-139">Bob</span></span>|<span data-ttu-id="d3a60-140">Bob</span><span class="sxs-lookup"><span data-stu-id="d3a60-140">Bob</span></span>|  
  
 <span data-ttu-id="d3a60-141">À 13h01, l'utilisateur 2 lit la même ligne.</span><span class="sxs-lookup"><span data-stu-id="d3a60-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="d3a60-142">À 1:03 h 00, utilisateur2 remplace **FirstName** de « Bob » par « Robert » et met à jour la base de données.</span><span class="sxs-lookup"><span data-stu-id="d3a60-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="d3a60-143">Nom de la colonne</span><span class="sxs-lookup"><span data-stu-id="d3a60-143">Column name</span></span>|<span data-ttu-id="d3a60-144">Valeur d'origine</span><span class="sxs-lookup"><span data-stu-id="d3a60-144">Original value</span></span>|<span data-ttu-id="d3a60-145">Valeur actuelle</span><span class="sxs-lookup"><span data-stu-id="d3a60-145">Current value</span></span>|<span data-ttu-id="d3a60-146">Valeur dans la base de données</span><span class="sxs-lookup"><span data-stu-id="d3a60-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d3a60-147">CustID</span><span class="sxs-lookup"><span data-stu-id="d3a60-147">CustID</span></span>|<span data-ttu-id="d3a60-148">101</span><span class="sxs-lookup"><span data-stu-id="d3a60-148">101</span></span>|<span data-ttu-id="d3a60-149">101</span><span class="sxs-lookup"><span data-stu-id="d3a60-149">101</span></span>|<span data-ttu-id="d3a60-150">101</span><span class="sxs-lookup"><span data-stu-id="d3a60-150">101</span></span>|  
|<span data-ttu-id="d3a60-151">LastName</span><span class="sxs-lookup"><span data-stu-id="d3a60-151">LastName</span></span>|<span data-ttu-id="d3a60-152">Smith</span><span class="sxs-lookup"><span data-stu-id="d3a60-152">Smith</span></span>|<span data-ttu-id="d3a60-153">Smith</span><span class="sxs-lookup"><span data-stu-id="d3a60-153">Smith</span></span>|<span data-ttu-id="d3a60-154">Smith</span><span class="sxs-lookup"><span data-stu-id="d3a60-154">Smith</span></span>|  
|<span data-ttu-id="d3a60-155">FirstName</span><span class="sxs-lookup"><span data-stu-id="d3a60-155">FirstName</span></span>|<span data-ttu-id="d3a60-156">Bob</span><span class="sxs-lookup"><span data-stu-id="d3a60-156">Bob</span></span>|<span data-ttu-id="d3a60-157">Robert</span><span class="sxs-lookup"><span data-stu-id="d3a60-157">Robert</span></span>|<span data-ttu-id="d3a60-158">Bob</span><span class="sxs-lookup"><span data-stu-id="d3a60-158">Bob</span></span>|  
  
 <span data-ttu-id="d3a60-159">La mise à jour réussit car les valeurs de la base de données au moment de la mise à jour correspondent aux valeurs d'origine dont dispose l'utilisateur 2.</span><span class="sxs-lookup"><span data-stu-id="d3a60-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="d3a60-160">À 13h05, l'utilisateur 1 modifie la valeur de prénom pour remplacer « Bob » par « James » et tente de mettre à jour la base de données.</span><span class="sxs-lookup"><span data-stu-id="d3a60-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="d3a60-161">Nom de la colonne</span><span class="sxs-lookup"><span data-stu-id="d3a60-161">Column name</span></span>|<span data-ttu-id="d3a60-162">Valeur d'origine</span><span class="sxs-lookup"><span data-stu-id="d3a60-162">Original value</span></span>|<span data-ttu-id="d3a60-163">Valeur actuelle</span><span class="sxs-lookup"><span data-stu-id="d3a60-163">Current value</span></span>|<span data-ttu-id="d3a60-164">Valeur dans la base de données</span><span class="sxs-lookup"><span data-stu-id="d3a60-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d3a60-165">CustID</span><span class="sxs-lookup"><span data-stu-id="d3a60-165">CustID</span></span>|<span data-ttu-id="d3a60-166">101</span><span class="sxs-lookup"><span data-stu-id="d3a60-166">101</span></span>|<span data-ttu-id="d3a60-167">101</span><span class="sxs-lookup"><span data-stu-id="d3a60-167">101</span></span>|<span data-ttu-id="d3a60-168">101</span><span class="sxs-lookup"><span data-stu-id="d3a60-168">101</span></span>|  
|<span data-ttu-id="d3a60-169">LastName</span><span class="sxs-lookup"><span data-stu-id="d3a60-169">LastName</span></span>|<span data-ttu-id="d3a60-170">Smith</span><span class="sxs-lookup"><span data-stu-id="d3a60-170">Smith</span></span>|<span data-ttu-id="d3a60-171">Smith</span><span class="sxs-lookup"><span data-stu-id="d3a60-171">Smith</span></span>|<span data-ttu-id="d3a60-172">Smith</span><span class="sxs-lookup"><span data-stu-id="d3a60-172">Smith</span></span>|  
|<span data-ttu-id="d3a60-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="d3a60-173">FirstName</span></span>|<span data-ttu-id="d3a60-174">Bob</span><span class="sxs-lookup"><span data-stu-id="d3a60-174">Bob</span></span>|<span data-ttu-id="d3a60-175">James</span><span class="sxs-lookup"><span data-stu-id="d3a60-175">James</span></span>|<span data-ttu-id="d3a60-176">Robert</span><span class="sxs-lookup"><span data-stu-id="d3a60-176">Robert</span></span>|  
  
 <span data-ttu-id="d3a60-177">À ce stade, l'utilisateur 1 est confronté à une violation d'accès simultané optimiste, car la valeur de la base de données (« Robert ») ne correspond plus à la valeur d'origine qu'attendait l'utilisateur 1 (« Bob »).</span><span class="sxs-lookup"><span data-stu-id="d3a60-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="d3a60-178">La violation d'accès concurrentiel vous indique simplement que la mise à jour a échoué.</span><span class="sxs-lookup"><span data-stu-id="d3a60-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="d3a60-179">Il convient maintenant de décider si les modifications apportées par l'utilisateur 2 devront être remplacées par celles de l'utilisateur 1 ou si ces dernières devront être annulées.</span><span class="sxs-lookup"><span data-stu-id="d3a60-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="d3a60-180">Recherche des violations d'accès simultané optimiste</span><span class="sxs-lookup"><span data-stu-id="d3a60-180">Testing for Optimistic Concurrency Violations</span></span>  

 <span data-ttu-id="d3a60-181">Il existe plusieurs techniques qui permettent de déceler la présence d'une violation d'accès simultané optimiste.</span><span class="sxs-lookup"><span data-stu-id="d3a60-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="d3a60-182">L'une d'entre elles consiste à inclure une colonne horodateur dans la table.</span><span class="sxs-lookup"><span data-stu-id="d3a60-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="d3a60-183">Les bases de données proposent généralement une fonctionnalité d'horodatage qui peut être utilisée pour connaître la date et l'heure de la dernière mise à jour d'un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d3a60-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="d3a60-184">En utilisant cette technique, une colonne horodateur est incluse dans la définition de la table.</span><span class="sxs-lookup"><span data-stu-id="d3a60-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="d3a60-185">Chaque fois que l'enregistrement est mis à jour, l'horodatage est également mis à jour en fonction de la date et de l'heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="d3a60-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="d3a60-186">Dans un test visant à déceler la présence de violations d'accès simultané optimiste, la colonne horodateur est retournée avec toute requête liée au contenu de la table.</span><span class="sxs-lookup"><span data-stu-id="d3a60-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="d3a60-187">Lors d'une tentative de mise à jour, la valeur d'horodatage figurant dans la base de données est comparée à la valeur d'origine contenue dans la ligne modifiée.</span><span class="sxs-lookup"><span data-stu-id="d3a60-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="d3a60-188">Si les valeurs correspondent, la modification est apportée et la colonne horodateur est mise à jour en fonction de la date et de l'heure actuelles afin de refléter la modification.</span><span class="sxs-lookup"><span data-stu-id="d3a60-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="d3a60-189">Si elles ne correspondent pas, une violation d'accès simultané optimiste s'est produite.</span><span class="sxs-lookup"><span data-stu-id="d3a60-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="d3a60-190">Une autre technique de recherche des violations d'accès simultané optimiste consiste à vérifier que toutes les valeurs de colonne d'origine d'une ligne correspondent toujours à celles qui figurent dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="d3a60-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="d3a60-191">Examinons, par exemple, la requête suivante :</span><span class="sxs-lookup"><span data-stu-id="d3a60-191">For example, consider the following query:</span></span>  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="d3a60-192">Pour tester une violation de l’accès concurrentiel optimiste lors de la mise à jour d’une ligne dans **table1**, vous devez émettre l’instruction UPDATE suivante :</span><span class="sxs-lookup"><span data-stu-id="d3a60-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="d3a60-193">Tant que les valeurs d'origine correspondent à celles qui figurent dans la base de données, la mise à jour est effectuée.</span><span class="sxs-lookup"><span data-stu-id="d3a60-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="d3a60-194">Si une valeur a été modifiée, la mise à jour ne modifiera pas la ligne car la clause WHERE ne trouvera pas de correspondance.</span><span class="sxs-lookup"><span data-stu-id="d3a60-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="d3a60-195">Notez qu'il est recommandé de toujours retourner une valeur de clé primaire unique dans votre requête.</span><span class="sxs-lookup"><span data-stu-id="d3a60-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="d3a60-196">Sinon, l'instruction UPDATE précédente risque de mettre à jour plusieurs lignes, ce qui n'est pas nécessairement dans vos intentions.</span><span class="sxs-lookup"><span data-stu-id="d3a60-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="d3a60-197">Si une colonne de votre source de données accepte les valeurs null, vous devrez peut-être étendre votre clause WHERE pour vérifier s'il existe une référence null dans votre table locale et sa correspondance dans votre source de données.</span><span class="sxs-lookup"><span data-stu-id="d3a60-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="d3a60-198">Par exemple, l'instruction UPDATE suivante vérifie qu'une référence null dans la ligne locale correspond toujours à une référence null dans la source de données, ou si la valeur dans la ligne locale correspond toujours à celle de la source de données.</span><span class="sxs-lookup"><span data-stu-id="d3a60-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="d3a60-199">Vous pouvez aussi choisir d'appliquer des critères moins restrictifs lorsque vous utilisez un modèle d'accès simultané optimiste.</span><span class="sxs-lookup"><span data-stu-id="d3a60-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="d3a60-200">Par exemple, utiliser uniquement les colonnes de clé primaire dans la clause WHERE aboutit au remplacement des données, que les autres colonnes aient ou non subi une mise à jour depuis la dernière requête.</span><span class="sxs-lookup"><span data-stu-id="d3a60-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="d3a60-201">Vous pouvez aussi appliquer une clause WHERE à certaines colonnes uniquement, ce qui aura pour effet de remplacer les données, sauf si des champs spécifiques ont été mis à jour depuis la dernière requête les concernant.</span><span class="sxs-lookup"><span data-stu-id="d3a60-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="d3a60-202">Événement DataAdapter.RowUpdated</span><span class="sxs-lookup"><span data-stu-id="d3a60-202">The DataAdapter.RowUpdated Event</span></span>  

 <span data-ttu-id="d3a60-203">L’événement **RowUpdated** de l' <xref:System.Data.Common.DataAdapter> objet peut être utilisé conjointement avec les techniques décrites précédemment, afin de fournir une notification à votre application en cas de violations de l’accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="d3a60-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="d3a60-204">**RowUpdated** se produit après chaque tentative de mise à jour d’une ligne **modifiée** à partir d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="d3a60-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="d3a60-205">Cela vous permet d'ajouter un code de gestion spécial, qui traitera les exceptions le cas échéant, ajoutera des informations d'erreur personnalisées, ajoutera une logique pour les nouvelles tentatives, etc.</span><span class="sxs-lookup"><span data-stu-id="d3a60-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="d3a60-206">L' <xref:System.Data.Common.RowUpdatedEventArgs> objet retourne une propriété **RecordsAffected** contenant le nombre de lignes affectées par une commande de mise à jour particulière pour une ligne modifiée dans une table.</span><span class="sxs-lookup"><span data-stu-id="d3a60-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="d3a60-207">En définissant la commande de mise à jour pour tester l’accès concurrentiel optimiste, la propriété **RecordsAffected** retourne la valeur 0 lorsqu’une violation d’accès concurrentiel optimiste s’est produite, car aucun enregistrement n’a été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="d3a60-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="d3a60-208">Dans ce cas, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="d3a60-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="d3a60-209">L’événement **RowUpdated** vous permet de gérer cette occurrence et d’éviter l’exception en définissant une valeur **RowUpdatedEventArgs. Status** appropriée, telle que **UpdateStatus. SkipCurrentRow**.</span><span class="sxs-lookup"><span data-stu-id="d3a60-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="d3a60-210">Pour plus d’informations sur l’événement **RowUpdated** , consultez [gestion des événements DataAdapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="d3a60-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="d3a60-211">Si vous le souhaitez, vous pouvez affecter à **DataAdapter. ContinueUpdateOnError** la **valeur true**, avant d’appeler **Update**, et répondre aux informations d’erreur stockées dans la propriété **RowError** d’une ligne particulière lorsque la **mise à jour** est terminée.</span><span class="sxs-lookup"><span data-stu-id="d3a60-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="d3a60-212">Pour plus d’informations, consultez [informations sur les erreurs de ligne](./dataset-datatable-dataview/row-error-information.md).</span><span class="sxs-lookup"><span data-stu-id="d3a60-212">For more information, see [Row Error Information](./dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="d3a60-213">Exemple d'accès simultané optimiste</span><span class="sxs-lookup"><span data-stu-id="d3a60-213">Optimistic Concurrency Example</span></span>  

 <span data-ttu-id="d3a60-214">Voici un exemple simple qui définit le **UpdateCommand** d’un **DataAdapter** pour tester l’accès concurrentiel optimiste, puis utilise l’événement **RowUpdated** pour tester les violations de l’accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="d3a60-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="d3a60-215">En cas de violation de l’accès concurrentiel optimiste, l’application définit le **RowError** de la ligne pour laquelle la mise à jour a été émise afin de refléter une violation d’accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="d3a60-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="d3a60-216">Notez que les valeurs de paramètre transmises à la clause WHERE de la commande UPDATE sont mappées aux valeurs **d’origine** de leurs colonnes respectives.</span><span class="sxs-lookup"><span data-stu-id="d3a60-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3a60-217">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3a60-217">See also</span></span>

- [<span data-ttu-id="d3a60-218">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d3a60-218">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="d3a60-219">Mise à jour des sources de données avec les DataAdapter</span><span class="sxs-lookup"><span data-stu-id="d3a60-219">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="d3a60-220">Informations sur l'erreur de ligne</span><span class="sxs-lookup"><span data-stu-id="d3a60-220">Row Error Information</span></span>](./dataset-datatable-dataview/row-error-information.md)
- [<span data-ttu-id="d3a60-221">Transactions et accès simultané</span><span class="sxs-lookup"><span data-stu-id="d3a60-221">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="d3a60-222">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d3a60-222">ADO.NET Overview</span></span>](ado-net-overview.md)
