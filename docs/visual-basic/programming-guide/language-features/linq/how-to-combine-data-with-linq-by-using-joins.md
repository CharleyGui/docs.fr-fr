---
title: 'Comment : combiner des données avec LINQ à l’aide de jointures'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: 7279908c5d262b65f4c4da9cd9b6c1b4117bc402
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345001"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Comment : combiner des données avec LINQ à l'aide de jointures (Visual Basic)
Visual Basic fournit les clauses de requête `Join` et `Group Join` pour vous permettre de combiner le contenu de plusieurs collections en fonction de valeurs communes entre les collections. Ces valeurs sont appelées valeurs de *clés* . Les développeurs familiarisés avec les concepts de base de données relationnelle reconnaissent la clause `Join` comme jointure interne et la clause `Group Join` comme, en fait, une jointure externe gauche.  
  
 Les exemples de cette rubrique illustrent les différentes façons de combiner des données à l’aide des clauses de requête `Join` et `Group Join`.  
  
## <a name="create-a-project-and-add-sample-data"></a>Créer un projet et ajouter des exemples de données  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Pour créer un projet qui contient des exemples de données et des types  
  
1. Pour exécuter les exemples de cette rubrique, ouvrez Visual Studio et ajoutez un nouveau Visual Basic projet d’application console. Double-cliquez sur le fichier Module1. vb créé par Visual Basic.  
  
2. Les exemples de cette rubrique utilisent la `Person` et les types de `Pet` et les données de l’exemple de code suivant. Copiez ce code dans le module `Module1` par défaut créé par Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Effectuer une jointure interne à l’aide de la clause join  
 Une jointure interne combine les données de deux collections. Les éléments pour lesquels les valeurs de clé spécifiées correspondent sont inclus. Tous les éléments de l’une des collections qui n’ont pas d’élément correspondant dans l’autre collection sont exclus.  
  
 Dans Visual Basic, LINQ fournit deux options pour effectuer une jointure interne : une jointure implicite et une jointure explicite.  
  
 Une jointure implicite spécifie les collections à joindre dans une clause `From` et identifie les champs de clé correspondants dans une clause `Where`. Visual Basic joint implicitement les deux collections en fonction des champs de clé spécifiés.  
  
 Vous pouvez spécifier une jointure explicite à l’aide de la clause `Join` lorsque vous souhaitez être précis en ce qui concerne les champs clés à utiliser dans la jointure. Dans ce cas, il est toujours possible d’utiliser une clause `Where` pour filtrer les résultats de la requête.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Pour effectuer une jointure interne à l’aide de la clause join  
  
1. Ajoutez le code suivant au module `Module1` de votre projet pour voir des exemples de jointure interne implicite et explicite.  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Effectuer une jointure externe gauche à l’aide de la clause Group Join  
 Une jointure externe gauche comprend tous les éléments de la collection du côté gauche de la jointure et uniquement les valeurs correspondantes de la collection de droite de la jointure. Tous les éléments de la collection située à droite de la jointure qui n’ont pas d’élément correspondant dans la collection de gauche sont exclus du résultat de la requête.  
  
 La clause `Group Join` effectue, en effet, une jointure externe gauche. La différence entre ce qui est généralement appelé jointure externe gauche et ce que la clause `Group Join` retourne est que la clause `Group Join` regroupe les résultats de la collection de droite de la jointure pour chaque élément de la collection de gauche. Dans une base de données relationnelle, une jointure externe gauche retourne un résultat non groupé dans lequel chaque élément du résultat de la requête contient des éléments correspondants des deux collections de la jointure. Dans ce cas, les éléments de la collection du côté gauche de la jointure sont répétés pour chaque élément correspondant de la collection de droite. Vous verrez à quoi cela ressemble quand vous effectuez la procédure suivante.  
  
 Vous pouvez récupérer les résultats d’une requête `Group Join` en tant que résultat non groupé en étendant votre requête pour retourner un élément pour chaque résultat de la requête groupée. Pour ce faire, vous devez vous assurer que vous interrogez la méthode `DefaultIfEmpty` de la collection groupée. Cela permet de s’assurer que les éléments de la collection de la jointure située à gauche sont toujours inclus dans le résultat de la requête, même s’ils n’ont aucun résultat correspondant de la collection de droite. Vous pouvez ajouter du code à votre requête pour fournir une valeur de résultat par défaut lorsqu’il n’existe aucune valeur correspondante de la collection de droite de la jointure.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Pour effectuer une jointure externe gauche à l’aide de la clause Group Join  
  
1. Ajoutez le code suivant au module `Module1` de votre projet pour voir des exemples de jointure externe gauche groupée et d’une jointure externe gauche non groupée.  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Effectuer une jointure à l’aide d’une clé composite  
 Vous pouvez utiliser le mot clé `And` dans une clause `Join` ou `Group Join` pour identifier plusieurs champs clés à utiliser lors de la mise en correspondance des valeurs des collections jointes. Le mot clé `And` spécifie que tous les champs clés spécifiés doivent correspondre pour les éléments à joindre.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Pour effectuer une jointure à l’aide d’une clé composite  
  
1. Ajoutez le code suivant au module `Module1` de votre projet pour voir des exemples de jointure qui utilise une clé composite.  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a>Exécuter le code  
  
#### <a name="to-add-code-to-run-the-examples"></a>Pour ajouter du code pour exécuter les exemples  
  
1. Remplacez le `Sub Main` dans le module `Module1` de votre projet par le code suivant pour exécuter les exemples de cette rubrique.  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. Appuyez sur F5 pour exécuter les exemples.  
  
## <a name="see-also"></a>Voir aussi

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Join (clause)](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Group Join (clause)](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [From (clause)](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Where (clause)](../../../../visual-basic/language-reference/queries/where-clause.md)
- [Requêtes](../../../../visual-basic/language-reference/queries/index.md)
- [Transformations de données avec LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
