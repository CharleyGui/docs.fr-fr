---
title: Documents dans WPF
ms.date: 03/30/2017
helpviewer_keywords:
- documents [WPF], packaging
- documents [WPF], text layout
- documents [WPF], XPS
- 'XPS documents [WPF], , '
- documents [WPF], controls
- documents [WPF], types of
- documents [WPF], browser-viewable
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
ms.openlocfilehash: b83d9c972dbdadb721bae8b7d616c94a0c1c831f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804742"
---
# <a name="documents-in-wpf"></a>Documents dans WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre une large gamme de fonctionnalités liées aux documents qui permettent de créer du contenu haute fidélité conçu pour être accessible et lu plus facilement que sur les générations précédentes de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. En plus d’une amélioration des capacités et de la qualité, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit également des services intégrés pour l’affichage, le packaging et la sécurité des documents. Cette rubrique fournit une introduction aux types et au packaging des documents [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="types_of_documents"></a>   
## <a name="types-of-documents"></a>Types de documents  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] divise les documents en deux grandes catégories basées sur leur utilisation prévue. Ces catégories de documents sont appelées "documents fixes" et "documents dynamiques".  
  
 Les documents fixes sont prévus pour les applications qui requièrent une présentation [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] précise, indépendamment du matériel d’affichage ou d’impression utilisé. Les documents fixes sont principalement utilisés pour la PAO (Publication Assistée par Ordinateur), le traitement de texte et la présentation d’un formulaire, où le respect de la conception de la page d’origine est essentiel. Dans le cadre de sa disposition, un document fixe conserve l’emplacement précis des éléments de contenu, indépendamment de l’écran d’affichage ou de l’appareil d’impression utilisé. Par exemple, une page de document fixe affichée en 96 ppp (points par pouce) apparaît de la même manière que lorsqu’elle est imprimée sur une imprimante laser 600 ppp ou une photocomposeuse 4800 ppp. Dans tous les cas, la disposition de la page reste la même, tandis que la qualité du document s’optimise selon les capacités de chaque appareil.  
  
 En comparaison, les documents dynamiques sont conçus pour optimiser l’affichage et la lisibilité. Ils trouvent leur meilleure exploitation quand la facilité de lecture est le scénario principal d’utilisation du document. Au lieu d’avoir une disposition prédéfinie, ces documents dynamiques ajustent et refluent dynamiquement leur contenu en fonction des variables d’exécution telles que la taille de la fenêtre, la résolution de l’appareil et les préférences facultatives de l’utilisateur. Une page web est un exemple simple de document dynamique où le contenu est mis en forme dynamiquement pour s’adapter à la fenêtre active. Les documents dynamiques optimisent l’expérience d’affichage et de lecture de l’utilisateur, en fonction de l’environnement d’exécution. Par exemple, le même document dynamique se remet en forme dynamiquement pour une lisibilité optimale sur un écran haute résolution de 19 pouces ou un petit écran de PDA de 2x3 pouces. En outre, les documents dynamiques possèdent plusieurs fonctionnalités intégrées, notamment la recherche, les modes d’affichage qui optimisent la lisibilité et la possibilité de changer la taille et l’apparence des polices.  Pour obtenir des illustrations, des exemples et des informations complètes sur les documents dynamiques, consultez [Vue d’ensemble des documents dynamiques](flow-document-overview.md).  
  
