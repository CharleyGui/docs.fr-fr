---
title: Connectez .NET pour Apache Spark à SQL Server
description: Découvrez comment vous connecter à une instance de SQL Server à partir de votre application .NET for Apache Spark.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 773e743a67c066438cb86d983ebfa34f73692c2d
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877887"
---
# <a name="connect-net-for-apache-spark-to-sql-server"></a>Connectez .NET pour Apache Spark à SQL Server

Dans cet article, vous allez apprendre à vous connecter à une instance de SQL Server à partir de votre application [.net pour Apache Spark](https://github.com/dotnet/spark) .

## <a name="configure-sql-server-to-grant-your-application-access"></a>Configurer SQL Server pour accorder l’accès à votre application

1. Ajoutez un utilisateur et un mot de passe de connexion en choisissant l’authentification SQL Server sur votre instance SQL Server.
2. Accordez les autorisations nécessaires à l’utilisateur de connexion au niveau de la base de données appropriée, comme indiqué ci-dessous :

    ![Autorisations SQL Server](./media/connect-external-sources/SqlServerAuth.png)

3. Assurez-vous que le port par défaut pour SQL Server `1433` est autorisé via le pare-feu.
4. Ouvrez le gestionnaire de configuration SQL pour activer TCP/IP via la configuration du réseau, comme indiqué ci-dessous :

    ![Activer le protocole TCP/IP SQL Server](./media/connect-external-sources/SqlServerTCPIP.png)

    Notez également la valeur de l’onglet **écouter tout dans les** éléments ci-dessus sous **protocole**.

5. Configurez le port TCP/IP sur 1433 pour toutes les adresses IP requises si `Listen All` a la valeur `No` . Dans le cas contraire, définissez le port TCP dans IPAll.

    ![Port TCP/IP SQL Server](./media/connect-external-sources/SQLServerTCPIIPPort.png)

## <a name="connect-to-sql-server-from-your-application"></a>Se connecter à SQL Server à partir de votre application

1. Utilisez le pilote JDBC Microsoft pour SQL Server pour assurer la connectivité de la base de données via votre application (téléchargement à partir de [ce site Web officiel](https://docs.microsoft.com/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)).
2. Définissez les configurations suivantes pour vous connecter à l’instance et à la base de données SQL Server à partir de votre application :
    1. **connection_url**: il s’agit de l’URL utilisée pour se connecter à la base de données ou à l’instance SQL Server et a le format suivant :

        ```
        jdbc:sqlserver://<SQL_server_IP_address>:1433;instanceName=<instance_name>;databaseName=<database_name>;
        ```

    2. **DBTABLE**: nom de la table en cours d’accès.
    3. **utilisateur**: connexion utilisateur configurée à l’étape 1 de la configuration de SQL Server.
    4. **mot**de passe : mot de passe de l’utilisateur configuré à l’étape 1 de la configuration de SQL Server.
3. Utilisez la configuration ci-dessus dans le code de votre application pour lire les données d’une table, comme indiqué ci-dessous :

    ```csharp
    static void Main()
    {
        SparkSession spark = SparkSession
            .Builder()
            .AppName("Connect to SQL Server")
            .GetOrCreate();

        string connection_url = "<URL to connect to SQL server instance>";
        string dbtable = "<database table to access>";
        string user = "<Login user name>";
        string password = "<Login user password>";

        DataFrame jdbcDF = spark.Read()
            .Format("jdbc")
            .Option("driver", "com.microsoft.sqlserver.jdbc.SQLServerDriver")
            .Option("url", connection_url)
            .Option("dbtable", dbtable)
            .Option("user", user)
            .Option("password", password).Load();
        jdbcDF.Show(); // Displays the content of the SQL table as a DataFrame
    }
    ```
