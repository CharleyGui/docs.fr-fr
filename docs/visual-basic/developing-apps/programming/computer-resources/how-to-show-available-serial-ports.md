---
title: 'Procédure : afficher les ports série disponibles en Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: d6b092b499af2003e8a43987677b13741c362b1b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662718"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Procédure : afficher les ports série disponibles en Visual Basic
Cette rubrique explique comment utiliser `My.Computer.Ports` pour afficher les ports série disponibles sur l’ordinateur en Visual Basic.  
  
 Pour permettre à un utilisateur de sélectionner le port à utiliser, les noms des ports série sont placés dans un contrôle <xref:System.Windows.Forms.ListBox>.  
  
## <a name="example"></a>Exemple  
 Cet exemple exécute une boucle sur toutes les chaînes retournées par la propriété `My.Computer.Ports.SerialPortNames`. Ces chaînes correspondent aux noms des ports série disponibles sur l’ordinateur.  
  
 En règle générale, un utilisateur sélectionne le port série que l’application doit utiliser dans la liste des ports disponibles. Dans cet exemple, les noms de port série sont stockés dans un contrôle <xref:System.Windows.Forms.ListBox>. Pour plus d’informations, consultez [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve sous **Connectivité et réseau**. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Une référence de projet à System.Windows.Forms.dll  
  
- Un accès aux membres de l’espace de noms <xref:System.Windows.Forms>. Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- Votre formulaire doit avoir un contrôle <xref:System.Windows.Forms.ListBox> nommé `ListBox1`.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Vous n’avez pas besoin d’utiliser le contrôle <xref:System.Windows.Forms.ListBox> pour afficher les noms des ports série disponibles. À la place, vous pouvez utiliser un contrôle <xref:System.Windows.Forms.ComboBox> ou autre. Si l’application n’a pas besoin d’une réponse de l’utilisateur, vous pouvez utiliser un contrôle <xref:System.Windows.Forms.TextBox> pour afficher les informations.  
  
> [!NOTE]
>  Les noms de port retournés par `My.Computer.Ports.SerialPortNames` peuvent ne pas être corrects sur Windows 98. Pour éviter les erreurs d’application, utilisez la gestion des exceptions, comme les instructions `Try...Catch...Finally` et `Using`, lorsque vous utilisez les noms de ports pour ouvrir des ports.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Guide pratique pour passer des appels avec des modems attachés aux ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Guide pratique pour envoyer des chaînes aux ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Guide pratique pour recevoir des chaînes provenant des ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
