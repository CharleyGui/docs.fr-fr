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
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a><span data-ttu-id="78cdb-102">Comment : modifier l'apparence du contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78cdb-102">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>
<span data-ttu-id="78cdb-103">Le contrôle Windows Forms <xref:System.Windows.Forms.MonthCalendar> vous permet de personnaliser l’apparence du calendrier de nombreuses façons.</span><span class="sxs-lookup"><span data-stu-id="78cdb-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="78cdb-104">Par exemple, vous pouvez définir le modèle de couleurs et choisir d’afficher ou de masquer les numéros de semaine et la date actuelle.</span><span class="sxs-lookup"><span data-stu-id="78cdb-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="78cdb-105">Pour modifier le modèle de couleurs du calendrier du mois</span><span class="sxs-lookup"><span data-stu-id="78cdb-105">To change the month calendar's color scheme</span></span>  
  
- <span data-ttu-id="78cdb-106">Définir des propriétés telles que <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> et <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="78cdb-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="78cdb-107">La propriété <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> détermine également la couleur de police des jours de la semaine.</span><span class="sxs-lookup"><span data-stu-id="78cdb-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="78cdb-108">La propriété <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> détermine la couleur des dates qui précèdent et suivent le mois ou les mois affichés.</span><span class="sxs-lookup"><span data-stu-id="78cdb-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
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
    > <span data-ttu-id="78cdb-109">À compter de Windows Vista et selon le thème, la définition de certaines propriétés peut ne pas modifier l’apparence du calendrier.</span><span class="sxs-lookup"><span data-stu-id="78cdb-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="78cdb-110">Par exemple, si Windows est configuré pour utiliser le thème Aero, la définition des propriétés <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>ou <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="78cdb-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="78cdb-111">Cela est dû au fait qu’une version mise à jour du calendrier est rendue avec une apparence dérivée au moment de l’exécution à partir du thème du système d’exploitation actuel.</span><span class="sxs-lookup"><span data-stu-id="78cdb-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="78cdb-112">Si vous souhaitez utiliser ces propriétés et activer la version antérieure du calendrier, vous pouvez désactiver les styles visuels pour votre application.</span><span class="sxs-lookup"><span data-stu-id="78cdb-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="78cdb-113">La désactivation des styles visuels peut affecter l’apparence et le comportement d’autres contrôles dans votre application.</span><span class="sxs-lookup"><span data-stu-id="78cdb-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="78cdb-114">Pour désactiver les styles visuels dans Visual Basic, ouvrez le concepteur de projets et décochez la case **activer les styles visuels XP** .</span><span class="sxs-lookup"><span data-stu-id="78cdb-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="78cdb-115">Pour désactiver les styles visuels C#dans, ouvrez Program.cs et commentez `Application.EnableVisualStyles();`.</span><span class="sxs-lookup"><span data-stu-id="78cdb-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="78cdb-116">Pour plus d’informations sur les styles visuels, consultez [activation des styles visuels](/windows/desktop/controls/cookbook-overview).</span><span class="sxs-lookup"><span data-stu-id="78cdb-116">For more information about visual styles, see [Enabling Visual Styles](/windows/desktop/controls/cookbook-overview).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="78cdb-117">Pour afficher la date actuelle au bas du contrôle</span><span class="sxs-lookup"><span data-stu-id="78cdb-117">To display the current date at the bottom of the control</span></span>  
  
- <span data-ttu-id="78cdb-118">Affectez à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="78cdb-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="78cdb-119">L’exemple ci-dessous bascule entre l’affichage et l’omission de la date du jour lors d’un double-clic sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="78cdb-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
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
  
     <span data-ttu-id="78cdb-120">(Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="78cdb-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="78cdb-121">Pour afficher les numéros de semaine</span><span class="sxs-lookup"><span data-stu-id="78cdb-121">To display week numbers</span></span>  
  
- <span data-ttu-id="78cdb-122">Affectez à la propriété <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="78cdb-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="78cdb-123">Vous pouvez définir cette propriété dans le code ou dans la Fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="78cdb-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="78cdb-124">Les numéros de semaine apparaissent dans une colonne distincte à gauche du premier jour de la semaine.</span><span class="sxs-lookup"><span data-stu-id="78cdb-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="78cdb-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78cdb-125">See also</span></span>

- [<span data-ttu-id="78cdb-126">MonthCalendar, contrôle</span><span class="sxs-lookup"><span data-stu-id="78cdb-126">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="78cdb-127">Guide pratique pour sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78cdb-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="78cdb-128">Guide pratique pour afficher en gras certains jours à l'aide du contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78cdb-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [<span data-ttu-id="78cdb-129">Guide pratique pour afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78cdb-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
