---
title: Créer des fonctions définies par l’utilisateur (UDF) dans .NET pour Apache Spark
description: Découvrez comment implémenter des fonctions définies par l’utilisateur (UDF) dans .NET pour les applications Apache Spark.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 50e631b0c561ebdf081d4c1b7d16bf25abb322e5
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224183"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a><span data-ttu-id="48078-103">Créer des fonctions définies par l’utilisateur (UDF) dans .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="48078-103">Create user-defined functions (UDF) in .NET for Apache Spark</span></span>

<span data-ttu-id="48078-104">Dans cet article, vous allez apprendre à utiliser des fonctions définies par l’utilisateur (UDF) dans .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="48078-104">In this article, you learn how to use user-defined functions (UDF) in .NET for Apache Spark.</span></span> <span data-ttu-id="48078-105">[Fonctions définies](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) par l’utilisateur) est une fonctionnalité Spark qui vous permet d’utiliser des fonctions personnalisées pour étendre les fonctionnalités intégrées du système.</span><span class="sxs-lookup"><span data-stu-id="48078-105">[UDFs)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) are a Spark feature that allow you to use custom functions to extend the system's built-in functionality.</span></span> <span data-ttu-id="48078-106">Les fonctions définies par l’utilisateur transforment les valeurs d’une ligne unique dans une table pour produire une valeur de sortie correspondante unique par ligne en fonction de la logique définie dans la fonction définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="48078-106">UDFs transform values from a single row within a table to produce a single corresponding output value per row based on the logic defined in the UDF.</span></span>

## <a name="define-udfs"></a><span data-ttu-id="48078-107">Définir des fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="48078-107">Define UDFs</span></span>

<span data-ttu-id="48078-108">Passez en revue la définition UDF suivante :</span><span class="sxs-lookup"><span data-stu-id="48078-108">Review the following UDF definition:</span></span>

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

<span data-ttu-id="48078-109">La fonction UDF prend `string` comme entrée sous la forme d’une [colonne](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) d’un [tableau](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) et retourne un `string` avec `hello` ajouté devant l’entrée.</span><span class="sxs-lookup"><span data-stu-id="48078-109">The UDF takes a `string` as an input in the form of a [Column](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) of a [Dataframe](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) and returns a `string` with `hello` appended in front of the input.</span></span>

<span data-ttu-id="48078-110">Le tableau suivant `df` contient une liste de noms :</span><span class="sxs-lookup"><span data-stu-id="48078-110">The following DataFrame `df` contains a list of names:</span></span>

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

<span data-ttu-id="48078-111">À présent, nous allons appliquer ce `udf` qui est défini à tableau `df` :</span><span class="sxs-lookup"><span data-stu-id="48078-111">Now let's apply the above defined `udf` to the DataFrame `df`:</span></span>

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

<span data-ttu-id="48078-112">Le tableau suivant `udfResult` est le résultat de la fonction UDF :</span><span class="sxs-lookup"><span data-stu-id="48078-112">The following DataFrame `udfResult` is the result of the UDF:</span></span>

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

