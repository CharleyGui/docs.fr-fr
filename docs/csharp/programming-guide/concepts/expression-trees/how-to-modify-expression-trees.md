---
title: Comment modifier les arborescences d’expressions (C#)
description: Découvrez comment modifier une arborescence d’expressions en créant une copie d’une arborescence d’expressions existante et en effectuant les modifications requises.
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 01176f489794a0f4ca29d229d29507fdba0fd5a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167689"
---
# <a name="how-to-modify-expression-trees-c"></a>Comment modifier les arborescences d’expressions (C#)

Cette rubrique montre comment modifier une arborescence d’expressions. Les arborescences d’expressions sont immuables, ce qui signifie qu’elles ne peuvent pas être modifiées directement. Pour changer une arborescence d’expressions, vous devez créer une copie d’une arborescence d’expressions existante et, quand vous créez la copie, apporter les modifications nécessaires. Vous pouvez utiliser la classe <xref:System.Linq.Expressions.ExpressionVisitor> pour parcourir une arborescence d’expressions existante et copier chaque nœud visité.  
  
### <a name="to-modify-an-expression-tree"></a>Pour modifier une arborescence d’expressions  
  
1. Créez un projet d' **application console** .  
  
2. Ajoutez une directive `using` au fichier pour l’espace de noms `System.Linq.Expressions`.  
  
3. Ajoutez la classe `AndAlsoModifier` à votre projet.  
  
    ```csharp  
    public class AndAlsoModifier : ExpressionVisitor  
    {  
        public Expression Modify(Expression expression)  
        {  
            return Visit(expression);  
        }  
  
        protected override Expression VisitBinary(BinaryExpression b)  
        {  
            if (b.NodeType == ExpressionType.AndAlso)  
            {  
                Expression left = this.Visit(b.Left);  
                Expression right = this.Visit(b.Right);  
  
                // Make this binary expression an OrElse operation instead of an AndAlso operation.  
                return Expression.MakeBinary(ExpressionType.OrElse, left, right, b.IsLiftedToNull, b.Method);  
            }  
  
            return base.VisitBinary(b);  
        }  
    }  
    ```  
  
     Cette classe hérite de la classe `AND` et est spécialisée pour modifier les expressions qui représentent des opérations <xref:System.Linq.Expressions.ExpressionVisitor> conditionnelles. Elle convertit ces opérations d’un `AND` conditionnel en un `OR` conditionnel. Pour ce faire, la classe substitue la méthode <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> du type de base, car les expressions `AND` conditionnelles sont représentées sous forme d’expressions binaires. Dans la méthode `VisitBinary`, si l’expression passée représente une opération `AND` conditionnelle, le code construit une nouvelle expression qui contient l’opérateur `OR` conditionnel au lieu de l’opérateur `AND` conditionnel. Si l’expression passée à `VisitBinary` ne représente pas une opération `AND` conditionnelle, la méthode emploie l’implémentation de classe de base. Les méthodes de classe de base construisent des nœuds qui sont comme les arborescences d’expressions passées, mais les nœuds voient leurs sous-arborescences remplacées par les arborescences d’expressions produites de manière récursive par le visiteur.  
  
4. Ajoutez une directive `using` au fichier pour l’espace de noms `System.Linq.Expressions`.  
  
5. Ajoutez le code à la méthode `Main` dans le fichier Program.cs pour créer une arborescence d’expressions, et passez-le à la méthode qui le modifiera.  
  
    ```csharp  
    Expression<Func<string, bool>> expr = name => name.Length > 10 && name.StartsWith("G");  
    Console.WriteLine(expr);  
  
    AndAlsoModifier treeModifier = new AndAlsoModifier();  
    Expression modifiedExpr = treeModifier.Modify((Expression) expr);  
  
    Console.WriteLine(modifiedExpr);  
  
    /*  This code produces the following output:  
  
        name => ((name.Length > 10) && name.StartsWith("G"))  
        name => ((name.Length > 10) || name.StartsWith("G"))  
    */  
    ```  
  
     Le code crée une expression qui contient une opération `AND` conditionnelle. Il crée ensuite une instance de la classe `AndAlsoModifier` et passe l’expression à la méthode `Modify` de cette classe. Les arborescences d’expressions d’origine et modifiée sont toutes deux générées pour montrer la modification.  
  
6. Compilez et exécutez l'application.  
  
## <a name="see-also"></a>Voir aussi

- [Comment exécuter des arborescences d’expressions (C#)](./how-to-execute-expression-trees.md)
- [Arborescences d’expressions (C#)](./index.md)
