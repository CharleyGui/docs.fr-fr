---
title: REM (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 68c898145bd8845c657b6ebb8776a3a9027c359c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404263"
---
# <a name="rem-statement-visual-basic"></a>REM, instruction (Visual Basic)
Utilisé pour inclure des remarques explicatives dans le code source d’un programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Éléments  
 `comment`  
 Facultatif. Texte de tous les commentaires que vous souhaitez inclure. Un espace est requis entre le `REM` mot clé et `comment` .  
  
## <a name="remarks"></a>Notes  
 Vous pouvez placer une `REM` instruction seule sur une ligne, ou vous pouvez la placer sur une ligne après une autre instruction. L' `REM` instruction doit être la dernière instruction de la ligne. S’il suit une autre instruction, le `REM` doit être séparé de cette instruction par un espace.  
  
 Vous pouvez utiliser un guillemet simple () à la `'` place de `REM` . Cela est vrai si votre commentaire suit une autre instruction sur la même ligne ou s’il se trouve seul sur une ligne.  
  
> [!NOTE]
> Vous ne pouvez pas continuer une `REM` instruction à l’aide d’une séquence de continuation de ligne ( `_` ). Une fois qu’un commentaire commence, le compilateur n’examine pas les caractères pour une signification particulière. Pour un commentaire de plusieurs lignes, utilisez une autre `REM` instruction ou un symbole de commentaire ( `'` ) sur chaque ligne.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l' `REM` instruction, qui est utilisée pour inclure des remarques explicatives dans un programme. Elle illustre également l’utilisation du caractère guillemet simple ( `'` ) au lieu de `REM` .  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Commentaires dans le code](../../programming-guide/program-structure/comments-in-code.md)
- [Procédure : Diviser et combiner des instructions dans le code](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
