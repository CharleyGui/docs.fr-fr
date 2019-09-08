---
title: Instances utilisateur SQL Server Express
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: 7cd02a0a315ffdb155af09ac4e4fabbea1724a4d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780831"
---
# <a name="sql-server-express-user-instances"></a>Instances utilisateur SQL Server Express
Microsoft SQL Server Express Edition (SQL Server Express) prend en charge une nouvelle fonctionnalité, l’instance utilisateur, disponible uniquement avec le fournisseur de données .NET Framework pour SQL Server (`SqlClient`). Une instance utilisateur est une instance séparée du moteur de base de données SQL Server Express qui est générée par une instance parente. Les instances utilisateur permettent aux utilisateurs qui ne sont pas des administrateurs système sur leur ordinateur local de s'attacher et de se connecter aux bases de données SQL Server Express. Chaque instance s'exécute dans le contexte de sécurité de l'utilisateur individuel, sur la base d'une instance par utilisateur.  
  
## <a name="user-instance-capabilities"></a>Fonctionnalités de l'instance utilisateur  
 Les instances utilisateur sont utiles aux utilisateurs qui exécutent Windows sous un compte avec les privilèges minimum (LUA) car elles leur permettent d'exécuter des privilèges (`sysadmin`) d'administrateur système SQL Server sur l'instance de leur ordinateur sans avoir à s'exécuter également en tant qu'administrateur Windows. Les logiciels qui s'exécutent sur une instance utilisateur avec des autorisations limitées ne peuvent pas effectuer de modifications au niveau du système parce que l'instance de SQL Server Express s'exécute sous le compte Windows non-administrateur de l'utilisateur, pas en tant que service. Chaque instance utilisateur est isolée de son instance parente et des autres instances utilisateur en cours d'exécution sur le même ordinateur. Les bases de données qui s'exécutent sur une instance utilisateur sont ouvertes en mode mono-utilisateur uniquement ; plusieurs utilisateurs ne peuvent pas se connecter à ces bases de données. La réplication et les requêtes distribuées sont également désactivées pour les instances utilisateur.  
  
 Pour plus d'informations, voir « Instances utilisateur » dans la documentation en ligne de SQL Server.  
  
> [!NOTE]
> Les instances utilisateur ne sont pas nécessaires pour les utilisateurs qui sont déjà administrateurs sur leur propre ordinateur ou pour les scénarios qui impliquent plusieurs utilisateurs de base de données.  
  
## <a name="enabling-user-instances"></a>Activation des instances utilisateur  
 Pour générer des instances utilisateur, une instance parente de SQL Server Express doit être en cours d'exécution. Les instances utilisateur sont activées par défaut lors de l’installation de SQL Server Express, et elles peuvent être activées ou désactivées de manière explicite par un administrateur système qui exécute la procédure stockée système **sp_configure** sur l’instance parente.  
  
