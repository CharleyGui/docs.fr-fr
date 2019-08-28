---
title: Écriture de requêtes dans Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 256075ad5de5b88595dd4be7f199a74b5912c082
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046545"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>Procédure pas à pas : Écriture de requêtes dans Visual Basic

Cette procédure pas à pas montre comment vous pouvez utiliser des fonctionnalités [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] de langage Visual Basic pour écrire des expressions de requête. La procédure pas à pas montre comment créer des requêtes sur une liste d’objets Student, comment exécuter les requêtes et comment les modifier. Les requêtes incorporent plusieurs fonctionnalités, notamment les initialiseurs d’objets, l’inférence de type local et les types anonymes.

À l’issue de cette procédure pas à pas, vous serez prêt à passer aux exemples et à la [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] documentation du fournisseur spécifique qui vous intéresse. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]les fournisseurs [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]incluent, LINQ to DataSet et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].

## <a name="create-a-project"></a>Créer un projet

### <a name="to-create-a-console-application-project"></a>Pour créer un projet d’application console

1. Démarrez Visual Studio.

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3. Dans la liste **modèles installés** , cliquez sur **Visual Basic**.

4. Dans la liste des types de projets, cliquez sur **application console**. Dans la zone **nom** , tapez un nom pour le projet, puis cliquez sur **OK**.

    Un projet est créé. Par défaut, il contient une référence à System. Core. dll. En outre, la liste des **espaces de noms** importés sur la [page références, le concepteur de projets (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) comprend l' <xref:System.Linq?displayProperty=nameWithType> espace de noms.

5. Sur la [page compiler, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), vérifiez que **Option Infer** a la valeur **on**.

## <a name="add-an-in-memory-data-source"></a>Ajouter une source de données en mémoire

La source de données pour les requêtes de cette procédure pas à pas `Student` est une liste d’objets. Chaque `Student` objet contient un prénom, un nom, une année de classe et un classement universitaire dans le corps de l’étudiant.

### <a name="to-add-the-data-source"></a>Pour ajouter la source de données

- Définissez une `Student` classe et créez une liste d’instances de la classe.

  > [!IMPORTANT]
  > Le code nécessaire à la définition `Student` de la classe et à la création de la liste utilisée dans les [exemples de procédures pas à pas est fourni dans How to: Créer une liste d’éléments](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Vous pouvez la copier à partir de là et la coller dans votre projet. Le nouveau code remplace le code qui s’est affiché lorsque vous avez créé le projet.

### <a name="to-add-a-new-student-to-the-students-list"></a>Pour ajouter un nouvel étudiant à la liste des étudiants

- Suivez le modèle dans la `getStudents` méthode pour ajouter une autre instance de `Student` la classe à la liste. L’ajout de l’étudiant vous introduira des initialiseurs d’objets. Pour plus d’informations, [consultez Initialiseurs d’objets: Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)nommés et anonymes.

## <a name="create-a-query"></a>Créer une requête

Une fois exécutée, la requête ajoutée dans cette section produit une liste des étudiants dont le classement universitaire les place dans les dix premiers. Étant donné que la requête sélectionne `Student` l’objet complet à chaque fois, le type du résultat `IEnumerable(Of Student)`de la requête est. Toutefois, le type de la requête n’est généralement pas spécifié dans les définitions de requête. Au lieu de cela, le compilateur utilise l’inférence de type local pour déterminer le type. Pour plus d’informations, consultez inférence de [type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). La variable de portée de la `currentStudent`requête,, sert de référence à `Student` chaque instance dans la source `students`,, qui fournit l’accès aux propriétés de chaque `students`objet dans.

### <a name="to-create-a-simple-query"></a>Pour créer une requête simple

1. Recherchez l’emplacement dans la `Main` méthode du projet qui est marqué comme suit:

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    Copiez le code suivant et collez-le dans.

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. Placez le pointeur de la `studentQuery` souris au-dessus de votre code pour vérifier que le type `IEnumerable(Of Student)`assigné par le compilateur est.

## <a name="run-the-query"></a>Exécuter la requête

La variable `studentQuery` contient la définition de la requête, et non les résultats de l’exécution de la requête. Une `For Each` boucle est un mécanisme classique pour exécuter une requête. Chaque élément de la séquence retournée est accessible via la variable d’itération de la boucle. Pour plus d’informations sur l’exécution des requêtes, consultez [écriture de votre première requête LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).

### <a name="to-run-the-query"></a>Pour exécuter la requête

1. Ajoutez la boucle `For Each` suivante sous la requête dans votre projet.

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. Placez le pointeur de la souris sur la variable `studentRecord` de contrôle de boucle pour voir son type de données. Le type de `studentRecord` est déduit `Student`comme étant, car `studentQuery` retourne une collection d' `Student` instances.

3. Générez et exécutez l’application en appuyant sur CTRL + F5. Notez les résultats dans la fenêtre de console.

## <a name="modify-the-query"></a>Modifier la requête

Il est plus facile d’analyser les résultats de la requête s’ils sont dans un ordre spécifié. Vous pouvez trier la séquence retournée en fonction de n’importe quel champ disponible.

### <a name="to-order-the-results"></a>Pour classer les résultats

1. Ajoutez la clause `Order By` suivante entre l' `Where` instruction et l' `Select` instruction de la requête. La `Order By` clause classe les résultats par ordre alphabétique de A à Z, en fonction du nom de famille de chaque étudiant.

    ```
    Order By currentStudent.Last Ascending
    ```

2. Pour classer par nom de famille, puis par prénom, ajoutez les deux champs à la requête:

    ```
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    Vous pouvez également spécifier `Descending` l’ordre de Z à A.

3. Générez et exécutez l’application en appuyant sur CTRL + F5. Notez les résultats dans la fenêtre de console.

### <a name="to-introduce-a-local-identifier"></a>Pour introduire un identificateur local

1. Ajoutez le code dans cette section pour introduire un identificateur local dans l’expression de requête. L’identificateur local contiendra un résultat intermédiaire. Dans l’exemple suivant, `name` est un identificateur qui contient une concaténation du prénom et du nom de l’étudiant. Un identificateur local peut être utilisé pour des raisons pratiques, ou il peut améliorer les performances en stockant les résultats d’une expression qui serait autrement calculée plusieurs fois.

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. Générez et exécutez l’application en appuyant sur CTRL + F5. Notez les résultats dans la fenêtre de console.

### <a name="to-project-one-field-in-the-select-clause"></a>Pour projeter un champ dans la clause SELECT

1. Ajoutez la requête et `For Each` la boucle à partir de cette section pour créer une requête qui produit une séquence dont les éléments diffèrent des éléments de la source. Dans l’exemple suivant, la source est une collection d' `Student` objets, mais un seul membre de chaque objet est retourné: le prénom des étudiants dont le nom est Garcia. Étant `currentStudent.First` donné que est une chaîne, le type de données de la `studentQuery3` séquence `IEnumerable(Of String)`retournée par est, une séquence de chaînes. Comme dans les exemples précédents, l’assignation d’un type de `studentQuery3` données pour est laissée au compilateur pour déterminer à l’aide de l’inférence de type local.

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. Placez le pointeur de la `studentQuery3` souris au-dessus de votre code pour vérifier que `IEnumerable(Of String)`le type affecté est.

3. Générez et exécutez l’application en appuyant sur CTRL + F5. Notez les résultats dans la fenêtre de console.

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Pour créer un type anonyme dans la clause SELECT

1. Ajoutez le code de cette section pour voir comment les types anonymes sont utilisés dans les requêtes. Vous les utilisez dans des requêtes lorsque vous souhaitez retourner plusieurs champs de la source de données plutôt que des enregistrements`currentStudent` complets (enregistrements dans des exemples précédents) ou`First` des champs uniques (dans la section précédente). Au lieu de définir un nouveau type nommé qui contient les champs que vous souhaitez inclure dans le résultat, vous spécifiez les champs `Select` dans la clause et le compilateur crée un type anonyme avec ces champs comme propriétés. Pour plus d’informations, consultez [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

    L’exemple suivant crée une requête qui retourne le nom et le rang de garantiront dont le classement universitaire est compris entre 1 et 10, par ordre de classement universitaire. Dans cet exemple, le type de `studentQuery4` doit être déduit, car la `Select` clause retourne une instance d’un type anonyme, et un type anonyme n’a pas de nom utilisable.

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. Générez et exécutez l’application en appuyant sur CTRL + F5. Notez les résultats dans la fenêtre de console.

## <a name="additional-examples"></a>Exemples supplémentaires

Maintenant que vous comprenez les notions de base, voici une liste d’exemples supplémentaires pour illustrer la flexibilité et la [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] puissance des requêtes. Chaque exemple est précédé d’une brève description de ce qu’il fait. Placez le pointeur de la souris sur la variable de résultat de la requête pour chaque requête pour voir le type inféré. Utilisez une `For Each` boucle pour produire les résultats.

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a>Informations supplémentaires

Une fois que vous êtes familiarisé avec les concepts de base de l’utilisation des requêtes, vous êtes prêt à lire la documentation et les exemples [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pour le type de fournisseur spécifique qui vous intéresse:

- [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)

- [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)

- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a>Voir aussi

- [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Bien démarrer avec LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Initialiseurs d’objets: Types nommés et anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Requêtes](../../../../visual-basic/language-reference/queries/index.md)
