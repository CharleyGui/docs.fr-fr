---
title: Créer des fonctions définies par l’utilisateur (UDF) dans .NET pour Apache Spark
description: Découvrez comment implémenter des fonctions définies par l’utilisateur (UDF) dans .NET pour les applications Apache Spark.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 97afda8ed17d3719c534d72ad3ad026745a70922
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620922"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a>Créer des fonctions définies par l’utilisateur (UDF) dans .NET pour Apache Spark

Dans cet article, vous allez apprendre à utiliser des fonctions définies par l’utilisateur (UDF) dans .NET pour Apache Spark. [Fonctions définies](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) par l’utilisateur) est une fonctionnalité Spark qui vous permet d’utiliser des fonctions personnalisées pour étendre les fonctionnalités intégrées du système. Les fonctions définies par l’utilisateur transforment les valeurs d’une ligne unique dans une table pour produire une valeur de sortie correspondante unique par ligne en fonction de la logique définie dans la fonction définie par l’utilisateur.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="define-udfs"></a>Définir des fonctions définies par l’utilisateur

Passez en revue la définition UDF suivante :

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

La fonction UDF prend `string` comme entrée sous la forme d’une [colonne](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) d’un [tableau](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) et retourne un `string` avec `hello` ajouté devant l’entrée.

Le tableau suivant `df` contient une liste de noms :

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

À présent, nous allons appliquer ce `udf` qui est défini à tableau `df` :

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

Le tableau suivant `udfResult` est le résultat de la fonction UDF :

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

Pour mieux comprendre comment implémenter des fonctions définies par l’utilisateur, consultez les [fonctions d’assistance UDF](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) et des [exemples](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) sur GitHub.

## <a name="udf-serialization"></a>Sérialisation UDF

Comme les fonctions définies par l’utilisateur sont des fonctions qui doivent être exécutées sur les Workers, elles doivent être sérialisées et envoyées aux employés dans le cadre de la charge utile du pilote. Le [délégué](../../csharp/programming-guide/delegates/index.md), qui est une référence à la méthode, doit être sérialisé ainsi que sa [cible](xref:System.Delegate.Target%2A), qui est l’instance de classe sur laquelle le délégué actuel appelle la méthode d’instance. Passez en revue cet [exemple de code dans GitHub](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) pour mieux comprendre le fonctionnement de la sérialisation UDF.

.NET pour Apache Spark utilise .NET Core, qui ne prend pas en charge la sérialisation des délégués. Au lieu de cela, la réflexion est utilisée pour sérialiser la cible où le délégué est défini. Lorsque plusieurs délégués sont définis dans une étendue commune, ils ont une fermeture partagée qui devient la cible de la réflexion pour la sérialisation.

### <a name="serialization-example"></a>Exemple de sérialisation

L’extrait de code suivant définit deux variables de chaîne qui sont référencées dans deux délégués de fonction qui retournent les chaînes respectives comme résultat :

```csharp
using System;

public class C {
    public void M() {
        string s1 = "s1";
        string s2 = "s2";
        Func<string, string> a = str => s1;
        Func<string, string> b = str => s2;
    }
}
```

Le code C# ci-dessus génère le code du code machine C# suivant (source de crédit : [sharplab.IO](https://sharplab.io)) à partir du compilateur :

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        public string s2;

        internal string <M>b__0(string str)
        {
            return s1;
        }

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        <>c__DisplayClass0_.s2 = "s2";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_.<M>b__1);
    }
}
```

`func`Et `func2` partagent la même fermeture `<>c__DisplayClass0_0` , qui est la cible qui est sérialisée lors de la sérialisation des délégués `func` et `func2` . Même si `Func<string, string> a` fait uniquement référence `s1` `s2` à, est également sérialisé lorsque les octets sont envoyés aux threads de travail.

Cela peut entraîner des comportements inattendus au moment de l’exécution (comme dans le cas de l’utilisation de [variables de diffusion](broadcast-guide.md)), c’est pourquoi nous vous recommandons de limiter la visibilité des variables utilisées dans une fonction à la portée de cette fonction.

L’extrait de code suivant est la méthode recommandée pour implémenter le comportement de sérialisation souhaité :

```csharp
using System;

public class C {
    public void M() {
        {
            string s1 = "s1";
            Func<string, string> a = str => s1;
        }
        {
            string s2 = "s2";
            Func<string, string> b = str => s2;
        }
    }
}
```

Le code C# ci-dessus génère le code du code machine C# suivant (source de crédit : [sharplab.IO](https://sharplab.io)) à partir du compilateur :

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        internal string <M>b__0(string str)
        {
            return s1;
        }
    }

    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_1
    {
        public string s2;

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        <>c__DisplayClass0_1 <>c__DisplayClass0_2 = new <>c__DisplayClass0_1();
        <>c__DisplayClass0_2.s2 = "s2";
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_2.<M>b__1);
    }
}
```

Notez que `func` et `func2` ne partagent plus de fermeture et qu’ils ont leurs propres fermetures distinctes `<>c__DisplayClass0_0` et `<>c__DisplayClass0_1` respectivement. Lorsqu’il est utilisé comme cible pour la sérialisation, rien d’autre que les variables référencées ne sera sérialisé pour le délégué. Ce comportement est important à prendre en compte lors de l’implémentation de plusieurs fonctions définies par l’utilisateur dans une étendue commune.

## <a name="some-spark-udf-caveats"></a>Certains avertissements UDF Spark

* Les valeurs NULL dans les fonctions définies par l’utilisateur peuvent lever des exceptions. Il incombe au développeur de les gérer.
* Les fonctions définies par l’utilisateur n’exploitent pas les optimisations fournies par les fonctions intégrées d’Spark. il est donc recommandé d’utiliser des fonctions intégrées dans la mesure du possible.

## <a name="next-steps"></a>Étapes suivantes

* [Bien démarrer avec .NET pour Apache Spark](../tutorials/get-started.md)
* [Déboguer une application .NET pour Apache Spark sur Windows](debug.md)
