---
title: 'Procédure : Utiliser une classe générique (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: b069d3a0249f6aff2f9f09c5a560e5708bd60aa6
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593360"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Procédure : Utiliser une classe générique (Visual Basic)
Une classe qui accepte des *paramètres de type* est appelée *classe générique*. Si vous utilisez une classe générique, vous pouvez générer une *classe construite* à partir de celle-ci en fournissant un *argument de type* pour chacun de ces paramètres. Vous pouvez ensuite déclarer une variable du type classe construite, et vous pouvez créer une instance de la classe construite et l’assigner à cette variable.  
  
 En plus des classes, vous pouvez définir et utiliser des structures, interfaces, procédures et délégués génériques.  
  
 La procédure suivante prend une classe générique définie dans le .NET Framework et crée une instance à partir de celui-ci.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Pour utiliser une classe qui prend un paramètre de type  
  
1. Au début de votre fichier source, incluez une [instruction Imports (.NET Namespace et Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour importer le <xref:System.Collections.Generic?displayProperty=nameWithType> espace de noms. Cela vous permet de faire référence à la classe <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> sans avoir à la qualifier pleinement pour la différencier des autres classes de file d’attente, telles que <xref:System.Collections.Queue?displayProperty=nameWithType>.  
  
2. Créez l’objet de façon normale, mais ajoutez `(Of type)` immédiatement après le nom de classe.  
  
     L’exemple suivant utilise la même classe (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) pour créer deux objets de file d’attente qui contiennent des éléments de différents types de données. Il ajoute des éléments à la fin de chaque file d’attente, puis supprime et affiche les éléments du début de chaque file d’attente.  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Voir aussi

- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Indépendance du langage et composants indépendants du langage](../../../../standard/language-independence-and-language-independent-components.md)
- [Of](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Imports (instruction) (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Guide pratique pour définir une classe qui fournisse des fonctionnalités identiques pour différents types de données](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Itérateurs](../../../../visual-basic/programming-guide/concepts/iterators.md)
