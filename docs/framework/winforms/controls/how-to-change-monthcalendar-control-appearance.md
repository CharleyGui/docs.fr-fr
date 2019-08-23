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
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a><span data-ttu-id="f8652-102">Procédure : modifier l’aspect du contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f8652-102">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>
<span data-ttu-id="f8652-103">Le contrôle <xref:System.Windows.Forms.MonthCalendar> Windows Forms vous permet de personnaliser l’apparence du calendrier de nombreuses façons.</span><span class="sxs-lookup"><span data-stu-id="f8652-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="f8652-104">Par exemple, vous pouvez définir le modèle de couleurs et choisir d’afficher ou de masquer les numéros de semaine et la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="f8652-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="f8652-105">Pour modifier le modèle de couleurs du calendrier du mois</span><span class="sxs-lookup"><span data-stu-id="f8652-105">To change the month calendar's color scheme</span></span>  
  
- <span data-ttu-id="f8652-106">Définir des propriétés telles <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>que <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> , <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>et.</span><span class="sxs-lookup"><span data-stu-id="f8652-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="f8652-107">La <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> propriété détermine également la couleur de police des jours de la semaine.</span><span class="sxs-lookup"><span data-stu-id="f8652-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="f8652-108">La <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> propriété détermine la couleur des dates qui précèdent et suivent le mois ou les mois affichés.</span><span class="sxs-lookup"><span data-stu-id="f8652-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
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
    > <span data-ttu-id="f8652-109">À compter de Windows Vista et selon le thème, la définition de certaines propriétés peut ne pas modifier l’apparence du calendrier.</span><span class="sxs-lookup"><span data-stu-id="f8652-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="f8652-110">Par exemple, si Windows est configuré pour utiliser le thème Aero, la définition <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>des <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>propriétés <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>,, <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> ou n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="f8652-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="f8652-111">Cela est dû au fait qu’une version mise à jour du calendrier est rendue avec une apparence dérivée au moment de l’exécution à partir du thème du système d’exploitation actuel.</span><span class="sxs-lookup"><span data-stu-id="f8652-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="f8652-112">Si vous souhaitez utiliser ces propriétés et activer la version antérieure du calendrier, vous pouvez désactiver les styles visuels pour votre application.</span><span class="sxs-lookup"><span data-stu-id="f8652-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="f8652-113">La désactivation des styles visuels peut affecter l’apparence et le comportement d’autres contrôles dans votre application.</span><span class="sxs-lookup"><span data-stu-id="f8652-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="f8652-114">Pour désactiver les styles visuels dans Visual Basic, ouvrez le concepteur de projets et décochez la case **activer les styles visuels XP** .</span><span class="sxs-lookup"><span data-stu-id="f8652-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="f8652-115">Pour désactiver les styles visuels C#dans, ouvrez Program.cs et commentez `Application.EnableVisualStyles();`.</span><span class="sxs-lookup"><span data-stu-id="f8652-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="f8652-116">Pour plus d’informations sur les styles visuels, consultez [activation des styles visuels](/windows/desktop/controls/cookbook-overview).</span><span class="sxs-lookup"><span data-stu-id="f8652-116">For more information about visual styles, see [Enabling Visual Styles](/windows/desktop/controls/cookbook-overview).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="f8652-117">Pour afficher la date actuelle au bas du contrôle</span><span class="sxs-lookup"><span data-stu-id="f8652-117">To display the current date at the bottom of the control</span></span>  
  
- <span data-ttu-id="f8652-118">Affectez à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="f8652-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="f8652-119">L’exemple ci-dessous bascule entre l’affichage et l’omission de la date du jour lors d’un double-clic sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="f8652-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
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
  
     <span data-ttu-id="f8652-120">(Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="f8652-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="f8652-121">Pour afficher les numéros de semaine</span><span class="sxs-lookup"><span data-stu-id="f8652-121">To display week numbers</span></span>  
  
- <span data-ttu-id="f8652-122">Affectez à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="f8652-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="f8652-123">Vous pouvez définir cette propriété dans le code ou dans la Fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="f8652-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="f8652-124">Les numéros de semaine apparaissent dans une colonne distincte à gauche du premier jour de la semaine.</span><span class="sxs-lookup"><span data-stu-id="f8652-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f8652-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8652-125">See also</span></span>

- [<span data-ttu-id="f8652-126">MonthCalendar, contrôle</span><span class="sxs-lookup"><span data-stu-id="f8652-126">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="f8652-127">Guide pratique pour Sélectionner une plage de dates dans le contrôle Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="f8652-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="f8652-128">Guide pratique pour Afficher des jours spécifiques en gras avec le contrôle Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="f8652-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [<span data-ttu-id="f8652-129">Guide pratique pour Afficher plus d’un mois dans le contrôle Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="f8652-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
