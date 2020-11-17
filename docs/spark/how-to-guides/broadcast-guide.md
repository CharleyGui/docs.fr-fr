---
title: Utiliser des variables de diffusion dans .NET pour Apache Spark
description: Découvrez comment utiliser des variables de diffusion dans .NET pour les applications Apache Spark.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: ca6dab01cbd639594da0b51f145272a9a150e93c
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687751"
---
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a>Utiliser des variables de diffusion dans .NET pour Apache Spark

Dans cet article, vous allez apprendre à utiliser des variables de diffusion dans .NET pour Apache Spark. Les [variables de diffusion en Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) sont des mécanismes de partage de variables entre les exécuteurs qui sont destinés à être en lecture seule. Les variables de diffusion vous permettent de conserver une variable en lecture seule mise en cache sur chaque ordinateur plutôt que de lui envoyer une copie avec des tâches. Vous pouvez utiliser des variables de diffusion pour octroyer à chaque nœud une copie d’un jeu de données d’entrée volumineux de manière efficace.

Étant donné que les données ne sont envoyées qu’une seule fois, les variables de diffusion présentent des avantages en matière de performances par rapport aux variables locales qui sont expédiées aux exécuteurs avec chaque tâche. Reportez-vous à la [documentation relative à la variable officielle](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) pour obtenir une compréhension plus approfondie des variables de diffusion et de la raison pour laquelle elles sont utilisées.

## <a name="create-broadcast-variables"></a>Créer des variables de diffusion

Pour créer une variable de diffusion, appelez `SparkContext.Broadcast(v)` pour toute variable `v` . La variable de diffusion est un wrapper autour de la variable `v` , et sa valeur est accessible en appelant la `Value()` méthode.

Dans l’extrait de code suivant, une variable de chaîne `v` est créée et une variable de diffusion `bv` est créée lorsque `SparkContext.Broadcast(v)` est appelé. Notez que le paramètre de type pour `Broadcast` , String, correspond au type de la variable en cours de diffusion. La fonction définie par l’utilisateur (UDF) retourne la valeur de `bv` .

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a>Supprimer les variables de diffusion

La variable de diffusion peut être supprimée de tous les exécuteurs en appelant la `Destroy()` méthode.

```csharp
bv.Destroy();
```

`Destroy()` supprime toutes les données et métadonnées associées à la variable de diffusion et doit être utilisée avec précaution. Une fois qu’une variable de diffusion est détruite, elle ne peut plus être réutilisée.

## <a name="limit-broadcast-variable-scope-in-udfs"></a>Limiter l’étendue des variables de diffusion dans les fonctions définies par l’utilisateur

Lorsque vous utilisez des variables de diffusion dans des fonctions définies par l’utilisateur, vous devez limiter l’étendue de la variable à la fonction définie par l’utilisateur qui fait référence à la variable. Le [Guide d’utilisation des fonctions définies](udf-guide.md) par l’utilisateur décrit ce phénomène en détail. L’étendue est particulièrement essentielle lorsque vous appelez `Destroy()` sur la variable Broadcast.

Si la variable de diffusion qui a été détruite est visible ou accessible à partir d’autres fonctions définies par l’utilisateur, elle est récupérée pour la sérialisation par toutes les fonctions définies par l’utilisateur, même si elle n’y est pas référencée. .NET pour Apache Spark ne peut pas sérialiser la variable de diffusion détruite, ce qui génère une erreur. L’extrait de code suivant illustre cette erreur :

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

L’extrait de code suivant montre comment s’assurer que la destruction `bv` n’affecte pas en `udf2` raison d’un comportement de sérialisation inattendu :

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

## <a name="faqs"></a>FAQ

**Pourquoi les variables de diffusion ne fonctionnent-elles pas avec .NET interactive ?**  
Les variables de diffusion ne fonctionnent pas avec les scénarios interactifs en raison de la conception de .NET interactive qui ajoute chaque objet défini dans une cellule avec sa classe d’envoi de cellules, car n’est pas marqué comme sérialisable, échoue avec la même exception que celle qui est indiquée précédemment. Pour plus d’informations, consultez [cet article](dotnet-interactive-udf-issue.md).

## <a name="next-steps"></a>Étapes suivantes

* [Bien démarrer avec .NET pour Apache Spark](../tutorials/get-started.md)
* [Déboguer une application .NET pour Apache Spark sur Windows](debug.md)
* [Déployer .NET pour les fichiers binaires de fonctions définies par l’utilisateur et de Apache Spark Worker](deploy-worker-udf-binaries.md)