```  
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 Le protocole réseau pour les instances utilisateur doit être canaux nommés locaux. Une instance utilisateur ne peut pas être démarrée sur une instance distante de SQL Server et les connexions SQL Server ne sont pas autorisées.  
  
## <a name="connecting-to-a-user-instance"></a>Connexion à une instance utilisateur  
 Les `User Instance` mots `AttachDBFilename` clés et <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> permettent <xref:System.Data.SqlClient.SqlConnection> à un de se connecter à une instance utilisateur. Les instances utilisateur sont également prises en charge par les propriétés <xref:System.Data.SqlClient.SqlConnectionStringBuilder>`UserInstance` et `AttachDBFilename`.  
  
 Notez les éléments suivants sur l'exemple de chaîne de connexion ci-dessous :  
  
- Le mot clé `Data Source` fait référence à l'instance parente de SQL Server Express qui génère l'instance utilisateur. L'instance par défaut est .\sqlexpress.  
  
- `Integrated Security` a la valeur `true`. Pour vous connecter à une instance utilisateur, l'authentification Windows est nécessaire ; les connexions SQL Server ne sont pas prises en charge.  
  
- `User Instance` a la valeur `true` qui appelle une instance utilisateur. (La valeur par défaut est `false`).  
  
- Le mot clé de la chaîne de connexion `AttachDbFileName` est utilisé pour joindre le fichier (.mdf) de base de données primaire, qui doit inclure le chemin d’accès complet. `AttachDbFileName` correspond aussi aux clés « extended properties » et « initial file name » dans une chaîne de connexion <xref:System.Data.SqlClient.SqlConnection>.  
  
- La chaîne de substitution `|DataDirectory|` placée entre deux barres verticales fait référence au répertoire des données de l'application qui ouvre la connexion et fournit un chemin d'accès relatif à l'emplacement des fichiers journaux et de base de données .mdf et .ldf. Si vous souhaitez placer ces fichiers ailleurs, vous devez indiquer le chemin d’accès complet des fichiers.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
> Vous pouvez également utiliser les propriétés <xref:System.Data.SqlClient.SqlConnectionStringBuilder><xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> et <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> pour créer une chaîne de connexion au moment de l'exécution.  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>Utilisation de &#124;la&#124; chaîne de substitution DataDirectory  
 `AttachDbFileName` a été étendu dans ADO.NET 2.0 avec l'introduction de la chaîne de substitution `|DataDirectory|` (dans les symboles de barre verticale). `DataDirectory` est utilisé conjointement à `AttachDbFileName` pour indiquer un chemin d'accès relatif à un fichier de données, ce qui permet aux développeurs de créer des chaînes de connexion basées sur un chemin d'accès relatif à la source de données au lieu de devoir spécifier un chemin d'accès complet.  
  
 L'emplacement physique que désigne `DataDirectory` varie en fonction du type d'application. Dans cet exemple, le fichier Northwind.mdf à joindre se trouve dans le dossier \app_data de l’application.  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 Lorsque `DataDirectory` est utilisé, le chemin d’accès du fichier résultant ne peut pas se trouver plus haut dans la structure des répertoires que le répertoire vers lequel pointe la chaîne de substitution. Par exemple, si le `DataDirectory` complètement étendu est C:\AppDirectory\app_data, la chaîne de connexion dans l'exemple ci-dessus fonctionne car elle est située sous c:\AppDirectory. Cependant, si vous tentez de spécifier `DataDirectory` sous la forme de `|DataDirectory|\..\data`, il en résulte une erreur car \data n'est pas un sous-répertoire de \AppDirectory.  
  
 Si la chaîne de connexion a une chaîne de substitution dont la mise en forme est incorrecte, une exception <xref:System.ArgumentException> sera levée.  
  
> [!NOTE]
> <xref:System.Data.SqlClient> résout les chaînes de substitution en chemins d'accès complets sur le système de fichiers de l'ordinateur local. Par conséquent, les noms de chemin d’accès de serveur distant, HTTP et UNC ne sont pas pris en charge. Une exception est levée si la connexion est ouverte lorsque le serveur n'est pas situé sur l'ordinateur local.  
  
 Lorsque <xref:System.Data.SqlClient.SqlConnection> est ouvert, il est redirigé depuis l'instance SQL Server Express par défaut vers une instance initiée au moment de l'exécution et qui s'exécute sous le compte de l'appelant.  
  
> [!NOTE]
> Vous devrez peut-être augmenter la valeur <xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> car le chargement des instances utilisateur peut nécessiter plus de temps que les instances normales.  
  
 Le fragment de code suivant ouvre une nouvelle `SqlConnection`, affiche la chaîne de connexion dans la fenêtre de console puis ferme la connexion lorsque le bloc de code `using` n'est plus utilisé.  
  
```vb  
Private Sub OpenSqlConnection()  
    ' Retrieve the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Using connection As New SqlConnection(connectionString)  
        connection.Open()  
        Console.WriteLine("ConnectionString: {0}", _  
           connection.ConnectionString)  
    End Using  
