---
title: Conversion simplifiée des délégués
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: ffb242842553382ba26121333c38fc65eaa168a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345215"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Conversion simplifiée des délégués (Visual Basic)
La conversion souple des délégués vous permet d’assigner des fonctions et des fonctions aux délégués ou aux gestionnaires même lorsque leurs signatures ne sont pas identiques. Par conséquent, la liaison aux délégués devient cohérente avec la liaison déjà autorisée pour les appels de méthode.  
  
## <a name="parameters-and-return-type"></a>Paramètres et type de retour  
 Au lieu de la correspondance exacte de signature, la conversion souple exige que les conditions suivantes soient remplies lorsque `Option Strict` a la valeur `On`:  
  
- Une conversion étendue doit exister à partir du type de données de chaque paramètre délégué vers le type de données du paramètre correspondant de la fonction ou de la `Sub`assignée. Dans l’exemple suivant, le délégué `Del1` possède un paramètre, un `Integer`. Le `m` de paramètres dans les expressions lambda affectées doit avoir un type de données pour lequel il existe une conversion étendue à partir de `Integer`, comme `Long` ou `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     Les conversions restrictives sont autorisées uniquement lorsque `Option Strict` est défini sur `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- Une conversion étendue doit exister dans la direction opposée du type de retour de la fonction assignée ou `Sub` au type de retour du délégué. Dans les exemples suivants, le corps de chaque expression lambda assignée doit correspondre à un type de données qui s’étend à `Integer` parce que le type de retour de `del1` est `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 Si `Option Strict` est défini sur `Off`, la restriction étendue est supprimée dans les deux directions.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>Omission de spécifications de paramètres  
 Les délégués souples vous permettent également d’omettre complètement les spécifications de paramètres dans la méthode assignée :  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 Notez que vous ne pouvez pas spécifier certains paramètres et omettre d’autres paramètres.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 La possibilité d’omettre des paramètres est utile dans une situation telle que la définition d’un gestionnaire d’événements, où plusieurs paramètres complexes sont impliqués. Les arguments de certains gestionnaires d’événements ne sont pas utilisés. Au lieu de cela, le gestionnaire accède directement à l’état du contrôle sur lequel l’événement est inscrit et ignore les arguments. Les délégués souples vous permettent d’omettre les arguments dans ces déclarations quand aucune ambiguïté ne résulte. Dans l’exemple suivant, la méthode entièrement spécifiée `OnClick` peut être réécrite comme `RelaxedOnClick`.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>Exemples AddressOf  
 Les expressions lambda sont utilisées dans les exemples précédents pour faciliter la consultation des relations de type. Toutefois, les mêmes assouplissements sont autorisées pour les affectations de délégués qui utilisent `AddressOf`, `Handles`ou `AddHandler`.  
  
 Dans l’exemple suivant, les fonctions `f1`, `f2`, `f3`et `f4` peuvent toutes être affectées à `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 L’exemple suivant est valide uniquement lorsque `Option Strict` a la valeur `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>Suppression des retours de fonction  
 La conversion souple des délégués vous permet d’assigner une fonction à un délégué `Sub`, en ignorant la valeur de retour de la fonction. Toutefois, vous ne pouvez pas assigner un `Sub` à un délégué de fonction. Dans l’exemple suivant, l’adresse de la fonction `doubler` est assignée à `Sub` `Del3`délégué.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>Voir aussi

- [Expressions lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Guide pratique : passer des procédures à une autre procédure en Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
