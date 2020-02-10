---
title: Mise en forme de texte avancée
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
ms.openlocfilehash: 26ee3c2b8a431200c3dc04130deb2247b6c1446d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095240"
---
# <a name="advanced-text-formatting"></a>Mise en forme de texte avancée
Windows Presentation Foundation (WPF) fournit un ensemble d’API robuste pour inclure du texte dans votre application. Les API de mise en page et de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], telles que les <xref:System.Windows.Controls.TextBlock>, fournissent les éléments les plus courants et les plus généraux pour la présentation de texte. Les API de dessin, telles que <xref:System.Windows.Media.GlyphRunDrawing> et <xref:System.Windows.Media.FormattedText>, permettent d’inclure du texte mis en forme dans des dessins. Au niveau le plus avancé, WPF fournit un moteur de mise en forme du texte extensible pour contrôler tous les aspects de la présentation du texte, tels que la gestion du magasin de texte, la gestion de la mise en forme du texte et la gestion des objets incorporés.  
  
 Cette rubrique fournit une introduction à la mise en forme du texte WPF. Il se concentre sur l’implémentation du client et l’utilisation du moteur de mise en forme du texte WPF.  
  
> [!NOTE]
> Tous les exemples de code de ce document se trouvent dans l' [exemple de mise en forme de texte avancée](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI/TextFormatting).  

