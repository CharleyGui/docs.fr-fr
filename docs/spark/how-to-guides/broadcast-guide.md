---
title: Utiliser des variables de diffusion dans .NET pour Apache Spark
description: Découvrez comment utiliser des variables de diffusion dans .NET pour les applications Apache Spark.
ms.date: 06/11/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 391e32cda14a9b3186ac96800351ddcb39a3d359
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105595"
---
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a><span data-ttu-id="12e1f-103">Utiliser des variables de diffusion dans .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="12e1f-103">Use broadcast variables in .NET for Apache Spark</span></span>

<span data-ttu-id="12e1f-104">Dans cet article, vous allez apprendre à utiliser des variables de diffusion dans .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="12e1f-104">In this article, you learn how to use broadcast variables in .NET for Apache Spark.</span></span> <span data-ttu-id="12e1f-105">Les [variables de diffusion en Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) sont des mécanismes de partage de variables entre les exécuteurs qui sont destinés à être en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="12e1f-105">[Broadcast variables in Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) are mechanisms for sharing variables across executors that are meant to be read-only.</span></span> <span data-ttu-id="12e1f-106">Les variables de diffusion vous permettent de conserver une variable en lecture seule mise en cache sur chaque ordinateur plutôt que de lui envoyer une copie avec des tâches.</span><span class="sxs-lookup"><span data-stu-id="12e1f-106">Broadcast variables allow you to keep a read-only variable cached on each machine rather than shipping a copy of it with tasks.</span></span> <span data-ttu-id="12e1f-107">Vous pouvez utiliser des variables de diffusion pour octroyer à chaque nœud une copie d’un jeu de données d’entrée volumineux de manière efficace.</span><span class="sxs-lookup"><span data-stu-id="12e1f-107">You can use broadcast variables to give every node a copy of a large input dataset in an efficient manner.</span></span>

<span data-ttu-id="12e1f-108">Étant donné que les données ne sont envoyées qu’une seule fois, les variables de diffusion présentent des avantages en matière de performances par rapport aux variables locales qui sont expédiées aux exécuteurs avec chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="12e1f-108">Because the data is sent only once, broadcast variables have performance benefits when compared to local variables that are shipped to the executors with each task.</span></span> <span data-ttu-id="12e1f-109">Reportez-vous à la [documentation relative à la variable officielle](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) pour obtenir une compréhension plus approfondie des variables de diffusion et de la raison pour laquelle elles sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="12e1f-109">Refer to the [official broadcast variable documentation](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) to get a deeper understanding of broadcast variables and why they are used.</span></span>

## <a name="create-broadcast-variables"></a><span data-ttu-id="12e1f-110">Créer des variables de diffusion</span><span class="sxs-lookup"><span data-stu-id="12e1f-110">Create broadcast variables</span></span>

<span data-ttu-id="12e1f-111">Pour créer une variable de diffusion, appelez `SparkContext.Broadcast(v)` pour toute variable `v` .</span><span class="sxs-lookup"><span data-stu-id="12e1f-111">To create a broadcast variable, call `SparkContext.Broadcast(v)` for any variable `v`.</span></span> <span data-ttu-id="12e1f-112">La variable de diffusion est un wrapper autour de la variable `v` , et sa valeur est accessible en appelant la `Value()` méthode.</span><span class="sxs-lookup"><span data-stu-id="12e1f-112">The broadcast variable is a wrapper around the variable `v`, and its value can be accessed by calling the `Value()` method.</span></span>

<span data-ttu-id="12e1f-113">Dans l’extrait de code suivant, une variable de chaîne `v` est créée et une variable de diffusion `bv` est créée lorsque `SparkContext.Broadcast(v)` est appelé.</span><span class="sxs-lookup"><span data-stu-id="12e1f-113">In the following code snippet, a string variable `v` is created, and a broadcast variable `bv` is created when `SparkContext.Broadcast(v)`is called.</span></span> <span data-ttu-id="12e1f-114">Notez que le paramètre de type pour `Broadcast` , String, correspond au type de la variable en cours de diffusion.</span><span class="sxs-lookup"><span data-stu-id="12e1f-114">Notice the type parameter for `Broadcast`, string, matches the type of the variable being broadcasted.</span></span> <span data-ttu-id="12e1f-115">La fonction définie par l’utilisateur (UDF) retourne la valeur de `bv` .</span><span class="sxs-lookup"><span data-stu-id="12e1f-115">The user-defined function (UDF) returns the value of `bv`.</span></span>

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a><span data-ttu-id="12e1f-116">Supprimer les variables de diffusion</span><span class="sxs-lookup"><span data-stu-id="12e1f-116">Delete broadcast variables</span></span>

<span data-ttu-id="12e1f-117">La variable de diffusion peut être supprimée de tous les exécuteurs en appelant la `Destroy()` méthode.</span><span class="sxs-lookup"><span data-stu-id="12e1f-117">The broadcast variable can be deleted from all executors by calling the `Destroy()` method.</span></span>

```csharp
bv.Destroy();
```

