---
title: Spécifier dynamiquement des filtres de prédicat au moment de l’exécution (LINQ en C#)
description: Découvrez comment spécifier dynamiquement des filtres de prédicat au moment de l’exécution à l’aide de LINQ en C#.
ms.date: 12/01/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 314be8f98b9ff014f14bef11a1f3581eff8574b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659941"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>Spécifier dynamiquement des filtres de prédicat au moment de l’exécution

Dans certains cas, ce n’est qu’au moment de l’exécution que vous savez combien de prédicats vous devez appliquer aux éléments sources dans la clause `where`. L’une des manières de spécifier plusieurs filtres de prédicat de manière dynamique consiste à utiliser la méthode <xref:System.Linq.Enumerable.Contains%2A>, comme indiqué dans l’exemple suivant. L’exemple est construit de deux façons. Tout d’abord, le projet est exécuté en filtrant les valeurs fournies dans le programme. Ensuite, le projet est réexécuté à l’aide de l’entrée fournie au moment de l’exécution.

## <a name="to-filter-by-using-the-contains-method"></a>Pour filtrer à l’aide de la méthode Contains

1. Ouvrez une nouvelle application console et nommez-la `PredicateFilters`.

2. Copiez la classe `StudentClass` à partir de [Interroger une collection d’objets](query-a-collection-of-objects.md) et collez-la dans l’espace de noms `PredicateFilters` sous la classe `Program`. `StudentClass` fournit une liste d’objets `Student`.

3. Commentez la méthode `Main` dans `StudentClass`.

4. Remplacez la classe `Program` par le code suivant :

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. Ajoutez la ligne suivante à la méthode `Main` dans la classe `DynamicPredicates`, sous la déclaration de `ids`.

     ```csharp
     QueryById(ids);
     ```

6. Exécutez le projet.

7. La sortie suivante s’affiche dans une fenêtre de console :

     Garcia: 114

     O’Donnell: 112

     Omelchenko: 111

8. L’étape suivante consiste à réexécuter le projet, cette fois en utilisant l’entrée saisie au moment de l’exécution plutôt que le tableau `ids`. Remplacez `QueryByID(ids)` par `QueryByID(args)` dans la méthode `Main`.

9. Exécutez le projet avec les arguments de ligne de commande `122 117 120 115`. Quand le projet s’exécute, ces valeurs deviennent des éléments de `args`, le paramètre de la méthode `Main`.

10. La sortie suivante s’affiche dans une fenêtre de console :

     Adams: 120

     Feng: 117

     Garcia: 115

     Tucker: 122

## <a name="to-filter-by-using-a-switch-statement"></a>Pour filtrer à l’aide d’une instruction switch

1. Vous pouvez utiliser une instruction `switch` pour sélectionner parmi d’autres requêtes prédéterminées. Dans l’exemple suivant, `studentQuery` utilise une autre clause `where` en fonction du niveau, ou de l’année, spécifié(e) au moment de l’exécution.

2. Copiez la méthode suivante et collez-la dans la classe `DynamicPredicates`.

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. Dans la méthode `Main`, remplacez l’appel à `QueryByID` par l’appel suivant, qui envoie le premier élément du tableau `args` comme argument : `QueryByYear(args[0])`.

4. Exécutez le projet avec un argument de ligne de commande d’une valeur entière comprise entre 1 et 4.

## <a name="see-also"></a>Voir aussi

- [Requête intégrée linguistique (LINQ)](index.md)
- [où la clause](../language-reference/keywords/where-clause.md)
