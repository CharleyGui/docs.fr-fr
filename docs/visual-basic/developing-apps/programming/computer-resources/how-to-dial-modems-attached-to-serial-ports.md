---
title: 'Procédure : passer des appels avec des modems attachés aux ports série'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: e55ce6399dae435fbd5b2f730d4d0848c98d8955
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363265"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Guide pratique pour passer des appels avec des modems attachés aux ports série dans Visual Basic

Cette rubrique explique comment utiliser `My.Computer.Ports` pour passer un appel avec un modem dans Visual Basic.  
  
 En règle générale, le modem est connecté à l’un des ports série sur l’ordinateur. Pour que l’application puisse communiquer avec le modem, elle doit envoyer des commandes au port série approprié.  
  
### <a name="to-dial-a-modem"></a>Pour communiquer avec un modem  
  
1. Déterminez le port série auquel le modem est connecté. Cet exemple part du principe que le modem est connecté à COM1.  
  
2. Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     Le bloc `Using` permet à l’application de fermer le port série, même si cela génère une exception. Tout le code qui manipule le port série doit apparaître dans ce bloc, ou dans un bloc `Try...Catch...Finally`.  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. Définissez la propriété `DtrEnable` pour indiquer que l’ordinateur est prêt à accepter une transmission en provenance du modem.  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. Envoyez la commande de numérotation et le numéro de téléphone au modem par l’intermédiaire du port série à l’aide de la méthode <xref:System.IO.Ports.SerialPort.Write%2A>.  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a>Exemple  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve sous **Connectivité et réseau**. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Compilation du code  

 Cet exemple nécessite une référence à l’espace de noms <xref:System?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programmation fiable  

 Cet exemple part du principe que le modem est connecté à COM1. Nous recommandons que le code autorise l’utilisateur à sélectionner le port série dans la liste des ports disponibles. Pour plus d’informations, consultez [Guide pratique pour afficher les ports série disponibles](how-to-show-available-serial-ports.md).  
  
 Cet exemple utilise un bloc `Using` pour garantir que l’application ferme le port même si elle lève une exception. Pour plus d’informations, consultez [using, instruction](../../../language-reference/statements/using-statement.md).  
  
 Dans cet exemple, l’application déconnecte le port série après avoir utilisé le modem. Dans la pratique, vous souhaiterez transférer des données vers et à partir du modem. Pour plus d’informations, consultez [Guide pratique pour recevoir des chaînes des ports série](how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Procédure : envoyer des chaînes aux ports série](how-to-send-strings-to-serial-ports.md)
- [Procédure : recevoir des chaînes provenant des ports série](how-to-receive-strings-from-serial-ports.md)
- [Procédure : afficher les ports série disponibles](how-to-show-available-serial-ports.md)
