---
title: 'Comment : supprimer une ressource système'
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
ms.openlocfilehash: c430bc7744f5aefaa65f2a86f3e5e22743ffed57
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077200"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Comment : supprimer une ressource système (Visual Basic)

Vous pouvez utiliser un `Using` bloc pour garantir que le système supprime une ressource quand votre code quitte le bloc. Cela est utile si vous utilisez une ressource système qui consomme une grande quantité de mémoire ou que d’autres composants souhaitent également utiliser.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Pour supprimer une connexion de base de données lorsque votre code en a terminé  
  
1. Veillez à inclure l' [instruction Imports appropriée (espace de noms et type .net)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) pour la connexion de base de données au début de votre fichier source (dans ce cas, <xref:System.Data.SqlClient> ).  
  
2. Créez un `Using` bloc avec les `Using` `End Using` instructions et. Dans le bloc, placez le code qui gère la connexion à la base de données.  
  
3. Déclarez la connexion et créez une instance de celle-ci dans le cadre de l' `Using` instruction.  
  
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
  
     Notez que vous ne pouvez pas accéder `sqc` depuis l’extérieur du `Using` bloc, car sa portée est limitée au bloc.  
  
     Vous pouvez utiliser cette même technique sur une ressource système telle qu’un handle de fichier ou un wrapper COM. Vous utilisez un `Using` bloc lorsque vous souhaitez être sûr de conserver la ressource disponible pour d’autres composants une fois que vous avez quitté le `Using` bloc.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.SqlClient.SqlConnection>
- [Flux de contrôle](index.md)
- [Structures de décision](decision-structures.md)
- [Structures de boucle](loop-structures.md)
- [Autres structures de contrôle](other-control-structures.md)
- [Structures de contrôle imbriquées](nested-control-structures.md)
- [Instruction using](../../../language-reference/statements/using-statement.md)
