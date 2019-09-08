---
title: Isolation d'instantanés dans SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.openlocfilehash: 2f17e9828f46e6355cdbbddb1b8a83f1188b1a01
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791743"
---
# <a name="snapshot-isolation-in-sql-server"></a>Isolation d'instantanés dans SQL Server
L'isolation de capture instantanée améliore l'accès concurrentiel aux applications OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Présentation de l'isolation d'instantané et gestion des versions de ligne  
 Une fois l’isolation d’instantané activée, les versions de ligne mises à jour pour chaque transaction sont conservées dans **tempdb**. Un numéro de séquence de transaction unique identifie chaque transaction et ces numéros uniques sont enregistrés pour chaque version de ligne. La transaction opère avec les versions de ligne les plus récentes dont le numéro de séquence est antérieur au numéro de séquence de la transaction. Les versions de ligne plus récentes, créées après que la transaction a commencé sont ignorées par la transaction.  
  
 Le terme « instantané » reflète le fait que toutes les requêtes de la transaction voient la même version, ou instantané, de la base de données, en fonction de l’état de la base de données au moment où la transaction commence. Aucun verrou n’est acquis sur les lignes de données ou les pages de données sous-jacentes dans une transaction d’instantané, ce qui permet à d’autres transactions de s’exécuter sans être bloquées par une transaction inachevée antérieure. Les transactions qui modifient des données ne bloquent pas les transactions qui lisent des données et celles qui lisent des données ne bloquent pas celles qui en écrivent, comme c'est normalement le cas avec le niveau d'isolation READ COMMITTED par défaut dans SQL Server. Ce comportement non bloquant réduit également sensiblement la probabilité d’interblocages pour les transactions complexes.  
  
 L'isolation d'instantané utilise un modèle d'accès simultané optimiste. Si une transaction d’instantané tente de valider des modifications apportées à des données ayant changé depuis le début de la transaction, la transaction est annulée et une erreur est déclenchée. Vous pouvez éviter cela en utilisant les indicateurs UPDLOCK pour les instructions SELECT qui accèdent à des données à modifier. Pour plus d'informations, voir « Locking Hints » dans la documentation en ligne de SQL Server.  
  
 L'isolation d'instantané doit être activée en définissant l'option de base de données ALLOW_SNAPSHOT_ISOLATION ON avant de l'utiliser dans des transactions. Cela active le mécanisme de stockage des versions de ligne dans la base de données temporaire (**tempdb**). Vous devez activer l'isolation d'instantané dans chaque base de données qui l'utilise avec l'instruction Transact-SQL ALTER DATABASE. À cet égard, l’isolation d’instantané diffère de niveaux d’isolation traditionnels des instructions READ COMMITTED, REPEATABLE READ, SERIALIZABLE et READ UNCOMMITTED qui ne requièrent aucune configuration. Les instructions suivantes activent l'isolation d'instantané et remplacent le comportement READ COMMITTED par défaut par SNAPSHOT :  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 La définition de l’option READ_COMMITTED_SNAPSHOT ON permet d’accéder à des lignes dont les versions sont gérées au niveau d’isolation READ COMMITTED par défaut. Si l'option READ_COMMITTED_SNAPSHOT a la valeur OFF, vous devez explicitement définir le niveau d'isolation d'instantané pour chaque session afin d'accéder aux lignes dont les versions sont gérées.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Gestion de l'accès simultané avec des niveaux d'isolation  
 Le niveau d'isolation auquel une instruction Transact-SQL s'exécute détermine son comportement de verrouillage et de gestion des versions de ligne. Un niveau d’isolation a une portée qui s’étend à une connexion et, une fois qu’il est défini pour une connexion avec l’instruction SET TRANSACTION ISOLATION LEVEL, il reste effectif jusqu’à ce que la connexion soit fermée ou qu’un autre niveau d’isolation soit défini. Lorsqu’une connexion est fermée et retournée au pool, le niveau d’isolement de la dernière instruction SET TRANSACTION ISOLATION LEVEL est conservé. Des connexions ultérieures réutilisant une connexion regroupée utilisent le niveau d'isolement qui s'appliquait au moment où la connexion a été mise en pool.  
  
 Des requêtes individuelles émises au sein d'une connexion peuvent contenir des indicateurs de verrou qui modifient l'isolement pour une instruction ou une transaction unique mais n'affectent pas le niveau d'isolement de la connexion. Les niveaux d'isolation ou indicateurs de verrou définis dans les procédures ou les fonctions stockées ne modifient pas le niveau d'isolation de la connexion qui les appelle et ne sont effectifs que pendant la durée de la procédure stockée ou de l'appel de fonction.  
  
 Quatre niveaux d'isolement définis dans la norme SQL-92 étaient pris en charge dans les premières versions de SQL Server :  
  
