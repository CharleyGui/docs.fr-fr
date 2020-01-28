---
title: Définir et retourner des dates avec le contrôle DateTimePicker
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
ms.openlocfilehash: 1e0aa58e98748ccde9411f0f4871adbae3a5f14d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747101"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="e6302-102">Comment : définir et retourner des dates à l'aide du contrôle DateTimePicker Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6302-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="e6302-103">La date ou l'heure actuellement sélectionnée dans le contrôle Windows Forms <xref:System.Windows.Forms.DateTimePicker> est déterminée par la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6302-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="e6302-104">Vous pouvez définir la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> avant l'affichage du contrôle (par exemple au moment du design ou dans l'événement <xref:System.Windows.Forms.Form.Load> du contrôle) pour déterminer la date qui sera initialement sélectionnée dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="e6302-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="e6302-105">Par défaut, la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> du contrôle a comme valeur la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="e6302-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="e6302-106">Si vous modifiez la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> du contrôle dans le code, le contrôle est automatiquement mis à jour sur le formulaire pour refléter le nouveau paramètre.</span><span class="sxs-lookup"><span data-stu-id="e6302-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="e6302-107">La propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> retourne une structure <xref:System.DateTime> comme valeur.</span><span class="sxs-lookup"><span data-stu-id="e6302-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="e6302-108">Il existe plusieurs propriétés de la structure <xref:System.DateTime> qui retournent des informations spécifiques sur la date affichée.</span><span class="sxs-lookup"><span data-stu-id="e6302-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="e6302-109">Ces propriétés peuvent être utilisées uniquement pour retourner une valeur. Vous ne devez pas les utiliser pour définir une valeur.</span><span class="sxs-lookup"><span data-stu-id="e6302-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
- <span data-ttu-id="e6302-110">Pour les valeurs de date, les propriétés <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A> et <xref:System.DateTime.Year%2A> retournent des valeurs entières pour ces unités de temps de la date sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="e6302-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="e6302-111">La propriété <xref:System.DateTime.DayOfWeek%2A> retourne une valeur qui indique le jour de la semaine sélectionné (les valeurs possibles sont répertoriées dans l'énumération <xref:System.DayOfWeek>).</span><span class="sxs-lookup"><span data-stu-id="e6302-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
- <span data-ttu-id="e6302-112">Pour les valeurs d'heure, les propriétés <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A> et <xref:System.DateTime.Millisecond%2A> retournent des valeurs entières pour ces unités de temps.</span><span class="sxs-lookup"><span data-stu-id="e6302-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="e6302-113">Pour configurer le contrôle de manière à afficher les heures, consultez [Comment : afficher l’heure avec le contrôle DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="e6302-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="e6302-114">Pour définir la valeur de date et d'heure du contrôle</span><span class="sxs-lookup"><span data-stu-id="e6302-114">To set the date and time value of the control</span></span>  
  
- <span data-ttu-id="e6302-115">Affectez à la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> une valeur de date ou d'heure.</span><span class="sxs-lookup"><span data-stu-id="e6302-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="e6302-116">Pour retourner la valeur de date et d'heure</span><span class="sxs-lookup"><span data-stu-id="e6302-116">To return the date and time value</span></span>  
  
- <span data-ttu-id="e6302-117">Appelez la propriété <xref:System.Windows.Forms.DateTimePicker.Text%2A> pour retourner la valeur entière telle que mise en forme dans le contrôle ou appelez la méthode appropriée de la propriété <xref:System.Windows.Forms.DateTimePicker.Value%2A> pour retourner une partie de la valeur.</span><span class="sxs-lookup"><span data-stu-id="e6302-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="e6302-118">Utilisez <xref:System.Windows.Forms.DateTimePicker.ToString%2A> pour convertir les informations en une chaîne qui peut être présentée à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e6302-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6302-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6302-119">See also</span></span>

- [<span data-ttu-id="e6302-120">DateTimePicker, contrôle</span><span class="sxs-lookup"><span data-stu-id="e6302-120">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="e6302-121">Guide pratique pour afficher une date dans un format personnalisé à l'aide du contrôle DateTimePicker Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6302-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