<span data-ttu-id="12e1f-118">`Destroy()`supprime toutes les données et métadonnées associées à la variable de diffusion et doit être utilisée avec précaution.</span><span class="sxs-lookup"><span data-stu-id="12e1f-118">`Destroy()` deletes all data and metadata related to the broadcast variable and should be used with caution.</span></span> <span data-ttu-id="12e1f-119">Une fois qu’une variable de diffusion est détruite, elle ne peut plus être réutilisée.</span><span class="sxs-lookup"><span data-stu-id="12e1f-119">Once a broadcast variable is destroyed, it can't be used again.</span></span>

## <a name="limit-broadcast-variable-scope-in-udfs"></a><span data-ttu-id="12e1f-120">Limiter l’étendue des variables de diffusion dans les fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="12e1f-120">Limit broadcast variable scope in UDFs</span></span>

<span data-ttu-id="12e1f-121">Lorsque vous utilisez des variables de diffusion dans des fonctions définies par l’utilisateur, vous devez limiter l’étendue de la variable à la fonction définie par l’utilisateur qui fait référence à la variable.</span><span class="sxs-lookup"><span data-stu-id="12e1f-121">When you use broadcast variables in UDFs, you need to limit the scope of the variable to only the UDF that is referencing the variable.</span></span> <span data-ttu-id="12e1f-122">Le [Guide d’utilisation des fonctions définies](udf-guide.md) par l’utilisateur décrit ce phénomène en détail.</span><span class="sxs-lookup"><span data-stu-id="12e1f-122">The [guide to using UDFs](udf-guide.md) describes this phenomenon in detail.</span></span> <span data-ttu-id="12e1f-123">L’étendue est particulièrement essentielle lorsque vous appelez `Destroy()` sur la variable Broadcast.</span><span class="sxs-lookup"><span data-stu-id="12e1f-123">Scope is especially crucial when you call `Destroy()` on the broadcast variable.</span></span>

<span data-ttu-id="12e1f-124">Si la variable de diffusion qui a été détruite est visible ou accessible à partir d’autres fonctions définies par l’utilisateur, elle est récupérée pour la sérialisation par toutes les fonctions définies par l’utilisateur, même si elle n’y est pas référencée.</span><span class="sxs-lookup"><span data-stu-id="12e1f-124">If the broadcast variable that has been destroyed is visible to or accessible from other UDFs, it gets picked up for serialization by all of the UDFs, even if it is not being referenced by them.</span></span> <span data-ttu-id="12e1f-125">.NET pour Apache Spark ne peut pas sérialiser la variable de diffusion détruite, ce qui génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="12e1f-125">.NET for Apache Spark is unable to serialize the destroyed broadcast variable, which results in an error.</span></span> <span data-ttu-id="12e1f-126">L’extrait de code suivant illustre cette erreur :</span><span class="sxs-lookup"><span data-stu-id="12e1f-126">The following code snippet demonstrates this error:</span></span>

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

// Using the broadcast variable in a UDF:
Func<Column, Column> udf1 = Udf<string, string>(
    str => $"{str}: {bv.Value()}");

// Destroying bv
bv.Destroy();

// Calling udf1 after destroying bv throws the following expected exception:
// org.apache.spark.SparkException: Attempted to use Broadcast(0) after it was destroyed
df.Select(udf1(df["_1"])).Show();

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 throws the following (unexpected) exception:
// [Error] [JvmBridge] org.apache.spark.SparkException: Task not serializable
df.Select(udf2(df["_1"])).Show();
```

<span data-ttu-id="12e1f-127">L’extrait de code suivant montre comment s’assurer que la destruction `bv` n’affecte pas en `udf2` raison d’un comportement de sérialisation inattendu :</span><span class="sxs-lookup"><span data-stu-id="12e1f-127">The following code snippet demonstrates how to ensure that destroying `bv` doesn't affect `udf2` because of an unexpected serialization behavior:</span></span>

```csharp
string v = "Variable to be broadcasted";
// Restricting the visibility of bv to only the UDF referencing it
{
    Broadcast<string> bv = SparkContext.Broadcast(v);

    // Using the broadcast variable in a UDF:
    Func<Column, Column> udf1 = Udf<string, string>(
        str => $"{str}: {bv.Value()}");

    // Destroying bv
    bv.Destroy();
}

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 works fine as expected
df.Select(udf2(df["_1"])).Show();
```

## <a name="next-steps"></a><span data-ttu-id="12e1f-128">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="12e1f-128">Next steps</span></span>

* [<span data-ttu-id="12e1f-129">Bien démarrer avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="12e1f-129">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="12e1f-130">Déboguer une application .NET pour Apache Spark sur Windows</span><span class="sxs-lookup"><span data-stu-id="12e1f-130">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
* [<span data-ttu-id="12e1f-131">Déployer .NET pour les fichiers binaires de fonctions définies par l’utilisateur et de Apache Spark Worker</span><span class="sxs-lookup"><span data-stu-id="12e1f-131">Deploy .NET for Apache Spark worker and user-defined function binaries</span></span>](deploy-worker-udf-binaries.md)
