---
title: '#Region, directive'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 4cf9b103486378d001b588aa285f590980b51bb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343796"
---
# <a name="region-directive"></a>#Region, directive

Réduit et masque des sections de code dans des fichiers Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`identifier_string`|Requis. Chaîne qui joue le rôle du titre d'une région quand elle est réduite. Les régions sont réduites par défaut.|  
|`#End Region`|Met fin au bloc `#Region`.|  
  
## <a name="remarks"></a>Notes  

 Utilisez la directive `#Region` pour spécifier un bloc de code que vous pouvez développer ou réduire dans le mode Plan de l'éditeur de code Visual Studio. Vous pouvez placer ou *imbriquer*des régions dans d’autres régions pour regrouper des régions similaires.  
  
## <a name="example"></a>Exemple  

 Cet exemple utilise la directive `#Region`.  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [#If...Then...#Else, directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Mode Plan](/visualstudio/ide/outlining)
- [Guide pratique : réduire et masquer des sections de code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
