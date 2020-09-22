---
title: Stop (instruction)
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
ms.openlocfilehash: c9226ccaea9a0709a9d6a49900f69cb9ac9e1dbe
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871746"
---
# <a name="stop-statement-visual-basic"></a>Stop, instruction (Visual Basic)

Interrompt l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Notes  

 Vous pouvez placer `Stop` des instructions n’importe où dans les procédures pour interrompre l’exécution. L’utilisation de l' `Stop` instruction revient à définir un point d’arrêt dans le code.  
  
 L' `Stop` instruction interrompt l’exécution, mais contrairement `End` à, elle ne ferme pas les fichiers ou n’efface aucune variable, sauf si elle est rencontrée dans un fichier exécutable (. exe) compilé.  
  
> [!NOTE]
> Si l' `Stop` instruction est rencontrée dans le code qui s’exécute en dehors de l’environnement de développement intégré (IDE), le débogueur est appelé. Cela est vrai que le code ait été compilé en mode de débogage ou de vente au détail.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise l' `Stop` instruction pour suspendre l’exécution de chaque itération à travers la `For...Next` boucle.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Voir aussi

- [End, instruction](end-statement.md)
