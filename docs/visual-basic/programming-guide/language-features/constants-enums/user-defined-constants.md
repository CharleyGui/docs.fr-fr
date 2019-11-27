---
title: Constantes définies par l'utilisateur
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 194a420b3749ca5c858a65c07b8c164287c1582a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354005"
---
# <a name="user-defined-constants-visual-basic"></a>Constantes définies par l'utilisateur (Visual Basic)
Une constante est un nom explicite qui prend la place d’un nombre ou d’une chaîne qui ne change pas. Les constantes stockent des valeurs qui, comme leur nom l’indique, demeurent constantes tout au long de l’exécution d’une application. Vous pouvez utiliser des constantes définies par les contrôles ou les composants avec lesquels vous travaillez, ou vous pouvez créer les vôtres. Les constantes que vous créez vous-même sont décrites comme étant *définies par l’utilisateur*.  
  
 Vous déclarez une constante avec l’instruction `Const`, en utilisant les mêmes instructions que pour la création d’un nom de variable. Si `Option Strict` est `On`, vous devez déclarer explicitement le type de constante.  
  
## <a name="const-statement-usage"></a>Utilisation de l’instruction Const  
 Une instruction `Const` peut représenter une quantité mathématique ou de date/heure :  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 Il peut également définir des constantes de `String` :  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 L’expression à droite du signe égal (`=`) est souvent un nombre ou une chaîne littérale, mais il peut également s’agir d’une expression qui produit un nombre ou une chaîne (bien que cette expression ne puisse pas contenir d’appels à des fonctions). Vous pouvez même définir des constantes en termes de constantes précédemment définies :  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>Étendue des constantes définies par l’utilisateur  
 La portée d’une instruction `Const` est identique à celle d’une variable déclarée au même emplacement. Vous pouvez spécifier l’étendue de l’une des manières suivantes :  
  
- Pour créer une constante qui existe uniquement dans une procédure, déclarez-la dans cette procédure.  
  
- Pour créer une constante disponible pour toutes les procédures dans une classe, mais pas pour le code situé en dehors de ce module, déclarez-la dans la section déclarations de la classe.  
  
- Pour créer une constante qui est disponible pour tous les membres d’un assembly, mais pas pour les clients externes de l’assembly, déclarez-la à l’aide du mot clé `Friend` dans la section déclarations de la classe.  
  
- Pour créer une constante disponible dans l’ensemble de l’application, déclarez-la à l’aide du mot clé `Public` dans la section déclarations de la classe.  
  
 Pour plus d’informations, consultez [Comment : déclarer une constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Éviter les références circulaires  
 Étant donné que les constantes peuvent être définies en termes d’autres constantes, il est possible de créer par inadvertance un *cycle*, ou référence circulaire, entre deux constantes ou plus. Un cycle se produit lorsque vous avez au moins deux constantes publiques, chacune d’elles étant définie d’après les autres, comme dans l’exemple suivant :  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 Si un cycle se produit, Visual Basic génère une erreur du compilateur.  
  
## <a name="see-also"></a>Voir aussi

- [Const (instruction)](../../../../visual-basic/language-reference/statements/const-statement.md)
- [Constantes et types de données littérales](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Constantes et énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Vue d’ensemble des constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Énumérations et qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
