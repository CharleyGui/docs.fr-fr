---
title: 'Comment : supprimer une ressource système (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: c780ee1a174ad044593960bc30a3ee2e1f929390
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583141"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Comment : supprimer une ressource système (Visual Basic)
Vous pouvez utiliser un bloc `Using` pour garantir que le système supprime une ressource quand votre code quitte le bloc. Cela est utile si vous utilisez une ressource système qui consomme une grande quantité de mémoire ou que d’autres composants souhaitent également utiliser.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Pour supprimer une connexion de base de données lorsque votre code en a terminé  
  
1. Veillez à inclure l' [instruction Imports appropriée (espace de noms et type .net)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour la connexion de base de données au début de votre fichier source (dans ce cas, <xref:System.Data.SqlClient>).  
  
2. Créez un bloc `Using` avec les instructions `Using` et `End Using`. Dans le bloc, placez le code qui gère la connexion à la base de données.  
  
3. Déclarez la connexion et créez une instance de celle-ci dans le cadre de l’instruction `Using`.  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     Le système supprime la ressource, quelle que soit la façon dont vous quittez le bloc, y compris le cas d’une exception non gérée.  
  
     Notez que vous ne pouvez pas accéder à `sqc` à partir de l’extérieur du bloc `Using`, car sa portée est limitée au bloc.  
  
     Vous pouvez utiliser cette même technique sur une ressource système telle qu’un handle de fichier ou un wrapper COM. Vous utilisez un bloc `Using` lorsque vous souhaitez être sûr de conserver la ressource disponible pour d’autres composants après avoir quitté le bloc `Using`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.SqlClient.SqlConnection>
- [Flux de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Structures de décision](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Autres structures de contrôle](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Structures de contrôle imbriquées](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using (instruction)](../../../../visual-basic/language-reference/statements/using-statement.md)
