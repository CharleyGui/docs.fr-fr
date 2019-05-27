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
ms.openlocfilehash: 21fa6798c431b71d36c1909937ddad6bf5030782
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053095"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>Procédure : modifier l’aspect du contrôle MonthCalendar Windows Forms
Les formulaires Windows <xref:System.Windows.Forms.MonthCalendar> contrôle vous permet de personnaliser l’apparence du calendrier de nombreuses façons. Par exemple, vous pouvez définir le jeu de couleurs et choisir d’afficher ou masquer les numéros de semaine et la date actuelle.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Pour modifier le modèle de couleurs du calendrier du mois  
  
- Définir des propriétés telles que <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> et <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. Le <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> propriété détermine également la couleur de police pour les jours de la semaine. Le <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> propriété détermine la couleur des dates qui précèdent et suivent l’ou les mois affichés.  
  
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
    >  À compter de Windows Vista et selon le thème, la définition de certaines propriétés ne modifiera pas nécessairement l’apparence du calendrier. Par exemple, si Windows est configuré pour utiliser le thème Aero, affecter le <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, ou <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> propriétés n’a aucun effet. Il s’agit, car une version mise à jour du calendrier est restituée avec une apparence qui est dérivée en cours d’exécution le thème du système d’exploitation actuel. Si vous souhaitez utiliser ces propriétés et activer la version antérieure du calendrier, vous pouvez désactiver les styles visuels pour votre application. La désactivation de styles visuels peut affecter l’apparence et le comportement d’autres contrôles dans votre application. Pour désactiver des styles visuels dans Visual Basic, ouvrez le Concepteur de projets et désactivez le **les styles visuels XP activer** case à cocher. Pour désactiver des styles visuels dans c#, ouvrez Program.cs et commentez `Application.EnableVisualStyles();`. Pour plus d’informations sur les styles visuels, consultez [activation des Styles visuels](/windows/desktop/controls/cookbook-overview).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Pour afficher la date actuelle en bas du contrôle  
  
- Affectez à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> la valeur `true`. L’exemple suivant bascule entre l’affichage et l’omission du jour lorsque le formulaire est sur lequel double-cliquer.  
  
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
  
     (Visual C#, Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Pour afficher les numéros de semaine  
  
- Affectez à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> la valeur `true`. Vous pouvez définir cette propriété dans le code ou dans la fenêtre Propriétés.  
  
     Numéros de semaine s’affichent dans une autre colonne à gauche du premier jour de la semaine.  
  
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
- [Guide pratique pour Sélectionnez une plage de Dates dans le contrôle MonthCalendar Windows Forms](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Guide pratique pour Afficher en gras certains jours avec les Windows Forms du contrôle MonthCalendar](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Guide pratique pour Afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms](display-more-than-one-month-wf-monthcalendar-control.md)
