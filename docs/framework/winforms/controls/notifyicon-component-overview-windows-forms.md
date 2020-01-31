---
title: Vue d'ensemble du composant NotifyIcon
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 587bf514db853f1122ed16abc05a195985c5ce8d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742128"
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="7468a-102">Vue d'ensemble du composant NotifyIcon (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7468a-102">NotifyIcon Component Overview (Windows Forms)</span></span>

<span data-ttu-id="7468a-103">Le composant Windows Forms <xref:System.Windows.Forms.NotifyIcon> est généralement utilisé pour afficher des icônes pour les processus qui s'exécutent en arrière-plan et n'affichent pas d'interface utilisateur la plupart du temps.</span><span class="sxs-lookup"><span data-stu-id="7468a-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="7468a-104">En guise d’exemple, on pourrait citer un programme antivirus accessible en cliquant sur une icône dans la zone de notification d’état de la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="7468a-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>

## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="7468a-105">Principales propriétés de NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="7468a-105">Key Properties of NotifyIcons</span></span>

<span data-ttu-id="7468a-106">Chaque composant <xref:System.Windows.Forms.NotifyIcon> affiche une seule icône dans la zone d'état.</span><span class="sxs-lookup"><span data-stu-id="7468a-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="7468a-107">Si vous avez trois processus d'arrière-plan et que vous voulez afficher une icône pour chacun d'eux, vous devez ajouter trois composants <xref:System.Windows.Forms.NotifyIcon> au formulaire.</span><span class="sxs-lookup"><span data-stu-id="7468a-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="7468a-108">Les principales propriétés du composant <xref:System.Windows.Forms.NotifyIcon> sont <xref:System.Windows.Forms.NotifyIcon.Icon%2A> et <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="7468a-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="7468a-109">La propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A> définit l'icône affichée dans la zone d'état.</span><span class="sxs-lookup"><span data-stu-id="7468a-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="7468a-110">Pour que cette icône s'affiche, la propriété <xref:System.Windows.Forms.NotifyIcon.Visible%2A> doit avoir la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="7468a-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>

## <a name="notifyicons-options"></a><span data-ttu-id="7468a-111">Options de NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="7468a-111">NotifyIcons Options</span></span>

<span data-ttu-id="7468a-112">Vous pouvez associer des info-bulles et des menus contextuels à un <xref:System.Windows.Forms.NotifyIcon> pour aider l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7468a-112">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>

<span data-ttu-id="7468a-113">Vous pouvez afficher des info-bulles pour un <xref:System.Windows.Forms.NotifyIcon> en appelant la méthode <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> en spécifiant la durée d'affichage souhaitée pour l'info-bulle.</span><span class="sxs-lookup"><span data-stu-id="7468a-113">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="7468a-114">Vous pouvez également spécifier le texte, l'icône et le titre de l'info-bulle avec les propriétés <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> et <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectivement.</span><span class="sxs-lookup"><span data-stu-id="7468a-114">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="7468a-115">Vous pouvez aussi associer des info-bulles et des menus contextuels à des composants <xref:System.Windows.Forms.NotifyIcon>.</span><span class="sxs-lookup"><span data-stu-id="7468a-115"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="7468a-116">Pour plus d’informations, consultez [vue d’ensemble des composants ToolTip](tooltip-component-overview-windows-forms.md) et [vue d’ensemble du composant ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7468a-116">For more information, see [ToolTip Component Overview](tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7468a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7468a-117">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- [<span data-ttu-id="7468a-118">NotifyIcon, composant</span><span class="sxs-lookup"><span data-stu-id="7468a-118">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
