---
title: Créer un contrôle qui affiche la progression
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 9d2cf353ba2309380221bb51733baaca1b81a5d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731179"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="f39e1-102">Comment : créer un contrôle Windows Forms qui affiche la progression</span><span class="sxs-lookup"><span data-stu-id="f39e1-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="f39e1-103">L’exemple de code suivant illustre un contrôle personnalisé appelé `FlashTrackBar` qui peut être utilisé pour afficher le niveau ou la progression d’une application.</span><span class="sxs-lookup"><span data-stu-id="f39e1-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="f39e1-104">Il utilise un dégradé pour représenter visuellement la progression.</span><span class="sxs-lookup"><span data-stu-id="f39e1-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="f39e1-105">Le contrôle `FlashTrackBar` illustre les concepts suivants :</span><span class="sxs-lookup"><span data-stu-id="f39e1-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
- <span data-ttu-id="f39e1-106">Définition de propriétés personnalisées.</span><span class="sxs-lookup"><span data-stu-id="f39e1-106">Defining custom properties.</span></span>  
  
- <span data-ttu-id="f39e1-107">Définition d’événements personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f39e1-107">Defining custom events.</span></span> <span data-ttu-id="f39e1-108">(`FlashTrackBar` définit l’événement `ValueChanged`.)</span><span class="sxs-lookup"><span data-stu-id="f39e1-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
- <span data-ttu-id="f39e1-109">Substitution de la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> pour fournir une logique pour dessiner le contrôle.</span><span class="sxs-lookup"><span data-stu-id="f39e1-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
- <span data-ttu-id="f39e1-110">Calcul de la zone disponible pour dessiner le contrôle à l’aide de sa propriété <xref:System.Windows.Forms.Control.ClientRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="f39e1-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="f39e1-111">`FlashTrackBar` procède de cette manière dans sa méthode `OptimizedInvalidate`.</span><span class="sxs-lookup"><span data-stu-id="f39e1-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
- <span data-ttu-id="f39e1-112">Implémentation de la sérialisation ou de la persistance d’une propriété lorsqu’elle est modifiée dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f39e1-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="f39e1-113">`FlashTrackBar` définit les méthodes `ShouldSerializeStartColor` et `ShouldSerializeEndColor` pour sérialiser ses propriétés `StartColor` et `EndColor`.</span><span class="sxs-lookup"><span data-stu-id="f39e1-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="f39e1-114">Le tableau suivant présente les propriétés personnalisées définies par `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="f39e1-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="f39e1-115">Propriété</span><span class="sxs-lookup"><span data-stu-id="f39e1-115">Property</span></span>|<span data-ttu-id="f39e1-116">Description</span><span class="sxs-lookup"><span data-stu-id="f39e1-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="f39e1-117">Indique si l’utilisateur peut modifier la valeur de la barre de suivi Flash en cliquant dessus et en la faisant glisser.</span><span class="sxs-lookup"><span data-stu-id="f39e1-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="f39e1-118">Spécifie la couleur de fin de la barre de suivi.</span><span class="sxs-lookup"><span data-stu-id="f39e1-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="f39e1-119">Spécifie l’obscurcissement de l’arrière-plan par rapport au dégradé de premier plan.</span><span class="sxs-lookup"><span data-stu-id="f39e1-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="f39e1-120">Spécifie la valeur maximale de la barre de suivi.</span><span class="sxs-lookup"><span data-stu-id="f39e1-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="f39e1-121">Spécifie la valeur minimale de la barre de suivi.</span><span class="sxs-lookup"><span data-stu-id="f39e1-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="f39e1-122">Spécifie la couleur de début du dégradé.</span><span class="sxs-lookup"><span data-stu-id="f39e1-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="f39e1-123">Indique s’il faut afficher un pourcentage sur le dégradé.</span><span class="sxs-lookup"><span data-stu-id="f39e1-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="f39e1-124">Indique s’il faut afficher la valeur actuelle sur le dégradé.</span><span class="sxs-lookup"><span data-stu-id="f39e1-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="f39e1-125">Indique si la barre de suivi doit afficher un dégradé de couleur illustrant la valeur actuelle.</span><span class="sxs-lookup"><span data-stu-id="f39e1-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="f39e1-126">Spécifie la valeur actuelle de la barre de suivi.</span><span class="sxs-lookup"><span data-stu-id="f39e1-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="f39e1-127">Le tableau suivant montre d’autres membres définis par `FlashTrackBar:` l’événement modifié par une propriété et la méthode qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="f39e1-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="f39e1-128">Membre</span><span class="sxs-lookup"><span data-stu-id="f39e1-128">Member</span></span>|<span data-ttu-id="f39e1-129">Description</span><span class="sxs-lookup"><span data-stu-id="f39e1-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="f39e1-130">Événement déclenché lorsque la propriété `Value` de la barre de suivi change.</span><span class="sxs-lookup"><span data-stu-id="f39e1-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="f39e1-131">Méthode qui déclenche l’événement `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="f39e1-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="f39e1-132">`FlashTrackBar` utilise la classe <xref:System.EventArgs> pour les données d’événement et les <xref:System.EventHandler> pour le délégué d’événement.</span><span class="sxs-lookup"><span data-stu-id="f39e1-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="f39e1-133">Pour gérer les événements *EventName* correspondants, `FlashTrackBar` substitue les méthodes suivantes qu’il hérite de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="f39e1-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="f39e1-134">Pour gérer les événements de modification de propriété correspondants, `FlashTrackBar` substitue les méthodes suivantes qu’il hérite de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="f39e1-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="f39e1-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="f39e1-135">Example</span></span>  
 <span data-ttu-id="f39e1-136">Le contrôle `FlashTrackBar` définit deux éditeurs de type d’interface utilisateur, `FlashTrackBarValueEditor` et `FlashTrackBarDarkenByEditor`, qui sont affichés dans les listes de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="f39e1-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="f39e1-137">La classe `HostApp` utilise le contrôle `FlashTrackBar` sur un formulaire Windows.</span><span class="sxs-lookup"><span data-stu-id="f39e1-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="f39e1-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f39e1-138">See also</span></span>

- <span data-ttu-id="f39e1-139">[Extension de la prise en charge au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f39e1-139">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="f39e1-140">Concepts de base du développement de contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f39e1-140">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
