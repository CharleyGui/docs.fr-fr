---
title: Sérialisation et stockage de documents
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: 6703825d4453b2e0e65036fa2d9c856139ee473c
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094564"
---
# <a name="document-serialization-and-storage"></a>Sérialisation et stockage de documents

Microsoft .NET Framework fournit un environnement puissant pour créer et afficher des documents de haute qualité.  Les fonctionnalités améliorées qui prennent en charge à la fois les documents fixes et les documents dynamiques, les contrôles d’affichage avancés et les puissantes fonctionnalités graphiques 2D et 3D prennent .NET Framework applications à un niveau de qualité et d’expérience utilisateur inégalés.  La possibilité de gérer de manière flexible une représentation en mémoire d’un document est une fonctionnalité clé de .NET Framework, et la possibilité d’enregistrer et de charger efficacement des documents à partir d’un magasin de données est un besoin de presque toutes les applications.  Le processus de conversion d’un document d’une représentation en mémoire interne en magasin de données externe est appelé sérialisation.  Le processus inverse consistant à lire un magasin de données et à recréer l’instance en mémoire d’origine est appelé désérialisation.

<a name="AboutSerialization"></a>

## <a name="about-document-serialization"></a>À propos de la sérialisation de documents

Dans l’idéal, les processus de sérialisation et de désérialisation d’un document depuis et vers la mémoire sont transparents pour l’application.  L’application appelle une méthode de sérialiseur « en écriture » pour enregistrer le document, tandis qu’une méthode de désérialiseur « en lecture » accède au magasin de données pour recréer l’instance d’origine en mémoire.  Le format spécifique de stockage des données ne concerne généralement pas l’application tant que les processus de sérialisation et de désérialisation recréent le document d’origine.

Les applications fournissent souvent plusieurs options de sérialisation qui permettent à l’utilisateur d’enregistrer des documents sur différents médias ou dans un format différent.  Par exemple, une application peut proposer des options « Enregistrer sous » pour stocker un document dans un fichier sur disque, une base de données ou un service web.  De même, différents sérialiseurs peuvent stocker le document sous divers formats, tels que les formats HTML, RTF, XML ou XPS, ou encore un format tiers.  Pour l’application, la sérialisation définit une interface qui isole les détails du média de stockage dans l’implémentation de chaque sérialiseur spécifique.  Outre les avantages de l’encapsulation des détails de stockage, les API .NET Framework <xref:System.Windows.Documents.Serialization> offrent plusieurs autres fonctionnalités importantes.

### <a name="features-of-net-framework-30-document-serializers"></a>Fonctionnalités des sérialiseurs de documents .NET Framework 3.0

- L’accès direct aux objets de document de niveau supérieur (arborescence logique et visuels) permet un stockage efficace de contenu paginé, d’éléments 2D/3D, d’images, de fichiers multimédias, de liens hypertexte, d’annotations et autre contenu de support.

- Fonctionnement synchrone et asynchrone.

- Prise en charge de sérialiseurs de plug-ins avec fonctionnalités améliorées :

  - Accès à l’ensemble du système pour une utilisation par toutes les applications .NET Framework.

  - Découvertibilité de plug-ins d’application simplifiée.

  - Déploiement, installation et mise à jour simples pour les plug-ins tiers personnalisés.

  - Prise en charge des paramètres et des options d’exécution personnalisés par l’interface utilisateur.

### <a name="xps-print-path"></a>Chemin d'impression XPS

Le chemin d’impression Microsoft .NET Framework XPS fournit également un mécanisme extensible pour l’écriture de documents par le biais de la sortie d’impression.  XPS sert à la fois de format de fichier de document et est le format de spouleur d’impression natif pour Windows Vista.  Les documents XPS peuvent être envoyés directement aux imprimantes compatibles XPS, sans qu’il soit nécessaire de les convertir en un format intermédiaire.  Consultez la rubrique [Vue d’ensemble de l’impression](printing-overview.md) pour obtenir des informations supplémentaires sur les options et les fonctionnalités de chemin d’impression.

<a name="PluginSerializers"></a>

## <a name="plug-in-serializers"></a>Sérialiseurs de plug-ins

Les API <xref:System.Windows.Documents.Serialization> prennent en charge les sérialiseurs de plug-ins et les sérialiseurs liés qui sont installés séparément de l’application, qui sont liés au moment de l’exécution et sont accessibles à l’aide du mécanisme de détection <xref:System.Windows.Documents.Serialization.SerializerProvider>.  Les sérialiseurs de plug-ins simplifient grandement les déploiements et les utilisations à l’échelle du système.  Les sérialiseurs liés peuvent également être implémentés pour des environnements de confiance partielle tels que les applications de navigateur XAML (XBAP) où les sérialiseurs de plug-ins ne sont pas accessibles.  Les sérialiseurs liés, qui sont basés sur une implémentation dérivée de la classe <xref:System.Windows.Documents.Serialization.SerializerWriter>, sont compilés et liés directement à l’application.  Les sérialiseurs de plug-ins comme les sérialiseurs liés fonctionnent selon des méthodes et des événements publics identiques qui facilitent leur utilisation séparée ou simultanée dans la même application.