<a name="document_viewer"></a>   
## <a name="document-controls-and-text-layout"></a>Contrôles de document et disposition du texte  
 Le .NET Framework fournit un ensemble de contrôles prédéfinis qui simplifient l’utilisation de documents fixes, dynamiques et documents texte dans votre application.  L’affichage du contenu de document fixe est pris en charge à l’aide de la <xref:System.Windows.Controls.DocumentViewer> contrôle.  Affichage du contenu de document dynamique est pris en charge par trois contrôles différents : <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, et <xref:System.Windows.Controls.FlowDocumentScrollViewer> correspondent à différents scénarios utilisateur (voir les sections ci-dessous).  D’autres contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournissent une disposition simplifiée pour la prise en charge des utilisations générales de texte (voir [Texte dans l’interface utilisateur](#text_in_the_user_interface), ci-dessous).  
  
### <a name="fixed-document-control---documentviewer"></a>Contrôle de document fixe - DocumentViewer  
 Le <xref:System.Windows.Controls.DocumentViewer> contrôle est conçu pour afficher <xref:System.Windows.Documents.FixedDocument> contenu. Le <xref:System.Windows.Controls.DocumentViewer> contrôle fournit une interface utilisateur intuitive qui fournit la prise en charge intégrée pour les opérations courantes telles que la sortie imprimée, copiez dans le Presse-papiers, le zoom et les fonctionnalités de recherche de texte. Le contrôle permet d’accéder aux pages de contenu par le biais d’un mécanisme de défilement familier. Comme tous les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôles, <xref:System.Windows.Controls.DocumentViewer> prend en charge la modification complète ou partielle du style, ce qui permet le contrôle d’être intégré visuellement dans pratiquement n’importe quelle application ou d’un environnement.  
  
 <xref:System.Windows.Controls.DocumentViewer> est conçu pour afficher le contenu d’une manière en lecture seule ; modification ou la modification de contenu n’est pas disponible et n’est pas pris en charge.  
  
<a name="flow_document"></a>   
### <a name="flow-document-controls"></a>Contrôles de document dynamique  

> [!NOTE]
>  Pour plus d’informations sur les fonctionnalités de document de flux et comment les créer, consultez [vue d’ensemble du Document de flux](flow-document-overview.md).  
  
 Affichage du contenu de document dynamique est pris en charge par trois contrôles : <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, et <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> inclut des fonctionnalités qui permettent aux utilisateurs de choisir dynamiquement entre plusieurs modes d’affichage, y compris un mode d’affichage de page unique (page-à-un-time), un deux-page-à-à la fois (format livre) un mode de défilement continu (sans marge inférieure) et du mode d’affichage.  Pour plus d’informations sur ces modes d’affichage, consultez <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Si vous n’avez pas besoin de la possibilité de basculer dynamiquement entre les différents modes d’affichage, <xref:System.Windows.Controls.FlowDocumentPageViewer> et <xref:System.Windows.Controls.FlowDocumentScrollViewer> fournissent les flux légère afficheurs de contenu qui sont résolus dans un mode d’affichage particulier.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer et FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> Affiche le contenu dans la page au moment mode d’affichage, tandis que <xref:System.Windows.Controls.FlowDocumentScrollViewer> affiche le contenu en mode de défilement continu.  Les deux <xref:System.Windows.Controls.FlowDocumentPageViewer> et <xref:System.Windows.Controls.FlowDocumentScrollViewer> ont été corrigés pour un mode d’affichage particulier. Comparer à <xref:System.Windows.Controls.FlowDocumentReader>, inclut des fonctionnalités qui permettent à l’utilisateur de choisir dynamiquement entre plusieurs modes d’affichage (tel que fourni par le <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> énumération), mais qui en plus de ressources que <xref:System.Windows.Controls.FlowDocumentPageViewer> ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Par défaut, une barre de défilement verticale est toujours affichée et une barre de défilement horizontale apparaît si nécessaire. La valeur par défaut [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour <xref:System.Windows.Controls.FlowDocumentScrollViewer> n’inclut pas d’une barre d’outils ; Toutefois, le <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> propriété peut être utilisée pour activer une barre d’outils intégrée.  
  
<a name="text_in_the_user_interface"></a>   
### <a name="text-in-the-user-interface"></a>Texte dans l’interface utilisateur  
 En plus d’ajouter du texte à des documents, vous pouvez bien évidemment utiliser du texte dans l’interface utilisateur de l’application, notamment dans des formulaires. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut plusieurs contrôles pour dessiner le texte à l’écran. Chaque contrôle cible un scénario différent et dispose de sa propre liste de fonctionnalités et limitations. En règle générale, le <xref:System.Windows.Controls.TextBlock> élément doit être utilisé lors de la prise en charge de texte limitée est requis, par exemple, une courte phrase dans un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> peut être utilisé lors de la prise en charge de texte minimale est requise. Pour plus d’informations, consultez [Vue d’ensemble de TextBlock](../controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## <a name="document-packaging"></a>Packaging de documents  
 Le <xref:System.IO.Packaging> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] offrent un moyen efficace pour organiser les données d’application et les ressources associées dans un conteneur unique facile d’accès, portable et facile à distribuer du contenu du document. Un fichier ZIP est un exemple d’un <xref:System.IO.Packaging.Package> type capable de contenir plusieurs objets dans une seule unité. L’empaquetage [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] fournir une valeur par défaut <xref:System.IO.Packaging.ZipPackage> implémentation conçue à l’aide d’une norme Open Packaging Conventions avec une architecture de fichiers XML et ZIP. Les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] de packaging [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simplifient la création de packages, ainsi que le stockage et l’accès aux objets s’y trouvant. Un objet stocké dans un <xref:System.IO.Packaging.Package> est appelé un <xref:System.IO.Packaging.PackagePart> (« partie »). Les packages peuvent également inclure des certificats numériques signés pouvant être utilisés pour identifier le créateur d’une partie, et pour valider que le contenu d’un package n’a pas été modifié.  Les packages comprennent également une <xref:System.IO.Packaging.PackageRelationship> fonctionnalité qui permet d’obtenir des informations supplémentaires à ajouter à un package ou associés à des parties spécifiques sans modifier réellement le contenu des parties existantes.  Les services de package prennent aussi en charge [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)].  
  
 L’architecture de package [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sert de base à de nombreuses technologies clés :  
  
- [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]Documents XPS conformes au type [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)].  
  
- Documents au format Microsoft Office "12" Open XML (.docx).  
  
- Formats de stockage personnalisés pour la conception de vos propres applications.  
  
 Basé sur les API, d’empaquetage un <xref:System.Windows.Xps.Packaging.XpsDocument> est spécialement conçu pour stocker [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contenu de documents fixes. Un <xref:System.Windows.Xps.Packaging.XpsDocument> est un document autonome qui peut être ouvert dans une visionneuse, affichée dans un <xref:System.Windows.Controls.DocumentViewer> contrôle, routé vers un spool d’impression ou envoyé directement à un [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-imprimante compatible.  
  
 Les sections suivantes fournissent des informations supplémentaires sur le <xref:System.IO.Packaging.Package> et <xref:System.Windows.Xps.Packaging.XpsDocument> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] fourni avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### <a name="package-components"></a>Composants d’un package  
 Les API de packaging [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permettent d’organiser les données et documents d’une application en une seule unité portable. Un fichier ZIP est l’un des types de package les plus courants. Il s’agit du type de package par défaut fourni avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package> lui-même est une classe abstraite à partir de laquelle <xref:System.IO.Packaging.ZipPackage> est implémenté à l’aide d’une architecture de fichiers ZIP et XML standard ouverte.  Le <xref:System.IO.Packaging.Package.Open%2A> méthode utilise <xref:System.IO.Packaging.ZipPackage> pour créer et utiliser des fichiers ZIP par défaut. Un package peut contenir trois types d’éléments de base :  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Contenu d’application, données, documents et fichiers de ressources.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|Certificat X.509 pour l’identification, l’authentification et la validation.|  
|<xref:System.IO.Packaging.PackageRelationship>|Informations ajoutées relatives au package ou à une partie spécifique.|  
  
<a name="PackageParts"></a>   
#### <a name="packageparts"></a>PackageParts  
 Un <xref:System.IO.Packaging.PackagePart> (« partie ») est une classe abstraite qui fait référence à un objet stocké dans un <xref:System.IO.Packaging.Package>. Dans un fichier ZIP, les parties du package correspondent aux fichiers individuels stockés qu’il contient.  <xref:System.IO.Packaging.ZipPackagePart> fournit l’implémentation par défaut pour les objets sérialisables stockés dans un <xref:System.IO.Packaging.ZipPackage>.  Comme pour un système de fichiers, les parties contenues dans le package sont stockées dans des répertoires hiérarchiques ou sous forme de dossiers.  À l’aide de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API de packaging, applications peuvent écrire, stocker et lire plusieurs <xref:System.IO.Packaging.PackagePart> objets à l’aide d’un seul conteneur de fichier ZIP.  
  
<a name="PackageDigitalSignatures"></a>   
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Pour la sécurité, un <xref:System.IO.Packaging.PackageDigitalSignature> (« signature numérique ») peut être associé à des parties d’un package. Un <xref:System.IO.Packaging.PackageDigitalSignature> intègre un [509] qui fournit deux fonctionnalités :  
  
1. Identifie et authentifie le créateur de la partie.  
  
2. Vérifie que la partie n’a pas été modifiée.  
  
 La signature numérique n’empêche pas la modification d’une partie, mais un contrôle de validation par rapport à la signature numérique échoue si la partie est modifiée d’une façon ou d’une autre. L’application peut alors exécuter l’action appropriée : par exemple, bloquer l’ouverture de la partie, ou notifier l’utilisateur que la partie a été modifiée et n’est pas sécurisée.  
  
<a name="PackageRelationships"></a>   
#### <a name="packagerelationships"></a>PackageRelationships  
 Un <xref:System.IO.Packaging.PackageRelationship> (« relation ») fournit un mécanisme permettant d’associer des informations supplémentaires avec le package ou une partie du package. Une relation est une fonctionnalité de package qui peut associer des informations supplémentaires à une partie sans en modifier le contenu actuel. L’insertion directe de nouvelles données dans le contenu de la partie n’est généralement pas très pratique dans de nombreux cas :  
  
- Le type réel de la partie et son schéma de contenu ne sont pas connus.  
  
- Même s’il est connu, le schéma de contenu peut ne pas fournir de moyen d’ajouter de nouvelles informations.  
  
- La partie peut être chiffrée ou signée numériquement, empêchant toute modification.  
  
 Les relations de package fournissent un moyen détectable d’ajouter et d’associer des informations supplémentaires à des parties individuelles ou à l’ensemble du package. Les relations de package sont utilisées pour deux fonctions principales :  
  
1. Définition des relations de dépendance d’une partie à l’autre.  
  
2. Définition des relations d’information qui ajoutent des notes ou d’autres données relatives à la partie.  
  
 Un <xref:System.IO.Packaging.PackageRelationship> fournit un moyen rapide et détectable de définir des dépendances et ajouter d’autres informations associées à une partie du package ou le package dans sa globalité.  
  
<a name="Dependency_Relationships"></a>   
##### <a name="dependency-relationships"></a>Relations de dépendance  
 Les relations de dépendance sont utilisées pour décrire les dépendances qu’une partie crée sur d’autres parties. Par exemple, un package peut contenir une partie HTML comprenant une ou plusieurs balises d’image \<img>. Les balises d’image font référence à des images situées sur d’autres parties internes au package ou externes au package (comme celles accessibles sur Internet). Création d’un <xref:System.IO.Packaging.PackageRelationship> associé facilite la fichier HTML découverte et l’accès à des ressources dépendantes simples et rapides. Une application de navigateur ou de visionneuse peut accéder directement aux relations de parties et commencer immédiatement l’assemblage des ressources dépendantes sans connaître le schéma ou analyser le document.  
  
<a name="Information_Relationships"></a>   
##### <a name="information-relationships"></a>Relations d’informations  
 Similaire à une remarque ou une annotation, un <xref:System.IO.Packaging.PackageRelationship> peut également être utilisé pour stocker d’autres types d’informations à associer à une partie sans avoir à modifier réellement le contenu de la partie.  
  
<a name="XPS_Documents"></a>   
## <a name="xps-documents"></a>Documents XPS  
 Un document [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] est un package qui contient un ou plusieurs documents fixes, ainsi que toutes les ressources et informations nécessaires pour le rendu.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] est également le format de fichier de spool d’impression [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] natif.  Un <xref:System.Windows.Xps.Packaging.XpsDocument> est stocké dans le dataset ZIP standard et peut inclure une combinaison de composants XML et binaires, tels que les fichiers image et de police. Des [PackageRelationships](#PackageRelationships) sont utilisés pour définir les dépendances entre le contenu et les ressources nécessaires pour afficher le document.  Le <xref:System.Windows.Xps.Packaging.XpsDocument> conception fournit une solution de haute fidélité de document unique prenant en charge plusieurs utilisations :  
  
- Lecture, écriture et stockage de ressources et de contenu de document fixe sous la forme d’un fichier unique, portable et facile à distribuer.  
  
- Affichage de documents avec l’application Visionneuse [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
- Sortie de documents au format de sortie de spool d’impression natif de [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  
  
- Routage direct de documents vers une imprimante compatible avec le format [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Text](optimizing-performance-text.md)
- [Vue d’ensemble des documents dynamiques](flow-document-overview.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
- [Sérialisation et stockage de documents](document-serialization-and-storage.md)
