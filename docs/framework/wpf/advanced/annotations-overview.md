---
title: Vue d'ensemble des annotations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
ms.openlocfilehash: dc9c4125f9ac3c44be41efe92b9e495599e5c130
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004035"
---
# <a name="annotations-overview"></a>Vue d'ensemble des annotations
Écrire des notes ou des commentaires sur des documents papier est une activité si banale que nous pensons qu’elle va de soi. Ces notes ou commentaires sont des « annotations » que nous ajoutons à un document pour marquer des informations ou mettre en évidence des éléments présentant un intérêt particulier afin de nous y référer plus tard. Bien que la rédaction de notes sur des documents imprimés soit une tâche simple et banale, la possibilité d’ajouter des commentaires personnels à des documents électroniques, quand cette fonctionnalité est disponible, est généralement très limitée.  
  
 Cette rubrique passe en revue plusieurs types d’annotations courants, en particulier les pense-bêtes et les mises en évidence, et illustre comment l’infrastructure des annotations Microsoft facilite ces types d’annotations dans les applications via le Windows Presentation Foundation (WPF ) des contrôles d’affichage de document.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] les contrôles d’affichage de document qui prennent en charge les annotations incluent <xref:System.Windows.Controls.FlowDocumentReader> et <xref:System.Windows.Controls.FlowDocumentScrollViewer>, ainsi que des contrôles dérivés de <xref:System.Windows.Controls.Primitives.DocumentViewerBase>, tels que <xref:System.Windows.Controls.DocumentViewer> et <xref:System.Windows.Controls.FlowDocumentPageViewer>.  

<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>Pense-bêtes  
 Un pense-bête classique contient des informations écrites sur un petit bout de papier de couleur, « collé » ensuite sur un document. Les pense-bête numériques offrent des fonctionnalités similaires pour les documents électroniques, mais avec une flexibilité accrue pour inclure de nombreux autres types de contenu, tels que du texte tapé, des notes manuscrites (par exemple, des traits « encres » de Tablet PC) ou des liens Web.  
  
 L’illustration suivante montre quelques exemples d’annotations sous forme de mises en surbrillance, de pense-bêtes ou de notes manuscrites.  
  
 ![Pense-bêtes de type mise en surbrillance, note tapée et note manuscrite.](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 L’exemple suivant illustre la méthode que vous pouvez utiliser pour activer la prise en charge des annotations dans votre application.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>Mises en surbrillance  
 Nous utilisons diverses méthodes créatives pour attirer l’attention sur des éléments présentant un intérêt particulier sur un document papier, par exemple en soulignant, en surlignant ou en encerclant des mots dans une phrase, ou en mettant des marques ou des annotations dans la marge.  Les annotations en surbrillance dans Microsoft annotations Framework offrent une fonctionnalité similaire pour marquer les informations affichées dans les contrôles d’affichage de document [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 L’illustration suivante montre un exemple d’annotation en surbrillance.  
  
 ![Annotation en surbrillance](./media/caf-callouts.png "CAF_Callouts")  
  
 Les utilisateurs créent généralement des annotations en sélectionnant d’abord du texte ou un élément digne d’intérêt, puis en cliquant avec le bouton droit pour afficher un <xref:System.Windows.Controls.ContextMenu> des options d’annotation.  L’exemple suivant illustre la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que vous pouvez utiliser pour déclarer une <xref:System.Windows.Controls.ContextMenu> avec des commandes routées auxquelles les utilisateurs peuvent accéder pour créer et gérer des annotations.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>Ancrage des données  
 L’infrastructure des annotations lie les annotations aux données que l’utilisateur sélectionne, et pas seulement à une position sur l’affichage. Ainsi, en cas de changement de l’affichage du document, par exemple si l’utilisateur fait défiler ou redimensionne la fenêtre d’affichage, l’annotation suit la sélection de données à laquelle elle est liée. Le graphique suivant illustre une annotation que l’utilisateur a faite sur une sélection de texte. En cas de changement de l’affichage du document (défilements, redimensionnements, mises à l’échelle ou tout autre type de déplacement), l’annotation en surbrillance se déplace avec la sélection de données d’origine.  
  
 ![Ancrage des données d’annotation](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>Mise en correspondance des annotations avec les objets annotés  
 Vous pouvez faire correspondre des annotations aux objets annotés associés. Par exemple, imaginez une simple application de lecture de document comportant un volet de commentaires. Le volet de commentaires peut être une zone de liste qui affiche le texte à partir d’une liste d’annotations ancrées à un document. Si l’utilisateur sélectionne un élément dans la zone de liste, l’application affiche le paragraphe du document auquel l’objet d’annotation correspondant est ancré.  
  
 L’exemple ci-dessous montre comment implémenter le gestionnaire d’événements de ce type de zone de liste pour servir de volet de commentaires.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Un autre exemple de scénario concerne les applications qui permettent l’échange d’annotations et de pense-bête entre les lecteurs de document par courrier électronique. Grâce à cette fonctionnalité, les applications peuvent amener le lecteur à la page qui contient l’annotation échangée.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [Schéma d'annotations](annotations-schema.md)
- [Vue d’ensemble de ContextMenu](../controls/contextmenu-overview.md)
- [Vue d’ensemble des commandes](commanding-overview.md)
- [Vue d’ensemble des documents dynamiques](flow-document-overview.md)
- [Guide pratique pour Ajouter une commande à un MenuItem @ no__t-0
