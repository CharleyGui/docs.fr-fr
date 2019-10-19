---
title: Instruction end (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 66dba1df125a08b8ae05519a0c66edb6da15ceaa
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583413"
---
# <a name="end-statement"></a>End, instruction
Termine immédiatement l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
End  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez placer l’instruction `End` n’importe où dans une procédure pour forcer l’arrêt de l’exécution de l’application entière. `End` ferme tous les fichiers ouverts avec une instruction `Open` et efface toutes les variables de l’application. L’application se ferme dès qu’aucun autre programme ne contient des références à ses objets et qu’aucun de son code n’est en cours d’exécution.  
  
> [!NOTE]
> L’instruction `End` arrête brusquement l’exécution du code et n’appelle pas la méthode `Dispose` ou `Finalize`, ni aucun autre code Visual Basic. Les références d’objets détenues par d’autres programmes sont invalidées. Si une instruction `End` est rencontrée dans un bloc `Try` ou `Catch`, le contrôle ne passe pas au bloc `Finally` correspondant.  
  
 L’instruction `Stop` interrompt l’exécution, mais contrairement à `End`, elle ne ferme pas les fichiers ou n’efface aucune variable, sauf si elle est rencontrée dans un fichier exécutable (. exe) compilé.  
  
 Étant donné que `End` met fin à votre application sans vous préoccuper des ressources qui peuvent être ouvertes, vous devez essayer de la fermer correctement avant de l’utiliser. Par exemple, si votre application a des formulaires ouverts, vous devez les fermer avant que le contrôle n’atteigne l’instruction `End`.  
  
 Vous devez utiliser `End` avec modération et uniquement lorsque vous devez arrêter immédiatement. Les méthodes normales pour mettre fin à une procédure ([instruction de retour](../../../visual-basic/language-reference/statements/return-statement.md) et [instruction de sortie](../../../visual-basic/language-reference/statements/exit-statement.md)) ferment uniquement la procédure proprement dit, mais elles permettent également au code appelant de fermer correctement. Une application console, par exemple, peut simplement `Return` à partir de la procédure `Main`.  
  
> [!IMPORTANT]
> L’instruction `End` appelle la méthode <xref:System.Environment.Exit%2A> de la classe <xref:System.Environment> dans l’espace de noms <xref:System>. <xref:System.Environment.Exit%2A> nécessite que vous disposiez d' `UnmanagedCode` autorisation. Si vous ne le faites pas, une erreur <xref:System.Security.SecurityException> se produit.  
  
 Lorsqu’il est suivi d’un mot clé supplémentaire, [end \<keyword instruction >](../../../visual-basic/language-reference/statements/end-keyword-statement.md) définit la fin de la définition de la procédure ou du bloc approprié. Par exemple, `End Function` termine la définition d’une procédure `Function`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’instruction `End` pour mettre fin à l’exécution du code si l’utilisateur le demande.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Notes de développement Smart Device  
 Cette instruction n’est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop (instruction)](../../../visual-basic/language-reference/statements/stop-statement.md)
- [End \<keyword instruction >](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
