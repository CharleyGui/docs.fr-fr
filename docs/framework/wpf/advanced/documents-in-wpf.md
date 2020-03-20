---
title: Documents
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
ms.openlocfilehash: e88604c42b253b48ee605f42f24fe301e339f74b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174678"
---
# <a name="documents-in-wpf"></a>Documents dans WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]offre un large éventail de fonctionnalités documentaires qui permettent la création de contenu haute fidélité qui est conçu pour être plus facilement accessible et lu que dans les générations précédentes de Windows. En plus d’une amélioration des capacités et de la qualité, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit également des services intégrés pour l’affichage, le packaging et la sécurité des documents. Cette rubrique fournit une introduction aux types et au packaging des documents [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="types_of_documents"></a>
## <a name="types-of-documents"></a>Types de documents  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] divise les documents en deux grandes catégories basées sur leur utilisation prévue. Ces catégories de documents sont appelées "documents fixes" et "documents dynamiques".  
  
 Les documents fixes sont destinés à des applications qui nécessitent une présentation précise « ce que vous voyez est ce que vous obtenez » (WYSIWYG), indépendamment du matériel d’affichage ou d’imprimante utilisé. Les documents fixes sont principalement utilisés pour la PAO (Publication Assistée par Ordinateur), le traitement de texte et la présentation d’un formulaire, où le respect de la conception de la page d’origine est essentiel. Dans le cadre de sa disposition, un document fixe conserve l’emplacement précis des éléments de contenu, indépendamment de l’écran d’affichage ou de l’appareil d’impression utilisé. Par exemple, une page de document fixe affichée en 96 ppp (points par pouce) apparaît de la même manière que lorsqu’elle est imprimée sur une imprimante laser 600 ppp ou une photocomposeuse 4800 ppp. Dans tous les cas, la disposition de la page reste la même, tandis que la qualité du document s’optimise selon les capacités de chaque appareil.  
  
 En comparaison, les documents dynamiques sont conçus pour optimiser l’affichage et la lisibilité. Ils trouvent leur meilleure exploitation quand la facilité de lecture est le scénario principal d’utilisation du document. Au lieu d’avoir une disposition prédéfinie, ces documents dynamiques ajustent et refluent dynamiquement leur contenu en fonction des variables d’exécution telles que la taille de la fenêtre, la résolution de l’appareil et les préférences facultatives de l’utilisateur. Une page web est un exemple simple de document dynamique où le contenu est mis en forme dynamiquement pour s’adapter à la fenêtre active. Les documents dynamiques optimisent l’expérience d’affichage et de lecture de l’utilisateur, en fonction de l’environnement d’exécution. Par exemple, le même document dynamique se remet en forme dynamiquement pour une lisibilité optimale sur un écran haute résolution de 19 pouces ou un petit écran de PDA de 2x3 pouces. En outre, les documents dynamiques possèdent plusieurs fonctionnalités intégrées, notamment la recherche, les modes d’affichage qui optimisent la lisibilité et la possibilité de changer la taille et l’apparence des polices.  Pour obtenir des illustrations, des exemples et des informations complètes sur les documents dynamiques, consultez [Vue d’ensemble des documents dynamiques](flow-document-overview.md).  
  
