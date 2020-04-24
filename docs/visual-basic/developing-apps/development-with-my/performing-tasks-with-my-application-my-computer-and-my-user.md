---
title: Exécution de tâches avec My.Application, My.Computer et My.User
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], developing applications
- rapid application development (RAD), My.Application
- rapid application development (RAD), My.Computer
- rapid application development (RAD), My.User
- My.Computer object [Visual Basic], developing applications
- My.User object [Visual Basic], developing applications
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
ms.openlocfilehash: fc9fd9093a3db4785bfc94719dbae9ec1d586050
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329576"
---
# <a name="performing-tasks-with-myapplication-mycomputer-and-myuser-visual-basic"></a>Exécution de tâches avec My.Application, My.Computer et My.User (Visual Basic)

Les trois objets `My` centraux qui fournissent l’accès aux informations et aux fonctionnalités `My.Application` couramment<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>utilisées sont `My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>), ( `My.User` )<xref:Microsoft.VisualBasic.ApplicationServices.User>et (). Vous pouvez utiliser ces objets pour accéder aux informations relatives à l’application actuelle, à l’ordinateur sur lequel l’application est installée, ou à l’utilisateur actuel de l’application, respectivement.  
  
## <a name="myapplication-mycomputer-and-myuser"></a>My. application, My. Computer et My. User  

 Les exemples suivants montrent comment les informations peuvent être récupérées à l’aide `My`de.  
  
 [!code-vb[VbVbcnMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbcnMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#2)]  
  
 En plus de récupérer des informations, les membres exposés par le biais de ces trois objets vous permettent également d’exécuter des méthodes associées à cet objet. Par exemple, vous pouvez accéder à diverses méthodes pour manipuler des fichiers ou mettre à jour le `My.Computer`Registre à l’aide de.  
  
 L’e/s de fichier est beaucoup plus facile `My`et plus rapide avec, qui comprend une variété de méthodes et de propriétés permettant de manipuler des fichiers, des répertoires et des lecteurs. L' <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> objet vous permet de lire à partir de fichiers structurés volumineux qui ont des champs délimités ou à largeur fixe. Cet exemple ouvre et `TextFieldParser` `reader` l’utilise pour lire à partir `C:\TestFolder1\test1.txt`de.  
  
 [!code-vb[VbVbalrTextFieldParser#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#23)]  
  
 `My.Application`vous permet de modifier la culture de votre application. L’exemple suivant montre comment cette méthode peut être appelée.  
  
 [!code-vb[VbVbcnMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Comment My dépend du type de projet](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
