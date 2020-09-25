---
title: Fournisseur de statistiques pour SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: 21bf7662094d5bc8948a1ce6378c454713cacc62
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183115"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="a46fb-102">Fournisseur de statistiques pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="a46fb-102">Provider Statistics for SQL Server</span></span>

<span data-ttu-id="a46fb-103">À partir du .NET Framework version 2.0, le fournisseur de données .NET Framework pour SQL Server prend en charge des statistiques d'exécution.</span><span class="sxs-lookup"><span data-stu-id="a46fb-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="a46fb-104">Vous devez activer les statistiques en affectant à la propriété <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> de l’objet <xref:System.Data.SqlClient.SqlConnection> la valeur `True` une fois que vous avez créé un objet de connexion valide.</span><span class="sxs-lookup"><span data-stu-id="a46fb-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="a46fb-105">Une fois les statistiques activées, vous pouvez les examiner comme un « instantané dans le temps » en extrayant une référence <xref:System.Collections.IDictionary> via la méthode <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> de l’objet <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="a46fb-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="a46fb-106">Vous énumérez la liste sous la forme d’un ensemble d’entrées de dictionnaire avec des paires nom/valeur.</span><span class="sxs-lookup"><span data-stu-id="a46fb-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="a46fb-107">Ces paires nom/valeur ne sont pas ordonnées.</span><span class="sxs-lookup"><span data-stu-id="a46fb-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="a46fb-108">À tout moment, vous pouvez appeler la méthode <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> de l’objet <xref:System.Data.SqlClient.SqlConnection> pour réinitialiser les compteurs.</span><span class="sxs-lookup"><span data-stu-id="a46fb-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="a46fb-109">Si la collecte de statistiques n’a pas été activée, aucune exception n’est générée.</span><span class="sxs-lookup"><span data-stu-id="a46fb-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="a46fb-110">En outre, si <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> est appelé sans que <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> ait été appelé au préalable, les valeurs récupérées sont les valeurs initiales de chaque entrée.</span><span class="sxs-lookup"><span data-stu-id="a46fb-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="a46fb-111">Si vous activez les statistiques, exécutez votre application pendant un certain temps, puis désactivez les statistiques, les valeurs récupérées reflètent les valeurs collectées jusqu’au point où les statistiques ont été désactivées.</span><span class="sxs-lookup"><span data-stu-id="a46fb-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="a46fb-112">Toutes les valeurs statistiques rassemblées sont basées sur une connexion individuelle.</span><span class="sxs-lookup"><span data-stu-id="a46fb-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="a46fb-113">Valeurs statistiques disponibles</span><span class="sxs-lookup"><span data-stu-id="a46fb-113">Statistical Values Available</span></span>  

 <span data-ttu-id="a46fb-114">Actuellement, il existe 18 éléments différents disponibles auprès du fournisseur Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a46fb-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="a46fb-115">Le nombre d’éléments disponibles est accessible par le biais de la propriété **Count** de la référence d’interface <xref:System.Collections.IDictionary> retournée par <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span><span class="sxs-lookup"><span data-stu-id="a46fb-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="a46fb-116">Tous les compteurs relatifs aux statistiques de fournisseur utilisent le type Common Language Runtime <xref:System.Int64> (**long** en C# et Visual Basic), dont la taille est de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="a46fb-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="a46fb-117">La valeur maximale du type de données **int64**, telle que définie par le champ **int64.MaxValue**, est ((2^63)-1)).</span><span class="sxs-lookup"><span data-stu-id="a46fb-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="a46fb-118">Lorsque les valeurs des compteurs atteignent cette valeur maximale, elles ne doivent plus être considérées comme exactes.</span><span class="sxs-lookup"><span data-stu-id="a46fb-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="a46fb-119">Cela signifie que **int64.MaxValue**-1((2^63)-2) est effectivement la valeur valide la plus élevée pour toute statistique.</span><span class="sxs-lookup"><span data-stu-id="a46fb-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a46fb-120">Un dictionnaire est utilisé pour renvoyer les statistiques du fournisseur, car le nombre, le nom et l’ordre des statistiques renvoyées sont susceptibles de changer à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="a46fb-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="a46fb-121">Les applications ne doivent pas s’appuyer sur une valeur spécifique trouvée dans le dictionnaire, mais doivent plutôt vérifier si la valeur existe et créer une branche en conséquence.</span><span class="sxs-lookup"><span data-stu-id="a46fb-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="a46fb-122">Le tableau suivant décrit les valeurs statistiques actuelles disponibles.</span><span class="sxs-lookup"><span data-stu-id="a46fb-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="a46fb-123">Notez que les noms clés pour les valeurs individuelles ne sont pas localisés dans les versions régionales de Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a46fb-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="a46fb-124">Nom de la clé</span><span class="sxs-lookup"><span data-stu-id="a46fb-124">Key Name</span></span>|<span data-ttu-id="a46fb-125">Description</span><span class="sxs-lookup"><span data-stu-id="a46fb-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="a46fb-126">Renvoie le nombre de paquets Tabular Data Stream (TDS) reçus par le fournisseur à partir de SQL Server après que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="a46fb-127">Renvoie le nombre de paquets TDS envoyés à SQL Server par le fournisseur une fois que les statistiques ont été activées.</span><span class="sxs-lookup"><span data-stu-id="a46fb-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="a46fb-128">Les commandes de grande taille peuvent nécessiter plusieurs mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="a46fb-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="a46fb-129">Par exemple, si une commande de grande taille est envoyée au serveur et nécessite six paquets, `ServerRoundtrips` est incrémenté d’une unité et `BuffersSent` est incrémenté de six.</span><span class="sxs-lookup"><span data-stu-id="a46fb-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="a46fb-130">Renvoie le nombre d’octets de données dans les paquets TDS reçus par le fournisseur à partir de SQL Server une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="a46fb-131">Renvoie le nombre d’octets de données envoyés à SQL Server dans les paquets TDS une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="a46fb-132">La durée (en millisecondes) pendant laquelle les connexions ont été ouvertes après que les statistiques ont été activées (temps de connexion total si les statistiques ont été activées avant l’ouverture de la connexion).</span><span class="sxs-lookup"><span data-stu-id="a46fb-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="a46fb-133">Retourne le nombre de fois qu’un curseur a été ouvert via la connexion une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="a46fb-134">Notez que les résultats en lecture seule/avant uniquement renvoyés par les instructions SELECT ne sont pas considérés comme des curseurs et n’affectent donc pas ce compteur.</span><span class="sxs-lookup"><span data-stu-id="a46fb-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="a46fb-135">Retourne la durée cumulée (en millisecondes) que le fournisseur a consacré au traitement une fois les statistiques activées, y compris le temps passé à attendre des réponses du serveur, ainsi que le temps passé à exécuter du code dans le fournisseur proprement dit.</span><span class="sxs-lookup"><span data-stu-id="a46fb-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="a46fb-136">Les classes qui incluent le code de minutage sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a46fb-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="a46fb-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="a46fb-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="a46fb-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="a46fb-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="a46fb-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="a46fb-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="a46fb-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="a46fb-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="a46fb-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="a46fb-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="a46fb-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="a46fb-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="a46fb-143">Pour maintenir le plus petit nombre possible de membres critiques en matière de performances, les membres suivants ne sont pas chronométrés :</span><span class="sxs-lookup"><span data-stu-id="a46fb-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="a46fb-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="a46fb-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="a46fb-145">Opérateur this[] (toutes les surcharges)</span><span class="sxs-lookup"><span data-stu-id="a46fb-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="a46fb-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="a46fb-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="a46fb-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="a46fb-147">GetChar</span></span><br /><br /> <span data-ttu-id="a46fb-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="a46fb-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="a46fb-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="a46fb-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="a46fb-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="a46fb-150">GetDouble</span></span><br /><br /> <span data-ttu-id="a46fb-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="a46fb-151">GetFloat</span></span><br /><br /> <span data-ttu-id="a46fb-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="a46fb-152">GetGuid</span></span><br /><br /> <span data-ttu-id="a46fb-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="a46fb-153">GetInt16</span></span><br /><br /> <span data-ttu-id="a46fb-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="a46fb-154">GetInt32</span></span><br /><br /> <span data-ttu-id="a46fb-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="a46fb-155">GetInt64</span></span><br /><br /> <span data-ttu-id="a46fb-156">GetName</span><span class="sxs-lookup"><span data-stu-id="a46fb-156">GetName</span></span><br /><br /> <span data-ttu-id="a46fb-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="a46fb-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="a46fb-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="a46fb-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="a46fb-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="a46fb-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="a46fb-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="a46fb-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="a46fb-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="a46fb-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="a46fb-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="a46fb-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="a46fb-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="a46fb-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="a46fb-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="a46fb-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="a46fb-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="a46fb-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="a46fb-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="a46fb-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="a46fb-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="a46fb-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="a46fb-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="a46fb-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="a46fb-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="a46fb-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="a46fb-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="a46fb-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="a46fb-171">GetString</span><span class="sxs-lookup"><span data-stu-id="a46fb-171">GetString</span></span><br /><br /> <span data-ttu-id="a46fb-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="a46fb-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="a46fb-173">Retourne le nombre total d’instructions INSERT, DELETE et UPDATE exécutées via la connexion une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="a46fb-174">Retourne le nombre total de lignes affectées par les instructions INSERT, DELETE et UPDATE exécutées via la connexion une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="a46fb-175">Retourne la durée cumulée (en millisecondes) que le fournisseur a passé à attendre des réponses du serveur après que l’application a démarré à l’aide du fournisseur et a activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="a46fb-176">Retourne le nombre de commandes préparées exécutées via la connexion une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="a46fb-177">Retourne le nombre d’instructions préparées via la connexion une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="a46fb-178">Retourne le nombre d’instructions SELECT exécutées via la connexion une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="a46fb-179">Cela comprend les instructions FETCH permettant d’extraire des lignes de curseurs, et le nombre d’instructions SELECT est mis à jour lorsque la fin d’un <xref:System.Data.SqlClient.SqlDataReader> est atteinte.</span><span class="sxs-lookup"><span data-stu-id="a46fb-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="a46fb-180">Retourne le nombre de lignes sélectionnées une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="a46fb-181">Ce compteur reflète toutes les lignes générées par les instructions SQL, y compris celles qui n'ont pas été consommées réellement par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="a46fb-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="a46fb-182">Par exemple, la fermeture d’un lecteur de données avant la lecture du jeu de résultats entier n’affecte pas le compteur.</span><span class="sxs-lookup"><span data-stu-id="a46fb-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="a46fb-183">Cela comprend les lignes extraites des curseurs à l’aide d’instructions FETCH.</span><span class="sxs-lookup"><span data-stu-id="a46fb-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="a46fb-184">Retourne le nombre de fois que la connexion a envoyé des commandes au serveur et reçu une réponse une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="a46fb-185">Retourne le nombre de jeux de résultats utilisés une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="a46fb-186">Par exemple, cela inclut tous les jeux de résultats renvoyés au client.</span><span class="sxs-lookup"><span data-stu-id="a46fb-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="a46fb-187">Pour les curseurs, chaque opération d’extraction ou de récupération de bloc est considérée comme un jeu de résultats indépendant.</span><span class="sxs-lookup"><span data-stu-id="a46fb-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="a46fb-188">Retourne le nombre de transactions utilisateur démarrées une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques, y compris les restaurations.</span><span class="sxs-lookup"><span data-stu-id="a46fb-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="a46fb-189">Si une connexion est en cours d’exécution avec la validation automatique activée, chaque commande est considérée comme une transaction.</span><span class="sxs-lookup"><span data-stu-id="a46fb-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="a46fb-190">Ce compteur incrémente le nombre de transactions dès qu’une instruction BEGIN TRAN est exécutée, que la transaction soit validée ou annulée ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="a46fb-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="a46fb-191">Retourne le nombre d’instructions non préparées exécutées via la connexion une fois que l’application a démarré à l’aide du fournisseur et activé les statistiques.</span><span class="sxs-lookup"><span data-stu-id="a46fb-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="a46fb-192">Extraction d'une valeur</span><span class="sxs-lookup"><span data-stu-id="a46fb-192">Retrieving a Value</span></span>  

 <span data-ttu-id="a46fb-193">L’application console suivante montre comment activer les statistiques sur une connexion, récupérer quatre valeurs de statistiques individuelles et les écrire dans la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="a46fb-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a46fb-194">L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a46fb-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="a46fb-195">La chaîne de connexion fournie dans l’exemple de code suppose que la base de données est installée et disponible sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a46fb-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="a46fb-196">Modifiez la chaîne de connexion en fonction des besoins de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="a46fb-196">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="a46fb-197">Extraction de toutes les valeurs</span><span class="sxs-lookup"><span data-stu-id="a46fb-197">Retrieving All Values</span></span>  

 <span data-ttu-id="a46fb-198">L’application console suivante montre comment activer les statistiques sur une connexion, récupérer toutes les valeurs statistiques disponibles à l’aide de l’énumérateur et les écrire dans la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="a46fb-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a46fb-199">L’exemple suivant utilise l’exemple de base de données **AdventureWorks** inclus dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a46fb-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="a46fb-200">La chaîne de connexion fournie dans l’exemple de code suppose que la base de données est installée et disponible sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a46fb-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="a46fb-201">Modifiez la chaîne de connexion en fonction des besoins de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="a46fb-201">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a46fb-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a46fb-202">See also</span></span>

- [<span data-ttu-id="a46fb-203">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a46fb-203">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="a46fb-204">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a46fb-204">ADO.NET Overview</span></span>](../ado-net-overview.md)
