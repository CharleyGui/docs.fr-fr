---
title: Appeler des fonctions définies par l’utilisateur Java à partir de .NET pour Apache Spark application
description: Découvrez comment appeler une fonction UDF Java à partir d’une application .NET pour Apache Spark.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: e309a1e8cda2a559f300a07155c005677db85945
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877917"
---
# <a name="call-a-java-udf-from-your-net-for-apache-spark-application"></a><span data-ttu-id="c6acf-103">Appeler une fonction UDF Java à partir de votre application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="c6acf-103">Call a Java UDF from your .NET for Apache Spark application</span></span>

<span data-ttu-id="c6acf-104">Dans cet article, vous allez apprendre à appeler une fonction de User-Defined Java (UDF) à partir de votre application [.net for Apache Spark](https://github.com/dotnet/spark) .</span><span class="sxs-lookup"><span data-stu-id="c6acf-104">In this article, you learn how to call a Java User-Defined Function (UDF) from your [.NET for Apache Spark](https://github.com/dotnet/spark) application.</span></span>

1. <span data-ttu-id="c6acf-105">Comment définir vos fonctions définies par l’utilisateur Java et les compiler dans un fichier jar-cette étape n’est pas nécessaire si vous avez déjà défini une FDU dans un fichier jar.</span><span class="sxs-lookup"><span data-stu-id="c6acf-105">How to define your Java UDFs and compile them into a jar - this step is not needed if you already have a UDF defined in a jar file.</span></span> <span data-ttu-id="c6acf-106">Dans ce cas, tout ce dont vous avez besoin est le nom complet de la fonction UDF, y compris le package.</span><span class="sxs-lookup"><span data-stu-id="c6acf-106">In which case, all you need is the full name of the UDF function including the package.</span></span>
2. <span data-ttu-id="c6acf-107">Inscrivez-vous et appelez votre UDF Java dans votre application .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="c6acf-107">Register and call your Java UDF in your .NET for Apache Spark application.</span></span>

## <a name="define-and-compile-your-java-udfs"></a><span data-ttu-id="c6acf-108">Définir et compiler vos fonctions définies par l’utilisateur Java</span><span class="sxs-lookup"><span data-stu-id="c6acf-108">Define and compile your Java UDFs</span></span>

1. <span data-ttu-id="c6acf-109">Créez un projet Maven ou SBT et ajoutez les dépendances suivantes dans le fichier de configuration du projet :</span><span class="sxs-lookup"><span data-stu-id="c6acf-109">Create a Maven or SBT project and add the following dependencies into the project configuration file:</span></span>
    1. `org.apache.spark.spark-core_2.11.<version>`
    2. `org.apache.spark.spark-sql_2.11.<version>`
2. <span data-ttu-id="c6acf-110">Définissez votre UDF Java en implémentant l' [interface appropriée](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (en fonction de la signature de votre UDF) et en important le package approprié comme indiqué ci-dessous dans un exemple simple</span><span class="sxs-lookup"><span data-stu-id="c6acf-110">Define your Java UDF by implementing the [relevant interface](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (according to your UDF's signature) and importing the relevant package as shown below in a simple example</span></span>

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

3. <span data-ttu-id="c6acf-111">Compilez et empaquetez votre projet pour créer et exécuter un fichier jar `UdfApp-0.0.1.jar` .</span><span class="sxs-lookup"><span data-stu-id="c6acf-111">Compile and package your project to create and executable jar say `UdfApp-0.0.1.jar`.</span></span>

## <a name="register-and-call-java-udfs-in-net-for-apache-spark"></a><span data-ttu-id="c6acf-112">Inscrire et appeler des fonctions définies par l’utilisateur Java dans .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="c6acf-112">Register and call Java UDFs in .NET for Apache Spark</span></span>

1. <span data-ttu-id="c6acf-113">Utilisez l' [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API pour inscrire votre UDF Java avec Spark SQL.</span><span class="sxs-lookup"><span data-stu-id="c6acf-113">Use the [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API to register your Java UDF with Spark SQL.</span></span>
2. <span data-ttu-id="c6acf-114">Inscrivez le `DataFrame` sur lequel vous souhaitez appeler votre UDF en tant que table SQL à l’aide de la [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) fonction.</span><span class="sxs-lookup"><span data-stu-id="c6acf-114">Register the `DataFrame` on which you want to call your UDF as an SQL Table using the [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) function.</span></span>
3. <span data-ttu-id="c6acf-115">Utilisez `SparkSession.Sql` pour appeler l’UDF sur la vue table à l’aide de Spark SQL.</span><span class="sxs-lookup"><span data-stu-id="c6acf-115">Use `SparkSession.Sql` to call the UDF on the table view using Spark SQL.</span></span>
<span data-ttu-id="c6acf-116">Voici un exemple de base pour illustrer les étapes ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="c6acf-116">A basic example to illustrate the above steps:</span></span>

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

4. <span data-ttu-id="c6acf-117">Soumettez cette application `spark-submit` en utilisant en passant le fichier jar Java UDF précédemment compilé par le biais de l' `--jars` option :</span><span class="sxs-lookup"><span data-stu-id="c6acf-117">Submit this application using `spark-submit` by passing the previously compiled Java UDF jar through the `--jars` option:</span></span>

    ```bash
    spark-submit --master local --jars UdfApp-0.0.1.jar --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-3.0.x-0.12.1.jar InterRuntimeUDFs.exe
    ```

    <span data-ttu-id="c6acf-118">Le `dfUdf` tableau résultant avait le nombre 5 ajouté à chaque ligne de la colonne d’entrée, comme défini par `JavaUdf` :</span><span class="sxs-lookup"><span data-stu-id="c6acf-118">The resultant `dfUdf` DataFrame had the number 5 added to each row of the input column as defined by `JavaUdf`:</span></span>

    ```text
    +-------+
    | Result|
    +-------+
    |      7|
    |     10|
    +-------+
    ```

## <a name="call-net-udf-from-scala-or-python-in-apache-spark"></a><span data-ttu-id="c6acf-119">Appeler la fonction UDF .NET à partir de Scala ou python dans Apache Spark</span><span class="sxs-lookup"><span data-stu-id="c6acf-119">Call .NET UDF from Scala or Python in Apache Spark</span></span>

<span data-ttu-id="c6acf-120">Vous pouvez également inscrire et appeler une fonction UDF C# à partir d’une application Apache Spark écrite en Scala ou python à l’aide de [l’outil sparkdotnetudf Open source](https://github.com/imback82/sparkdotnetudf).</span><span class="sxs-lookup"><span data-stu-id="c6acf-120">You can also register and invoke a C# UDF from an Apache Spark application written in Scala or Python using [the sparkdotnetudf open source tool](https://github.com/imback82/sparkdotnetudf).</span></span>
