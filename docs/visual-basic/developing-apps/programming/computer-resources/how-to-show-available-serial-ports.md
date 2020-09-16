---
title: 'Procédure : afficher les ports série disponibles'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: b19bdd56311ab7029fb224256d138a0dc0dd8ddc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557344"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Guide pratique pour afficher les ports série disponibles en Visual Basic

Cette rubrique explique comment utiliser `My.Computer.Ports` pour afficher les ports série disponibles sur l’ordinateur en Visual Basic.  
  
 Pour permettre à un utilisateur de sélectionner le port à utiliser, les noms des ports série sont placés dans un contrôle <xref:System.Windows.Forms.ListBox>.  
  
## <a name="example"></a> Exemple  

 Cet exemple exécute une boucle sur toutes les chaînes retournées par la propriété `My.Computer.Ports.SerialPortNames`. Ces chaînes correspondent aux noms des ports série disponibles sur l’ordinateur.  
  
 En règle générale, un utilisateur sélectionne le port série que l’application doit utiliser dans la liste des ports disponibles. Dans cet exemple, les noms de port série sont stockés dans un contrôle <xref:System.Windows.Forms.ListBox>. Pour plus d’informations, consultez [ListBox Control](/dotnet/desktop/winforms/controls/listbox-control-windows-forms).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve sous **Connectivité et réseau**. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Compilation du code  

 Cet exemple nécessite :  
  
- Une référence de projet à System.Windows.Forms.dll  
  
- Un accès aux membres de l’espace de noms <xref:System.Windows.Forms>. Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- Votre formulaire doit avoir un contrôle <xref:System.Windows.Forms.ListBox> nommé `ListBox1`.  
  
## <a name="robust-programming"></a>Programmation fiable  

 Vous n’avez pas besoin d’utiliser le contrôle <xref:System.Windows.Forms.ListBox> pour afficher les noms des ports série disponibles. À la place, vous pouvez utiliser un contrôle <xref:System.Windows.Forms.ComboBox> ou autre. Si l’application n’a pas besoin d’une réponse de l’utilisateur, vous pouvez utiliser un contrôle <xref:System.Windows.Forms.TextBox> pour afficher les informations.  
  
> [!NOTE]
> Les noms de port retournés par `My.Computer.Ports.SerialPortNames` peuvent ne pas être corrects sur Windows 98. Pour éviter les erreurs d’application, utilisez la gestion des exceptions, comme les instructions `Try...Catch...Finally` et `Using`, lorsque vous utilisez les noms de ports pour ouvrir des ports.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Procédure : passer des appels avec des modems attachés aux ports série](how-to-dial-modems-attached-to-serial-ports.md)
- [Procédure : envoyer des chaînes aux ports série](how-to-send-strings-to-serial-ports.md)
- [Procédure : recevoir des chaînes provenant des ports série](how-to-receive-strings-from-serial-ports.md)
