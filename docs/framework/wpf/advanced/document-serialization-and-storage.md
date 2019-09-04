---
title: Sérialisation et stockage de documents
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: 7ddd887eefd67a3300795396dac26e855f30989e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254120"
---
# <a name="document-serialization-and-storage"></a>Sérialisation et stockage de documents

Microsoft .NET Framework fournit un environnement puissant pour créer et afficher des documents de haute qualité.  Les fonctionnalités améliorées qui prennent en charge à la fois les documents fixes et les documents dynamiques, les contrôles d’affichage avancés et les puissantes fonctionnalités graphiques 2D et 3D prennent .NET Framework applications à un niveau de qualité et d’expérience utilisateur inégalés.  La possibilité de gérer de manière flexible une représentation en mémoire d’un document est une fonctionnalité clé de .NET Framework, et la possibilité d’enregistrer et de charger efficacement des documents à partir d’un magasin de données est un besoin de presque toutes les applications.  Le processus de conversion d’un document d’une représentation en mémoire interne en magasin de données externe est appelé sérialisation.  Le processus inverse consistant à lire un magasin de données et à recréer l’instance en mémoire d’origine est appelé désérialisation.

<a name="AboutSerialization"></a>

## <a name="about-document-serialization"></a>À propos de la sérialisation de documents

Dans l’idéal, les processus de sérialisation et de désérialisation d’un document depuis et vers la mémoire sont transparents pour l’application.  L’application appelle une méthode de sérialiseur « en écriture » pour enregistrer le document, tandis qu’une méthode de désérialiseur « en lecture » accède au magasin de données pour recréer l’instance d’origine en mémoire.  Le format spécifique de stockage des données ne concerne généralement pas l’application tant que les processus de sérialisation et de désérialisation recréent le document d’origine.

Les applications fournissent souvent plusieurs options de sérialisation qui permettent à l’utilisateur d’enregistrer des documents sur différents médias ou dans un format différent.  Par exemple, une application peut proposer des options « Enregistrer sous » pour stocker un document dans un fichier sur disque, une base de données ou un service web.  De même, différents sérialiseurs peuvent stocker le document sous divers formats, tels que les formats HTML, RTF, XML ou XPS, ou encore un format tiers.  Pour l’application, la sérialisation définit une interface qui isole les détails du média de stockage dans l’implémentation de chaque sérialiseur spécifique.  Outre les avantages de l’encapsulation des détails de stockage, les <xref:System.Windows.Documents.Serialization> API .NET Framework offrent plusieurs autres fonctionnalités importantes.

### <a name="features-of-net-framework-30-document-serializers"></a>Fonctionnalités des sérialiseurs de documents .NET Framework 3.0

- L’accès direct aux objets de document de niveau supérieur (arborescence logique et visuels) permet un stockage efficace de contenu paginé, d’éléments 2D/3D, d’images, de fichiers multimédias, de liens hypertexte, d’annotations et autre contenu de support.

- Fonctionnement synchrone et asynchrone.

- Prise en charge de sérialiseurs de plug-ins avec fonctionnalités améliorées :

  - Accès à l’ensemble du système pour une utilisation par toutes les applications .NET Framework.

  - Découvertibilité de plug-ins d’application simplifiée.

  - Déploiement, installation et mise à jour simples pour les plug-ins tiers personnalisés.

  - Prise en charge des paramètres et des options d’exécution personnalisés par l’interface utilisateur.

### <a name="xps-print-path"></a>Chemin d'impression XPS

Le chemin d’impression Microsoft .NET Framework XPS fournit également un mécanisme extensible pour l’écriture de documents par le biais de la sortie d’impression.  XPS sert à la fois de format de fichier de document et est le format de [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]spouleur d’impression natif pour.  Les documents XPS peuvent être envoyés directement aux imprimantes compatibles XPS, sans qu’il soit nécessaire de les convertir en un format intermédiaire.  Consultez la rubrique [Vue d’ensemble de l’impression](printing-overview.md) pour obtenir des informations supplémentaires sur les options et les fonctionnalités de chemin d’impression.

<a name="PluginSerializers"></a>

## <a name="plug-in-serializers"></a>Sérialiseurs de plug-ins

Les <xref:System.Windows.Documents.Serialization> API assurent la prise en charge des sérialiseurs de plug-ins et des sérialiseurs liés installés séparément de l’application, d’une liaison au moment de l’exécution <xref:System.Windows.Documents.Serialization.SerializerProvider> et sont accessibles à l’aide du mécanisme de découverte.  Les sérialiseurs de plug-ins simplifient grandement les déploiements et les utilisations à l’échelle du système.  Les sérialiseurs liés peuvent également être implémentés pour les environnements de confiance partielle tels que les [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] dans lesquelles les sérialiseurs de plug-ins ne sont pas accessibles.  Les sérialiseurs liés, qui sont basés sur une implémentation dérivée <xref:System.Windows.Documents.Serialization.SerializerWriter> de la classe, sont compilés et liés directement à l’application.  Les sérialiseurs de plug-ins comme les sérialiseurs liés fonctionnent selon des méthodes et des événements publics identiques qui facilitent leur utilisation séparée ou simultanée dans la même application.

