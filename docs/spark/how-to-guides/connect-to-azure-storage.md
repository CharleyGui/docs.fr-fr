---
title: Se connecter au stockage étendu à partir de votre ordinateur local
description: Connectez-vous aux comptes de stockage Azure à l’aide de .NET pour Apache Spark à partir de votre ordinateur local.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dc0c3b44279756596f3d456616821e690710ae04
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224015"
---
# <a name="connect-to-azure-data-lake-storage-gen-2-or-wasb-account"></a><span data-ttu-id="db8d9-103">Se connecter à Azure Data Lake Storage compte Gen 2 ou WASB</span><span class="sxs-lookup"><span data-stu-id="db8d9-103">Connect to Azure Data Lake Storage Gen 2 or WASB account</span></span>

<span data-ttu-id="db8d9-104">Dans cet article, vous allez apprendre à vous connecter à un compte Azure Data Lake Storage (ADLS) Gen 2 ou Windows Azure Storage Blob (WASB) par le biais d’une instance de [.net pour Apache Spark](https://github.com/dotnet/spark) s’exécutant localement sur votre ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="db8d9-104">In this article, you learn how to connect to an Azure Data Lake Storage (ADLS) Gen 2 or Windows Azure Storage Blob (WASB) account through an instance of [.NET for Apache Spark](https://github.com/dotnet/spark) running locally on your Windows machine.</span></span>

## <a name="set-up-the-environment"></a><span data-ttu-id="db8d9-105">Configurer l’environnement</span><span class="sxs-lookup"><span data-stu-id="db8d9-105">Set up the environment</span></span>

1. <span data-ttu-id="db8d9-106">Téléchargez la distribution Apache Spark créée sans Hadoop à partir du [site Web officiel](https://archive.apache.org/dist/spark/) (choisissez une version [prise en charge par .net pour Apache Spark](https://github.com/dotnet/spark#supported-apache-spark)) et extrayez-la dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="db8d9-106">Download the Apache Spark distribution built without Hadoop from [official website](https://archive.apache.org/dist/spark/) (choose a version [supported by .NET for Apache Spark](https://github.com/dotnet/spark#supported-apache-spark)), and extract it to a directory.</span></span> <span data-ttu-id="db8d9-107">Définissez la variable `SPARK_HOME` d’environnement sur ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="db8d9-107">Set the environment variable `SPARK_HOME` to this directory.</span></span>
2. <span data-ttu-id="db8d9-108">Téléchargez le fichier binaire Apache Hadoop à partir d' [ici](http://hadoop.apache.org/releases.html) et extrayez-le dans un dossier, puis définissez votre `HADOOP_HOME` variable d’environnement sur ce dossier.</span><span class="sxs-lookup"><span data-stu-id="db8d9-108">Download the Apache Hadoop binary from [here](http://hadoop.apache.org/releases.html) and extract to a folder, and set your `HADOOP_HOME` environment variable to this folder.</span></span>
3. <span data-ttu-id="db8d9-109">Téléchargez les `winutils.exe` `hadoop.dll` fichiers et à partir de [cet emplacement](https://github.com/cdarlint/winutils) (en fonction de la version de Hadoop installée à l’étape précédente) et placez-les dans le dossier bin de votre Hadoop.</span><span class="sxs-lookup"><span data-stu-id="db8d9-109">Download the `winutils.exe` and `hadoop.dll` files from [this location](https://github.com/cdarlint/winutils) (depending on the version of Hadoop installed in the previous step) and put them in the bin folder of your Hadoop.</span></span> <span data-ttu-id="db8d9-110">Ces fichiers binaires sont nécessaires sur Windows pour que tout soit correctement configuré (cela est expliqué en détail dans le [wiki Apache ici](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems)).</span><span class="sxs-lookup"><span data-stu-id="db8d9-110">These binaries are needed on Windows in order to get everything setup correctly (this is explained in detail in the [Apache wiki here](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems)).</span></span>
4. <span data-ttu-id="db8d9-111">Configurez votre installation Hadoop en apportant les modifications suivantes à votre `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` fichier :</span><span class="sxs-lookup"><span data-stu-id="db8d9-111">Configure your Hadoop installation by making the following changes to your `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` file:</span></span>
    1. <span data-ttu-id="db8d9-112">Définissez la `JAVA_HOME` propriété à l’aide du chemin d’accès dos (car Hadoop n’aime pas les espaces dans `JAVA_HOME` ).</span><span class="sxs-lookup"><span data-stu-id="db8d9-112">Set the `JAVA_HOME` property using the DOS path (since Hadoop doesn't like spaces in `JAVA_HOME`).</span></span> <span data-ttu-id="db8d9-113">Le résultat doit ressembler à ceci : `C:\Progra~1\Java\jdk1.8.0_241` (pointant vers n’importe quelle version de Java installée sur votre ordinateur local).</span><span class="sxs-lookup"><span data-stu-id="db8d9-113">This should look something like this: `C:\Progra~1\Java\jdk1.8.0_241` (Pointing to whatever version of Java you have installed on your local machine).</span></span>
    2. <span data-ttu-id="db8d9-114">Ajouter `%HADOOP_HOME%\share\hadoop\tools\lib\*` à `HADOOP_CLASSPATH` .</span><span class="sxs-lookup"><span data-stu-id="db8d9-114">Append `%HADOOP_HOME%\share\hadoop\tools\lib\*` to `HADOOP_CLASSPATH`.</span></span>
    <span data-ttu-id="db8d9-115">Votre `hadoop-env.cmd` fichier final doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="db8d9-115">Your final `hadoop-env.cmd` file should look something like this:</span></span>

    ![Fichier Hadoop-env. cmd final](./media/connect-external-sources/hadoop-env.png)

## <a name="configure-your-storage-account-in-hadoop"></a><span data-ttu-id="db8d9-117">Configurer votre compte de stockage dans Hadoop</span><span class="sxs-lookup"><span data-stu-id="db8d9-117">Configure your storage account in Hadoop</span></span>

1. <span data-ttu-id="db8d9-118">Ouvrez le compte de stockage ADLS Gen 2 ou WASB auquel vous souhaitez vous connecter par le biais de la [portail Azure](https://portal.azure.com) et ouvrez le volet **clés d’accès** dans le panneau **paramètres** , puis copiez la valeur de **clé** de sous key1.</span><span class="sxs-lookup"><span data-stu-id="db8d9-118">Open the ADLS Gen 2 or WASB storage account you want to connect to through the [Azure portal](https://portal.azure.com) and open the **Access keys** panel under the **Settings** blade and copy the value of **Key** from under key1.</span></span>
2. <span data-ttu-id="db8d9-119">Maintenant, pour configurer Hadoop afin d’accéder à votre compte ADLS Gen2, vous devez modifier votre `core-site.xml` fichier (situé dans `%HADOOP_HOME%\etc\hadoop\` ) qui contient une configuration à l’ensemble du cluster.</span><span class="sxs-lookup"><span data-stu-id="db8d9-119">Now in order to configure Hadoop to access your ADLS Gen2 account you would have to edit your `core-site.xml` (located in `%HADOOP_HOME%\etc\hadoop\` ) file which contains cluster-wide configuration.</span></span> <span data-ttu-id="db8d9-120">Ajoutez les propriétés suivantes à l’intérieur des `<configuration>` balises dans ce fichier :</span><span class="sxs-lookup"><span data-stu-id="db8d9-120">Add the following properties inside the `<configuration>` tags in this file:</span></span>

    ```xml
    <configuration>
      <property>
        <name>fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>SharedKey</value>
        <description></description>
      </property>
      <property>
        <name>fs.azure.account.key.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>YOUR ACCESS KEY (copied from Step 1)</value>
        <description>The secret password. Never share these.</description>
      </property>
    </configuration>
    ```

    <span data-ttu-id="db8d9-121">Si vous essayez de vous connecter à un compte WASB, remplacez `dfs` par `blob` dans les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="db8d9-121">If you are trying to connect to a WASB account, replace `dfs` with `blob` in the property names.</span></span> <span data-ttu-id="db8d9-122">Par exemple : `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net`.</span><span class="sxs-lookup"><span data-stu-id="db8d9-122">For example, `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net`.</span></span>
3. <span data-ttu-id="db8d9-123">Vous pouvez tester la connectivité à votre compte de stockage à partir de Hadoop en exécutant la commande suivante à partir de votre `%HADOOP_HOME%` répertoire :</span><span class="sxs-lookup"><span data-stu-id="db8d9-123">You can test the connectivity to your Storage Account from Hadoop by running the following command from your `%HADOOP_HOME%` directory:</span></span>

    ```bash
    bin\hdfs dfs -ls <URI to your account>
    ```

<span data-ttu-id="db8d9-124">Cela doit afficher une liste de tous les fichiers/dossiers dans le chemin d’accès fourni par votre URI.</span><span class="sxs-lookup"><span data-stu-id="db8d9-124">This should display a list of all files/folders in the path provided by your URI.</span></span>

> [!NOTE]
> <span data-ttu-id="db8d9-125">Le format de dérivation de l’URI vers votre compte de stockage est le suivant :</span><span class="sxs-lookup"><span data-stu-id="db8d9-125">The format to derive the URI to your Storage account is as follows:</span></span>
>
> ```
> For ADLS: abfs[s]://<file_system>@<account_name>.dfs.core.windows.net/<path>/<file_name>
> For WASB: wasb[s]://<file_system>@<account_name>.blob.core.windows.net/<path>/<file_name>
> ```

## <a name="connect-to-your-storage-account"></a><span data-ttu-id="db8d9-126">Connectez-vous à votre compte de stockage</span><span class="sxs-lookup"><span data-stu-id="db8d9-126">Connect to your storage account</span></span>

1. <span data-ttu-id="db8d9-127">Si la commande ci-dessus fonctionnait, vous pouvez maintenant passer à l’accès à ce compte de stockage via Spark.</span><span class="sxs-lookup"><span data-stu-id="db8d9-127">If the above command worked, you can now move on to accessing this storage account through Spark.</span></span> <span data-ttu-id="db8d9-128">Exécutez d’abord la commande `hadoop classpath` à partir de la ligne de commande dans `%HADOOP_HOME%` et copiez la sortie.</span><span class="sxs-lookup"><span data-stu-id="db8d9-128">First run the command `hadoop classpath` from the commandline inside `%HADOOP_HOME%` and copy the output.</span></span>
2. <span data-ttu-id="db8d9-129">Définissez la sortie de la commande exécutée à l’étape 1 sur la valeur de la variable d’environnement `SPARK_DIST_CLASSPATH` .</span><span class="sxs-lookup"><span data-stu-id="db8d9-129">Set the output of the command run in Step 1 to the value of environment variable `SPARK_DIST_CLASSPATH`.</span></span>
3. <span data-ttu-id="db8d9-130">Vous devez maintenant être en mesure d’accéder à votre compte de stockage ADLS ou WASB via Spark .NET à l’aide de l’URI ABFs, comme indiqué dans l’exemple simple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="db8d9-130">Now you should be able to access your ADLS or WASB storage account through Spark .NET using the abfs URI as shown in the simple example below.</span></span> <span data-ttu-id="db8d9-131">(Pour cet exemple, nous utilisons l' [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) exemple de fichier standard fourni avec chaque installation Apache Spark.) :</span><span class="sxs-lookup"><span data-stu-id="db8d9-131">(For this example we use the standard [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) example file provided with every Apache Spark installation.):</span></span>

    ```csharp
    SparkSession spark = SparkSession
       .Builder()
       .AppName("Connect to Azure Storage locally")
       .GetOrCreate();
    DataFrame df = spark.Read().Json("wasbs://file_system@account_name.blob.core.windows.net/path/people.json");
    //DataFrame df = spark.Read().Json("abfss://file_system@account_name.dfs.core.windows.net/path/file.json");
    df.Show();
    ```

    <span data-ttu-id="db8d9-132">Le résultat affiché est le tableau ( `df` ), comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="db8d9-132">The result as displayed is the DataFrame (`df`) as shown below:</span></span>

    ```text
    +----+-------+
    | age|   name|
    +----+-------+
    |null|Michael|
    |  30|   Andy|
    |  19| Justin|
    +----+-------+
    ```
