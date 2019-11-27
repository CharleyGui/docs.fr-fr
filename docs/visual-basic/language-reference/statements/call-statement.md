---
title: Call, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 7de194ea23827e08c49f4519c1000708a4bd91b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350160"
---
# <a name="call-statement-visual-basic"></a>Call, instruction (Visual Basic)

Transfère le contrôle à une procédure de bibliothèque de liens dynamiques (DLL) `Function`, `Sub`ou.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Composants  

|||
|---|---|
|`procedureName`|Requis. Nom de la procédure à appeler.|
|`argumentList`|Ce paramètre est facultatif. Liste de variables ou d’expressions représentant les arguments passés à la procédure quand elle est appelée. Les arguments multiples sont séparés par des virgules. Si vous incluez `argumentList`, vous devez le placer entre parenthèses.|
|||
  
## <a name="remarks"></a>Notes

 Vous pouvez utiliser le mot clé `Call` lorsque vous appelez une procédure. Pour la plupart des appels de procédure, vous n’êtes pas obligé d’utiliser ce mot clé.

 En général, vous utilisez le mot clé `Call` lorsque l’expression appelée ne commence pas par un identificateur. L’utilisation du mot clé `Call` pour d’autres utilisations n’est pas recommandée.

 Si la procédure retourne une valeur, l’instruction `Call` l’ignore.

## <a name="example"></a>Exemple

 Le code suivant montre deux exemples où le mot clé `Call` est nécessaire pour appeler une procédure. Dans les deux exemples, l’expression appelée ne commence pas par un identificateur.

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>Voir aussi

- [Function (instruction)](function-statement.md)
- [Sub (instruction)](sub-statement.md)
- [Declare Statement](declare-statement.md)
- [Expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