<span data-ttu-id="48078-113">Pour mieux comprendre comment implémenter des fonctions définies par l’utilisateur, consultez les [fonctions d’assistance UDF](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) et des [exemples](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="48078-113">To better understand how to implement UDFs, review the [UDF helper functions](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) and [examples](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) on GitHub.</span></span>

## <a name="udf-serialization"></a><span data-ttu-id="48078-114">Sérialisation UDF</span><span class="sxs-lookup"><span data-stu-id="48078-114">UDF serialization</span></span>

<span data-ttu-id="48078-115">Comme les fonctions définies par l’utilisateur sont des fonctions qui doivent être exécutées sur les Workers, elles doivent être sérialisées et envoyées aux employés dans le cadre de la charge utile du pilote.</span><span class="sxs-lookup"><span data-stu-id="48078-115">Because UDFs are functions that need to be executed on workers, they have to be serialized and sent to the workers as part of the payload from the driver.</span></span> <span data-ttu-id="48078-116">Le [délégué](../../csharp/programming-guide/delegates/index.md), qui est une référence à la méthode, doit être sérialisé ainsi que sa [cible](xref:System.Delegate.Target%2A), qui est l’instance de classe sur laquelle le délégué actuel appelle la méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="48078-116">The [delegate](../../csharp/programming-guide/delegates/index.md), which is a reference to the method, needs to be serialized as well as its [target](xref:System.Delegate.Target%2A), which is the class instance on which the current delegate invokes the instance method.</span></span> <span data-ttu-id="48078-117">Passez en revue cet [exemple de code dans GitHub](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) pour mieux comprendre le fonctionnement de la sérialisation UDF.</span><span class="sxs-lookup"><span data-stu-id="48078-117">Review this [code example in GitHub](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) to get a better understanding of how UDF serialization is being done.</span></span>

<span data-ttu-id="48078-118">.NET pour Apache Spark utilise .NET Core, qui ne prend pas en charge la sérialisation des délégués.</span><span class="sxs-lookup"><span data-stu-id="48078-118">.NET for Apache Spark uses .NET Core, which doesn't support serializing delegates.</span></span> <span data-ttu-id="48078-119">Au lieu de cela, la réflexion est utilisée pour sérialiser la cible où le délégué est défini.</span><span class="sxs-lookup"><span data-stu-id="48078-119">Instead, reflection is used to serialize the target where the delegate is defined.</span></span> <span data-ttu-id="48078-120">Lorsque plusieurs délégués sont définis dans une étendue commune, ils ont une fermeture partagée qui devient la cible de la réflexion pour la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="48078-120">When multiple delegates are defined in a common scope, they have a shared closure that becomes the target of reflection for serialization.</span></span>

### <a name="serialization-example"></a><span data-ttu-id="48078-121">Exemple de sérialisation</span><span class="sxs-lookup"><span data-stu-id="48078-121">Serialization example</span></span>

<span data-ttu-id="48078-122">L’extrait de code suivant définit deux variables de chaîne qui sont référencées dans deux délégués de fonction qui retournent les chaînes respectives comme résultat :</span><span class="sxs-lookup"><span data-stu-id="48078-122">The following code snippet defines two string variables that are being referenced in two function delegates that return the respective strings as a result:</span></span>

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

<span data-ttu-id="48078-123">Le code C# ci-dessus génère le code du code machine C# suivant (source de crédit : [sharplab.IO](https://sharplab.io)) à partir du compilateur :</span><span class="sxs-lookup"><span data-stu-id="48078-123">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="48078-124">`func`Et `func2` partagent la même fermeture `<>c__DisplayClass0_0` , qui est la cible qui est sérialisée lors de la sérialisation des délégués `func` et `func2` .</span><span class="sxs-lookup"><span data-stu-id="48078-124">Both `func` and `func2` share the same closure `<>c__DisplayClass0_0`, which is the target that is serialized when serializing the delegates `func` and `func2`.</span></span> <span data-ttu-id="48078-125">Même si `Func<string, string> a` fait uniquement référence `s1` `s2` à, est également sérialisé lorsque les octets sont envoyés aux threads de travail.</span><span class="sxs-lookup"><span data-stu-id="48078-125">Even though `Func<string, string> a` is only referencing `s1`, `s2` is also serialized when the bytes are sent to the workers.</span></span>

<span data-ttu-id="48078-126">Cela peut entraîner des comportements inattendus au moment de l’exécution (comme dans le cas de l’utilisation de [variables de diffusion](broadcast-guide.md)), c’est pourquoi nous vous recommandons de limiter la visibilité des variables utilisées dans une fonction à la portée de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="48078-126">This can lead to some unexpected behaviors at runtime (like in the case of using [broadcast variables](broadcast-guide.md)), which is why we recommend that you restrict the visibility of the variables used in a function to that function's scope.</span></span>

<span data-ttu-id="48078-127">L’extrait de code suivant est la méthode recommandée pour implémenter le comportement de sérialisation souhaité :</span><span class="sxs-lookup"><span data-stu-id="48078-127">The following code snippet is the recommended way to implement the desired serialization behavior:</span></span>

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

<span data-ttu-id="48078-128">Le code C# ci-dessus génère le code du code machine C# suivant (source de crédit : [sharplab.IO](https://sharplab.io)) à partir du compilateur :</span><span class="sxs-lookup"><span data-stu-id="48078-128">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="48078-129">Notez que `func` et `func2` ne partagent plus de fermeture et qu’ils ont leurs propres fermetures distinctes `<>c__DisplayClass0_0` et `<>c__DisplayClass0_1` respectivement.</span><span class="sxs-lookup"><span data-stu-id="48078-129">Notice that `func` and `func2` no longer share a closure, and they have their own separate closures `<>c__DisplayClass0_0` and `<>c__DisplayClass0_1` respectively.</span></span> <span data-ttu-id="48078-130">Lorsqu’il est utilisé comme cible pour la sérialisation, rien d’autre que les variables référencées ne sera sérialisé pour le délégué.</span><span class="sxs-lookup"><span data-stu-id="48078-130">When used as the target for serialization, nothing other than the referenced variables will get serialized for the delegate.</span></span> <span data-ttu-id="48078-131">Ce comportement est important à prendre en compte lors de l’implémentation de plusieurs fonctions définies par l’utilisateur dans une étendue commune.</span><span class="sxs-lookup"><span data-stu-id="48078-131">This behavior is important to keep in mind while implementing multiple UDFs in a common scope.</span></span>

## <a name="some-spark-udf-caveats"></a><span data-ttu-id="48078-132">Certains avertissements UDF Spark</span><span class="sxs-lookup"><span data-stu-id="48078-132">Some Spark UDF caveats</span></span>

* <span data-ttu-id="48078-133">Les valeurs NULL dans les fonctions définies par l’utilisateur peuvent lever des exceptions.</span><span class="sxs-lookup"><span data-stu-id="48078-133">Null values in UDFs can throw exceptions.</span></span> <span data-ttu-id="48078-134">Il incombe au développeur de les gérer.</span><span class="sxs-lookup"><span data-stu-id="48078-134">It's the responsibility of the developer to handle them.</span></span>
* <span data-ttu-id="48078-135">Les fonctions définies par l’utilisateur n’exploitent pas les optimisations fournies par les fonctions intégrées d’Spark. il est donc recommandé d’utiliser des fonctions intégrées dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="48078-135">UDFs don't leverage the optimizations provided by Spark's built-in functions, so it's recommended to use built-in functions where possible.</span></span>

## <a name="faqs"></a><span data-ttu-id="48078-136">FAQ</span><span class="sxs-lookup"><span data-stu-id="48078-136">FAQs</span></span>

<span data-ttu-id="48078-137">**Pourquoi est-ce que j’obtiens l’erreur `System.NotImplementedException: The method or operation is not implemented.` ou `System.InvalidCastException: Unable to cast object of type 'System.Collections.Hashtable' to type 'System.Collections.Generic.IDictionary` lorsque j’essaie d’appeler une fonction UDF avec `ArrayType` ,, `MapType` `ArrayList` ou `HashTable` comme argument ou type de retour ?**</span><span class="sxs-lookup"><span data-stu-id="48078-137">**Why do I get the error `System.NotImplementedException: The method or operation is not implemented.` or `System.InvalidCastException: Unable to cast object of type 'System.Collections.Hashtable' to type 'System.Collections.Generic.IDictionary` when trying to call a UDF with `ArrayType`, `MapType`, `ArrayList`, or `HashTable` as argument or return type?**</span></span>  
<span data-ttu-id="48078-138">La prise en charge de `ArrayType` et de `MapType` n’est pas fournie jusqu’à la version [v 1.0](https://github.com/dotnet/spark/releases/tag/v1.0.0). par conséquent, vous obtiendriez cette erreur si vous utilisez un .net pour Apache Spark version antérieure à celle-ci, et que vous essayiez de passer ces types comme arguments à l’UDF ou en tant que type de retour.</span><span class="sxs-lookup"><span data-stu-id="48078-138">Support for `ArrayType` and `MapType` is not provided until [v1.0](https://github.com/dotnet/spark/releases/tag/v1.0.0), and so you would get this error if using a .NET for Apache Spark version prior to that, and trying to pass these types either as arguments to the UDF or as a return type.</span></span>
<span data-ttu-id="48078-139">`ArrayList` les `HashTable` types et ne peuvent pas être pris en charge en tant que types de retour d’une fonction définie par l’utilisateur, car il s’agit de collections non génériques. par conséquent, leurs définitions de type d’élément ne peuvent pas être fournies à Spark</span><span class="sxs-lookup"><span data-stu-id="48078-139">`ArrayList` and `HashTable` types cannot be supported as return types of a UDF as they are non-generic collections and hence their element type definitions cannot be provided to Spark.</span></span>

## <a name="next-steps"></a><span data-ttu-id="48078-140">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="48078-140">Next steps</span></span>

* [<span data-ttu-id="48078-141">Bien démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="48078-141">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="48078-142">Déboguer une application .NET pour Apache Spark sur Windows</span><span class="sxs-lookup"><span data-stu-id="48078-142">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
