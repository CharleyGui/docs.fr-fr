---
title: Fonctionnement de l’entrée de la souris
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: 1164974e65ca1e96c0650569626ad4140baf004e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739636"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Fonctionnement des entrées de la souris dans les Windows Forms
La réception et le traitement de l’entrée de souris constitue une partie importante de chaque application Windows. Vous pouvez gérer les événements de souris pour exécuter une action dans votre application, ou utiliser les informations d’emplacement de la souris pour effectuer un test de positionnement ou d’autres actions. En outre, vous pouvez modifier la façon dont les contrôles de votre application gèrent l’entrée de la souris. Cette rubrique décrit ces événements de souris en détail et explique comment obtenir et modifier les paramètres système de la souris. Pour plus d’informations sur les données fournies avec les événements de souris et l’ordre dans lequel les événements de clic de souris sont déclenchés, consultez [événements de souris dans Windows Forms](mouse-events-in-windows-forms.md).  
  
## <a name="mouse-location-and-hit-testing"></a>Emplacement de la souris et test de positionnement  
 Lorsque l’utilisateur déplace la souris, le système d’exploitation déplace le pointeur de la souris. Le pointeur de la souris contient un pixel unique, appelé zone réactive, que le système d’exploitation suit et reconnaît comme position du pointeur. Quand l’utilisateur déplace la souris ou appuie sur un bouton de la souris, le <xref:System.Windows.Forms.Control> qui contient le <xref:System.Windows.Forms.Cursor.HotSpot%2A> déclenche l’événement de souris approprié. Vous pouvez obtenir la position actuelle de la souris avec la propriété <xref:System.Windows.Forms.MouseEventArgs.Location%2A> du <xref:System.Windows.Forms.MouseEventArgs> lors de la gestion d’un événement de souris ou à l’aide de la propriété <xref:System.Windows.Forms.Cursor.Position%2A> de la classe <xref:System.Windows.Forms.Cursor>. Vous pouvez ensuite utiliser les informations d’emplacement de la souris pour effectuer des tests de positionnement, puis effectuer une action en fonction de l’emplacement de la souris. La fonctionnalité de test d’atteinte est intégrée à plusieurs contrôles dans Windows Forms tels que les contrôles <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> et <xref:System.Windows.Forms.DataGridView>. Utilisé avec l’événement de souris approprié, <xref:System.Windows.Forms.Control.MouseHover> par exemple, le test d’atteinte est très utile pour déterminer quand votre application doit effectuer une action spécifique.  
  
## <a name="mouse-events"></a>Événements de souris  
 Le principal moyen de répondre à l’entrée de la souris consiste à gérer les événements de souris. Le tableau suivant montre les événements de souris et décrit quand ils sont déclenchés.  
  
|Événement de souris|Description|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|Cet événement se produit lorsque le bouton de la souris est relâché, en général avant l’événement <xref:System.Windows.Forms.Control.MouseUp>. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.EventArgs>. Gérez cet événement lorsque vous devez uniquement déterminer quand un clic se produit.|  
|<xref:System.Windows.Forms.Control.MouseClick>|Cet événement se produit lorsque l’utilisateur clique sur le contrôle avec la souris. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>. Gérez cet événement lorsque vous avez besoin d’obtenir des informations sur la souris lorsqu’un clic se produit.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|Cet événement se produit lors d’un double-clic sur le contrôle. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.EventArgs>. Gérez cet événement lorsque vous devez uniquement déterminer quand un double-clic se produit.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|Cet événement se produit lorsque l’utilisateur double-clique sur le contrôle avec la souris. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>. Gérez cet événement lorsque vous avez besoin d’obtenir des informations sur la souris lorsqu’un double-clic se produit.|  
|<xref:System.Windows.Forms.Control.MouseDown>|Cet événement se produit lorsque le pointeur de la souris se trouve sur le contrôle et que l’utilisateur appuie sur un bouton de la souris. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|Cet événement se produit lorsque le pointeur de la souris entre dans la bordure ou la zone cliente du contrôle, en fonction du type de contrôle. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|Cet événement se produit lorsque le pointeur de la souris s’arrête et se positionne sur le contrôle. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|Cet événement se produit lorsque le pointeur de la souris quitte la bordure ou la zone cliente du contrôle, en fonction du type du contrôle. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|Cet événement se produit lorsque le pointeur de la souris se déplace alors qu’il se trouve sur un contrôle. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|Cet événement se produit lorsque le pointeur de la souris se trouve sur le contrôle et que l’utilisateur relâche un bouton de la souris. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|Cet événement se produit lorsque l’utilisateur fait tourner la roulette de la souris pendant que le contrôle a le focus. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>. Vous pouvez utiliser la propriété <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> de <xref:System.Windows.Forms.MouseEventArgs> pour déterminer la distance de défilement de la souris.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Modification de l’entrée de la souris et détection des paramètres système  
 Vous pouvez détecter et modifier la manière dont un contrôle gère l’entrée de la souris en dérivant du contrôle et à l’aide des méthodes <xref:System.Windows.Forms.Control.GetStyle%2A> et <xref:System.Windows.Forms.Control.SetStyle%2A>. La méthode <xref:System.Windows.Forms.Control.SetStyle%2A> prend une combinaison d’opérations de bits de valeurs <xref:System.Windows.Forms.ControlStyles> pour déterminer si le contrôle aura un comportement de clic ou de double-clic standard ou si le contrôle gère son propre traitement de souris. En outre, la classe <xref:System.Windows.Forms.SystemInformation> comprend des propriétés qui décrivent les fonctionnalités de la souris et spécifient comment la souris interagit avec le système d’exploitation. Le tableau suivant récapitule ces propriétés.  
  
|Les|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Obtient les dimensions, en pixels, de la zone dans laquelle l’utilisateur doit cliquer deux fois pour que le système d’exploitation considère deux clics comme un double-clic.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|Obtient le nombre maximal de millisecondes qui peuvent s’écouler entre un premier clic et un deuxième clic pour que le système d’exploitation considère l’action de la souris comme un double-clic.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Obtient le nombre de boutons de la souris.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Obtient une valeur qui indique si les fonctions des boutons gauche et droit de la souris ont été permutées.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Obtient les dimensions en pixels du rectangle dans lequel le pointeur de la souris doit rester pendant le délai de pointage de la souris avant qu'un message de pointage soit généré.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Obtient le temps en millisecondes pendant lequel le pointeur doit rester dans le rectangle sélectionné automatiquement par pointage avec la souris avant qu'un message de pointage soit généré.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Obtient une valeur indiquant si une souris est installée.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Obtient une valeur indiquant la vitesse actuelle de la souris, comprise entre 1 et 20.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Obtient une valeur indiquant si une souris avec roulette est installée.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Obtient le montant de la valeur delta de l’incrément d’une rotation de roulette de souris unique.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Obtient le nombre de lignes à faire défiler lors de la rotation de la roulette de la souris.|  
  
## <a name="see-also"></a>Voir aussi

- [Entrée de la souris dans une application Windows Forms](mouse-input-in-a-windows-forms-application.md)
- [Capture de la souris dans les Windows Forms](mouse-capture-in-windows-forms.md)
- [Pointeurs de souris dans les Windows Forms](mouse-pointers-in-windows-forms.md)
