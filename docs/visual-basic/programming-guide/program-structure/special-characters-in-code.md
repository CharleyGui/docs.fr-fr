---
title: Caractères spéciaux dans le code
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: 60f815f0d30fa785f4a2166db5a041d3851aa954
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097824"
---
# <a name="special-characters-in-code-visual-basic"></a>Caractères spéciaux dans le code (Visual Basic)

Parfois, vous devez utiliser des caractères spéciaux dans votre code, autrement dit, des caractères qui ne sont pas alphabétiques ou numériques. La ponctuation et les caractères spéciaux du jeu de caractères Visual Basic ont plusieurs utilisations, de l’organisation du texte de programme à la définition des tâches exécutées par le compilateur ou le programme compilé. Ils ne spécifient pas d'opération à effectuer.  
  
## <a name="parentheses"></a>Parenthèses  

 Utilisez des parenthèses lorsque vous définissez une procédure, telle que `Sub` ou `Function` . Vous devez placer toutes les listes d’arguments de procédure entre parenthèses. Vous utilisez également des parenthèses pour placer des variables ou des arguments dans des groupes logiques, en particulier pour remplacer l’ordre de priorité par défaut des opérateurs dans une expression complexe. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 Après l’exécution du code précédent, la valeur de `d` est 8,225 et la valeur de `e` est 3. Le calcul pour `d` utilise la priorité par défaut de `/` sur `+` et équivaut à `d = b + (c / a)` . Les parenthèses dans le calcul de `e` remplacent la priorité par défaut.  
  
## <a name="separators"></a>Séparateurs  

 Les séparateurs effectuent ce que leur nom suggère : ils séparent des sections de code. Dans Visual Basic, le caractère de séparation est le signe deux-points ( `:` ). Utilisez des séparateurs lorsque vous souhaitez inclure plusieurs instructions sur une seule ligne plutôt que des lignes distinctes. Cela permet d’économiser de l’espace et d’améliorer la lisibilité de votre code. L’exemple suivant montre trois instructions séparées par des signes deux-points.  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 Pour plus d’informations, consultez [Comment : arrêter et combiner des instructions dans le code](how-to-break-and-combine-statements-in-code.md).  
  
 Le caractère deux-points ( `:` ) est également utilisé pour identifier une étiquette d’instruction. Pour plus d’informations, consultez [Comment : étiqueter des instructions](how-to-label-statements.md).  
  
## <a name="concatenation"></a>Concaténation  

 Utilisez l' `&` opérateur pour la *concaténation*ou la liaison de chaînes. Ne confondez pas l’opérateur avec l' `+` opérateur, qui additionne les valeurs numériques. Si vous utilisez l' `+` opérateur pour concaténer lorsque vous travaillez sur des valeurs numériques, vous pouvez obtenir des résultats incorrects. l’exemple ci-dessous illustre ce cas de figure.  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 Après l’exécution du code précédent, la valeur de `resultA` est 21,01 et la valeur de `resultB` est « 10,0111 ».  
  
## <a name="member-access-operators"></a>Opérateurs d’accès aux membres  

 Pour accéder à un membre d’un type, vous utilisez l’opérateur point ( `.` ) ou point d’exclamation ( `!` ) entre le nom de type et le nom de membre.  
  
### <a name="dot--operator"></a>Point (.) And  

 Utilisez l' `.` opérateur sur une classe, une structure, une interface ou une énumération en tant qu’opérateur d’accès aux membres. Le membre peut être un champ, une propriété, un événement ou une méthode. L'exemple suivant illustre ce comportement.  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>Point d’exclamation ( !) And  

 Utilisez l' `!` opérateur uniquement sur une classe ou une interface comme opérateur d’accès au dictionnaire. La classe ou l’interface doit avoir une propriété par défaut qui accepte un seul `String` argument. L’identificateur qui suit immédiatement l' `!` opérateur devient la valeur d’argument passée à la propriété par défaut sous forme de chaîne. l’exemple ci-dessous illustre ce cas de figure.  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 Les trois lignes de sortie de `MsgBox` tous affichent la valeur `32856` . La première ligne utilise l’accès traditionnel à la propriété `index` , la seconde utilise le fait qu’il `index` s’agit de la propriété par défaut de la classe `hasDefault` , et la troisième utilise l’accès au dictionnaire pour la classe.  
  
 Notez que le deuxième opérande de l' `!` opérateur doit être un identificateur de Visual Basic valide qui n’est pas placé entre guillemets doubles ( `" "` ). En d’autres termes, vous ne pouvez pas utiliser un littéral de chaîne ou une variable de chaîne. La modification suivante apportée à la dernière ligne de l' `MsgBox` appel génère une erreur, car `"X"` est un littéral de chaîne délimité.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> Les références aux collections par défaut doivent être explicites. En particulier, vous ne pouvez pas utiliser l' `!` opérateur sur une variable à liaison tardive.  
  
 Le `!` caractère est également utilisé comme `Single` caractère de type.  
  
## <a name="see-also"></a>Voir aussi

- [Structure de programme et conventions de code](program-structure-and-code-conventions.md)
- [Caractères de type](../language-features/data-types/type-characters.md)