<a name="document_viewer"></a>
## <a name="document-controls-and-text-layout"></a>Contrôles de document et disposition du texte  
 Le cadre .NET fournit un ensemble de contrôles pré-construits qui simplifient à l’aide de documents fixes, de documents d’écoulement et de texte général dans votre application.  L’affichage du contenu fixe <xref:System.Windows.Controls.DocumentViewer> du document est pris en charge à l’aide du contrôle.  L’affichage du contenu des documents <xref:System.Windows.Controls.FlowDocumentReader>de <xref:System.Windows.Controls.FlowDocumentPageViewer>flux <xref:System.Windows.Controls.FlowDocumentScrollViewer> est pris en charge par trois contrôles différents : , et quelle carte vers différents scénarios d’utilisateurs (voir les sections ci-dessous).  D’autres contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournissent une disposition simplifiée pour la prise en charge des utilisations générales de texte (voir [Texte dans l’interface utilisateur](#text_in_the_user_interface), ci-dessous).  
  
### <a name="fixed-document-control---documentviewer"></a>Contrôle de document fixe - DocumentViewer  
 Le <xref:System.Windows.Controls.DocumentViewer> contrôle est <xref:System.Windows.Documents.FixedDocument> conçu pour afficher du contenu. Le <xref:System.Windows.Controls.DocumentViewer> contrôle fournit une interface utilisateur intuitive qui fournit un support intégré pour les opérations courantes, y compris la sortie d’impression, copier-papiers, zoom, et les fonctionnalités de recherche de texte. Le contrôle permet d’accéder aux pages de contenu par le biais d’un mécanisme de défilement familier. Comme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tous <xref:System.Windows.Controls.DocumentViewer> les contrôles, prend en charge le restyling complet ou partiel, ce qui permet d’intégrer visuellement le contrôle dans pratiquement n’importe quelle application ou environnement.  
  
 <xref:System.Windows.Controls.DocumentViewer>est conçu pour afficher le contenu d’une manière lue uniquement; l’édition ou la modification du contenu n’est pas disponible et n’est pas prise en charge.  
  
<a name="flow_document"></a>
### <a name="flow-document-controls"></a>Contrôles de document dynamique  

> [!NOTE]
> Pour plus d’informations détaillées sur les fonctionnalités des documents de flux et sur la façon de les créer, voir [Aperçu du document de flux](flow-document-overview.md).  
  
 L’affichage du contenu des documents <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer>de <xref:System.Windows.Controls.FlowDocumentScrollViewer>flux est pris en charge par trois contrôles : , , et .  
  
#### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader>comprend des fonctionnalités qui permettent à l’utilisateur de choisir dynamiquement entre différents modes de visualisation, y compris un mode de visualisation d’une page (page à la fois), un mode de visualisation de deux pages à la fois (format de lecture de livre) et un mode de visualisation continu de défilement (sans fond).  Pour plus d’informations sur <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>ces modes de visualisation, voir .  Si vous n’avez pas besoin de la <xref:System.Windows.Controls.FlowDocumentPageViewer> possibilité <xref:System.Windows.Controls.FlowDocumentScrollViewer> de basculer dynamiquement entre les différents modes de visualisation, et de fournir des téléspectateurs de contenu de flux plus légers qui sont fixés dans un mode de visualisation particulier.  
  
#### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer et FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>affiche le contenu en mode de visualisation <xref:System.Windows.Controls.FlowDocumentScrollViewer> page à la fois, tandis que le contenu affiche le contenu en mode défilement continu.  Les <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> deux et sont fixés à un mode de visualisation particulier. Comparez <xref:System.Windows.Controls.FlowDocumentReader>à , qui comprend des fonctionnalités qui permettent à l’utilisateur de choisir dynamiquement entre différents modes d’affichage (comme fourni par le <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> recensement), au prix d’être plus gourmand en ressources que <xref:System.Windows.Controls.FlowDocumentPageViewer> ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Par défaut, une barre de défilement verticale est toujours affichée et une barre de défilement horizontale apparaît si nécessaire. La [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] valeur <xref:System.Windows.Controls.FlowDocumentScrollViewer> par défaut n’inclut pas une barre d’outils; cependant, <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> la propriété peut être utilisée pour permettre une barre d’outils intégrée.  
  
<a name="text_in_the_user_interface"></a>
### <a name="text-in-the-user-interface"></a>Texte dans l’interface utilisateur  
 En plus d’ajouter du texte à des documents, vous pouvez bien évidemment utiliser du texte dans l’interface utilisateur de l’application, notamment dans des formulaires. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut plusieurs contrôles pour dessiner le texte à l’écran. Chaque contrôle est ciblé sur un scénario différent et dispose de sa propre liste de fonctionnalités et limitations. En général, <xref:System.Windows.Controls.TextBlock> l’élément doit être utilisé lorsque le support texte [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]limité est nécessaire, comme une brève phrase dans un . <xref:System.Windows.Controls.Label>peut être utilisé lorsque le support texte minimal est nécessaire. Pour plus d’informations, consultez [Vue d’ensemble de TextBlock](../controls/textblock-overview.md).  
  
<a name="packaging"></a>
## <a name="document-packaging"></a>Packaging de documents  
 Les <xref:System.IO.Packaging> API fournissent un moyen efficace d’organiser les données d’application, le contenu des documents et les ressources connexes dans un seul conteneur qui est simple d’accès, portable et facile à distribuer. Un fichier ZIP est <xref:System.IO.Packaging.Package> un exemple d’un type capable de contenir plusieurs objets comme une seule unité. Les API d’emballage fournissent une implémentation par défaut <xref:System.IO.Packaging.ZipPackage> conçue à l’aide d’une norme Open Packaging Conventions avec l’architecture de fichiers XML et ZIP. Les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API d’emballage facilitent la création d’emballages et le stockage et l’accès des objets à leur intérieur. Un objet stocké <xref:System.IO.Packaging.Package> dans un est <xref:System.IO.Packaging.PackagePart> appelé une ("partie"). Les packages peuvent également inclure des certificats numériques signés pouvant être utilisés pour identifier le créateur d’une partie, et pour valider que le contenu d’un package n’a pas été modifié.  Les paquets <xref:System.IO.Packaging.PackageRelationship> comprennent également une fonctionnalité qui permet d’ajouter des informations supplémentaires à un paquet ou associés à des pièces spécifiques sans modifier réellement le contenu des pièces existantes.  Les services de forfait prennent également en charge Microsoft Windows Rights Management (RM).  
  
 L’architecture de package [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sert de base à de nombreuses technologies clés :  
  
- Documents XPS conformes à la spécification papier XML (XPS).  
  
- Documents au format Microsoft Office "12" Open XML (.docx).  
  
- Formats de stockage personnalisés pour la conception de vos propres applications.  
  
 Basé sur les API <xref:System.Windows.Xps.Packaging.XpsDocument> d’emballage, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] un est spécifiquement conçu pour stocker des documents de contenu fixe. Un <xref:System.Windows.Xps.Packaging.XpsDocument> document est un document autonome qui peut être <xref:System.Windows.Controls.DocumentViewer> ouvert dans un visualiseur, affiché dans un contrôle, acheminé vers une bobine d’impression, ou la sortie directement à une imprimante compatible XPS.  
  
 Les sections suivantes fournissent <xref:System.IO.Packaging.Package> des <xref:System.Windows.Xps.Packaging.XpsDocument> informations supplémentaires [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]sur les API et les API fournies avec .  
  
<a name="packages"></a>
### <a name="package-components"></a>Composants d’un package  
 Les API de packaging [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permettent d’organiser les données et documents d’une application en une seule unité portable. Un fichier ZIP est l’un des types de package les plus courants. Il s’agit du type de package par défaut fourni avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package>elle-même est une <xref:System.IO.Packaging.ZipPackage> classe abstraite à partir de laquelle est implémenté en utilisant une architecture de fichier XML et ZIP standard ouvert.  La <xref:System.IO.Packaging.Package.Open%2A> méthode <xref:System.IO.Packaging.ZipPackage> utilise pour créer et utiliser des fichiers ZIP par défaut. Un package peut contenir trois types d’éléments de base :  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Contenu d’application, données, documents et fichiers de ressources.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|Certificat X.509 pour l’identification, l’authentification et la validation.|  
|<xref:System.IO.Packaging.PackageRelationship>|Informations ajoutées relatives au package ou à une partie spécifique.|  
  
<a name="PackageParts"></a>
#### <a name="packageparts"></a>PackageParts  
 A <xref:System.IO.Packaging.PackagePart> ("partie") est une classe abstraite qui <xref:System.IO.Packaging.Package>se réfère à un objet stocké dans un . Dans un fichier ZIP, les parties du package correspondent aux fichiers individuels stockés qu’il contient.  <xref:System.IO.Packaging.ZipPackagePart>fournit la mise en œuvre <xref:System.IO.Packaging.ZipPackage>par défaut pour les objets sérialisables stockés dans un .  Comme pour un système de fichiers, les parties contenues dans le package sont stockées dans des répertoires hiérarchiques ou sous forme de dossiers.  À [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’aide des API d’emballage, <xref:System.IO.Packaging.PackagePart> les applications peuvent écrire, stocker et lire plusieurs objets à l’aide d’un seul conteneur de fichiers ZIP.  
  
<a name="PackageDigitalSignatures"></a>
#### <a name="packagedigitalsignatures"></a>PackageDigitalSignatures  
 Pour la <xref:System.IO.Packaging.PackageDigitalSignature> sécurité, une (« signature numérique ») peut être associée à des pièces dans un paquet. A <xref:System.IO.Packaging.PackageDigitalSignature> intègre un [509] qui fournit deux caractéristiques :  
  
1. Identifie et authentifie le créateur de la partie.  
  
2. Vérifie que la partie n’a pas été modifiée.  
  
 La signature numérique n’empêche pas la modification d’une partie, mais un contrôle de validation par rapport à la signature numérique échoue si la partie est modifiée d’une façon ou d’une autre. L’application peut alors exécuter l’action appropriée : par exemple, bloquer l’ouverture de la partie, ou notifier l’utilisateur que la partie a été modifiée et n’est pas sécurisée.  
  
<a name="PackageRelationships"></a>
#### <a name="packagerelationships"></a>PackageRelationships  
 A <xref:System.IO.Packaging.PackageRelationship> ("relation") fournit un mécanisme pour associer des informations supplémentaires avec le paquet ou une pièce dans le paquet. Une relation est une fonctionnalité de package qui peut associer des informations supplémentaires à une partie sans en modifier le contenu actuel. L’insertion directe de nouvelles données dans le contenu de la partie n’est généralement pas très pratique dans de nombreux cas :  
  
- Le type réel de la partie et son schéma de contenu ne sont pas connus.  
  
- Même s’il est connu, le schéma de contenu peut ne pas fournir de moyen d’ajouter de nouvelles informations.  
  
- La partie peut être chiffrée ou signée numériquement, empêchant toute modification.  
  
 Les relations de package fournissent un moyen détectable d’ajouter et d’associer des informations supplémentaires à des parties individuelles ou à l’ensemble du package. Les relations de package sont utilisées pour deux fonctions principales :  
  
1. Définition des relations de dépendance d’une partie à l’autre.  
  
2. Définition des relations d’information qui ajoutent des notes ou d’autres données relatives à la partie.  
  
 A <xref:System.IO.Packaging.PackageRelationship> fournit un moyen rapide et détectable de définir les dépendances et d’ajouter d’autres informations associées à une partie du paquet ou à l’ensemble du paquet.  
  
<a name="Dependency_Relationships"></a>
##### <a name="dependency-relationships"></a>Relations de dépendance  
 Les relations de dépendance sont utilisées pour décrire les dépendances qu’une partie crée sur d’autres parties. Par exemple, un package peut contenir une partie HTML comprenant une ou plusieurs balises d’image \<img>. Les balises d’image font référence à des images situées sur d’autres parties internes au package ou externes au package (comme celles accessibles sur Internet). La <xref:System.IO.Packaging.PackageRelationship> création d’un fichier HTML est la découverte et l’accès aux ressources dépendantes rapidement et facilement. Une application de navigateur ou de visionneuse peut accéder directement aux relations de parties et commencer immédiatement l’assemblage des ressources dépendantes sans connaître le schéma ou analyser le document.  
  
<a name="Information_Relationships"></a>
##### <a name="information-relationships"></a>Relations d’informations  
 Semblable à une note ou <xref:System.IO.Packaging.PackageRelationship> une annotation, un peut également être utilisé pour stocker d’autres types d’informations à associer à une pièce sans avoir à modifier réellement le contenu de la pièce elle-même.  
  
<a name="XPS_Documents"></a>
## <a name="xps-documents"></a>Documents XPS  
 Le document XML Paper Specification (XPS) est un ensemble qui contient un ou plusieurs documents fixes ainsi que toutes les ressources et informations nécessaires au rendu.  XPS est également le format de fichier de bobine d’impression Windows Vista.  Un <xref:System.Windows.Xps.Packaging.XpsDocument> est stocké dans un jeu de données ZIP standard, et peut inclure une combinaison de XML et de composants binaires, tels que les fichiers d’images et de polices. Des [PackageRelationships](#PackageRelationships) sont utilisés pour définir les dépendances entre le contenu et les ressources nécessaires pour afficher le document.  La <xref:System.Windows.Xps.Packaging.XpsDocument> conception fournit une solution de document unique et haute fidélité qui prend en charge plusieurs utilisations :  
  
- Lecture, écriture et stockage de ressources et de contenu de document fixe sous la forme d’un fichier unique, portable et facile à distribuer.  
  
- Affichage de documents avec l’application XPS Viewer.  
  
- Produire des documents dans le format de sortie de bobine d’impression natif de Windows Vista.  
  
- Routage des documents directement vers une imprimante compatible XPS.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Documents.FixedDocument>
- <xref:System.Windows.Documents.FlowDocument>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.IO.Packaging.ZipPackage>
- <xref:System.IO.Packaging.ZipPackagePart>
- <xref:System.IO.Packaging.PackageRelationship>
- <xref:System.Windows.Controls.DocumentViewer>
- [Texte](optimizing-performance-text.md)
- [Vue d’ensemble des documents dynamiques](flow-document-overview.md)
- [Vue d'ensemble de l'impression](printing-overview.md)
- [Sérialisation et stockage de documents](document-serialization-and-storage.md)
