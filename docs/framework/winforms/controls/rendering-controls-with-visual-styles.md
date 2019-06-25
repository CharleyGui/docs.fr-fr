---
title: Rendu des contrôles avec les styles visuels
ms.date: 03/30/2017
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- themes [Windows Forms], XP visual styles in Window Forms
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- visual themes [Windows Forms], rendering Windows Forms controls
- user controls [Windows Forms], painting
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a5b178ba-610e-46c4-a6c0-509c0886a744
ms.openlocfilehash: 558600c9256f205598288f9e20d38cb94608c920
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348487"
---
# <a name="rendering-controls-with-visual-styles"></a>Rendu des contrôles avec les styles visuels
Le .NET Framework prend en charge pour le rendu des contrôles et d’autres utilisateurs de Windows les éléments d’interface (UI) à l’aide de styles visuels dans les systèmes d’exploitation qui les prennent en charge. Cette rubrique aborde les différents niveaux de prise en charge dans le .NET Framework pour le rendu des contrôles et autres éléments d’interface utilisateur avec le style visuel actuel du système d’exploitation.  
  
## <a name="rendering-classes-for-common-controls"></a>Classes de rendu pour les contrôles courants  
 Le rendu d’un contrôle fait référence au dessin de l’interface utilisateur d’un contrôle. L’espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> fournit la classe <xref:System.Windows.Forms.ControlPaint> pour le rendu de certains contrôles Windows Forms courants. Cependant, cette classe dessine des contrôles dans le style Windows classique, ce qui peut rendre difficile de maintenir cohérente une expérience de l’interface utilisateur quand des contrôles personnalisés sont dessinés dans des applications où les styles visuels sont activés.  
  
 Le .NET Framework 2.0 inclut des classes dans le <xref:System.Windows.Forms?displayProperty=nameWithType> espace de noms qui rendent les parties et les États de contrôles courants avec les styles visuels. Chacune de ces classes inclut des méthodes `static` permettant de dessiner le contrôle ou des parties du contrôle dans un état particulier avec le style visuel actuel du système d’exploitation.  
  
 Certaines de ces classes sont conçues pour dessiner le contrôle concerné, que les styles visuels soient ou non disponibles. Si les styles visuels sont activés, les membres de la classe dessinent le contrôle concerné avec des styles visuels ; si les styles visuels sont désactivés, les membres de la classe dessinent le contrôle dans le style Windows classique. Ces classes incluent :  
  
- <xref:System.Windows.Forms.ButtonRenderer>  
  
- <xref:System.Windows.Forms.CheckBoxRenderer>  
  
- <xref:System.Windows.Forms.GroupBoxRenderer>  
  
- <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Les autres classes peuvent dessiner seulement le contrôle concerné quand des styles visuels sont disponibles, et leurs membres génèrent une exception si les styles visuels sont désactivés. Ces classes incluent :  
  
- <xref:System.Windows.Forms.ComboBoxRenderer>  
  
- <xref:System.Windows.Forms.ProgressBarRenderer>  
  
- <xref:System.Windows.Forms.ScrollBarRenderer>  
  
- <xref:System.Windows.Forms.TabRenderer>  
  
- <xref:System.Windows.Forms.TextBoxRenderer>  
  
- <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Pour plus d’informations sur l’utilisation de ces classes pour dessiner un contrôle, consultez [Comment : Utiliser une classe de rendu des contrôles](how-to-use-a-control-rendering-class.md).  
  
