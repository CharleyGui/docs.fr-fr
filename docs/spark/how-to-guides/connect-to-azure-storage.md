---
title: Se connecter au stockage étendu à partir de votre ordinateur local
description: Connectez-vous aux comptes de stockage Azure à l’aide de .NET pour Apache Spark à partir de votre ordinateur local.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 09e92b0cae848f9c98b691a11842f131f613396b
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877893"
---
# <a name="connect-to-azure-data-lake-storage-gen-2-or-wasb-account"></a>Se connecter à Azure Data Lake Storage compte Gen 2 ou WASB

Dans cet article, vous allez apprendre à vous connecter à un compte Azure Data Lake Storage (ADLS) Gen 2 ou Windows Azure Storage Blob (WASB) par le biais d’une instance de [.net pour Apache Spark](https://github.com/dotnet/spark) s’exécutant localement sur votre ordinateur Windows.

## <a name="set-up-the-environment"></a>Configurer l’environnement

1. Téléchargez la distribution Apache Spark créée sans Hadoop à partir du [site Web officiel](https://archive.apache.org/dist/spark/) (choisissez une version [prise en charge par .net pour Apache Spark](https://github.com/dotnet/spark#supported-apache-spark)) et extrayez-la dans un répertoire. Définissez la variable `SPARK_HOME` d’environnement sur ce répertoire.
2. Téléchargez le fichier binaire Apache Hadoop à partir d' [ici](http://hadoop.apache.org/releases.html) et extrayez-le dans un dossier, puis définissez votre `HADOOP_HOME` variable d’environnement sur ce dossier.
3. Téléchargez les `winutils.exe` `hadoop.dll` fichiers et à partir de [cet emplacement](https://github.com/cdarlint/winutils) (en fonction de la version de Hadoop installée à l’étape précédente) et placez-les dans le dossier bin de votre Hadoop. Ces fichiers binaires sont nécessaires sur Windows pour que tout soit correctement configuré (cela est expliqué en détail dans le [wiki Apache ici](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems)).
4. Configurez votre installation Hadoop en apportant les modifications suivantes à votre `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` fichier :
    1. Définissez la `JAVA_HOME` propriété à l’aide du chemin d’accès dos (car Hadoop n’aime pas les espaces dans `JAVA_HOME` ). Le résultat doit ressembler à ceci : `C:\Progra~1\Java\jdk1.8.0_241` (pointant vers n’importe quelle version de Java installée sur votre ordinateur local).
    2. Ajouter `%HADOOP_HOME%\share\hadoop\tools\lib\*` à `HADOOP_CLASSPATH` .
    Votre `hadoop-env.cmd` fichier final doit ressembler à ceci :

    ![Fichier Hadoop-env. cmd final](./media/connect-external-sources/hadoop-env.png)

## <a name="configure-your-storage-account-in-hadoop"></a>Configurer votre compte de stockage dans Hadoop

1. Ouvrez le compte de stockage ADLS Gen 2 ou WASB auquel vous souhaitez vous connecter par le biais de la [portail Azure](https://portal.azure.com) et ouvrez le volet **clés d’accès** dans le panneau **paramètres** , puis copiez la valeur de **clé** de sous key1.
2. Maintenant, pour configurer Hadoop afin d’accéder à votre compte ADLS Gen2, vous devez modifier votre `core-site.xml` fichier (situé dans `%HADOOP_HOME%\etc\hadoop\` ) qui contient une configuration à l’ensemble du cluster. Ajoutez les propriétés suivantes à l’intérieur des `<configuration>` balises dans ce fichier :

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

    Si vous essayez de vous connecter à un compte WASB, remplacez `dfs` par `blob` dans les noms de propriété. Par exemple : `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net`.
3. Vous pouvez tester la connectivité à votre compte de stockage à partir de Hadoop en exécutant la commande suivante à partir de votre `%HADOOP_HOME%` répertoire :

    ```bash
    bin\hdfs dfs -ls <URI to your account>
    ```

Cela doit afficher une liste de tous les fichiers/dossiers dans le chemin d’accès fourni par votre URI.

> [!NOTE]
> Le format de dérivation de l’URI vers votre compte de stockage est le suivant :
>
> ```
> For ADLS: abfs[s]://<file_system>@<account_name>.dfs.core.windows.net/<path>/<file_name>
> For WASB: wasb[s]://<file_system>@<account_name>.blob.core.windows.net/<path>/<file_name>
> ```

## <a name="connect-to-your-storage-account"></a>Connectez-vous à votre compte de stockage

1. Si la commande ci-dessus fonctionnait, vous pouvez maintenant passer à l’accès à ce compte de stockage via Spark. Exécutez d’abord la commande `hadoop classpath` à partir de la ligne de commande dans `%HADOOP_HOME%` et copiez la sortie.
2. Définissez la sortie de la commande exécutée à l’étape 1 sur la valeur de la variable d’environnement `SPARK_DIST_CLASSPATH` .
3. Vous devez maintenant être en mesure d’accéder à votre compte de stockage ADLS ou WASB via Spark .NET à l’aide de l’URI ABFs, comme indiqué dans l’exemple simple ci-dessous. (Pour cet exemple, nous utilisons l' [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) exemple de fichier standard fourni avec chaque installation Apache Spark.) :

    ```csharp
    SparkSession spark = SparkSession
       .Builder()
       .AppName("Connect to Azure Storage locally")
       .GetOrCreate();
    DataFrame df = spark.Read().Json("wasbs://file_system@account_name.blob.core.windows.net/path/people.json");
    //DataFrame df = spark.Read().Json("abfss://file_system@account_name.dfs.core.windows.net/path/file.json");
    df.Show();
    ```

    Le résultat affiché est le tableau ( `df` ), comme indiqué ci-dessous :

    ```text
    +----+-------+
    | age|   name|
    +----+-------+
    |null|Michael|
    |  30|   Andy|
    |  19| Justin|
    +----+-------+
    ```