Les sérialiseurs de plug-ins aident les développeurs d’applications en fournissant une extensibilité aux nouvelles conceptions de stockage et aux nouveaux formats de fichiers sans nécessiter de codage direct pour chaque format potentiel au moment de la génération.  Ils représentent également un atout pour les développeurs tiers, qui bénéficient ainsi d’un moyen standardisé pour déployer, installer et mettre à jour les plug-ins système accessibles pour les formats de fichiers personnalisés ou propriétaires.

### <a name="using-a-plug-in-serializer"></a>Utilisation d’un sérialiseur de plug-ins

Les sérialiseurs de plug-ins sont simples à utiliser.  La <xref:System.Windows.Documents.Serialization.SerializerProvider> classe énumère un <xref:System.Windows.Documents.Serialization.SerializerDescriptor> objet pour chaque plug-in installé sur le système.  La <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> propriété filtre les plug-ins installés en fonction de la configuration actuelle et vérifie que le sérialiseur peut être chargé et utilisé par l’application.  Fournit également d’autres propriétés, telles que <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> et <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, que l’application peut utiliser pour inviter l’utilisateur à sélectionner un sérialiseur pour un format de sortie disponible. <xref:System.Windows.Documents.Serialization.SerializerDescriptor>  Un sérialiseur de plug-ins par défaut pour XPS est fourni avec .NET Framework et est toujours énuméré.  Une fois que l’utilisateur a sélectionné un format <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> de sortie, la méthode est <xref:System.Windows.Documents.Serialization.SerializerWriter> utilisée pour créer un pour le format spécifique.  L’élément de langage <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> la méthode peut ensuite être appelée pour générer le flux de document dans le magasin de données.

L’exemple suivant illustre une application qui utilise la <xref:System.Windows.Documents.Serialization.SerializerProvider> méthode dans une propriété « PlugInFileFilter ».  PlugInFileFilter énumère les plug-ins installés et génère une chaîne de filtrage avec les options de fichier disponibles pour <xref:Microsoft.Win32.SaveFileDialog>un.

[!code-csharp[DocumentSerialize#DocSerializeFileFilter](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]

Une fois qu’un nom de fichier de sortie a été sélectionné par l’utilisateur, l’exemple suivant illustre <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> l’utilisation de la méthode pour stocker un document donné dans un format spécifié.

[!code-csharp[DocumentSerialize#DocSerializePlugIn](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]

<a name="InstallingPluginSerializers"></a>

### <a name="installing-plug-in-serializers"></a>Installation de sérialiseurs de plug-ins

La <xref:System.Windows.Documents.Serialization.SerializerProvider> classe fournit l’interface d’application de niveau supérieur pour la découverte et l’accès des sérialiseurs de plug-ins.  <xref:System.Windows.Documents.Serialization.SerializerProvider>localise et fournit à l’application une liste des sérialiseurs installés et accessibles sur le système.  Les caractéristiques des sérialiseurs installés sont définies à l’aide des paramètres du Registre.  Les sérialiseurs de plug-ins peuvent être ajoutés au registre à l' <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> aide de la méthode ; ou si .NET Framework n’est pas encore installé, le script d’installation du plug-in peut définir directement les valeurs de registre.  La <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> méthode peut être utilisée pour supprimer un plug-in précédemment installé, ou les paramètres du Registre peuvent être réinitialisés de façon similaire par un script de désinstallation.

### <a name="creating-a-plug-in-serializer"></a>Création d’un sérialiseur de plug-ins

Les sérialiseurs de plug-ins et les sérialiseurs liés utilisent les mêmes méthodes et événements publics exposés, et sont conçus pour un fonctionnement synchrone ou asynchrone.  La création d’un sérialiseur de plug-ins se déroule généralement en trois étapes principales :

1. La première étape consiste à implémenter et à déboguer le sérialiseur comme sérialiseur lié.  Le fait de créer un sérialiseur compilé et lié directement dans une application de test permet d’accéder aux points d’arrêt et autres services de débogage utiles lors du test.

2. Une fois le sérialiseur entièrement testé, une <xref:System.Windows.Documents.Serialization.ISerializerFactory> interface est ajoutée pour créer un plug-in.  L' <xref:System.Windows.Documents.Serialization.ISerializerFactory> interface autorise un accès complet à tous les objets .NET Framework, y compris l' <xref:System.Windows.UIElement> arborescence logique <xref:System.Windows.Documents.IDocumentPaginatorSource>, les <xref:System.Windows.Media.Visual> objets, et les éléments.  <xref:System.Windows.Documents.Serialization.ISerializerFactory> Fournit également les mêmes méthodes et événements synchrones et asynchrones que ceux utilisés par les sérialiseurs liés.  La sortie des documents volumineux pouvant prendre un certain temps, un fonctionnement asynchrone est recommandé de sorte à maintenir la réactivité de l’intervention de l’utilisateur tout en offrant une option « Annuler » en cas de problème avec le magasin de données.

3. Une fois le sérialiseur de plug-ins créé, un script d’installation est implémenté pour distribuer et installer (ou désinstaller) le plug-in (voir la section ci-dessus intitulée "[Installation de sérialiseurs de plug-ins](#InstallingPluginSerializers)).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Documents.Serialization>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
- [Spécification Paper XML : Vue d’ensemble](https://go.microsoft.com/fwlink?LinkID=106246)
