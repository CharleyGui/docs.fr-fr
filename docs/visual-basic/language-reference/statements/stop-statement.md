---
title: Stop, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: e9382ee34842fc3a3b4b23f71848bda602c99780
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583224"
---
# <a name="stop-statement-visual-basic"></a>Stop, instruction (Visual Basic)
Interrompt l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez placer `Stop` instructions n’importe où dans les procédures pour interrompre l’exécution. L’utilisation de l’instruction `Stop` est semblable à la définition d’un point d’arrêt dans le code.  
  
 L’instruction `Stop` interrompt l’exécution, mais contrairement à `End`, elle ne ferme pas les fichiers ou n’efface aucune variable, sauf si elle est rencontrée dans un fichier exécutable (. exe) compilé.  
  
> [!NOTE]
> Si l’instruction `Stop` est rencontrée dans le code qui s’exécute en dehors de l’environnement de développement intégré (IDE), le débogueur est appelé. Cela est vrai que le code ait été compilé en mode de débogage ou de vente au détail.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’instruction `Stop` pour interrompre l’exécution de chaque itération via la boucle `For...Next`.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Voir aussi

- [End (instruction)](../../../visual-basic/language-reference/statements/end-statement.md)