<a name="prereq"></a>   
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique suppose que vous êtes familiarisé avec les API de niveau supérieur utilisées pour la présentation de texte. La plupart des scénarios utilisateur ne nécessitent pas les API de mise en forme de texte avancées présentées dans cette rubrique. Pour obtenir une présentation des différentes API Text, consultez [documents dans WPF](documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Mise en forme de texte avancée  
 La disposition du texte et les contrôles de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans WPF fournissent des propriétés de mise en forme qui vous permettent d’inclure facilement du texte mis en forme dans votre application. Ces contrôles exposent un certain nombre de propriétés permettant de gérer la présentation du texte, ce qui inclut sa police, sa taille et sa couleur. Normalement, ces contrôles peuvent gérer la majorité de la présentation du texte dans votre application. Toutefois, certains scénarios avancés nécessitent le contrôle du stockage de texte, ainsi que sa présentation. WPF fournit un moteur de mise en forme de texte extensible à cet effet.  
  
 Les fonctionnalités avancées de mise en forme du texte qui se trouvent dans WPF consistent en un moteur de mise en forme du texte, un magasin de texte, des séquences de texte et des propriétés de mise en forme. Le moteur de mise en forme du texte, <xref:System.Windows.Media.TextFormatting.TextFormatter>, crée des lignes de texte à utiliser pour la présentation. Pour ce faire, vous devez lancer le processus de mise en forme de ligne et appeler le <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>du formateur de texte. Le formateur de texte récupère les séquences de texte de votre magasin de texte en appelant la méthode de <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> du magasin. Les objets <xref:System.Windows.Media.TextFormatting.TextRun> sont ensuite formés en <xref:System.Windows.Media.TextFormatting.TextLine> objets par le formateur de texte et donnés à votre application à des fins d’inspection ou d’affichage.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Utilisation du formateur de texte  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> est le moteur de mise en forme du texte WPF et fournit des services pour la mise en forme et l’interruption des lignes de texte. Le formateur de texte peut gérer différents formats de caractères alphabétiques et prend en charge la présentation du texte international.  
  
 Contrairement à une API texte traditionnelle, le <xref:System.Windows.Media.TextFormatting.TextFormatter> interagit avec un client de disposition de texte par le biais d’un ensemble de méthodes de rappel. Elle requiert que le client fournisse ces méthodes dans une implémentation de la classe <xref:System.Windows.Media.TextFormatting.TextSource>. Le diagramme suivant illustre l’interaction de la disposition du texte entre l’application cliente et <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagramme du client de disposition du texte et TextFormatter](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Le formateur de texte est utilisé pour récupérer des lignes de texte mises en forme à partir du magasin de texte, qui est une implémentation de <xref:System.Windows.Media.TextFormatting.TextSource>. Pour ce faire, vous devez d’abord créer une instance du formateur de texte à l’aide de la méthode <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A>. Cette méthode crée une instance du formateur de texte et définit la hauteur et la largeur de ligne maximales. Dès qu’une instance du formateur de texte est créée, le processus de création de ligne est lancé en appelant la méthode <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. <xref:System.Windows.Media.TextFormatting.TextFormatter> rappelle la source de texte pour récupérer le texte et les paramètres de mise en forme pour les exécutions de texte qui forment une ligne.  
  
 L’exemple suivant illustre le processus de mise en forme d’un magasin de texte. L’objet <xref:System.Windows.Media.TextFormatting.TextFormatter> est utilisé pour récupérer des lignes de texte du magasin de texte, puis mettre en forme la ligne de texte pour dessiner dans le <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implémentation du magasin de texte client  
 Quand vous étendez le moteur de mise en forme du texte, vous devez implémenter et gérer tous les aspects du magasin de texte. Cela n’est pas une tâche facile. Le magasin de texte est chargé de suivre les propriétés de séquence de texte, les propriétés de paragraphe, les objets incorporés et tout autre contenu similaire. Il fournit également le formateur de texte avec des objets <xref:System.Windows.Media.TextFormatting.TextRun> individuels que le formateur de texte utilise pour créer des objets <xref:System.Windows.Media.TextFormatting.TextLine>.  
  
 Pour gérer la virtualisation du magasin de texte, le magasin de texte doit être dérivé de <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource> définit la méthode utilisée par le formateur de texte pour récupérer les séquences de texte du magasin de texte. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> est la méthode utilisée par le formateur de texte pour récupérer les séquences de texte utilisées dans la mise en forme de ligne. L’appel à <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> est effectué de façon répétée par le formateur de texte jusqu’à ce que l’une des conditions suivantes se produise :  
  
- Une <xref:System.Windows.Media.TextFormatting.TextEndOfLine> ou une sous-classe est retournée.  
  
- La largeur cumulée des séquences de texte dépasse la largeur de ligne maximale spécifiée dans l’appel pour créer le formateur de texte ou l’appel à la méthode <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> du formateur de texte.  
  
- Une séquence de saut de ligne Unicode, telle que « CF », « LF » ou « CRLF », est retournée.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Fourniture des séquences de texte  
 Le cœur du processus de mise en forme du texte est l’interaction entre le formateur de texte et le magasin de texte. Votre implémentation de <xref:System.Windows.Media.TextFormatting.TextSource> fournit le formateur de texte avec les objets <xref:System.Windows.Media.TextFormatting.TextRun> et les propriétés avec lesquelles mettre en forme les séquences de texte. Cette interaction est gérée par la méthode <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>, qui est appelée par le formateur de texte.  
  
 Le tableau suivant présente certains des objets <xref:System.Windows.Media.TextFormatting.TextRun> prédéfinis.  
  
|Type TextRun|Usage|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Séquence de texte spécialisée utilisée pour passer une représentation des glyphes de caractères au formateur de texte.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Séquence de texte spécialisée utilisée pour fournir du contenu dont la mesure, le test de positionnement et le dessin sont effectués globalement, par exemple un bouton ou une image dans le texte.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Séquence de texte spécialisée utilisée pour marquer la fin d’une ligne.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Séquence de texte spécialisée utilisée pour marquer la fin d’un paragraphe.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Séquence de texte spécialisée utilisée pour marquer la fin d’un segment, par exemple pour terminer l’étendue affectée par une exécution de <xref:System.Windows.Media.TextFormatting.TextModifier> précédente.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Séquence de texte spécialisée utilisée pour marquer une plage de caractères masqués.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Séquence de texte spécialisée utilisée pour modifier les propriétés des séquences de texte dans sa portée. La portée s’étend à la prochaine <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> de la séquence de texte correspondante, ou à la <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>suivante.|  
  
 L’un des objets <xref:System.Windows.Media.TextFormatting.TextRun> prédéfinis peut être sous-classé. Cela permet à votre source de texte de fournir au formateur de texte des séquences de texte qui incluent des données personnalisées.  
  
 L’exemple suivant illustre une méthode <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>. Ce magasin de texte retourne <xref:System.Windows.Media.TextFormatting.TextRun> objets au formateur de texte pour traitement.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> Dans cet exemple, le magasin de texte fournit les mêmes propriétés de texte à l’ensemble du texte. Les magasins de texte avancés doivent implémenter leur propre gestion de plage pour que les caractères individuels aient des propriétés distinctes.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Spécification des propriétés de mise en forme  
 les objets <xref:System.Windows.Media.TextFormatting.TextRun> sont mis en forme à l’aide des propriétés fournies par le magasin de texte. Ces propriétés sont de deux types : <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> et <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> gérer les propriétés inclusives des paragraphes, comme <xref:System.Windows.TextAlignment> et <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties> sont des propriétés qui peuvent être différentes pour chaque séquence de texte dans un paragraphe, telles que le pinceau de premier plan, les <xref:System.Windows.Media.Typeface>et la taille de police. Pour implémenter des types de propriétés de paragraphe personnalisé et de séquence de texte personnalisée, votre application doit créer des classes qui dérivent de <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> et <xref:System.Windows.Media.TextFormatting.TextRunProperties> respectivement.  
  
## <a name="see-also"></a>Voir aussi

- [Typographie dans WPF](typography-in-wpf.md)
- [Documents dans WPF](documents-in-wpf.md)
