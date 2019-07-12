---
title: Sérialisation et stockage de documents
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: b60b3964ff8e1b1f05b6c0820c63ec06d9ea0f4c
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859656"
---
# <a name="document-serialization-and-storage"></a>Sérialisation et stockage de documents

Microsoft .NET Framework fournit un environnement puissant pour créer et afficher des documents de haute qualité.  Les fonctionnalités améliorées qui prennent en charge les documents fixes et des documents dynamiques, advanced contrôles d’affichage associé à 2D puissantes et des capacités graphiques 3D prennent des applications .NET Framework d’un nouveau niveau de qualité et l’expérience utilisateur.  En mesure de gérer de manière flexible une représentation en mémoire d’un document est une fonctionnalité clé de .NET Framework, et pouvoir enregistrer et charger des documents à partir d’un magasin de données efficacement est nécessaire de presque toutes les applications.  Le processus de conversion d’un document d’une représentation en mémoire interne en magasin de données externe est appelé sérialisation.  Le processus inverse consistant à lire un magasin de données et à recréer l’instance en mémoire d’origine est appelé désérialisation.

<a name="AboutSerialization"></a>

## <a name="about-document-serialization"></a>À propos de la sérialisation de documents

Dans l’idéal, les processus de sérialisation et de désérialisation d’un document depuis et vers la mémoire sont transparents pour l’application.  L’application appelle une méthode de sérialiseur « en écriture » pour enregistrer le document, tandis qu’une méthode de désérialiseur « en lecture » accède au magasin de données pour recréer l’instance d’origine en mémoire.  Le format spécifique de stockage des données ne concerne généralement pas l’application tant que les processus de sérialisation et de désérialisation recréent le document d’origine.

Les applications fournissent souvent plusieurs options de sérialisation qui permettent à l’utilisateur d’enregistrer des documents sur différents médias ou dans un format différent.  Par exemple, une application peut proposer des options « Enregistrer sous » pour stocker un document dans un fichier sur disque, une base de données ou un service web.  De même, différents sérialiseurs peuvent stocker le document sous divers formats, tels que les formats HTML, RTF, XML ou XPS, ou encore un format tiers.  Pour l’application, la sérialisation définit une interface qui isole les détails du média de stockage dans l’implémentation de chaque sérialiseur spécifique.  Outre les avantages de l’encapsulation des détails de stockage, le .NET Framework <xref:System.Windows.Documents.Serialization> API fournissent plusieurs autres fonctionnalités importantes.

### <a name="features-of-net-framework-30-document-serializers"></a>Fonctionnalités des sérialiseurs de documents .NET Framework 3.0

- L’accès direct aux objets de document de niveau supérieur (arborescence logique et visuels) permet un stockage efficace de contenu paginé, d’éléments 2D/3D, d’images, de fichiers multimédias, de liens hypertexte, d’annotations et autre contenu de support.

- Fonctionnement synchrone et asynchrone.

- Prise en charge de sérialiseurs de plug-ins avec fonctionnalités améliorées :

  - Accès de l’échelle du système pour une utilisation par toutes les applications .NET Framework.

  - Découvertibilité de plug-ins d’application simplifiée.

  - Déploiement, installation et mise à jour simples pour les plug-ins tiers personnalisés.

  - Prise en charge des paramètres et des options d’exécution personnalisés par l’interface utilisateur.

### <a name="xps-print-path"></a>Chemin d'impression XPS

