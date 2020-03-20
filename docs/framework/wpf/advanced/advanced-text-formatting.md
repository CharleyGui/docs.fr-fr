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
ms.openlocfilehash: 745d20e0bd4f877f9d4559f9fc7829b56689d35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185939"
---
# <a name="advanced-text-formatting"></a>Mise en forme de texte avancée
Windows Presentation Foundation (WPF) fournit un ensemble robuste d’API pour inclure le texte dans votre application. La [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mise en page <xref:System.Windows.Controls.TextBlock>et les API, telles que , fournissent les éléments les plus courants et à usage général pour la présentation de texte. Dessiner des API, tels que <xref:System.Windows.Media.GlyphRunDrawing> et <xref:System.Windows.Media.FormattedText>, fournir un moyen d’inclure le texte formaté dans les dessins. Au niveau le plus avancé, WPF fournit un moteur de formatage de texte extensible pour contrôler tous les aspects de la présentation de texte, tels que la gestion de magasin de texte, la gestion du formatage d’exécution de texte, et la gestion intégrée des objets.  
  
 Ce sujet fournit une introduction au formatage de texte WPF. Il se concentre sur la mise en œuvre des clients et l’utilisation du moteur de formatage de texte WPF.  
  
> [!NOTE]
> Tous les exemples de code contenus dans ce document peuvent être trouvés dans [l’échantillon de formatage](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI/TextFormatting)de texte avancé .  

<a name="prereq"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Ce sujet suppose que vous êtes familier avec les API de niveau supérieur utilisés pour la présentation de texte. La plupart des scénarios d’utilisateurs ne nécessiteront pas les API de formatage de texte avancé discutés dans ce sujet. Pour une introduction aux différents textes API, voir [Documents en WPF](documents-in-wpf.md).  
  
<a name="section1"></a>
## <a name="advanced-text-formatting"></a>Mise en forme de texte avancée  
 La disposition [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] et les contrôles de texte dans WPF fournissent des propriétés de formatage qui vous permettent d’inclure facilement du texte formaté dans votre application. Ces contrôles exposent un certain nombre de propriétés permettant de gérer la présentation du texte, ce qui inclut sa police, sa taille et sa couleur. Normalement, ces contrôles peuvent gérer la majorité de la présentation du texte dans votre application. Toutefois, certains scénarios avancés nécessitent le contrôle du stockage de texte, ainsi que sa présentation. WPF fournit un moteur de formatage de texte extensible à cette fin.  
  
 Les fonctionnalités avancées de formatage de texte trouvées dans WPF se composent d’un moteur de formatage de texte, d’un magasin de texte, d’essais de texte et de propriétés de formatage. Le moteur de <xref:System.Windows.Media.TextFormatting.TextFormatter>formatage de texte, crée des lignes de texte à utiliser pour la présentation. Ceci est réalisé en initiant le processus de formatage de ligne et en appelant le formateur de <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>texte. Le formateur de texte récupère le texte de votre <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> magasin de texte en appelant la méthode du magasin. Les <xref:System.Windows.Media.TextFormatting.TextRun> objets sont <xref:System.Windows.Media.TextFormatting.TextLine> ensuite formés en objets par le formateur de texte et remis à votre application d’inspection ou d’affichage.  
  
<a name="section2"></a>
## <a name="using-the-text-formatter"></a>Utilisation du formateur de texte  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>est le moteur de formatage de texte WPF et fournit des services pour le formatage et la rupture des lignes de texte. Le formateur de texte peut gérer différents formats de caractères alphabétiques et prend en charge la présentation du texte international.  
  
 Contrairement à une API <xref:System.Windows.Media.TextFormatting.TextFormatter> texte traditionnelle, l’interaction avec un client de mise en page de texte à travers un ensemble de méthodes de rappel. Il exige du client qu’il fournisse ces méthodes dans le cas d’une mise en œuvre de la <xref:System.Windows.Media.TextFormatting.TextSource> classe. Le diagramme suivant illustre l’interaction de <xref:System.Windows.Media.TextFormatting.TextFormatter>mise en page de texte entre l’application client et .  
  
 ![Diagramme du client de disposition du texte et TextFormatter](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Le formateur de texte est utilisé pour récupérer les lignes de <xref:System.Windows.Media.TextFormatting.TextSource>texte formatées du magasin de texte, qui est une implémentation de . Cela se fait en créant d’abord un <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> exemple du formateur de texte en utilisant la méthode. Cette méthode crée une instance du formateur de texte et définit la hauteur et la largeur de ligne maximales. Dès qu’une instance du formateur de texte est créée, <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> le processus de création de ligne est commencé par appeler la méthode. <xref:System.Windows.Media.TextFormatting.TextFormatter>rappelle la source de texte pour récupérer le texte et les paramètres de formatage pour les exécutions de texte qui forment une ligne.  
  
 L’exemple suivant illustre le processus de mise en forme d’un magasin de texte. L’objet <xref:System.Windows.Media.TextFormatting.TextFormatter> est utilisé pour récupérer les lignes de texte de <xref:System.Windows.Media.DrawingContext>la boutique de texte, puis formater la ligne de texte pour dessiner dans le .  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>
## <a name="implementing-the-client-text-store"></a>Implémentation du magasin de texte client  
 Quand vous étendez le moteur de mise en forme du texte, vous devez implémenter et gérer tous les aspects du magasin de texte. Cela n’est pas une tâche facile. Le magasin de texte est chargé de suivre les propriétés de séquence de texte, les propriétés de paragraphe, les objets incorporés et tout autre contenu similaire. Il fournit également au formateur de texte des objets individuels <xref:System.Windows.Media.TextFormatting.TextRun> que le formateur de texte utilise pour créer des <xref:System.Windows.Media.TextFormatting.TextLine> objets.  
  
 Pour gérer la virtualisation du magasin de texte, <xref:System.Windows.Media.TextFormatting.TextSource>le magasin de texte doit être dérivé de . <xref:System.Windows.Media.TextFormatting.TextSource>définit la méthode utilisée par le formateur de texte pour récupérer les extraits de texte dans le magasin de texte. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>est la méthode utilisée par le formateur de texte pour récupérer les exécutions de texte utilisées dans le formatage en ligne. L’appel <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> à est fait à plusieurs reprises par le formateur de texte jusqu’à ce que l’une des conditions suivantes se produise:  
  
- Une <xref:System.Windows.Media.TextFormatting.TextEndOfLine> ou une sous-classe est retournée.  
  
- La largeur accumulée des flux de texte dépasse la largeur maximale de la ligne spécifiée dans <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> l’appel pour créer le formateur de texte ou l’appel à la méthode du formateur de texte.  
  
- Une séquence de nouvelle ligne Unicode, comme « CF », « LF » ou « CRLF », est retournée.  
  
<a name="section4"></a>
## <a name="providing-text-runs"></a>Fourniture des séquences de texte  
 Le cœur du processus de mise en forme du texte est l’interaction entre le formateur de texte et le magasin de texte. Votre implémentation fournit au formateur de <xref:System.Windows.Media.TextFormatting.TextSource> texte les <xref:System.Windows.Media.TextFormatting.TextRun> objets et les propriétés avec lesquelles formater le texte s’exécute. Cette interaction est gérée <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> par la méthode, qui est appelée par le formateur de texte.  
  
 Le tableau suivant montre certains des <xref:System.Windows.Media.TextFormatting.TextRun> objets prédéfinis.  
  
|Type TextRun|Usage|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Séquence de texte spécialisée utilisée pour passer une représentation des glyphes de caractères au formateur de texte.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Séquence de texte spécialisée utilisée pour fournir du contenu dont la mesure, le test de positionnement et le dessin sont effectués globalement, par exemple un bouton ou une image dans le texte.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Séquence de texte spécialisée utilisée pour marquer la fin d’une ligne.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Séquence de texte spécialisée utilisée pour marquer la fin d’un paragraphe.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Le texte spécialisé a été utilisé pour marquer la fin d’un <xref:System.Windows.Media.TextFormatting.TextModifier> segment, par exemple pour mettre fin à la portée affectée par une course précédente.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Séquence de texte spécialisée utilisée pour marquer une plage de caractères masqués.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Séquence de texte spécialisée utilisée pour modifier les propriétés des séquences de texte dans sa portée. La portée s’étend <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> à la prochaine <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>exécution de texte correspondant, ou la suivante .|  
  
 N’importe lequel des <xref:System.Windows.Media.TextFormatting.TextRun> objets prédéfinis peut être sous-classé. Cela permet à votre source de texte de fournir au formateur de texte des séquences de texte qui incluent des données personnalisées.  
  
 L’exemple suivant <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> montre une méthode. Ce magasin <xref:System.Windows.Media.TextFormatting.TextRun> de texte renvoie des objets au formateur de texte pour le traitement.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> Dans cet exemple, le magasin de texte fournit les mêmes propriétés de texte à l’ensemble du texte. Les magasins de texte avancés doivent implémenter leur propre gestion de plage pour que les caractères individuels aient des propriétés distinctes.  
  
<a name="section5"></a>
## <a name="specifying-formatting-properties"></a>Spécification des propriétés de mise en forme  
 <xref:System.Windows.Media.TextFormatting.TextRun>objets sont formatés en utilisant les propriétés fournies par le magasin de texte. Ces propriétés viennent <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> en <xref:System.Windows.Media.TextFormatting.TextRunProperties>deux types, et . <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>gérer les propriétés <xref:System.Windows.TextAlignment> <xref:System.Windows.FlowDirection>inclusives paragraphe telles que et . <xref:System.Windows.Media.TextFormatting.TextRunProperties>sont des propriétés qui peuvent être différentes pour chaque texte <xref:System.Windows.Media.Typeface>exécuté dans un paragraphe, tels que la brosse de premier plan, , et la taille de la police. Pour implémenter des types de propriétés personnalisées <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> de <xref:System.Windows.Media.TextFormatting.TextRunProperties> paragraphe et de texte personnalisé, votre application doit créer des classes qui dérivent et respectivement.  
  
## <a name="see-also"></a>Voir aussi

- [Typographie dans WPF](typography-in-wpf.md)
- [Documents dans WPF](documents-in-wpf.md)
