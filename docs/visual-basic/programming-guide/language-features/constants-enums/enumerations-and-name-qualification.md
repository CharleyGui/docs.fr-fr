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
ms.openlocfilehash: 4b09284b8282c481e406050d37cbdb2f3c8686bc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414503"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Énumérations et qualification de noms (Visual Basic)
Normalement, lorsque vous faites référence à un membre d’une énumération, vous devez qualifier le nom du membre avec le nom de l’énumération. Par exemple, pour faire référence au `Sunday` membre de votre `Days` énumération, vous devez utiliser la syntaxe suivante :  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Utilisation de l’instruction Imports  
 Vous pouvez éviter d’utiliser des noms qualifiés complets en ajoutant une `Imports` instruction à la section déclarations d’espace de noms de votre code, comme dans l’exemple suivant :  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 Une `Imports` instruction importe des noms d’espaces de noms à partir de projets et d’assemblys référencés et dans le même projet que le module dans lequel l’instruction apparaît. Une fois cette instruction ajoutée, vous pouvez faire référence à vos membres de l’énumération sans qualification, comme dans l’exemple suivant :  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 En organisant des ensembles de constantes associées dans des énumérations, vous pouvez utiliser les mêmes noms de constantes dans des contextes différents. Par exemple, vous pouvez utiliser les mêmes noms pour les constantes de jour de la semaine dans les `Days` `WorkDays` énumérations et. Si vous utilisez l' `Imports` instruction avec vos énumérations, vous devez veiller à éviter les références ambiguës. Prenons l’exemple suivant :  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 En supposant que `Monday` est membre de l' `Days` énumération et de l' `Workdays` énumération, ce code génère une erreur du compilateur. Pour éviter des références ambiguës quand vous faites référence à une constante individuelle, qualifiez le nom de la constante avec son énumération. Le code suivant fait référence aux `Saturday` constantes dans les `Days` `WorkDays` énumérations et.  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>Voir aussi

- [Constantes et énumérations](../../../language-reference/constants-and-enumerations.md)
- [How to: Declare an, énumération](how-to-declare-enumerations.md)
- [Comment : faire référence à un membre d'énumération](how-to-refer-to-an-enumeration-member.md)
- [Comment : itérer au sein d'une énumération dans Visual Basic](how-to-iterate-through-an-enumeration.md)
- [Comment : déterminer la chaîne associée à une valeur d'énumération](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Quand utiliser une énumération](when-to-use-an-enumeration.md)
- [Constantes et types de données littérales](constant-and-literal-data-types.md)
- [Enum (instruction)](../../../language-reference/statements/enum-statement.md)
- [Imports, instruction (espace de noms et type .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Types de données](../../../language-reference/data-types/index.md)
