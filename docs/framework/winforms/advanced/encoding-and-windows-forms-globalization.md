---
title: Encodage et globalisation des applications Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
ms.openlocfilehash: 60ca9f7ba2f716b5dab1b0276bc3cd07ddd8f65c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736887"
---
# <a name="encoding-and-windows-forms-globalization"></a><span data-ttu-id="6b9dc-102">Encodage et globalisation des applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b9dc-102">Encoding and Windows Forms Globalization</span></span>

<span data-ttu-id="6b9dc-103">Les applications Windows Forms sont totalement compatibles Unicode, ce qui signifie que chaque caractère est représenté par un nombre unique, quels que soient la plate-forme, le programme ou la langue.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-103">Windows Forms applications are entirely Unicode-enabled, meaning that each character is represented by a unique number, no matter what the platform, program, or language.</span></span> <span data-ttu-id="6b9dc-104">Pour plus d’informations sur Unicode, consultez le [site Web du consortium Unicode](https://www.unicode.org).</span><span class="sxs-lookup"><span data-stu-id="6b9dc-104">For more information about Unicode, see the [Unicode consortium Web site](https://www.unicode.org).</span></span>

## <a name="benefits-of-unicode"></a><span data-ttu-id="6b9dc-105">Avantages d'Unicode</span><span class="sxs-lookup"><span data-stu-id="6b9dc-105">Benefits of Unicode</span></span>

<span data-ttu-id="6b9dc-106">Les avantages des formulaires Unicode incluent la possibilité de travailler avec des scripts qui sont Unicode uniquement, tels que l'Hindi.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-106">The benefits of Unicode-enabled forms include the ability to work with scripts that are Unicode-only, such as Hindi.</span></span> <span data-ttu-id="6b9dc-107">En outre, vous pouvez utiliser plusieurs langues sur un même formulaire.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-107">In addition, you can use multiple languages on a single form.</span></span> <span data-ttu-id="6b9dc-108">En Unicode, tous les caractères font deux octets. Aucun effort particulier n'est donc nécessaire pour représenter des caractères codés sur deux octets.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-108">In Unicode, all characters are two bytes long, so no special effort is needed to represent double-byte characters.</span></span> <span data-ttu-id="6b9dc-109">Vous pouvez aussi écrire un seul ensemble de code qui fonctionne sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-109">You can also write a single set of code that will work on all platforms.</span></span> <span data-ttu-id="6b9dc-110">Il s’agit d’une modification par rapport aux versions précédentes de Visual Basic, dans lesquelles vous deviez écrire du code différent pour différentes plateformes, comme Windows NT et Windows 98.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-110">This is a change from previous versions of Visual Basic, in which you had to write different code for different platforms, such as Windows NT and Windows 98.</span></span>

<span data-ttu-id="6b9dc-111">Toutefois, certains contrôles ne prennent pas en charge Unicode dans Windows 98 et Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-111">However, certain controls do not support Unicode in Windows 98 and Windows Millennium Edition.</span></span> <span data-ttu-id="6b9dc-112">Ces contrôles, qui héritent tous du contrôle commun, traitent les données avec les pages de code Windows, au format ANSI.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-112">These controls, all of which inherit from the common control, will process data with the Windows code pages, as ANSI.</span></span> <span data-ttu-id="6b9dc-113">Il s'agit des contrôles suivants : <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, et <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-113">These controls are: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, and <xref:System.Windows.Forms.StatusBar>.</span></span> <span data-ttu-id="6b9dc-114">Par conséquent, vous ne pouvez pas afficher de données Unicode dans ces contrôles sur les plateformes répertoriées.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-114">As a result, you cannot display Unicode data in these controls on the listed platforms.</span></span> <span data-ttu-id="6b9dc-115">Par exemple, vous ne pouvez pas afficher de caractères japonais sur un système d’exploitation Windows 98 en anglais.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-115">For example, you cannot display Japanese characters on an English Windows 98 operating system.</span></span>

<span data-ttu-id="6b9dc-116">Pour disposer d'alternatives aux contrôles <xref:System.Windows.Forms.ToolBar> et <xref:System.Windows.Forms.StatusBar> prenant en charge Unicode, utilisez les contrôles <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.StatusStrip>, qui remplacent ces anciens contrôles.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-116">For Unicode-aware alternatives to the <xref:System.Windows.Forms.ToolBar> and <xref:System.Windows.Forms.StatusBar> controls, use the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip> controls, which replace these older controls.</span></span> <span data-ttu-id="6b9dc-117">Pour conserver une apparence semblable entre les éléments visuels dans votre application, utilisez le contrôle <xref:System.Windows.Forms.MenuStrip> pour afficher les menus plutôt que <xref:System.Windows.Forms.MainMenu>.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-117">To maintain a similar look and feel between visual elements in your application, use the <xref:System.Windows.Forms.MenuStrip> control for rendering menus instead of <xref:System.Windows.Forms.MainMenu>.</span></span> <span data-ttu-id="6b9dc-118">Comme <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> peut également traiter et afficher des caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="6b9dc-118">Like <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> can also process and display Unicode characters.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b9dc-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b9dc-119">See also</span></span>

- [<span data-ttu-id="6b9dc-120">Globalisation des applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b9dc-120">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