- READ UNCOMMITTED est le niveau d’isolation le moins restrictif car il ignore les verrous placés par d’autres transactions. Les transactions qui s'exécutent au niveau d'isolation READ UNCOMMITTED peuvent lire des valeurs de données modifiées non encore validées par d'autres transactions ; ces dernières sont appelées lectures modifiées (« dirty »).  
  
- READ COMMITTED est le niveau d’isolation par défaut pour SQL Server. Il empêche les lectures modifiées en spécifiant que les instructions ne peuvent pas lire de valeurs de données qui ont été modifiées mais pas encore validées par d’autres transactions. D’autres transactions peuvent encore modifier, insérer ou supprimer des données entre les exécutions d’instructions individuelles à l’intérieur de la transaction en cours, ce qui entraîne des lectures qui ne peuvent pas être répétées ou données fantômes.  
  
- REPEATABLE READ est un niveau d’isolation plus restrictif que READ COMMITTED. Il englobe READ COMMITTED et spécifie qu’aucune autre transaction ne peut modifier ou supprimer des données lues par la transaction en cours tant que celle-ci n’est pas validée. L’accès simultané est inférieur à celui obtenu avec READ COMMITTED parce que les blocs partagés sur les données lues sont conservés pendant la durée de la transaction au lieu d’être libérés à la fin de chaque instruction.  
  
- SERIALIZABLE est le niveau d’isolation le plus restrictif parce qu’il verrouille des plages entières de touches et maintient les verrous jusqu’à ce que la transaction soit achevée. Il englobe REPEATABLE READ et ajoute la restriction en vertu de laquelle d’autres transactions ne peuvent pas insérer de nouvelles lignes dans les plages qui ont été lues par la transaction tant que celle-ci n’est pas achevée.  
  
 Pour plus d’informations, reportez-vous au guide sur le [verrouillage des transactions et le contrôle de version de ligne](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide).  
  
### <a name="snapshot-isolation-level-extensions"></a>Extensions de niveau d'isolation d'instantané  
 SQL Server introduit des extensions des niveaux d’isolation de SQL-92 avec le niveau d’isolation SNAPSHOT et l’implémentation supplémentaire de READ COMMITTED. Le niveau d'isolation READ_COMMITTED_SNAPSHOT peut remplacer de façon transparente READ COMMITTED pour toutes les transactions.  
  
- L'isolation SNAPSHOT spécifie que les données lues dans une transaction ne refléteront jamais les modifications apportées par d'autres transactions simultanées. Au démarrage, la transaction utilise les versions de ligne de données existantes. Aucun verrou n’est appliqué aux données lors de leur lecture, de sorte que les transactions SNAPSHOT n’empêchent pas d’autres transactions d’écrire des données. Les transactions qui écrivent des données n’empêchent pas les transactions d’instantané de lire des données. Vous devez activer une isolation d'instantané en définissant l'option de base de données ALLOW_SNAPSHOT_ISOLATION de façon à ce qu'elle l'utilise.  
  
- L’option de base de données READ_COMMITTED_SNAPSHOT détermine le comportement du niveau d’isolation READ COMMITTED par défaut lorsque l’isolation d’instantané est activée dans une base de données. Si vous ne spécifiez pas explicitement READ_COMMITTED_SNAPSHOT ON, READ COMMITTED est appliqué à toutes les transactions implicites. Cela produit le même comportement que définir READ_COMMITTED_SNAPSHOT OFF (par défaut). Lorsque READ_COMMITTED_SNAPSHOT OFF est effectif, le moteur de base de données utilise des verrous partagés pour appliquer le niveau d'isolation par défaut. Si vous définissez l'option de base de données READ_COMMITTED_SNAPSHOT sur ON, le moteur de base de données utilise par défaut la gestion de versions de ligne et l'isolation d'instantané, au lieu d'utiliser des verrous pour protéger les données.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Fonctionnement de l'isolation d'instantané et de la gestion des versions de ligne  
 Lorsque le niveau d’isolement d’instantané est activé, chaque fois qu’une ligne est mise à jour, le SQL Server Moteur de base de données stocke une copie de la ligne d’origine dans **tempdb**et ajoute un numéro de séquence de transaction à la ligne. La section suivante présente la séquence des événements qui se produit :  
  