Microsoft .NET Framework [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] chemin d’impression fournit également un mécanisme extensible pour l’écriture de documents via la sortie d’impression.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] fait office à la fois de format de fichier de document et de spool d’impression natif pour [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  Les documents [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] peuvent être envoyés directement aux imprimantes compatibles [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] sans nécessiter de conversion dans un format intermédiaire.  Consultez la rubrique [Vue d’ensemble de l’impression](printing-overview.md) pour obtenir des informations supplémentaires sur les options et les fonctionnalités de chemin d’impression.

<a name="PluginSerializers"></a>

## <a name="plug-in-serializers"></a>Sérialiseurs de plug-ins

Le <xref:System.Windows.Documents.Serialization> API prennent en charge les sérialiseurs de plug-in et les sérialiseurs liés installés séparément de l’application, liez au moment de l’exécution et sont accessibles à l’aide de la <xref:System.Windows.Documents.Serialization.SerializerProvider> mécanisme de découverte.  Les sérialiseurs de plug-ins simplifient grandement les déploiements et les utilisations à l’échelle du système.  Les sérialiseurs liés peuvent également être implémentés pour les environnements de confiance partielle tels que les [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] dans lesquelles les sérialiseurs de plug-ins ne sont pas accessibles.  Sérialiseurs liés, qui sont basés sur une implémentation dérivée de la <xref:System.Windows.Documents.Serialization.SerializerWriter> classe, sont compilés et liés directement dans l’application.  Les sérialiseurs de plug-ins comme les sérialiseurs liés fonctionnent selon des méthodes et des événements publics identiques qui facilitent leur utilisation séparée ou simultanée dans la même application.

Les sérialiseurs de plug-ins aident les développeurs d’applications en fournissant une extensibilité aux nouvelles conceptions de stockage et aux nouveaux formats de fichiers sans nécessiter de codage direct pour chaque format potentiel au moment de la génération.  Ils représentent également un atout pour les développeurs tiers, qui bénéficient ainsi d’un moyen standardisé pour déployer, installer et mettre à jour les plug-ins système accessibles pour les formats de fichiers personnalisés ou propriétaires.

### <a name="using-a-plug-in-serializer"></a>Utilisation d’un sérialiseur de plug-ins

Les sérialiseurs de plug-ins sont simples à utiliser.  Le <xref:System.Windows.Documents.Serialization.SerializerProvider> classe énumère un <xref:System.Windows.Documents.Serialization.SerializerDescriptor> pour chaque plug-in installé sur le système de l’objet.  Le <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> propriété filtre les plug-ins installés selon la configuration actuelle et vérifie que le sérialiseur peut être chargé et utilisé par l’application.  Le <xref:System.Windows.Documents.Serialization.SerializerDescriptor> fournit également d’autres propriétés, telles que <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> et <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, que l’application peut utiliser pour inviter l’utilisateur à sélectionner un sérialiseur pour un format de sortie disponible.  Un sérialiseur de plug-in par défaut pour [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] est fourni avec .NET Framework et est toujours énuméré.  Une fois que l’utilisateur sélectionne un format de sortie, le <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> méthode est utilisée pour créer un <xref:System.Windows.Documents.Serialization.SerializerWriter> pour le format spécifique.  L’élément de langage <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> méthode peut ensuite être appelée pour le flux du document dans le magasin de données de sortie.

L’exemple suivant illustre une application qui utilise le <xref:System.Windows.Documents.Serialization.SerializerProvider> méthode dans une propriété « PlugInFileFilter ».  La propriété PlugInFileFilter énumère les plug-ins installés et génère une chaîne de filtre avec les options de fichiers disponible pour un <xref:Microsoft.Win32.SaveFileDialog>.

[!code-csharp[DocumentSerialize#DocSerializeFileFilter](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]

Une fois un nom de fichier de sortie a été sélectionné par l’utilisateur, l’exemple suivant illustre l’utilisation de la <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> méthode pour stocker un document donné dans un format spécifié.

[!code-csharp[DocumentSerialize#DocSerializePlugIn](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]

<a name="InstallingPluginSerializers"></a>

### <a name="installing-plug-in-serializers"></a>Installation de sérialiseurs de plug-ins

Le <xref:System.Windows.Documents.Serialization.SerializerProvider> classe fournit l’interface de l’application de niveau supérieur pour l’accès et de découverte du sérialiseur de plug-in.  <xref:System.Windows.Documents.Serialization.SerializerProvider> localise et fournit la liste des sérialiseurs installés et accessibles sur le système de l’application.  Les caractéristiques des sérialiseurs installés sont définies à l’aide des paramètres du Registre.  Les sérialiseurs de plug-in peuvent être ajoutés au Registre à l’aide de la <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> méthode ; ou si .NET Framework n’est pas encore installé, le script d’installation de plug-in peut définir directement les valeurs de Registre lui-même.  Le <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> méthode peut être utilisée pour supprimer un précédemment installées plug-in, ou les paramètres du Registre peuvent être réinitialisés même par un script de désinstallation.

### <a name="creating-a-plug-in-serializer"></a>Création d’un sérialiseur de plug-ins

Les sérialiseurs de plug-ins et les sérialiseurs liés utilisent les mêmes méthodes et événements publics exposés, et sont conçus pour un fonctionnement synchrone ou asynchrone.  La création d’un sérialiseur de plug-ins se déroule généralement en trois étapes principales :

1. La première étape consiste à implémenter et à déboguer le sérialiseur comme sérialiseur lié.  Le fait de créer un sérialiseur compilé et lié directement dans une application de test permet d’accéder aux points d’arrêt et autres services de débogage utiles lors du test.

2. Une fois le sérialiseur intégralement testé, un <xref:System.Windows.Documents.Serialization.ISerializerFactory> interface est ajoutée pour créer un plug-in.  Le <xref:System.Windows.Documents.Serialization.ISerializerFactory> interface permet un accès total à tous les objets de .NET Framework qui inclut l’arborescence logique, <xref:System.Windows.UIElement> objets, <xref:System.Windows.Documents.IDocumentPaginatorSource>, et <xref:System.Windows.Media.Visual> éléments.  En outre <xref:System.Windows.Documents.Serialization.ISerializerFactory> fournit les mêmes méthodes synchrones et asynchrones et les événements utilisés par les sérialiseurs liés.  La sortie des documents volumineux pouvant prendre un certain temps, un fonctionnement asynchrone est recommandé de sorte à maintenir la réactivité de l’intervention de l’utilisateur tout en offrant une option « Annuler » en cas de problème avec le magasin de données.

3. Une fois le sérialiseur de plug-ins créé, un script d’installation est implémenté pour distribuer et installer (ou désinstaller) le plug-in (voir la section ci-dessus intitulée "[Installation de sérialiseurs de plug-ins](#InstallingPluginSerializers)).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Documents.Serialization>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
- [XML Paper Specification : Vue d’ensemble](https://go.microsoft.com/fwlink?LinkID=106246)
