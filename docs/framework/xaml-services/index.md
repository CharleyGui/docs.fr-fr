---
title: Services XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: a99b9f3cb8c008f72eaac7ee1b8790d63c547a8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453955"
---
# <a name="xaml-services"></a>Services XAML
Cette rubrique décrit les fonctionnalités d’un ensemble de technologies connu sous le nom de services XAML .NET Framework. La plupart des services et API décrits se trouvent dans l’assembly System. xaml, qui est un assembly introduit avec l’ensemble .NET Framework 4 d’assemblys .NET Core. Les services incluent les lecteurs et les writers, les classes de schéma et la prise en charge des schémas, les fabriques, l’attribution des classes, la prise en charge intrinsèque du langage XAML et d’autres fonctionnalités du langage XAML.  
  
## <a name="about-this-documentation"></a>À propos de cette documentation  
 La documentation conceptuelle relative à .NET Framework les services XAML suppose que vous avez déjà utilisé le langage XAML et comment il peut s’appliquer à un Framework spécifique, par exemple [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ou Windows Workflow Foundation, ou un domaine de fonctionnalités technologiques spécifique. par exemple, les fonctionnalités de personnalisation de la build dans <xref:Microsoft.Build.Framework.XamlTypes>. Cette documentation n’a pas pour but d’expliquer les principes fondamentaux de XAML en tant que langage de balisage, terminologie de syntaxe XAML ou autre matériel d’introduction. Au lieu de cela, cette documentation se concentre sur l’utilisation spécifique des services XAML .NET Framework qui sont activés dans la bibliothèque d’assemblys System. Xaml. La plupart de ces API sont destinées aux scénarios d’intégration et d’extensibilité du langage XAML. Il peut s’agir de l’un des éléments suivants :  
  
- Extension des fonctionnalités des lecteurs XAML de base ou des writers XAML (traitement direct du flux de nœud XAML ; dérivation de votre propre lecteur XAML ou writer XAML).  
  
- Définition de types personnalisés XAML qui n’ont pas de dépendances d’infrastructure spécifiques et attribution des types pour transmettre leurs caractéristiques de système de type XAML à .NET Framework les services XAML.  
  
- Hébergement de lecteurs et de writers XAML en tant que composant d’une application, tel qu’un concepteur visuel ou un éditeur interactif pour les sources de balisage XAML.  
  
- Écriture de convertisseurs de valeur XAML (extensions de balisage ; convertisseurs de type pour les types personnalisés).  
  
- Définition d’un contexte de schéma XAML personnalisé (à l’aide de techniques de chargement d’assembly alternatives pour la sauvegarde des sources de type ; à l’aide de techniques de recherche de types connus au lieu de la réflexion systématique des assemblys ; à l’aide de concepts d’assembly chargés qui n’utilisent pas le `AppDomain` CLR et de son modèle de sécurité associé).  
  
- Extension du système de type XAML de base.  
  
- À l’aide des techniques `Lookup` ou `Invoker` pour influencer le système de type XAML et comment les sauvegardes de type sont évaluées.  
  
 Si vous recherchez des éléments de présentation du langage XAML, vous pouvez essayer la [vue d’ensemble du langage XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md). Cette rubrique décrit XAML pour un public qui est nouveau à la [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] et à l’utilisation des fonctionnalités de balisage XAML et de langage XAML. Un autre document utile est le matériel d’introduction de la [spécification du langage XAML](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET Framework les services XAML et System. xaml dans l’architecture .NET  
 Dans les versions précédentes de Microsoft .NET Framework, la prise en charge des fonctionnalités de langage XAML était implémentée par les frameworks reposant sur Microsoft .NET Framework ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Windows Workflow Foundation et Windows Communication Foundation (WCF)), et par conséquent variation de son comportement et de l’API utilisée en fonction de l’infrastructure spécifique que vous utilisez. Cela comprenait l’analyseur XAML et son mécanisme de création de graphique d’objets, les intrinsèques du langage XAML, la prise en charge de la sérialisation, et ainsi de suite.  
  
 Dans .NET Framework 4, .NET Framework les services XAML et l’assembly System. Xaml définissent la majeure partie de ce qui est nécessaire pour prendre en charge les fonctionnalités du langage XAML. Cela comprend les classes de base pour les lecteurs XAML et les writers XAML. La fonctionnalité la plus importante ajoutée à .NET Framework les services XAML qui n’étaient pas présents dans les implémentations XAML spécifiques à l’infrastructure est une représentation de système de type pour XAML. La représentation de système de type présente du code XAML dans une méthode orientée objet qui se centre sur les fonctionnalités XAML sans avoir de dépendances avec des fonctionnalités spécifiques des frameworks.  
  
 Le système de type XAML n’est pas limité par la forme de balisage ou les caractéristiques d’exécution de l’origine XAML ; elle n’est pas non plus limitée par un système de type de stockage spécifique. Le système de type XAML comprend des représentations d’objet pour les types, les membres, les contextes de schéma XAML, les concepts de niveau XML et d’autres concepts de langage XAML ou intrinsèques XAML. L’utilisation ou l’extension du système de type XAML permet de dériver des classes comme les lecteurs XAML et les writers XAML, et d’étendre les fonctionnalités des représentations XAML dans des fonctionnalités spécifiques activées par une infrastructure, une technologie ou une application qui consomme ou émet du code XAML. Le concept d’un contexte de schéma XAML permet d’effectuer des opérations d’écriture de graphique d’objets pratiques à partir de la combinaison d’une implémentation du writer d’objet XAML, du système de type de stockage d’une technologie comme communiqué par le biais des informations d’assembly dans le contexte et du nœud XAML. code. Pour plus d’informations sur le concept de schéma XAML. consultez [contexte de schéma XAML par défaut et contexte de schéma XAML WPF](default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Flux de nœud XAML, lecteurs XAML et writers XAML  
 Pour comprendre le rôle joué par .NET Framework les services XAML dans la relation entre le langage XAML et des technologies spécifiques qui utilisent XAML comme langage, il est utile de comprendre le concept d’un flux de nœud XAML et comment ce concept forme l’API et correspondance. Le flux de nœud XAML est un élément de conception intermédiaire conceptuel entre une représentation de langage XAML et le graphique d’objet que le XAML représente ou définit.  
  
- Un lecteur XAML est une entité qui traite le XAML sous une forme et produit un flux de nœud XAML. Dans l’API, un lecteur XAML est représenté par la classe de base <xref:System.Xaml.XamlReader>.  
  
- Un writer XAML est une entité qui traite un flux de nœud XAML et produit autre chose. Dans l’API, un writer XAML est représenté par la classe de base <xref:System.Xaml.XamlWriter>.  
  
 Les deux scénarios les plus courants impliquant XAML sont le chargement du XAML pour instancier un graphique d’objet et l’enregistrement d’un graphique d’objet à partir d’une application ou d’un outil et la génération d’une représentation XAML (généralement sous forme de balisage enregistrée sous forme de fichier texte). Le chargement du XAML et la création d’un graphique d’objet sont souvent référencés dans cette documentation comme chemin de chargement. L’enregistrement ou la sérialisation d’un graphique d’objet existant dans XAML est souvent référencé dans cette documentation en tant que chemin d’enregistrement.  
  
 Le type le plus courant de chemin de chargement peut être décrit comme suit :  
  
- Commencez par une représentation XAML, au format XML encodé en UTF et enregistrée en tant que fichier texte.  
  
- Chargez ce XAML dans <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> est une sous-classe <xref:System.Xaml.XamlReader>.  
  
- Le résultat est un flux de nœud XAML. Vous pouvez accéder à des nœuds individuels du flux de nœud XAML à l’aide de <xref:System.Xaml.XamlXmlReader>API <xref:System.Xaml.XamlReader>  / . L’opération la plus courante ici consiste à avancer dans le flux de nœud XAML, en traitant chaque nœud à l’aide d’une métaphore « enregistrement actuel ».  
  
- Transmettez les nœuds résultants du flux de nœud XAML à une API <xref:System.Xaml.XamlObjectWriter>. <xref:System.Xaml.XamlObjectWriter> est une sous-classe <xref:System.Xaml.XamlWriter>.  
  
- Le <xref:System.Xaml.XamlObjectWriter> écrit un graphique d’objet, un objet à la fois, en fonction de la progression dans le flux de nœud XAML source. Cela s’effectue avec l’assistance d’un contexte de schéma XAML et d’une implémentation qui peut accéder aux assemblys et aux types d’un système de type de stockage et d’une infrastructure.  
  
- Appelez <xref:System.Xaml.XamlObjectWriter.Result%2A> à la fin du flux de nœud XAML pour obtenir l’objet racine du graphique d’objets.  
  
 Le type le plus courant de chemin d’enregistrement peut être décrit comme suit :  
  
- Commencez par le graphique d’objet d’une exécution complète de l’application, le contenu de l’interface utilisateur et l’état d’une exécution, ou un segment plus petit de la représentation d’objet d’une application globale au moment de l’exécution.  
  
- À partir d’un objet de démarrage logique, par exemple la racine d’une application ou la racine d’un document, chargez les objets dans <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> est une sous-classe <xref:System.Xaml.XamlReader>.  
  
- Le résultat est un flux de nœud XAML. Vous pouvez accéder à des nœuds individuels du flux de nœud XAML à l’aide de <xref:System.Xaml.XamlObjectReader> et <xref:System.Xaml.XamlReader> API. L’opération la plus courante ici consiste à avancer dans le flux de nœud XAML, en traitant chaque nœud à l’aide d’une métaphore « enregistrement actuel ».  
  
- Transmettez les nœuds résultants du flux de nœud XAML à une API <xref:System.Xaml.XamlXmlWriter>. <xref:System.Xaml.XamlXmlWriter> est une sous-classe <xref:System.Xaml.XamlWriter>.  
  
- Le <xref:System.Xaml.XamlXmlWriter> écrit du code XAML dans un encodage UTF XML. Vous pouvez l’enregistrer en tant que fichier texte, en tant que flux ou dans d’autres formes.  
  
- Appelez <xref:System.Xaml.XamlXmlWriter.Flush%2A> pour obtenir la sortie finale.  
  
 Pour plus d’informations sur les concepts de flux de nœud XAML, consultez [Présentation des concepts et structures du flux de nœud XAML](understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>La classe XamlServices  
 Il n’est pas toujours nécessaire de traiter un flux de nœud XAML. Si vous souhaitez un chemin de chargement de base ou un chemin d’enregistrement de base, vous pouvez utiliser les API de la classe <xref:System.Xaml.XamlServices>.  
  
- Diverses signatures de <xref:System.Xaml.XamlServices.Load%2A> implémentent un chemin de chargement. Vous pouvez charger un fichier ou un flux, ou vous pouvez charger un <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> ou <xref:System.Xaml.XamlReader> qui encapsulent votre entrée XAML en chargeant avec les API de ce lecteur.  
  
- Diverses signatures de <xref:System.Xaml.XamlServices.Save%2A> enregistrer un graphique d’objet et produire une sortie sous la forme d’un flux, d’un fichier ou d' <xref:System.Xml.XmlWriter>/<xref:System.IO.TextWriter> instance.  
  
- <xref:System.Xaml.XamlServices.Transform%2A> convertit le code XAML en liant un chemin de chargement et un chemin d’enregistrement comme une seule opération. Un contexte de schéma ou un système de type de stockage différent peut être utilisé pour <xref:System.Xaml.XamlReader> et <xref:System.Xaml.XamlWriter>, ce qui influence le mode de transformation du code XAML obtenu.  
  
 Pour plus d’informations sur l’utilisation de <xref:System.Xaml.XamlServices>, consultez [classe XamlServices et lecture ou écriture XAML de base](xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>Système de type XAML  
 Le système de type XAML fournit les API requises pour utiliser un nœud individuel donné d’un flux de nœud XAML.  
  
 <xref:System.Xaml.XamlType> est la représentation d’un objet, ce que vous traitez entre un nœud d’objet de début et un nœud d’objet de fin.  
  
 <xref:System.Xaml.XamlMember> est la représentation d’un membre d’un objet, ce que vous traitez entre un nœud de membre de début et un nœud de membre de fin.  
  
 Les API telles que <xref:System.Xaml.XamlType.GetAllMembers%2A> et <xref:System.Xaml.XamlType.GetMember%2A> et <xref:System.Xaml.XamlMember.DeclaringType%2A> rapportent les relations entre une <xref:System.Xaml.XamlType> et une <xref:System.Xaml.XamlMember>.  
  
 Le comportement par défaut du système de type XAML implémenté par .NET Framework les services XAML est basé sur le common language runtime (CLR) et l’analyse statique des types CLR dans les assemblys à l’aide de la réflexion. Par conséquent, pour un type CLR spécifique, l’implémentation par défaut du système de type XAML peut exposer le schéma XAML de ce type et de ses membres et le signaler en termes de système de type XAML. Dans le système de type XAML par défaut, le concept d’assignation des types est mappé sur l’héritage CLR, et les concepts des instances, des types valeur, etc., sont également mappés aux comportements et fonctionnalités de prise en charge du CLR.  
  
## <a name="reference-for-xaml-language-features"></a>Informations de référence sur les fonctionnalités du langage XAML  
 Pour prendre en charge XAML, les services XAML .NET Framework fournissent une implémentation spécifique des concepts de langage XAML tels qu’ils sont définis pour l’espace de noms XAML du langage XAML. Celles-ci sont documentées sous forme de pages de référence spécifiques. Les fonctionnalités de langage sont documentées du point de vue de la façon dont ces fonctionnalités de langage se comportent lorsqu’elles sont traitées par un lecteur XAML ou un writer XAML défini par .NET Framework les services XAML. Pour plus d'informations, consultez [XAML Namespace (x:) Language Features](xaml-namespace-x-language-features.md).
