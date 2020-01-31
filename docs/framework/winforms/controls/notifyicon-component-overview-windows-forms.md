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
# <a name="notifyicon-component-overview-windows-forms"></a>Vue d'ensemble du composant NotifyIcon (Windows Forms)

Le composant Windows Forms <xref:System.Windows.Forms.NotifyIcon> est généralement utilisé pour afficher des icônes pour les processus qui s'exécutent en arrière-plan et n'affichent pas d'interface utilisateur la plupart du temps. En guise d’exemple, on pourrait citer un programme antivirus accessible en cliquant sur une icône dans la zone de notification d’état de la barre des tâches.

## <a name="key-properties-of-notifyicons"></a>Principales propriétés de NotifyIcons

Chaque composant <xref:System.Windows.Forms.NotifyIcon> affiche une seule icône dans la zone d'état. Si vous avez trois processus d'arrière-plan et que vous voulez afficher une icône pour chacun d'eux, vous devez ajouter trois composants <xref:System.Windows.Forms.NotifyIcon> au formulaire. Les principales propriétés du composant <xref:System.Windows.Forms.NotifyIcon> sont <xref:System.Windows.Forms.NotifyIcon.Icon%2A> et <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. La propriété <xref:System.Windows.Forms.NotifyIcon.Icon%2A> définit l'icône affichée dans la zone d'état. Pour que cette icône s'affiche, la propriété <xref:System.Windows.Forms.NotifyIcon.Visible%2A> doit avoir la valeur `true`.

## <a name="notifyicons-options"></a>Options de NotifyIcons

Vous pouvez associer des info-bulles et des menus contextuels à un <xref:System.Windows.Forms.NotifyIcon> pour aider l'utilisateur.

Vous pouvez afficher des info-bulles pour un <xref:System.Windows.Forms.NotifyIcon> en appelant la méthode <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> en spécifiant la durée d'affichage souhaitée pour l'info-bulle. Vous pouvez également spécifier le texte, l'icône et le titre de l'info-bulle avec les propriétés <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> et <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectivement. Vous pouvez aussi associer des info-bulles et des menus contextuels à des composants <xref:System.Windows.Forms.NotifyIcon>. Pour plus d’informations, consultez [vue d’ensemble des composants ToolTip](tooltip-component-overview-windows-forms.md) et [vue d’ensemble du composant ContextMenu](contextmenu-component-overview-windows-forms.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.NotifyIcon>
- [NotifyIcon, composant](notifyicon-component-windows-forms.md)
