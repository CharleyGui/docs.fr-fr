---
title: Afficher une date dans un format personnalisé avec le contrôle DateTimePicker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: a27dbe737b81af86c0ac50b791bcd87bafe05b4f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745933"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Comment : afficher une date dans un format personnalisé à l'aide du contrôle DateTimePicker Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.DateTimePicker> vous donne la possibilité de mettre en forme l’affichage des dates et des heures dans le contrôle. La propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> vous permet de sélectionner des formats prédéfinis, listés dans le <xref:System.Windows.Forms.DateTimePickerFormat>. Si aucune de ces fonctions n’est adaptée à vos besoins, vous pouvez créer votre propre style de mise en forme à l’aide des caractères de format indiqués dans <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### <a name="to-display-a-custom-format"></a>Pour afficher un format personnalisé  
  
1. Affectez à la propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> la valeur `DateTimePickerFormat.Custom`.  
  
2. Affectez à la propriété <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> une chaîne de format.  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a>Pour ajouter du texte à la valeur mise en forme  
  
1. Utilisez des guillemets simples pour placer tout caractère qui n’est pas un caractère de format tel que « M » ou un délimiteur comme «  : ». Par exemple, la chaîne de format ci-dessous affiche la date actuelle au format « aujourd’hui : 05:30:31 vendredi 02, 2012 » dans la culture anglais (États-Unis).  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     En fonction du paramètre de culture, tous les caractères non placés entre guillemets simples peuvent être modifiés. Par exemple, la chaîne de format ci-dessus affiche la date actuelle au format « aujourd’hui : 05:30:31 vendredi 02, 2012 » dans la culture anglais (États-Unis). Notez que le premier signe deux-points est placé entre guillemets simples, car il n’est pas destiné à être un caractère de délimitation, car il se trouve dans « hh : mm : SS ». Dans une autre culture, le format peut apparaître comme suit : « aujourd’hui : 05.30.31 Friday mars 02, 2012 ».  
  
## <a name="see-also"></a>Voir aussi

- [DateTimePicker, contrôle](datetimepicker-control-windows-forms.md)
- [Guide pratique pour définir et retourner des dates à l'aide du contrôle DateTimePicker Windows Forms](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