- Une nouvelle transaction est initiée, qui reçoit un numéro de séquence de transaction.  
  
- Le Moteur de base de données lit une ligne dans la transaction et récupère la version de ligne de **tempdb** dont le numéro de séquence est le plus proche et le plus petit que le numéro de séquence de la transaction.  
  
- Le moteur de base de données vérifie si le numéro de séquence de la transaction ne figure pas dans la liste des numéros de séquence de transaction des transactions non validées actives au démarrage de la transaction d'instantané.  
  
- La transaction lit la version de la ligne à partir de **tempdb** qui était à jour depuis le début de la transaction. Elle ne voit pas de nouvelles lignes insérées après le démarrage de la transaction parce que ces valeurs de numéro de séquence sont supérieures à la valeur du numéro de séquence de la transaction.  
  
- La transaction en cours voit les lignes qui ont été supprimées après le début de la transaction, car il y aura une version de ligne dans **tempdb** avec une valeur de numéro de séquence inférieure.  
  
 L’effet net d’une isolation d’instantané est que la transaction voit toutes les données telles qu’elles existaient au début de la transaction, sans respecter ni appliquer de verrous aux tables sous-jacentes. Cela peut améliorer les performances dans des situations de conflit.  
  
 Une transaction d’instantané utilise toujours un contrôle d’accès simultané optimiste, rejetant tous les verrous qui empêcheraient d’autres transactions de mettre à jour les lignes. Si une transaction d'instantané tente de valider la mise à jour d'une ligne modifiée après le début de la transaction, la transaction est annulée et une erreur est déclenchée.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Utilisation de l'isolation d'instantané dans ADO.NET  
 L'isolation d'instantané est prise en charge dans ADO.NET par la classe <xref:System.Data.SqlClient.SqlTransaction>. Si une base de données a été activée pour l’isolation d’instantané mais n’est pas configurée pour READ_COMMITTED_SNAPSHOT <xref:System.Data.SqlClient.SqlTransaction> on, vous devez lancer une à l’aide de <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> la valeur d’énumération **IsolationLevel. Snapshot** lors de l’appel de la méthode. Ce fragment de code est basé sur l'hypothèse que la connexion est un objet <xref:System.Data.SqlClient.SqlConnection> ouvert.  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre comment les différents niveaux d'isolation se comportent en tentant d'accéder à des données verrouillées et n'est pas destiné à être utilisé dans un code de production.  
  
 Le code se connecte à l’exemple de base de données **AdventureWorks** dans SQL Server et crée une table nommée **TestSnapshot** et insère une ligne de données. Le code utilise l’instruction ALTER DATABASE Transact-SQL pour activer l’isolation d’instantané pour la base de données mais ne définit pas l’option READ_COMMITTED_SNAPSHOT, en conservant le comportement de niveau d’isolation READ COMMITTED par défaut. Le code effectue ensuite les actions suivantes :  
  
- Il commence à exécuter, sans l’achever, sqlTransaction1, qui utilise le niveau d’isolation SERIALIZABLE pour démarrer une transaction de mise à jour. Cela a pour effet de verrouiller la table.  
  
- Il ouvre une deuxième connexion et lance une deuxième transaction en utilisant le niveau d’isolement d’instantané pour lire les données dans la table **TestSnapshot** . Comme l’isolation d’instantané est activée, cette transaction peut lire les données qui existaient avant le démarrage de sqlTransaction1.  
  
