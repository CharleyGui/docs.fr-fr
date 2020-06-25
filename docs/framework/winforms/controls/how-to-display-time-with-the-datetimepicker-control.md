---
title: "Comment : afficher l'heure avec le contrôle DateTimePicker"
description: Découvrez comment utiliser le contrôle Windows Forms DateTimePicker pour permettre aux utilisateurs de sélectionner une date et une heure, et afficher cette date et cette heure au format spécifié.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: ab584367a189d05e567bb57d386c6bf629201102
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325585"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="92588-103">Comment : afficher l'heure avec le contrôle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="92588-103">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="92588-104">Si vous souhaitez que votre application permette aux utilisateurs de sélectionner une date et une heure et qu'elle affiche la date et l'heure au format spécifié, utilisez le contrôle <xref:System.Windows.Forms.DateTimePicker>.</span><span class="sxs-lookup"><span data-stu-id="92588-104">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="92588-105">La procédure suivante montre comment utiliser le contrôle <xref:System.Windows.Forms.DateTimePicker> pour afficher l'heure.</span><span class="sxs-lookup"><span data-stu-id="92588-105">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="92588-106">Pour afficher l'heure avec le contrôle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="92588-106">To display the time with the DateTimePicker control</span></span>  
  
1. <span data-ttu-id="92588-107">Affectez à la propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> la valeur <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="92588-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="92588-108">Affectez à la propriété <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> de <xref:System.Windows.Forms.DateTimePicker> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="92588-108">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="92588-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="92588-109">Example</span></span>  
 <span data-ttu-id="92588-110">L'exemple de code suivant montre comment créer un <xref:System.Windows.Forms.DateTimePicker> qui permet aux utilisateurs de choisir uniquement une heure.</span><span class="sxs-lookup"><span data-stu-id="92588-110">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="92588-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="92588-111">Compiling the Code</span></span>  
 <span data-ttu-id="92588-112">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="92588-112">This example requires:</span></span>  
  
- <span data-ttu-id="92588-113">Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="92588-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92588-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92588-114">See also</span></span>

- [<span data-ttu-id="92588-115">DateTimePicker, contrôle</span><span class="sxs-lookup"><span data-stu-id="92588-115">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
