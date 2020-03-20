---
title: Dates d’ensemble et de retour avec contrôle DateTimePicker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], setting in DateTimePicker
- DateTimePicker control [Windows Forms], setting and returning dates
- examples [Windows Forms], DateTimePicker control
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
ms.openlocfilehash: f958097640316715b38828e72107ab5bdb9389aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141911"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Comment : définir et retourner des dates à l'aide du contrôle DateTimePicker Windows Forms
La date ou l'heure actuellement sélectionnée dans le contrôle Windows Forms <xref:System.Windows.Forms.DateTimePicker> est déterminée par la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A>. Vous pouvez définir la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> avant l'affichage du contrôle (par exemple au moment du design ou dans l'événement <xref:System.Windows.Forms.Form.Load> du contrôle) pour déterminer la date qui sera initialement sélectionnée dans le contrôle. Par défaut, la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> du contrôle a comme valeur la date actuelle. Si vous modifiez la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> du contrôle dans le code, le contrôle est automatiquement mis à jour sur le formulaire pour refléter le nouveau paramètre.  
  
 La propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> retourne une structure <xref:System.DateTime> comme valeur. Il existe plusieurs propriétés de la structure <xref:System.DateTime> qui retournent des informations spécifiques sur la date affichée. Ces propriétés peuvent être utilisées uniquement pour retourner une valeur. Vous ne devez pas les utiliser pour définir une valeur.  
  
- Pour les valeurs de date, les propriétés <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A> et <xref:System.DateTime.Year%2A> retournent des valeurs entières pour ces unités de temps de la date sélectionnée. La propriété <xref:System.DateTime.DayOfWeek%2A> retourne une valeur qui indique le jour de la semaine sélectionné (les valeurs possibles sont répertoriées dans l'énumération <xref:System.DayOfWeek>).  
  
- Pour les valeurs d'heure, les propriétés <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A> et <xref:System.DateTime.Millisecond%2A> retournent des valeurs entières pour ces unités de temps. Pour configurer le contrôle pour afficher les temps, voir [Comment : Afficher l’heure avec le contrôle DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Pour définir la valeur de date et d'heure du contrôle  
  
- Affectez à la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> une valeur de date ou d'heure.  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a>Pour retourner la valeur de date et d'heure  
  
- Appelez la propriété <xref:System.Windows.Forms.DateTimePicker.Text%2A> pour retourner la valeur entière telle que mise en forme dans le contrôle ou appelez la méthode appropriée de la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> pour retourner une partie de la valeur. Utilisez <xref:System.Windows.Forms.DateTimePicker.ToString%2A> pour convertir les informations en une chaîne qui peut être présentée à l'utilisateur.  
  
    ```vb  
    MessageBox.Show("The selected value is ", DateTimePicker1.Text)  
    MessageBox.Show("The day of the week is ",
       DateTimePicker1.Value.DayOfWeek.ToString)  
    MessageBox.Show("Millisecond is: ",
       DateTimePicker1.Value.Millisecond.ToString)  
    ```  
  
    ```csharp  
    MessageBox.Show ("The selected value is " +
       dateTimePicker1.Text);  
    MessageBox.Show ("The day of the week is " +
       dateTimePicker1.Value.DayOfWeek.ToString());  
    MessageBox.Show("Millisecond is: " +
       dateTimePicker1.Value.Millisecond.ToString());  
    ```  
  
    ```cpp  
    MessageBox::Show (String::Concat("The selected value is ",  
       dateTimePicker1->Text));  
    MessageBox::Show (String::Concat("The day of the week is ",  
       dateTimePicker1->Value.DayOfWeek.ToString()));  
    MessageBox::Show(String::Concat("Millisecond is: ",  
       dateTimePicker1->Value.Millisecond.ToString()));  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [DateTimePicker, contrôle](datetimepicker-control-windows-forms.md)
- [Comment : afficher une date dans un format personnalisé à l'aide du contrôle DateTimePicker Windows Forms](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
