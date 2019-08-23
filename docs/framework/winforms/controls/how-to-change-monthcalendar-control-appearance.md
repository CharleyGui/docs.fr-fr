---
title: 'Procédure : modifier l’aspect du contrôle MonthCalendar Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: 5582624d881b2d8039bcd5e8ac45e548c7b38f57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929047"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>Procédure : modifier l’aspect du contrôle MonthCalendar Windows Forms
Le contrôle <xref:System.Windows.Forms.MonthCalendar> Windows Forms vous permet de personnaliser l’apparence du calendrier de nombreuses façons. Par exemple, vous pouvez définir le modèle de couleurs et choisir d’afficher ou de masquer les numéros de semaine et la date actuelle.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Pour modifier le modèle de couleurs du calendrier du mois  
  
- Définir des propriétés telles <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>que <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> , <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>et. La <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> propriété détermine également la couleur de police des jours de la semaine. La <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> propriété détermine la couleur des dates qui précèdent et suivent le mois ou les mois affichés.  
  
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
    > À compter de Windows Vista et selon le thème, la définition de certaines propriétés peut ne pas modifier l’apparence du calendrier. Par exemple, si Windows est configuré pour utiliser le thème Aero, la définition <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>des <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>propriétés <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>,, <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> ou n’a aucun effet. Cela est dû au fait qu’une version mise à jour du calendrier est rendue avec une apparence dérivée au moment de l’exécution à partir du thème du système d’exploitation actuel. Si vous souhaitez utiliser ces propriétés et activer la version antérieure du calendrier, vous pouvez désactiver les styles visuels pour votre application. La désactivation des styles visuels peut affecter l’apparence et le comportement d’autres contrôles dans votre application. Pour désactiver les styles visuels dans Visual Basic, ouvrez le concepteur de projets et décochez la case **activer les styles visuels XP** . Pour désactiver les styles visuels C#dans, ouvrez Program.cs et commentez `Application.EnableVisualStyles();`. Pour plus d’informations sur les styles visuels, consultez [activation des styles visuels](/windows/desktop/controls/cookbook-overview).  
  
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
- [Guide pratique pour Sélectionner une plage de dates dans le contrôle Windows Forms MonthCalendar](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Guide pratique pour Afficher des jours spécifiques en gras avec le contrôle Windows Forms MonthCalendar](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Guide pratique pour Afficher plus d’un mois dans le contrôle Windows Forms MonthCalendar](display-more-than-one-month-wf-monthcalendar-control.md)
