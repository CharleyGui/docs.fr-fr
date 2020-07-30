---
title: 'Procédure pas à pas : Écrire des requêtes en C# (LINQ)'
description: Cette procédure pas à pas montre comment les fonctionnalités du langage C# sont utilisées dans les expressions de requête LINQ. Cet article utilise Visual Studio comme environnement de développement.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: d49cb725c9ce9a417f78f638795e98a75a086893
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302215"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Procédure pas à pas : Écrire des requêtes en C# (LINQ)
Cette procédure pas à pas présente les fonctionnalités du langage C# utilisées pour écrire des expressions de requête LINQ.  
  
## <a name="create-a-c-project"></a>Créer un projet C#  
  
> [!NOTE]
> Les instructions suivantes s’appliquent à Visual Studio. Si vous utilisez un environnement de développement différent, créez un projet console avec une référence à System.Core.dll et une directive `using` pour l’espace de noms <xref:System.Linq?displayProperty=nameWithType>.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Pour créer un projet dans Visual Studio  
  
1. Démarrez Visual Studio.  
  
2. Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s’affiche.  
  
3. Développez **Installé**, **Modèles**, **Visual C#**, puis choisissez **Application console**.  
  
4. Dans la zone de texte **Nom**, entrez un nom différent ou acceptez le nom par défaut, puis choisissez le bouton **OK**.  
  
     Le nouveau projet s’affiche dans l’**Explorateur de solutions**.  
  
5. Notez que votre projet a une référence à System.Core.dll et une directive `using` pour l’espace de noms <xref:System.Linq?displayProperty=nameWithType>.  
  
## <a name="create-an-in-memory-data-source"></a>Créer une source de données en mémoire  
 La source de données pour les requêtes est une simple liste d’objets `Student`. Chaque enregistrement `Student` comporte un prénom, un nom et un tableau d’entiers représentant les notes d’examens en classe. Copiez ce code dans votre projet. Notez les caractéristiques suivantes :  
  
- La classe `Student` se compose de propriétés implémentées automatiquement.  
  
- Chaque étudiant de la liste est initialisé avec un initialiseur d’objet.  
  
