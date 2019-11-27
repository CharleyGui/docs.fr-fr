---
title: Énumérations et qualification de noms
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 4121266447b771ba954ad52a46e0d8b88de3f9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347496"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Énumérations et qualification de noms (Visual Basic)
Normalement, lorsque vous faites référence à un membre d’une énumération, vous devez qualifier le nom du membre avec le nom de l’énumération. Par exemple, pour faire référence au membre `Sunday` de votre énumération `Days`, utilisez la syntaxe suivante :  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Utilisation de l’instruction Imports  
 Vous pouvez éviter d’utiliser des noms qualifiés complets en ajoutant une instruction `Imports` à la section déclarations d’espace de noms de votre code, comme dans l’exemple suivant :  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 Une instruction `Imports` importe des noms d’espaces de noms à partir de projets et d’assemblys référencés, et de dans le même projet que le module dans lequel l’instruction apparaît. Une fois cette instruction ajoutée, vous pouvez faire référence à vos membres de l’énumération sans qualification, comme dans l’exemple suivant :  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 En organisant des ensembles de constantes associées dans des énumérations, vous pouvez utiliser les mêmes noms de constantes dans des contextes différents. Par exemple, vous pouvez utiliser les mêmes noms pour les constantes de jour de la semaine dans les énumérations `Days` et `WorkDays`. Si vous utilisez l’instruction `Imports` avec vos énumérations, vous devez veiller à éviter les références ambiguës. Prenons l'exemple suivant :  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 En supposant que `Monday` est membre de l’énumération `Days` et de l’énumération `Workdays`, ce code génère une erreur du compilateur. Pour éviter des références ambiguës quand vous faites référence à une constante individuelle, qualifiez le nom de la constante avec son énumération. Le code suivant fait référence aux constantes `Saturday` dans les énumérations `Days` et `WorkDays`.  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>Voir aussi

- [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Guide pratique : faire référence à un membre d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Comment : itérer au sein d’une énumération dans Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Guide pratique : déterminer la chaîne associée à une valeur d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Quand utiliser une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Constantes et types de données littérales](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Enum (instruction)](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Imports (instruction) (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Types de données](../../../../visual-basic/language-reference/data-types/index.md)
