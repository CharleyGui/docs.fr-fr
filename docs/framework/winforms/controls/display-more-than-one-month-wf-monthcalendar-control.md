---
title: Afficher plus d’un mois dans le contrôle MonthCalendar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
ms.openlocfilehash: 5d3925bc19ddcd67742f0ab8b5b2e45530820f38
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745901"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="b0974-102">Comment : afficher plusieurs mois dans le contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0974-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="b0974-103">Le contrôle Windows Forms <xref:System.Windows.Forms.MonthCalendar> peut afficher jusqu’à 12 mois à la fois.</span><span class="sxs-lookup"><span data-stu-id="b0974-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="b0974-104">Par défaut, le contrôle affiche un seul mois, mais vous pouvez spécifier le nombre de mois affichés et la façon dont ils sont organisés dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="b0974-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="b0974-105">Lorsque vous modifiez les dimensions du calendrier, le contrôle est redimensionné. Assurez-vous qu’il y a suffisamment d’espace sur le formulaire pour les nouvelles dimensions.</span><span class="sxs-lookup"><span data-stu-id="b0974-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="b0974-106">Pour afficher plusieurs mois</span><span class="sxs-lookup"><span data-stu-id="b0974-106">To display multiple months</span></span>  
  
- <span data-ttu-id="b0974-107">Définissez la propriété <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> sur le nombre de mois à afficher horizontalement et verticalement.</span><span class="sxs-lookup"><span data-stu-id="b0974-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b0974-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0974-108">See also</span></span>

- [<span data-ttu-id="b0974-109">MonthCalendar, contrôle</span><span class="sxs-lookup"><span data-stu-id="b0974-109">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="b0974-110">Guide pratique pour sélectionner une plage de dates dans le contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0974-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="b0974-111">Guide pratique pour modifier l'apparence du contrôle MonthCalendar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0974-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
