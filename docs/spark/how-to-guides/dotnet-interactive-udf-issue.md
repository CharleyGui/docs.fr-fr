---
title: Écrivez et appelez des fonctions définies par l’utilisateur dans .NET pour Apache Spark environnements interactifs.
description: Découvrez comment écrire et appeler des fonctions définies par l’utilisateur dans .NET pour Apache Spark des shells interactifs.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 8fb729a0b8220d15af641f916383bbd6146e2e33
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94441074"
---
# <a name="write-and-call-udfs-in-net-for-apache-spark-interactive-environments"></a>Écrire et appeler des fonctions définies par l’utilisateur dans .NET pour Apache Spark environnements interactifs

Dans cet article, vous allez apprendre à utiliser des fonctions définies par l’utilisateur (UDF) dans un .NET pour Apache Spark environnement interactif.

## <a name="prerequisites"></a>Prérequis

1. Installer [.net interactive](https://github.com/dotnet/interactive)
2. Installer [Jupyter Lab](https://jupyter.org/)

## <a name="net-for-apache-spark-interactive-experience"></a>.NET pour Apache Spark l’expérience interactive

[.Net pour Apache Spark](https://github.com/dotnet/spark) utilise [.net interactive](https://devblogs.microsoft.com/dotnet/net-interactive-is-here-net-notebooks-preview-2/) pour assurer la prise en charge par .net de l’expérience interactive dans Spark. Pour comprendre comment configurer l’environnement afin d’essayer .NET interactive avec des blocs-notes Jupyter, consultez le [référentiel interactif .net](https://github.com/dotnet/interactive).

En outre, il est recommandé de parcourir [cet article sur la SÉRIALISATION UDF dans .net pour Apache Spark](udf-guide.md) pour comprendre quelles sont les fonctions définies par l’utilisateur et comment elles sont sérialisées dans .net pour Apache Spark.
Ce guide utilise les blocs-notes Jupyter pour illustrer l’utilisation des fonctions définies par l’utilisateur dans une expérience interactive.

## <a name="define-a-udf-in-net-interactive"></a>Définir une FDU dans .NET interactive

Dans l’expérience interactive, une cellule peut être considérée comme l’extrait de code qui est soumis dans le cadre d’une itération de la [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop). Par exemple, jetez un coup d’œil au bloc-notes suivant pour comprendre ce que cela signifie :

![Cellules Jupyter Notebook](./media/dotnet-interactive/dotnet-interactive-cells.png)

Chacun de ces blocs marqués par la flèche rouge est une cellule, ou une soumission de code à Spark. Désormais, lors de la définition d’une fonction définie par l’utilisateur qui fait référence à un objet personnalisé défini par l’utilisateur, il est nécessaire que la fonction définie par l’utilisateur soit définie dans la même cellule que l’objet auquel elle fait référence. Examinons ce qui ressemble à un exemple :

![Travail UDF](./media/dotnet-interactive/working-udf.png)

## <a name="call-a-udf-on-a-dataframe"></a>Appeler une FDU sur un tableau

Lors de l’appel d’une FDU définie précédemment sur un `DataFrame` , il est important de s’assurer que la FDU est définie dans une cellule précédemment soumise, avant de l’appeler, comme illustré dans l’exemple précédent.

Voyons maintenant ce qui se passe si nous appelons la fonction UDF dans la même cellule où elle est définie.

![échec de l’appel UDF](./media/dotnet-interactive/udf_fails.png)

L’erreur en surbrillance ci-dessus est due au fait que les assemblys UDF doivent d’abord être compilés et expédiés aux Workers avant de pouvoir être appelés sur un tableau.

Voici quelques points importants à prendre en compte lors de l’implémentation de fonctions définies par l’utilisateur dans .NET pour Apache Spark une expérience interactive (comme les [Notebooks Azure Synapse](/azure/synapse-analytics/spark/apache-spark-development-using-notebooks)).

## <a name="faqs"></a>FAQ

1. **Pourquoi mon UDF référençant un objet personnalisé défini par l’utilisateur génère-t-il l’erreur `Type Submission#_ is not marked as serializable` ?**
    .NET interactive enveloppe chacune de ces cellules avec une classe wrapper du numéro d’envoi de cellule pour identifier de manière unique chaque cellule en cours d’envoi. Comme expliqué en détail dans [ce guide](udf-guide.md), lorsqu’une fonction UDF qui référence un objet personnalisé est sérialisée, sa cible est également sélectionnée pour la sérialisation, ce qui, dans le cas de .net interactive, est encapsulé par la classe wrapper de la cellule où l’objet personnalisé est défini.
    Voyons maintenant comment cela affecte la définition de la FDU dans le bloc-notes :

    ![Erreur de sérialisation UDF](./media/dotnet-interactive/udf-serialization-error.png)

    Comme vous pouvez le constater dans le cas de `udf2_fails` , nous voyons le message d’erreur indiquant que le type `Submission#7` n’est pas marqué comme sérialisable, car .net interactive encapsule chaque objet défini dans une cellule avec sa `Submission#` classe, qui est générée à la volée et n’est donc pas marquée comme `Serializable` .

    Pour cette raison, il est **nécessaire qu’une FDU référençant un objet personnalisé soit définie dans la même cellule que cet objet**.

2. **Pourquoi les variables de diffusion ne fonctionnent-elles pas avec .NET interactive ?**
    Pour les raisons expliquées précédemment, les variables de diffusion ne fonctionnent pas avec .NET interactive. Il est judicieux de parcourir [ce guide sur les variables de diffusion](broadcast-guide.md) pour mieux comprendre quelles sont les variables de diffusion et comment les utiliser. La raison pour laquelle les variables de diffusion ne fonctionnent pas avec des scénarios interactifs est due à la conception de .NET interactive qui ajoute chaque objet défini dans une cellule à sa classe d’envoi de cellules, car n’est pas marqué comme sérialisable, échoue avec la même exception que celle qui est indiquée précédemment.
    Examinons un peu plus en détail l’exemple suivant :

    ![Échec des variables de diffusion](./media/dotnet-interactive/broadcast-fails.png)

    Comme nous l’avons recommandé dans les sections précédentes, nous définissons à la fois l’UDF et l’objet auquel il fait référence (variable de diffusion dans ce cas) dans la même cellule, mais nous voyons toujours l' `SerializationException` erreur indiquant `Microsoft.Spark.Sql.Session` qu’il n’est pas marqué comme sérialisable. En effet, lorsque le compilateur tente de sérialiser l’objet de variable de diffusion `bv` , il trouve son nom à ajouter à l' [`SparkSession`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) objet `spark` , qu’il doit être marqué comme sérialisable. Cela peut être démontré plus facilement en examinant l’assembly décompilé de cette soumission de cellule :

    ![Code assembleur décompilé](./media/dotnet-interactive/decompiledAssembly.png)

    Si nous markons la [`SparkSession`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) classe en tant que `[Serializable]` , nous pouvons faire fonctionner, mais ce n’est pas une solution idéale, car nous ne souhaitons pas donner à l’utilisateur la possibilité de sérialiser un objet SparkSession, car cela pourrait entraîner un comportement étrange et indésirable. Il s’agit d’un [problème connu](https://github.com/dotnet/spark/issues/619) qui sera résolu dans les futures versions.
