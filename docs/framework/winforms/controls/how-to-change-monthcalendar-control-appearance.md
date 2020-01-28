---
title: Modifier l’apparence du contrôle MonthCalendar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: ded9059ede4ad03f637c0e697b880c41a9a8ba32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746654"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>Comment : modifier l'apparence du contrôle MonthCalendar Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.MonthCalendar> vous permet de personnaliser l’apparence du calendrier de nombreuses façons. Par exemple, vous pouvez définir le modèle de couleurs et choisir d’afficher ou de masquer les numéros de semaine et la date actuelle.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Pour modifier le modèle de couleurs du calendrier du mois  
  
- Définir des propriétés telles que <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> et <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. La propriété <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> détermine également la couleur de police des jours de la semaine. La propriété <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> détermine la couleur des dates qui précèdent et suivent le mois ou les mois affichés.  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    > À compter de Windows Vista et selon le thème, la définition de certaines propriétés peut ne pas modifier l’apparence du calendrier. Par exemple, si Windows est configuré pour utiliser le thème Aero, la définition des propriétés <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>ou <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> n’a aucun effet. Cela est dû au fait qu’une version mise à jour du calendrier est rendue avec une apparence dérivée au moment de l’exécution à partir du thème du système d’exploitation actuel. Si vous souhaitez utiliser ces propriétés et activer la version antérieure du calendrier, vous pouvez désactiver les styles visuels pour votre application. La désactivation des styles visuels peut affecter l’apparence et le comportement d’autres contrôles dans votre application. Pour désactiver les styles visuels dans Visual Basic, ouvrez le concepteur de projets et décochez la case **activer les styles visuels XP** . Pour désactiver les styles visuels C#dans, ouvrez Program.cs et commentez `Application.EnableVisualStyles();`. Pour plus d’informations sur les styles visuels, consultez [activation des styles visuels](/windows/desktop/controls/cookbook-overview).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Pour afficher la date actuelle au bas du contrôle  
  
- Affectez à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> la valeur `true`. L’exemple ci-dessous bascule entre l’affichage et l’omission de la date du jour lors d’un double-clic sur le formulaire.  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     (Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Pour afficher les numéros de semaine  
  
- Affectez à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> la valeur `true`. Vous pouvez définir cette propriété dans le code ou dans la Fenêtre Propriétés.  
  
     Les numéros de semaine apparaissent dans une colonne distincte à gauche du premier jour de la semaine.  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [MonthCalendar, contrôle](monthcalendar-control-windows-forms.md)
- [Guide pratique pour sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Guide pratique pour afficher en gras certains jours à l'aide du contrôle MonthCalendar Windows Forms](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Guide pratique pour afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms](display-more-than-one-month-wf-monthcalendar-control.md)