- La liste elle-même est initialisée avec un initialiseur de collection.  
  
 La totalité de cette structure de données est initialisée et instanciée sans appels explicites à un constructeur quelconque ni accès au membre explicite. Pour plus d’informations sur ces nouvelles fonctionnalités, consultez [Propriétés implémentées automatiquement](../../classes-and-structs/auto-implemented-properties.md) et [Initialiseurs d’objets et de collection](../../classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Pour ajouter la source de données  
  
- Ajoutez la classe `Student` et la liste initialisée d’étudiants à la classe `Program` dans votre projet.  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Pour ajouter un nouvel étudiant à la liste des étudiants  
  
1. Ajoutez un nouvel élément `Student` à la liste `Students` et utilisez le nom et les notes d’examens de votre choix. Essayez d’entrer toutes les informations relatives au nouvel étudiant pour mieux apprendre la syntaxe de l’initialiseur d’objet.  
  
## <a name="create-the-query"></a>Créer la requête  
  
#### <a name="to-create-a-simple-query"></a>Pour créer une requête simple  
  
- Dans la méthode `Main` de l’application, créez une requête simple qui, quand elle est exécutée, produit une liste de tous les étudiants dont la note pour le premier test est supérieure à 90. Notez que, puisque l’objet `Student` entier est sélectionné, le type de la requête est `IEnumerable<Student>`. Bien que le code puisse également utiliser un type implicite à l’aide du mot clé [var](../../../language-reference/keywords/var.md), les types explicites sont utilisés pour illustrer clairement les résultats. (Pour plus d’informations sur `var` , consultez [variables locales implicitement typées](../../classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Notez également que la variable de portée de la requête, `student`, sert de référence à chaque `Student` dans la source, en fournissant l’accès au membre pour chaque objet.  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a>Exécuter la requête  
  
#### <a name="to-execute-the-query"></a>Pour exécuter la requête  
  
1. Écrivez maintenant la boucle `foreach` qui entraînera l’exécution de la requête. Notez les points suivants concernant le code :  
  
    - Chaque élément de la séquence retournée est accessible via la variable d’itération dans la boucle `foreach`.  
  
    - Le type de cette variable est `Student` et le type de la variable de requête est compatible, `IEnumerable<Student>`.  
  
2. Après avoir ajouté ce code, générez et exécutez l’application pour visualiser les résultats dans la fenêtre de **console**.  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a>Pour ajouter une autre condition de filtre  
  
1. Vous pouvez associer plusieurs conditions booléennes dans la clause `where` pour affiner davantage une requête. Le code suivant ajoute une condition afin que la requête retourne les étudiants dont la première note est supérieure à 90 et dont la dernière est inférieure à 80. La clause `where` doit être semblable au code suivant.  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Pour plus d’informations, consultez [where, clause](../../../language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Modifier la requête  
  
#### <a name="to-order-the-results"></a>Pour classer les résultats  
  
1. Il est plus facile d’analyser les résultats s’ils sont classés. Vous pouvez classer la séquence retournée selon tous les champs accessibles dans les éléments sources. Par exemple, la clause `orderby` suivante classe les résultats dans l’ordre alphabétique de A à Z d’après le nom de chaque étudiant. Ajoutez la clause `orderby` suivante à votre requête, juste après l’instruction `where` et avant l’instruction `select` :  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. Modifiez à présent la clause `orderby` pour qu’elle classe les résultats dans l’ordre inverse d’après la note au premier examen, de la plus élevée à la plus faible.  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. Modifiez la chaîne de format `WriteLine` pour pouvoir consulter les notes :  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Pour plus d’informations, consultez [orderby, clause](../../../language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Pour regrouper les résultats  
  
1. Le regroupement est une fonction puissante des expressions de requête. Une requête avec une clause group produit une séquence de groupes dont chaque groupe contient lui-même un élément `Key` et une séquence composée de tous les membres de ce groupe. La nouvelle requête suivante regroupe les étudiants en utilisant la première lettre de leur nom comme clé.  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. Notez que le type de la requête a maintenant changé. Elle produit désormais une séquence de groupes qui ont un type `char` comme clé et une séquence d’objets `Student`. Étant donné que le type de la requête a changé, le code suivant modifie également la boucle d’exécution `foreach` :  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. Exécutez l’application et affichez les résultats dans la fenêtre de **console**.  
  
     Pour plus d’informations, consultez [Group, clause](../../../language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Pour rendre les variables implicitement typées  
  
1. Le codage explicite de `IEnumerables` de `IGroupings` peut rapidement s’avérer laborieux. Vous pouvez écrire la même requête et la même boucle `foreach` beaucoup plus facilement à l’aide de `var`. Le mot clé `var` ne modifie pas les types de vos objets ; il indique simplement au compilateur de déduire les types. Remplacez le type de `studentQuery` et la variable d’itération `group` par `var` et réexécutez la requête. Notez que, dans la boucle `foreach` interne, la variable d’itération est encore typée comme `Student` et que la requête fonctionne exactement comme précédemment. Remplacez la variable d’itération `s` par `var` et exécutez à nouveau la requête. Vous pouvez constater que les résultats obtenus sont exactement les mêmes.  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     Pour plus d’informations sur [var](../../../language-reference/keywords/var.md), consultez [Variables locales implicitement typées](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Pour classer les groupes selon leur valeur de clé  
  
1. Quand vous exécutez la requête précédente, vous remarquez que les groupes ne sont pas dans l’ordre alphabétique. Pour modifier cet ordre, vous devez fournir une clause `orderby` après la clause `group`. Toutefois, pour utiliser une clause `orderby`, vous avez d’abord besoin d’un identificateur servant de référence aux groupes créés par la clause `group`. Fournissez l’identificateur à l’aide du mot clé `into`, comme suit :  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     Quand vous exécutez cette requête, vous voyez que les groupes sont désormais classés par ordre alphabétique.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Pour introduire un identificateur à l’aide de let  
  
1. Vous pouvez utiliser le mot clé `let` pour introduire un identificateur pour tous les résultats d’expression dans l’expression de requête. Cet identificateur peut être pratique, comme dans l’exemple suivant, ou améliorer les performances en stockant les résultats d’une expression afin d’éviter qu’ils ne soient calculés plusieurs fois.  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     Pour plus d’informations, consultez [let, clause](../../../language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Pour utiliser la syntaxe de méthode dans une expression de requête  
  
1. Comme décrit dans [Syntaxe de requête et syntaxe de méthode dans LINQ](./query-syntax-and-method-syntax-in-linq.md), certaines opérations de requête peuvent être exprimées uniquement à l’aide de la syntaxe de méthode. Le code suivant calcule la note totale de chaque `Student` dans la séquence source, puis appelle la méthode `Average()` sur les résultats de cette requête pour calculer la note moyenne de la classe.
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Pour transformer ou projeter la clause select  
  
1. Il n’est pas rare qu’une requête produise une séquence dont les éléments diffèrent des éléments des séquences sources. Supprimez ou commentez votre requête et votre boucle d’exécution précédentes, et remplacez-les par le code suivant. Notez que la requête retourne une séquence de chaînes (pas `Students`) et que ce fait est répercuté dans la boucle `foreach`.  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. Le code utilisé précédemment dans cette procédure pas à pas indique que la note moyenne de la classe est d’environ 334. Pour produire une séquence de `Students` dont la note totale est supérieure à la moyenne de classe, avec les `Student ID` correspondants, vous pouvez utiliser un type anonyme dans l’instruction `select` :  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a>Étapes suivantes  
 Une fois que vous êtes familiarisé avec les aspects de base de l’utilisation de requêtes en C#, vous êtes prêt à lire la documentation et les exemples pour le type spécifique de fournisseur LINQ qui vous intéresse :  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ to XML (C#)](./linq-to-xml-overview.md)  
  
 [LINQ to Objects (C#)](./linq-to-objects.md)  
  
## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query) (C#)](./index.md)
- [Expressions de requête LINQ](../../../linq/index.md)