End Sub  
```  
  
```csharp  
private static void OpenSqlConnection()  
{  
    // Retrieve the connection string.  
    string connectionString = GetConnectionString();  
  
    using (SqlConnection connection =   
        new SqlConnection(connectionString))  
    {  
        connection.Open();  
        Console.WriteLine("ConnectionString: {0}",   
             connection.ConnectionString);  
    }  
}  
```  
  
> [!NOTE]
> Les instances utilisateur ne sont pas prises en charge par le code CLR (Common Language Runtime) qui s'exécute dans SQL Server. Une exception <xref:System.InvalidOperationException> est levée si `Open` est appelé sur une <xref:System.Data.SqlClient.SqlConnection> qui contient `User Instance=true` dans la chaîne de connexion.  
  
## <a name="lifetime-of-a-user-instance-connection"></a>Durée de vie d'une connexion à une instance utilisateur  
 Contrairement aux versions SQL Server qui s'exécutent en tant que service, il n'est pas nécessaire de démarrer et d'arrêter manuellement les instances de SQL Server Express. Chaque fois qu'un utilisateur ouvre une session et se connecte à une instance utilisateur, celle-ci est démarrée si elle n'est pas déjà en cours d'exécution. L'option `AutoClose` des bases de données d'instance utilisateur est définie de telle sorte que la base de données s'arrête automatiquement après une période d'inactivité. Le processus sqlservr.exe qui est démarré continue de s'exécuter durant une période limitée après la fermeture de la dernière connexion à l'instance. De cette manière, il n'est pas nécessaire de le redémarrer en cas d'ouverture d'une autre connexion avant l'expiration du délai d'attente. L'instance utilisateur s'arrête automatiquement si aucune nouvelle connexion ne s'ouvre avant l'expiration de cette période de délai d'attente. Un administrateur système sur l’instance parente peut définir la durée du délai d’attente pour une instance utilisateur à l’aide de **sp_configure** pour modifier l’option délai d’expiration de l' **instance utilisateur** . La valeur par défaut est 60 minutes.  
  
> [!NOTE]
> Si `Min Pool Size` est utilisé dans la chaîne de connexion avec une valeur supérieure à zéro, le dispositif de regroupement maintient toujours quelques connexions ouvertes pour ne pas que l'instance utilisateur ne se ferme automatiquement.  
  
## <a name="how-user-instances-work"></a>Fonctionnement des instances utilisateur  
 La première fois qu’une instance utilisateur est générée pour chaque utilisateur, les bases de données système **Master** et **msdb** sont copiées du dossier de données du modèle vers un chemin d’accès sous le répertoire de stockage des données de l’application locale de l’utilisateur pour une utilisation exclusive par l’instance utilisateur. Ce chemin d'accès est généralement `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS`. Lors du démarrage d’une instance utilisateur, les fichiers **tempdb**, log et de trace sont également écrits dans ce répertoire. Un nom est généré pour l'instance, ce qui garantit un nom unique pour chaque utilisateur.  
  
 Par défaut, tous les membres du groupe Builtin\Users de Windows reçoivent les autorisations de se connecter à l'instance locale ainsi que les autorisations en lecture et en écriture sur les binaires SQL Server. Une fois que les informations d'identification de l'utilisateur appelant qui héberge l'instance utilisateur ont été vérifiées, cet utilisateur devient `sysadmin` sur cette instance. Seule la mémoire partagée est activée pour les instances utilisateur, ce qui signifie que seules les opérations sur l'ordinateur local sont possibles.  
  
 Les utilisateurs doivent recevoir les autorisations en lecture et en écriture sur les fichiers .mdf et .ldf spécifiés dans la chaîne de connexion.  
  
> [!NOTE]
> Les fichiers .mdf et .ldf représentent les fichiers de base de données et du journal, respectivement. Ces deux fichiers forment une paire, les opérations de sauvegarde et de restauration doivent donc s'effectuer avec prudence. Le fichier de base de données contient des informations sur la version exacte du fichier journal, et la base de données ne s'ouvre pas si elle est associée au mauvais fichier journal.  
  
 Pour éviter d'endommager les données, une base de données dans l'instance utilisateur est ouverte avec un accès exclusif. Si deux instances utilisateur différentes partagent la même base de données sur le même ordinateur, l'utilisateur sur la première instance doit refermer la base de données pour qu'elle puisse être ouverte sur une deuxième instance.  
  
## <a name="user-instance-scenarios"></a>Scénarios d'instance utilisateur  
 Les instances utilisateur fournissent aux développeurs d'applications de base de données un magasin de données SQL Server qui ne nécessite pas que les développeurs disposent de comptes d'administration sur leurs ordinateurs de développement. Les instances utilisateur sont basées sur le modèle Access/Jet selon lequel il suffit que l'application de base de données se connecte à un fichier pour que l'utilisateur dispose automatiquement de toutes les autorisations sur tous les objets de base de données sans que l'intervention d'un administrateur système ne soit nécessaire. Ce modèle convient lorsque l'utilisateur s'exécute sous un compte avec les privilèges minimum (LUA) sans disposer de privilèges d'administration sur l'ordinateur local ou le serveur et qu'il a besoin de créer des objets et des applications de base de données. Les instances utilisateur permettent aux utilisateurs de créer des instances au moment de l'exécution qui s'exécutent sous le contexte de sécurité de l'utilisateur au lieu du contexte de sécurité d'un service système plus privilégié.  
  
> [!IMPORTANT]
> Les instances utilisateur doivent uniquement servir dans les scénarios où toutes les applications qui les utilisent sont totalement fiables.  
  
 Les scénarios d'instance utilisateur sont les suivants :  
  
- Toute application mono-utilisateur où le partage des données n'est pas requis.  
  
- Déploiement ClickOnce Si le .NET Framework 2.0 (ou version ultérieure) et SQL Server Express sont déjà installés sur l'ordinateur cible, le package d'installation téléchargé suite à une action ClickOnce peut être installé et utilisé par des utilisateurs qui ne sont pas administrateurs. Notez qu'un administrateur doit installer SQL Server Express si cette édition fait partie de l'installation. Pour plus d’informations, consultez [déploiement ClickOnce pour Windows Forms](../../../winforms/clickonce-deployment-for-windows-forms.md).
  
- Hébergement ASP.NET dédié à l'aide de l'authentification Windows. Une seule instance SQL Server Express peut être hébergée sur un intranet. L'application se connecte à l'aide du compte Windows ASPNET, et non à l'aide de l'emprunt d'identité. Les instances utilisateur ne doivent pas être utilisées dans les scénarios d'hébergement partagés ou tiers dans lesquels toutes les applications doivent partager la même instance utilisateur et ne plus être indépendantes les unes des autres.  
  
## <a name="see-also"></a>Voir aussi

- [SQL Server et ADO.NET](index.md)
- [Chaînes de connexion](../connection-strings.md)
- [Connexion à une source de données](../connecting-to-a-data-source.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
