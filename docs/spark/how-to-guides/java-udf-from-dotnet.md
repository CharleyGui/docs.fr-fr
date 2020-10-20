---
title: Appeler des fonctions définies par l’utilisateur Java à partir de .NET pour Apache Spark application
description: Découvrez comment appeler une fonction UDF Java à partir d’une application .NET pour Apache Spark.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: edf525102bf5503dcb51247b5fa590aa0d42b369
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224124"
---
# <a name="call-a-java-udf-from-your-net-for-apache-spark-application"></a>Appeler une fonction UDF Java à partir de votre application .NET pour Apache Spark

Dans cet article, vous allez apprendre à appeler une fonction de User-Defined Java (UDF) à partir de votre application [.net for Apache Spark](https://github.com/dotnet/spark) .

1. Comment définir vos fonctions définies par l’utilisateur Java et les compiler dans un fichier jar-cette étape n’est pas nécessaire si vous avez déjà défini une FDU dans un fichier jar. Dans ce cas, tout ce dont vous avez besoin est le nom complet de la fonction UDF, y compris le package.
2. Inscrivez-vous et appelez votre UDF Java dans votre application .NET pour Apache Spark.

## <a name="define-and-compile-your-java-udfs"></a>Définir et compiler vos fonctions définies par l’utilisateur Java

1. Créez un projet Maven ou SBT et ajoutez les dépendances suivantes dans le fichier de configuration du projet :
    1. `org.apache.spark.spark-core_2.11.<version>`
    2. `org.apache.spark.spark-sql_2.11.<version>`
2. Définissez votre UDF Java en implémentant l' [interface appropriée](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (en fonction de la signature de votre UDF) et en important le package approprié comme indiqué ci-dessous dans un exemple simple

    ```java
    package com.ScalaUdf.app; // Name of package where UDF is defined
    import org.apache.spark.sql.api.java.UDF1; // UDF interface to implement

    public class JavaUdf implements UDF1<Integer, Integer> { // Name of the Java UDF
        private static final int serialVersionUID = 1;
        @Override
        public Integer call(Integer num) throws Exception { // Define logic of UDF
            return (num + 5);
        }
    }
    ```

3. Compilez et empaquetez votre projet pour créer et exécuter un fichier jar `UdfApp-0.0.1.jar` .

## <a name="register-and-call-java-udfs-in-net-for-apache-spark"></a>Inscrire et appeler des fonctions définies par l’utilisateur Java dans .NET pour Apache Spark

1. Utilisez l' [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API pour inscrire votre UDF Java avec Spark SQL.
2. Inscrivez le `DataFrame` sur lequel vous souhaitez appeler votre UDF en tant que table SQL à l’aide de la [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) fonction.
3. Utilisez `SparkSession.Sql` pour appeler l’UDF sur la vue table à l’aide de Spark SQL.
Voici un exemple de base pour illustrer les étapes ci-dessus :

    ```csharp
    class Program
    {
        static void Main()
        {
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Scala/Java UDFs from .NET for Apache Spark")
                .GetOrCreate();
            spark.Udf().RegisterJava<int>("udfAdd5", "com.ScalaUdf.app.JavaUdf"); // Register your Java UDF as 'udfAdd5'
            DataFrame df = spark.CreateDataFrame(new int[] { 2, 5 });
            df.CreateOrReplaceTempView("numbersData"); // Create an SQL table from the DataFrame `df`
            DataFrame dfUdf = spark.Sql("SELECT udfAdd5(_1) As Result FROM numbersData"); // Call the registered UDF on the table
            dfUdf.Show();
            spark.Stop();
        }
    }
    ```

4. Soumettez cette application `spark-submit` en utilisant en passant le fichier jar Java UDF précédemment compilé par le biais de l' `--jars` option :

    ```bash
    spark-submit --master local --jars UdfApp-0.0.1.jar --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-3.0.x-0.12.1.jar InterRuntimeUDFs.exe
    ```

    Le `dfUdf` tableau résultant avait le nombre 5 ajouté à chaque ligne de la colonne d’entrée, comme défini par `JavaUdf` :

    ```text
    +-------+
    | Result|
    +-------+
    |      7|
    |     10|
    +-------+
    ```

## <a name="call-net-udf-from-scala-or-python-in-apache-spark"></a>Appeler la fonction UDF .NET à partir de Scala ou python dans Apache Spark

Vous pouvez également inscrire et appeler une fonction UDF C# à partir d’une application Apache Spark écrite en Scala ou python à l’aide de [l’outil sparkdotnetudf Open source](https://github.com/imback82/sparkdotnetudf).