- Il ouvre une troisième connexion et initie une transaction en utilisant le niveau d'isolation READ COMMITTED pour tenter de lire les données de la table. Dans ce cas, le code ne peut pas lire les données parce qu'il ne peut pas lire au-delà des verrous appliqués à la table dans la première transaction et le délai de temporisation expire. Le même résultat est obtenu si les niveaux d'isolation REPEATABLE READ et SERIALIZABLE ont été utilisés parce que ces niveaux ne peuvent pas non plus lire au-delà des verrous appliqués à la première transaction.  
  
- Il ouvre une quatrième connexion et initie une transaction à l’aide du niveau d’isolation READ UNCOMMITTED qui effectue une lecture modifiée de la valeur non validée dans sqlTransaction1. Il se peut que cette valeur n’existe en réalité jamais dans la base de données si la première transaction n’est pas validée.  
  
- Il restaure la première transaction et nettoie en supprimant la table **TestSnapshot** et en désactivant l’isolation d’instantané pour la base de données **AdventureWorks** .  
  
> [!NOTE]
> Les exemples ci-dessous utilisent la même chaîne de connexion avec la mise en pool des connexions désactivée. Si une connexion est mise en pool, la réinitialisation de son niveau d'isolement ne réinitialise pas le niveau d'isolement sur le serveur. Par conséquent, les connexions suivantes qui utilisent la même connexion interne regroupée démarrent avec leurs niveaux d'isolement définis sur celui de la connexion regroupée. Une alternative à la désactivation de la mise en pool des connexions consiste à définir le niveau d'isolement de manière explicite pour chaque connexion.  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>Exemple  
 L'exemple suivant illustre le comportement d'une isolation d'instantané en cas de modification de données. Le code exécute les actions suivantes :  
  
- Établit une connexion à l’exemple de base de données **AdventureWorks** et active l’isolement d’instantané.  
  
- Crée une table nommée **TestSnapshotUpdate** et insère trois lignes d’exemples de données.  
  
- Démarre, sans l'achever, sqlTransaction1 en utilisant une isolation SNAPSHOT. Trois lignes de données sont sélectionnées dans la transaction.  
  
- Crée un second **SqlConnection** à **AdventureWorks** et crée une deuxième transaction en utilisant le niveau d’isolation Read Committed qui met à jour une valeur dans l’une des lignes sélectionnées dans sqlTransaction1.  
  
- Valide sqlTransaction2.  
  
- Retourne à sqlTransaction1 et tente de mettre à jour la ligne déjà validée par sqlTransaction1. Une erreur 3960 est déclenchée et sqlTransaction1 est automatiquement annulé. **SqlException. Number** et **SqlException. message** s’affichent dans la fenêtre de console.  
  
- Exécute le code de nettoyage pour désactiver l’isolement d’instantané dans **AdventureWorks** et supprimer la table **TestSnapshotUpdate** .  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Utilisation d'indicateurs de verrou avec une isolation d'instantané  
 Dans l’exemple précédent, la première transaction sélectionne des données et une seconde transaction met à jour les données avant que la première transaction puisse se terminer, entraînant un conflit de mise à jour lorsque la première transaction tente de mettre à jour la même ligne. Vous pouvez réduire la probabilité de conflits de mise à jour dans les transactions d’instantané de longue durée en fournissant des indicateurs de verrou au début de la transaction. L'instruction SELECT suivante utilise l'indicateur UPDLOCK pour verrouiller les lignes sélectionnées :  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 L'utilisation de l'indicateur de verrou UPDLOCK bloque toutes les lignes tentant de mettre à jour les lignes avant la fin de la première transaction. Cela garantit que les lignes sélectionnées sont exemptes de conflits lors de leur mise à jour ultérieurement dans la transaction. Voir « Locking Hints » dans la documentation en ligne de SQL Server.  
  
 Si votre application rencontre de nombreux conflits, une isolation d'instantané n'est peut-être pas le meilleur choix. N'utilisez des indicateurs que si c'est réellement nécessaire. Votre application ne doit pas être conçue de façon à ce que son fonctionnement dépende constamment des indicateurs de verrou.  
  
## <a name="see-also"></a>Voir aussi

- [SQL Server et ADO.NET](index.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
- [Guide du verrouillage des transactions et du contrôle de version de ligne](/sql/relational-databases/sql-server-transaction-locking-and-row-versioning-guide)
