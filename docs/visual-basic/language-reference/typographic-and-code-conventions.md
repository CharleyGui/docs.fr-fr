---
title: Conventions typographiques et de code
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: 0e36d9d61b0dd2701210ce614d15fd38f08f5401
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401353"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Conventions typographiques (Visual Basic)

Visual Basic documentation utilise les conventions typographiques et de code suivantes.  
  
## <a name="typographic-conventions"></a>Conventions typographiques  
  
|Exemple|Description|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Les mots clés et les membres du runtime spécifiques à une langue ont des lettres majuscules initiales et sont mis en forme comme indiqué dans cet exemple.|  
|**SmallProject**, **ButtonCollection**|Les mots et les expressions que vous êtes invité à taper sont mis en forme comme indiqué dans cet exemple.|  
|[Module, instruction](statements/module-statement.md)|Les liens sur lesquels vous pouvez cliquer pour accéder à une autre page d’aide sont mis en forme comme indiqué dans cet exemple.|  
|*objet*, *NomVariable*,`argumentList`|Les espaces réservés pour les informations que vous fournissez sont mis en forme comme indiqué dans cet exemple.|  
|[Shadows], [ *expressionList* ]|Dans la syntaxe, les éléments facultatifs sont placés entre crochets.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|Dans la syntaxe, lorsque vous devez faire un choix entre deux ou plusieurs éléments, ceux-ci sont placés entre accolades et séparés par des barres verticales.<br /><br /> Vous devez en sélectionner un, et un seul, des éléments.|  
|[ `Protected` &#124; `Friend` ]|Dans la syntaxe, lorsque vous avez la possibilité de sélectionner entre deux ou plusieurs éléments, les éléments sont placés entre crochets et séparés par des barres verticales.<br /><br /> Vous pouvez sélectionner n’importe quelle combinaison d’éléments, ou aucun élément.|  
|[{ `ByVal` &#124; `ByRef` }]|Dans la syntaxe, lorsque vous ne pouvez sélectionner qu’un seul élément, mais que vous pouvez également omettre complètement les éléments, ceux-ci sont placés entre crochets entourés d’accolades et séparés par des barres verticales.|  
|*MemberName*1, *MemberName*2, *MemberName*3|Plusieurs instances du même espace réservé sont différenciées par des indices, comme illustré dans l’exemple.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|Dans la syntaxe, un bouton de sélection (...) est utilisé pour indiquer un nombre indéfini d’éléments du type immédiatement devant les points de suspension.<br /><br /> Dans le code, les ellipses signifient que le code est omis par souci de clarté.|  
|ECHAP, ENTRÉE|Les noms de clés et les séquences de touches du clavier s’affichent en majuscules.|  
|Alt+F1|Quand des signes plus (+) apparaissent entre les noms de clé, vous devez maintenir une touche enfoncée tout en appuyant sur l’autre. Par exemple, ALT + F1 signifie maintenir la touche ALT enfoncée tout en appuyant sur la touche F1.|  
  
## <a name="code-conventions"></a>Conventions de code  
  
|Exemple|Description|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Les exemples de code apparaissent dans une police à espacement fixe et sont mis en forme comme indiqué dans cet exemple.|  
|L’instruction précédente affecte à la valeur `sampleString` « Hello, World ! »|Les éléments de code en texte explicatif apparaissent dans une police à espacement fixe, comme illustré dans cet exemple.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Les commentaires de code sont introduits par une apostrophe (') ou le mot clé REM.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Un espace suivi d’un trait de soulignement (_) à la fin d’une ligne indique que l’instruction continue sur la ligne suivante.|  
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage Visual Basic](index.md)
- [Mots clés](keywords/index.md)
- [Membres de la bibliothèque runtime Visual Basic](runtime-library-members.md)
- [Conventions d'affectation de noms Visual Basic](../programming-guide/program-structure/naming-conventions.md)
- [Procédure : Diviser et combiner des instructions dans le code](../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Commentaires dans le code](../programming-guide/program-structure/comments-in-code.md)
