---
title: Connectez .NET pour Apache Spark à SQL Server
description: Découvrez comment vous connecter à une instance de SQL Server à partir de votre application .NET for Apache Spark.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 1fecd796aeefd6c5681c4c2ea623e89f3a5a3c1d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439532"
---
# <a name="connect-net-for-apache-spark-to-sql-server"></a><span data-ttu-id="ac2ae-103">Connectez .NET pour Apache Spark à SQL Server</span><span class="sxs-lookup"><span data-stu-id="ac2ae-103">Connect .NET for Apache Spark to SQL Server</span></span>

<span data-ttu-id="ac2ae-104">Dans cet article, vous allez apprendre à vous connecter à une instance de SQL Server à partir de votre application [.net pour Apache Spark](https://github.com/dotnet/spark) .</span><span class="sxs-lookup"><span data-stu-id="ac2ae-104">In this article, you learn how to connect to an SQL server instance from your [.NET for Apache Spark](https://github.com/dotnet/spark) application.</span></span>

## <a name="configure-sql-server-to-grant-your-application-access"></a><span data-ttu-id="ac2ae-105">Configurer SQL Server pour accorder l’accès à votre application</span><span class="sxs-lookup"><span data-stu-id="ac2ae-105">Configure SQL Server to grant your application access</span></span>

1. <span data-ttu-id="ac2ae-106">Ajoutez un utilisateur et un mot de passe de connexion en choisissant l’authentification SQL Server sur votre instance SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ac2ae-106">Add a login user and password choosing SQL Server authentication to your SQL Server instance.</span></span>
2. <span data-ttu-id="ac2ae-107">Accordez les autorisations nécessaires à l’utilisateur de connexion au niveau de la base de données appropriée, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="ac2ae-107">Give that login user necessary permissions at the relevant database level as shown below:</span></span>

    ![Autorisations SQL Server](./media/connect-external-sources/SqlServerAuth.png)

3. <span data-ttu-id="ac2ae-109">Assurez-vous que le port par défaut pour SQL Server `1433` est autorisé via le pare-feu.</span><span class="sxs-lookup"><span data-stu-id="ac2ae-109">Make sure the default port for SQL Server `1433` is allowed through the firewall.</span></span>
4. <span data-ttu-id="ac2ae-110">Ouvrez le gestionnaire de configuration SQL pour activer TCP/IP via la configuration du réseau, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="ac2ae-110">Open SQL configure manager to enable TCP/IP through the network configuration as shown below:</span></span>

    ![Activer le protocole TCP/IP SQL Server](./media/connect-external-sources/SqlServerTCPIP.png)

    <span data-ttu-id="ac2ae-112">Notez également la valeur de l’onglet **écouter tout dans les** éléments ci-dessus sous **protocole**.</span><span class="sxs-lookup"><span data-stu-id="ac2ae-112">Also note the value of **Listen All** in above tab under **Protocol**.</span></span>

5. <span data-ttu-id="ac2ae-113">Configurez le port TCP/IP sur 1433 pour toutes les adresses IP requises si `Listen All` a la valeur `No` .</span><span class="sxs-lookup"><span data-stu-id="ac2ae-113">Configure the TCP/IP port to 1433 for all required IP addresses if the `Listen All` is set to `No`.</span></span> <span data-ttu-id="ac2ae-114">Dans le cas contraire, définissez le port TCP dans IPAll.</span><span class="sxs-lookup"><span data-stu-id="ac2ae-114">Otherwise, set the TCP Port in IPAll.</span></span>

    ![Port TCP/IP SQL Server](./media/connect-external-sources/SQLServerTCPIIPPort.png)

## <a name="connect-to-sql-server-from-your-application"></a><span data-ttu-id="ac2ae-116">Se connecter à SQL Server à partir de votre application</span><span class="sxs-lookup"><span data-stu-id="ac2ae-116">Connect to SQL Server from your application</span></span>

1. <span data-ttu-id="ac2ae-117">Utilisez le pilote JDBC Microsoft pour SQL Server pour assurer la connectivité de la base de données via votre application (téléchargement à partir de [ce site Web officiel](/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)).</span><span class="sxs-lookup"><span data-stu-id="ac2ae-117">Use the Microsoft JDBC Driver for SQL Server to provide database connectivity through your application (download from [this official website](/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)).</span></span>
2. <span data-ttu-id="ac2ae-118">Définissez les configurations suivantes pour vous connecter à l’instance et à la base de données SQL Server à partir de votre application :</span><span class="sxs-lookup"><span data-stu-id="ac2ae-118">Set the following configurations to connect to the SQL server instance and database from your application:</span></span>
    1. <span data-ttu-id="ac2ae-119">**connection_url** : il s’agit de l’URL utilisée pour se connecter à la base de données ou à l’instance SQL Server et a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="ac2ae-119">**connection_url** : This is the URL used to connect to the SQL server instance/database and has the following format:</span></span>

        ```
        jdbc:sqlserver://<SQL_server_IP_address>:1433;instanceName=<instance_name>;databaseName=<database_name>;
        ```

    2. <span data-ttu-id="ac2ae-120">**DBTABLE** : nom de la table en cours d’accès.</span><span class="sxs-lookup"><span data-stu-id="ac2ae-120">**dbtable** : Name of table being accessed.</span></span>
    3. <span data-ttu-id="ac2ae-121">**utilisateur** : connexion utilisateur configurée à l’étape 1 de la configuration de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ac2ae-121">**user** : Login user set up in Step 1 of configuring the SQL server.</span></span>
    4. <span data-ttu-id="ac2ae-122">**mot** de passe : mot de passe de l’utilisateur configuré à l’étape 1 de la configuration de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ac2ae-122">**password** : Password of user set up in Step 1 of configuring the SQL server.</span></span>
3. <span data-ttu-id="ac2ae-123">Utilisez la configuration ci-dessus dans le code de votre application pour lire les données d’une table, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="ac2ae-123">Use the above configuration in your application code to read the data from a table as shown below:</span></span>

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
