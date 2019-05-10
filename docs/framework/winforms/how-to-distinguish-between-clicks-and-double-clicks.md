---
title: 'Procédure : faire la distinction entre les clics et les double-clics'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
ms.openlocfilehash: 210adda7e5444c3e91d869427062ff12ae41f033
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591549"
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a>Procédure : faire la distinction entre les clics et les double-clics
En règle générale, un *clic* unique lance une action d’interface utilisateur et un *double-clic* étend l’action. Par exemple, un clic sélectionne habituellement un élément et un double-clic modifie l'élément sélectionné. Toutefois, les événements de clic Windows Forms ne gèrent pas facilement les scénarios dans lesquels un clic et un double-clic effectuent des actions incompatibles, car une action liée à l'événement <xref:System.Windows.Forms.Control.Click> ou <xref:System.Windows.Forms.Control.MouseClick> est effectuée avant l'action liée à l'événement <xref:System.Windows.Forms.Control.DoubleClick> ou <xref:System.Windows.Forms.Control.MouseDoubleClick>. Cette rubrique illustre deux solutions à ce problème. Une solution consiste à gérer l'événement de double-clic et à annuler les actions dans la gestion de l'événement de clic. Dans de rares cas, vous devrez peut-être simuler le comportement de clic et de double-clic en gérant l'événement <xref:System.Windows.Forms.Control.MouseDown> et en utilisant les propriétés <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> et <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> de la classe <xref:System.Windows.Forms.SystemInformation>. Vous mesurez le délai entre les clics et si un deuxième clic se produit avant que la valeur de <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> soit atteinte et que le clic se trouve dans un rectangle défini par <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, vous exécutez l'action de double-clic ; sinon, vous exécutez l'action de clic.  
  
### <a name="to-roll-back-a-click-action"></a>Pour annuler une action de clic  
  
- Assurez-vous que le contrôle que vous utilisez a un comportement de double-clic standard. Si ce n'est pas le cas, activez le contrôle avec la méthode <xref:System.Windows.Forms.Control.SetStyle%2A>. Gérez l'événement de double-clic et annulez les actions de clic et de double-clic. L'exemple de code suivant montre comment créer un bouton personnalisé avec double-clic activé et comment annuler l'action de clic dans le code de gestion de l'événement de double-clic.  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a>Pour faire la distinction entre les clics dans l'événement MouseDown  
  
- Gérez l'événement <xref:System.Windows.Forms.Control.MouseDown> et déterminez l'emplacement et l'intervalle entre les clics à l'aide des propriétés <xref:System.Windows.Forms.SystemInformation> appropriées et d'un composant <xref:System.Windows.Forms.Timer>. Exécutez l'action appropriée selon qu'un clic ou un double-clic se produit. L'exemple de code suivant montre comment procéder.  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Ces exemples nécessitent :  
  
- Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d’informations sur la création de ces exemples à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer ces exemples dans Visual Studio en collant le code dans de nouveaux projets.  
  
## <a name="see-also"></a>Voir aussi

- [Entrée de la souris dans une application Windows Forms](mouse-input-in-a-windows-forms-application.md)
