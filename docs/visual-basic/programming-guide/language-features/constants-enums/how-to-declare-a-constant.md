---
title: 'Comment : déclarer une constante'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 138dd58dac9d1983e35e61f8b98a77810fc6e38b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058844"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>Comment : déclarer une constante (Visual Basic)

Vous utilisez l' `Const` instruction pour déclarer une constante et définir sa valeur. En déclarant une constante, vous assignez un nom explicite à une valeur. Une fois qu’une constante est déclarée, elle ne peut pas être modifiée ou assignée à une nouvelle valeur.  
  
 Vous déclarez une constante dans une procédure ou dans la section déclarations d’un module, d’une classe ou d’une structure. Les constantes au niveau de la classe ou de la structure sont `Private` par défaut, mais elles peuvent également être déclarées comme `Public` , `Friend` , `Protected` ou `Protected Friend` pour le niveau approprié d’accès au code.  
  
 La constante doit avoir un nom symbolique valide (les règles sont les mêmes que celles pour la création de noms de variables) et une expression composée de constantes et d’opérateurs numériques ou de chaîne (mais sans appel de fonction).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>Pour déclarer une constante  
  
- Écrivez une déclaration qui comprend un spécificateur d’accès, le `Const` mot clé et une expression, comme dans les exemples suivants :  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     Quand [Option Infer](../../../language-reference/statements/option-infer-statement.md) est `Off` et [option strict](../../../language-reference/statements/option-strict-statement.md) est `On` , vous devez déclarer explicitement une constante en spécifiant un type de données ( `Boolean` , `Byte` , `Char` , `DateTime` , `Decimal` , `Double` , `Integer` ,, `Long` `Short` , `Single` ou `String` ).  
  
     Lorsque `Option Infer` est `On` ou `Option Strict` a `Off` la clause, vous pouvez déclarer une constante sans spécifier de type de données avec une `As` clause. Le compilateur détermine le type de la constante à partir du type de l’expression. Pour plus d’informations, consultez [types de données constantes et littérales](constant-and-literal-data-types.md).  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>Pour déclarer une constante qui a un type de données défini explicitement  
  
- Écrivez une déclaration qui comprend le `As` mot clé et un type de données explicite, comme dans les exemples suivants :  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     Vous pouvez déclarer plusieurs constantes sur une seule ligne, même si votre code est plus lisible si vous déclarez une seule constante par ligne. Si vous déclarez plusieurs constantes sur une seule ligne, elles doivent toutes avoir le même niveau d’accès ( `Public` , `Private` ,, `Friend` `Protected` ou `Protected Friend` ).  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>Pour déclarer plusieurs constantes sur une seule ligne  
  
- Séparez les déclarations par une virgule et un espace, comme dans l’exemple suivant :  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Const (instruction)](../../../language-reference/statements/const-statement.md)
- [Constantes et types de données littérales](constant-and-literal-data-types.md)
- [Vue d'ensemble des constantes](constants-overview.md)
- [Comment : déclarer une constante](how-to-declare-a-constant.md)
- [Constantes définies par l'utilisateur](user-defined-constants.md)
- [Constantes et types de données littérales](constant-and-literal-data-types.md)
- [Comment : regrouper les valeurs de constante connexes](how-to-group-related-constant-values-together.md)
- [Vue d'ensemble des énumérations](enumerations-overview.md)
- [Guide pratique : déclarer des énumérations](how-to-declare-enumerations.md)
- [Comment : faire référence à un membre d'énumération](how-to-refer-to-an-enumeration-member.md)
- [Énumérations et qualification de noms](enumerations-and-name-qualification.md)
- [Guide pratique : itérer au sein d’une énumération](how-to-iterate-through-an-enumeration.md)
- [Comment : déterminer la chaîne associée à une valeur d'énumération](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Quand utiliser une énumération](when-to-use-an-enumeration.md)

- [Vue d'ensemble des énumérations](enumerations-overview.md)
- [Vue d'ensemble des constantes](constants-overview.md)
- [How to: Declare an, énumération](how-to-declare-enumerations.md)
- [Énumérations et qualification de noms](enumerations-and-name-qualification.md)
- [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)
- [Constantes et énumérations](../../../language-reference/constants-and-enumerations.md)
