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
ms.openlocfilehash: 433fee08d44720640d3f9d1bf2511a6a267eb58e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145460"
---
# <a name="annotations-overview"></a>Vue d'ensemble des annotations
Écrire des notes ou des commentaires sur des documents papier est une activité si banale que nous pensons qu’elle va de soi. Ces notes ou commentaires sont des « annotations » que nous ajoutons à un document pour marquer des informations ou mettre en évidence des éléments présentant un intérêt particulier afin de nous y référer plus tard. Bien que la rédaction de notes sur des documents imprimés soit une tâche simple et banale, la possibilité d’ajouter des commentaires personnels à des documents électroniques, quand cette fonctionnalité est disponible, est généralement très limitée.  
  
 Ce sujet passe en revue plusieurs types courants d’annotations, en particulier des notes collantes et des faits saillants, et illustre comment le cadre Microsoft Annotations facilite ces types d’annotations dans les applications par l’intermédiaire de la Fondation de présentation Windows (WPF ) contrôles d’affichage des documents.  Les contrôles d’affichage des documents <xref:System.Windows.Controls.FlowDocumentReader> WPF qui prennent en charge les annotations comprennent <xref:System.Windows.Controls.FlowDocumentScrollViewer>et, ainsi que les contrôles dérivés de <xref:System.Windows.Controls.Primitives.DocumentViewerBase> tels que <xref:System.Windows.Controls.DocumentViewer> et <xref:System.Windows.Controls.FlowDocumentPageViewer>.  

<a name="caf1_type_stickynotes"></a>
## <a name="sticky-notes"></a>Pense-bêtes  
 Un pense-bête classique contient des informations écrites sur un petit bout de papier de couleur, « collé » ensuite sur un document. Les notes collantes numériques offrent des fonctionnalités similaires pour les documents électroniques, mais avec la flexibilité supplémentaire d’inclure de nombreux autres types de contenu tels que le texte dactylographié, les notes manuscrites (par exemple, Tablet PC "encre" coups), ou des liens Web.  
  
 L’illustration suivante montre quelques exemples d’annotations sous forme de mises en surbrillance, de pense-bêtes ou de notes manuscrites.  
  
 ![Annotations pense-bête manuscrites et texte en surbrillance](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 L’exemple suivant illustre la méthode que vous pouvez utiliser pour activer la prise en charge des annotations dans votre application.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>
## <a name="highlights"></a>Points forts  
 Nous utilisons diverses méthodes créatives pour attirer l’attention sur des éléments présentant un intérêt particulier sur un document papier, par exemple en soulignant, en surlignant ou en encerclant des mots dans une phrase, ou en mettant des marques ou des annotations dans la marge.  Les annotations de mise en évidence dans le cadre d’annotations Microsoft fournissent une fonctionnalité similaire pour marquer les informations affichées dans les contrôles de visualisation des documents WPF.  
  
 L’illustration suivante montre un exemple d’annotation en surbrillance.  
  
 ![Annotation en surbrillance](./media/caf-callouts.png "CAF_Callouts")  
  
 Les utilisateurs créent généralement des annotations en sélectionnant d’abord un texte <xref:System.Windows.Controls.ContextMenu> ou un élément d’intérêt, puis en cliquant à droite pour afficher une option d’annotation.  L’exemple suivant [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] montre que vous <xref:System.Windows.Controls.ContextMenu> pouvez utiliser pour déclarer un avec des commandes acheminées que les utilisateurs peuvent accéder pour créer et gérer les annotations.  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>
## <a name="data-anchoring"></a>Ancrage des données  
 Le Cadre d’annotations lie les annotations aux données que l’utilisateur sélectionne, et pas seulement à une position sur la vue d’affichage. Ainsi, en cas de changement de l’affichage du document, par exemple si l’utilisateur fait défiler ou redimensionne la fenêtre d’affichage, l’annotation suit la sélection de données à laquelle elle est liée. Le graphique suivant illustre une annotation que l’utilisateur a faite sur une sélection de texte. En cas de changement de l’affichage du document (défilements, redimensionnements, mises à l’échelle ou tout autre type de déplacement), l’annotation en surbrillance se déplace avec la sélection de données d’origine.  
  
 ![Ancrage des données de l'annotation](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>
## <a name="matching-annotations-with-annotated-objects"></a>Mise en correspondance des annotations avec les objets annotés  
 Vous pouvez faire correspondre des annotations aux objets annotés associés. Par exemple, imaginez une simple application de lecture de document comportant un volet de commentaires. Le volet de commentaires peut être une zone de liste qui affiche le texte à partir d’une liste d’annotations ancrées à un document. Si l’utilisateur sélectionne un élément dans la zone de liste, l’application affiche le paragraphe du document auquel l’objet d’annotation correspondant est ancré.  
  
 L’exemple ci-dessous montre comment implémenter le gestionnaire d’événements de ce type de zone de liste pour servir de volet de commentaires.  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Un autre exemple de scénario implique des applications qui permettent l’échange d’annotations et de notes collantes entre lecteurs de documents par e-mail. Grâce à cette fonctionnalité, les applications peuvent amener le lecteur à la page qui contient l’annotation échangée.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [Schéma d'annotations](annotations-schema.md)
- [Vue d'ensemble de ContextMenu](../controls/contextmenu-overview.md)
- [Vue d’ensemble des commandes](commanding-overview.md)
- [Vue d’ensemble des documents dynamiques](flow-document-overview.md)
- [Guide pratique pour ajouter une commande à un MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
