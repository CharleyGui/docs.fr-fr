---
title: Relations des types dans des opérations de requête LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 41853e6858fae9e8d449aeed95a6a84f343d5874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635611"
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Relations des types dans des opérations de requête LINQ (C#)
Pour écrire efficacement des requêtes, vous devez comprendre comment les types des variables dans une opération de requête complète sont liés les uns aux autres. Si vous comprenez ces relations, vous comprendrez plus facilement les échantillons et les exemples de code linQ dans la documentation. En outre, vous comprendrez ce qui se passe en arrière-plan lorsque des variables sont implicitement typées à l’aide de `var`.  
  
 Les opérations de requête linQ sont fortement tapées dans la source de données, dans la requête elle-même et dans l’exécution de la requête. Le type des variables dans la requête doit être compatible avec le type des éléments dans la source de données, ainsi qu’avec le type de la variable d’itération dans l’instruction `foreach`. Ce typage fort garantit l’interception des erreurs de type au moment de la compilation lorsqu’elles peuvent être corrigées avant que les utilisateurs ne les rencontrent.  
  
 Pour illustrer ces relations de types, la plupart des exemples qui suivent utilisent le typage explicite pour toutes les variables. Le dernier exemple montre comment les mêmes principes s’appliquent même si vous utilisez le typage implicite à l’aide de [var](../../../language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Requêtes qui ne transforment pas les données sources  
 L’illustration suivante montre une opération de requête LINQ to Objects qui n’effectue aucune transformation sur les données. La source contient une séquence de chaînes et le résultat de la requête est également une séquence de chaînes.  
  
 ![Diagramme illustrant la relation entre les types de données dans une requête LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. L’argument de type de la source de données détermine le type de la variable de portée.  
  
2. Le type de l’objet sélectionné détermine le type de la variable de requête. Ici, `name` est une chaîne. Par conséquent, la variable de requête est un `IEnumerable<string>`.  
  
3. La variable de requête fait l’objet d’une itération dans l’instruction `foreach`. Comme la variable de requête est une séquence de chaînes, la variable d’itération est également une chaîne.  
  
## <a name="queries-that-transform-the-source-data"></a>Requêtes qui transforment les données sources  
 L’illustration suivante montre une opération de requête [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] qui effectue une transformation simple des données. La requête accepte une séquence d’objets `Customer` en entrée et sélectionne uniquement la propriété `Name` dans le résultat. Comme `Name` est une chaîne, la requête produit une séquence de chaînes en sortie.  
  
 ![Diagramme montrant une requête qui transforme le type de données.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. L’argument de type de la source de données détermine le type de la variable de portée.  
  
2. L’instruction `select` retourne la propriété `Name` à la place de l’objet `Customer` complet. Comme `Name` est une chaîne, l’argument de type de `custNameQuery` est `string`, et non pas `Customer`.  
  
3. Comme `custNameQuery` est une séquence de chaînes, la variable d’itération de la boucle `foreach` doit également être de type `string`.  
  
 L’illustration suivante montre une transformation légèrement plus complexe. L’instruction `select` retourne un type anonyme qui capture seulement deux membres de l’objet `Customer` original.  
  
 ![Diagramme montrant une requête plus complexe qui transforme le type de données.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. L’argument de type de la source de données est toujours le type de la variable de portée dans la requête.  
  
2. Comme l’instruction `select` génère un type anonyme, la variable de requête doit être implicitement typée à l’aide de `var`.  
  
3. Comme le type de la variable de requête est implicite, la variable d’itération dans la boucle `foreach` doit également être implicite.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Laisser le compilateur déduire les informations de type  
 Vous devez comprendre les relations des types dans une opération de requête. Toutefois, vous avez la possibilité de laisser le compilateur faire tout le travail à votre place. Le mot clé [var](../../../language-reference/keywords/var.md) peut être utilisé pour toute variable locale dans une opération de requête. L’illustration suivante est similaire à l’exemple numéro 2 qui a été abordé précédemment. Toutefois, le compilateur fournit le type fort pour chaque variable dans l’opération de requête.  
  
 ![Diagramme illustrant le flux de type avec typage implicite.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 Pour plus d’informations sur `var`, consultez [Variables locales implicitement typées](../../classes-and-structs/implicitly-typed-local-variables.md).  