## <a name="visual-style-element-and-rendering-classes"></a>Élément de style visuel et classes de rendu  
 L’espace de noms <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> inclut des classes qui peuvent être utilisées pour dessiner et obtenir des informations sur un contrôle ou un élément d’interface utilisateur qui est pris en charge par les styles visuels. Les contrôles pris en charge incluent des contrôles courants qui ont une classe de rendu dans l’espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> (voir la section précédente), ainsi que d’autres contrôles, comme des contrôles d’onglet et des contrôles rebar. Les autres éléments d’interface utilisateur pris en charge incluent les parties du menu **Démarrer** , la barre des tâches et la zone non cliente des fenêtres.  
  
 Les classes principales de l’espace de noms <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> sont <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> et <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> est une classe de base pour identifier tout contrôle ou élément d’interface utilisateur pris en charge par les styles visuels. En plus de <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> lui-même, l’espace de noms <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> inclut de nombreuses classes imbriquées de <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> avec des propriétés `static` qui retournent un <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> pour chaque état d’un contrôle, partie de contrôle ou autre élément d’interface pris en charge par des styles visuels.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> fournit les méthodes qui dessinent et obtiennent des informations sur chaque <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> défini par le style visuel actuel du système d’exploitation. Les informations qui peuvent être récupérées sur un élément sont sa taille par défaut, son type d’arrière-plan et ses définitions de couleur. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> encapsule les fonctionnalités de l’API des styles visuels (UxTheme) de la partie Windows Shell du Kit de développement Windows Platform SDK. Pour plus d’informations, consultez [activation des Styles visuels](/windows/desktop/controls/cookbook-overview).  
  
 Pour plus d’informations sur l’utilisation de <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> et <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>, consultez [Comment : Restituer un élément de Style visuel](how-to-render-a-visual-style-element.md).  
  
## <a name="enabling-visual-styles"></a>Activation des styles visuels  
 Pour activer des styles visuels dans une application écrite pour le .NET Framework version 1.0, les programmeurs doivent inclure un manifeste d’application qui spécifie que ComCtl32.dll version 6 ou version ultérieure doit être utilisée pour dessiner les contrôles. Les applications générées avec le .NET Framework version 1.1 ou ultérieure peuvent utiliser le <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> méthode de la <xref:System.Windows.Forms.Application> classe.  
  
## <a name="checking-for-visual-styles-support"></a>Vérification de la prise en charge des styles visuels  
 La propriété <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> de la classe <xref:System.Windows.Forms.Application> indique si l’application actuelle dessine des contrôles avec les styles visuels. Quand vous dessinez un contrôle personnalisé, vous pouvez vérifier la valeur de <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> pour déterminer si vous devez rendre votre contrôle avec ou sans styles visuels. Le tableau suivant répertorie les quatre conditions qui doivent exister pour que <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> retourne `true`.  
  
|Condition|Notes|  
|---------------|-----------|  
|Le système d’exploitation prend en charge les styles visuels.|Pour vérifier cette condition séparément, utilisez la propriété <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> de la classe <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> .|  
|L’utilisateur a activé des styles visuels dans le système d’exploitation.|Pour vérifier cette condition séparément, utilisez la propriété <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> de la classe <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> .|  
|Les styles visuels sont activés dans l’application.|Les styles visuels peuvent être activés dans une application en appelant la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> ou un utilisant un manifeste d’application qui spécifie que ComCtl32.dll version 6 ou ultérieure doit être utilisé pour dessiner les contrôles.|  
|Les styles visuels sont utilisés pour dessiner la zone cliente des fenêtres d’application.|Pour vérifier cette condition séparément, utilisez la propriété <xref:System.Windows.Forms.Application.VisualStyleState%2A> de la classe <xref:System.Windows.Forms.Application>, et vérifiez qu’elle a la valeur <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType><xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>.|  
  
 Pour déterminer quand un utilisateur active ou désactive les styles visuels ou bascule d’un style visuel à un autre, recherchez la valeur de <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> dans les gestionnaires pour les événements <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> ou <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> .  
  
> [!IMPORTANT]
>  Si vous voulez utiliser <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> pour restituer un contrôle ou un élément d’interface utilisateur quand l’utilisateur active ou change les styles visuels, faites cela lors du traitement de l’événement <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> et non pas de l’événement <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> . Une exception est générée si vous utilisez la classe <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> lors du traitement de <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>.  
  
## <a name="see-also"></a>Voir aussi

- [Dessin et rendu personnalisés des contrôles](custom-control-painting-and-rendering.md)
