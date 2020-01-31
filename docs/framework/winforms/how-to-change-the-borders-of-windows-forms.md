---
title: Modifier les bordures de formulaire
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
ms.openlocfilehash: 2c8eb25b44c7406e4312f432f2d69524346f94d6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739566"
---
# <a name="how-to-change-the-borders-of-windows-forms"></a>Comment : modifier les bordures des Windows Forms
Vous pouvez choisir parmi plusieurs styles de bordure quand vous déterminez l'apparence et le comportement de vos Windows Forms. En modifiant la propriété <xref:System.Windows.Forms.Form.FormBorderStyle%2A>, vous pouvez contrôler le comportement de redimensionnement du formulaire. De plus, la définition de <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affecte l'affichage de la barre de légende et de ses boutons. Pour plus d'informations, consultez <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Cette tâche est très bien prise en charge dans Visual Studio.  
  
 Voir aussi [Comment : modifier les bordures d’Windows Forms à l’aide du concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yettzh3e(v=vs.100)).  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a>Pour définir le style de bordure des Windows Forms par programmation  
  
- Affectez à la propriété <xref:System.Windows.Forms.Form.FormBorderStyle%2A> le style souhaité. L’exemple de code suivant définit le style de bordure des `DlgBx1` de formulaire sur <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     Consultez également [Comment : créer des boîtes de dialogue au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/55cz5x2c(v=vs.100)).  
  
     En outre, si vous avez choisi un style de bordure pour le formulaire qui fournit des boutons de **réduction** et d' **agrandissement** facultatifs, vous pouvez spécifier si vous souhaitez que l’un ou l’autre ou les deux boutons soient fonctionnels. Ils sont utiles quand vous souhaitez contrôler étroitement l'expérience utilisateur. Les boutons **réduire** et **agrandir** sont activés par défaut et leurs fonctionnalités sont manipulées par le biais de la fenêtre **Propriétés** .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FormBorderStyle>
- <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>
- [Bien démarrer avec Windows Forms](getting-started-with-windows-forms.md)