Les sérialiseurs de plug-ins aident les développeurs d’applications en fournissant une extensibilité aux nouvelles conceptions de stockage et aux nouveaux formats de fichiers sans nécessiter de codage direct pour chaque format potentiel au moment de la génération.  Ils représentent également un atout pour les développeurs tiers, qui bénéficient ainsi d’un moyen standardisé pour déployer, installer et mettre à jour les plug-ins système accessibles pour les formats de fichiers personnalisés ou propriétaires.

### <a name="using-a-plug-in-serializer"></a>Utilisation d’un sérialiseur de plug-ins

Les sérialiseurs de plug-ins sont simples à utiliser.  La classe <xref:System.Windows.Documents.Serialization.SerializerProvider> énumère un objet <xref:System.Windows.Documents.Serialization.SerializerDescriptor> pour chaque plug-in installé sur le système.  La propriété <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> filtre les plug-ins installés en fonction de la configuration actuelle et vérifie que le sérialiseur peut être chargé et utilisé par l’application.  Le <xref:System.Windows.Documents.Serialization.SerializerDescriptor> fournit également d’autres propriétés, telles que <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> et <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, que l’application peut utiliser pour inviter l’utilisateur à sélectionner un sérialiseur pour un format de sortie disponible.  Un sérialiseur de plug-ins par défaut pour XPS est fourni avec .NET Framework et est toujours énuméré.  Une fois que l’utilisateur a sélectionné un format de sortie, la méthode <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> est utilisée pour créer un <xref:System.Windows.Documents.Serialization.SerializerWriter> pour le format spécifique.  La méthode <xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A?displayProperty=nameWithType> peut ensuite être appelée pour générer le flux du document dans le magasin de données.

L’exemple suivant illustre une application qui utilise la méthode <xref:System.Windows.Documents.Serialization.SerializerProvider> dans une propriété « PlugInFileFilter ».  PlugInFileFilter énumère les plug-ins installés et génère une chaîne de filtrage avec les options de fichier disponibles pour un <xref:Microsoft.Win32.SaveFileDialog>.

[!code-csharp[DocumentSerialize#DocSerializeFileFilter](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]

Une fois qu’un nom de fichier de sortie a été sélectionné par l’utilisateur, l’exemple suivant illustre l’utilisation de la méthode <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> pour stocker un document donné dans un format spécifié.

[!code-csharp[DocumentSerialize#DocSerializePlugIn](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]

<a name="InstallingPluginSerializers"></a>

### <a name="installing-plug-in-serializers"></a>Installation de sérialiseurs de plug-ins

La classe <xref:System.Windows.Documents.Serialization.SerializerProvider> fournit l’interface d’application de niveau supérieur pour la découverte et l’accès des sérialiseurs de plug-ins.  <xref:System.Windows.Documents.Serialization.SerializerProvider> localise et fournit à l’application une liste des sérialiseurs installés et accessibles sur le système.  Les caractéristiques des sérialiseurs installés sont définies à l’aide des paramètres du Registre.  Les sérialiseurs de plug-ins peuvent être ajoutés au registre à l’aide de la méthode <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> ; Si .NET Framework n’est pas encore installé, le script d’installation du plug-in peut définir directement les valeurs du Registre.  La méthode <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> peut être utilisée pour supprimer un plug-in précédemment installé, ou les paramètres du Registre peuvent être réinitialisés de façon similaire par un script de désinstallation.

### <a name="creating-a-plug-in-serializer"></a>Création d’un sérialiseur de plug-ins

Les sérialiseurs de plug-ins et les sérialiseurs liés utilisent les mêmes méthodes et événements publics exposés, et sont conçus pour un fonctionnement synchrone ou asynchrone.  La création d’un sérialiseur de plug-ins se déroule généralement en trois étapes principales :

1. La première étape consiste à implémenter et à déboguer le sérialiseur comme sérialiseur lié.  Le fait de créer un sérialiseur compilé et lié directement dans une application de test permet d’accéder aux points d’arrêt et autres services de débogage utiles lors du test.

2. Une fois le sérialiseur entièrement testé, une interface de <xref:System.Windows.Documents.Serialization.ISerializerFactory> est ajoutée pour créer un plug-in.  L’interface <xref:System.Windows.Documents.Serialization.ISerializerFactory> autorise un accès complet à tous les objets .NET Framework qui incluent l’arborescence logique, les objets <xref:System.Windows.UIElement>, les <xref:System.Windows.Documents.IDocumentPaginatorSource>et les éléments <xref:System.Windows.Media.Visual>.  En outre <xref:System.Windows.Documents.Serialization.ISerializerFactory> fournit les mêmes méthodes et événements synchrones et asynchrones que ceux utilisés par les sérialiseurs liés.  La sortie des documents volumineux pouvant prendre un certain temps, un fonctionnement asynchrone est recommandé de sorte à maintenir la réactivité de l’intervention de l’utilisateur tout en offrant une option « Annuler » en cas de problème avec le magasin de données.

3. Une fois le sérialiseur de plug-ins créé, un script d’installation est implémenté pour distribuer et installer (ou désinstaller) le plug-in (voir la section ci-dessus intitulée "[Installation de sérialiseurs de plug-ins](#InstallingPluginSerializers)).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Documents.Serialization>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
- [Spécification XML Paper](https://www.ecma-international.org/activities/XML%20Paper%20Specification/XPS%20Standard%20WD%201.6.pdf)
