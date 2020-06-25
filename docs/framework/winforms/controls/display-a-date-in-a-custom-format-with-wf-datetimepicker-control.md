---
title: Afficher une date dans un format personnalisé avec le contrôle DateTimePicker
description: Découvrez comment utiliser le contrôle Windows Forms DateTimePicker pour mettre en forme l’affichage des dates et des heures dans le contrôle.
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
ms.openlocfilehash: 773070136e4fd43ab1bf510ebcaf6b0aa6a7ba8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325825"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="6b950-103">Comment : afficher une date dans un format personnalisé à l'aide du contrôle DateTimePicker Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b950-103">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="6b950-104">Le <xref:System.Windows.Forms.DateTimePicker> contrôle Windows Forms vous permet de mettre en forme l’affichage des dates et des heures dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="6b950-104">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="6b950-105">La <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriété vous permet de sélectionner des formats prédéfinis, listés dans la <xref:System.Windows.Forms.DateTimePickerFormat> .</span><span class="sxs-lookup"><span data-stu-id="6b950-105">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="6b950-106">Si aucune de ces fonctions n’est adaptée à vos besoins, vous pouvez créer votre propre style de mise en forme à l’aide des caractères de format indiqués dans <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> .</span><span class="sxs-lookup"><span data-stu-id="6b950-106">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="6b950-107">Pour afficher un format personnalisé</span><span class="sxs-lookup"><span data-stu-id="6b950-107">To display a custom format</span></span>  
  
1. <span data-ttu-id="6b950-108">Attribuez à la propriété <xref:System.Windows.Forms.DateTimePicker.Format%2A> la valeur `DateTimePickerFormat.Custom`.</span><span class="sxs-lookup"><span data-stu-id="6b950-108">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2. <span data-ttu-id="6b950-109">Affectez <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> à la propriété une chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="6b950-109">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="6b950-110">Pour ajouter du texte à la valeur mise en forme</span><span class="sxs-lookup"><span data-stu-id="6b950-110">To add text to the formatted value</span></span>  
  
1. <span data-ttu-id="6b950-111">Utilisez des guillemets simples pour placer tout caractère qui n’est pas un caractère de format tel que « M » ou un délimiteur comme «  : ».</span><span class="sxs-lookup"><span data-stu-id="6b950-111">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="6b950-112">Par exemple, la chaîne de format ci-dessous affiche la date actuelle au format « aujourd’hui : 05:30:31 vendredi 02, 2012 » dans la culture anglais (États-Unis).</span><span class="sxs-lookup"><span data-stu-id="6b950-112">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
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
  
     <span data-ttu-id="6b950-113">En fonction du paramètre de culture, tous les caractères non placés entre guillemets simples peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="6b950-113">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="6b950-114">Par exemple, la chaîne de format ci-dessus affiche la date actuelle au format « aujourd’hui : 05:30:31 vendredi 02, 2012 » dans la culture anglais (États-Unis).</span><span class="sxs-lookup"><span data-stu-id="6b950-114">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="6b950-115">Notez que le premier signe deux-points est placé entre guillemets simples, car il n’est pas destiné à être un caractère de délimitation, car il se trouve dans « hh : mm : SS ».</span><span class="sxs-lookup"><span data-stu-id="6b950-115">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="6b950-116">Dans une autre culture, le format peut apparaître comme suit : « aujourd’hui : 05.30.31 Friday mars 02, 2012 ».</span><span class="sxs-lookup"><span data-stu-id="6b950-116">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b950-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b950-117">See also</span></span>

- [<span data-ttu-id="6b950-118">DateTimePicker, contrôle</span><span class="sxs-lookup"><span data-stu-id="6b950-118">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="6b950-119">Guide pratique pour définir et retourner des dates à l'aide du contrôle DateTimePicker Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b950-119">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
