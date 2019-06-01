---
title: Services XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: c99e44c7d373d050113687753d4f18eca27e0de5
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457399"
---
# <a name="xaml-services"></a>Services XAML
Cette rubrique décrit les fonctionnalités d’un ensemble de la technologie .NET Framework XAML appelé des Services. La plupart des services et API décrits se trouvent dans l’assembly System.Xaml, qui a été introduit avec l’ensemble de .NET Framework 4 .NET des assemblys de base. Les services incluent des fabriques de lecteurs et writers, classes de schéma et de prise en charge du schéma, attribution de classes, de support intrinsèque du langage XAML et d’autres fonctionnalités de langage XAML.  
  
## <a name="about-this-documentation"></a>À propos de cette Documentation  
 Documentation conceptuelle pour les Services XAML .NET Framework suppose que vous avez une expérience précédente avec le langage XAML et comment il peut s’appliquer à un framework spécifique, par exemple [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ou Windows Workflow Foundation, ou une fonctionnalité spécifique de technologie zone, par exemple la personnalisation de la build fonctionnalités dans <xref:Microsoft.Build.Framework.XamlTypes>. Cette documentation ne tente pas d’expliquer les principes fondamentaux de XAML comme un langage de balisage, terminologie de la syntaxe XAML ou une autre partie introductive. Au lieu de cela, cette documentation se concentre sur l’utilisation spécifique des Services XAML .NET Framework qui sont activés dans la bibliothèque de l’assembly System.Xaml. La plupart de ces API est destinées aux scénarios d’extensibilité et intégration de langage XAML. Cela peut inclure les éléments suivants :  
  
- Extension des capacités de la base lecteurs XAML ou les writers XAML (traitement direct du flux de nœud XAML ; dériver votre propre lecteur XAML ou un writer XAML).  
  
- Définition de types personnalisés utilisables de XAML qui n’ont pas de dépendances de framework spécifique et en attribuant les types pour communiquer leur XAML type caractéristiques du système pour les Services XAML .NET Framework.  
  
- Hébergement XAML lecteurs ou writers XAML en tant que composant d’une application, tel qu’un concepteur visuel ou d’un éditeur interactif pour les sources de balisage XAML.  
  
- Écriture des convertisseurs de valeur XAML (extensions de balisage, les convertisseurs de type pour les types personnalisés).  
  
- Définition d’un contexte de schéma XAML personnalisé (à l’aide d’autres techniques de chargement d’assemblys pour les sources de type de sauvegarde ; à l’aide de techniques de recherche de types connus au lieu de toujours refléter des assemblys à l’aide de concepts d’assemblys chargés qui n’utilisent pas le CLR `AppDomain` et son modèle de sécurité associé).  
  
- Étendre le système de type XAML base.  
  
- À l’aide de la `Lookup` ou `Invoker` l’évaluation des stockages de type et système de type de techniques pour influencer le XAML.  
  
 Si vous recherchez une partie introductive dans XAML en tant que langage, vous pouvez essayer de [vue d’ensemble de XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md). Cette rubrique aborde XAML pour un public qui est une nouveauté pour [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] et également à l’aide de balisage XAML et les fonctionnalités du langage XAML. Un autre document utile est la partie introductive dans le [spécification du langage XAML](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>Les Services XAML .NET framework et System.Xaml dans l’Architecture .NET  
 Dans les versions précédentes de Microsoft .NET Framework, prend en charge des fonctionnalités du langage XAML a été implémentée par les infrastructures qui reposant sur Microsoft .NET Framework ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Windows Workflow Foundation et Windows Communication Foundation (WCF)) et par conséquent variées dans son comportement et l’API utilisée selon l’infrastructure spécifique que vous utilisiez. Cela inclus le XAML analyseur et son objet de graphiquement mécanisme de création, intrinsèques du langage XAML, prise en charge de la sérialisation et ainsi de suite.  
  
 Dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], les Services XAML .NET Framework et l’assembly System.Xaml définissent une grande partie de ce qui est nécessaire pour prendre en charge des fonctionnalités de langage XAML. Cela inclut les classes de base pour les lecteurs XAML et les writers XAML. La fonctionnalité la plus importante ajoutée aux Services XAML .NET Framework qui n’était pas présent dans un des implémentations XAML spécifiques à l’infrastructure est une représentation de système de type pour XAML. La représentation sous forme de système de type présente XAML d’une manière orientée objet qui se concentre sur les fonctionnalités XAML sans définir de dépendances sur des fonctions spécifiques des infrastructures.  
  
 Le système de type XAML n’est pas limité par la forme de balisage ou les caractéristiques d’exécution de l’origine XAML ; ni est-il limité par n’importe quel système de type de stockage spécifique. Le système de type XAML inclut des représentations sous forme de l’objet pour les types, membres, les contextes de schéma XAML, les concepts de niveau XML et d’autres concepts du langage XAML ou XAML intrinsèques. L’utilisation ou l’extension du système de type XAML permet de dériver de classes telles que les lecteurs XAML et les writers XAML et étendre les fonctionnalités des représentations XAML dans des fonctionnalités spécifiques activées par une infrastructure, une technologie ou une application qui consomme ou émet le XAML. Le concept d’un contexte de schéma XAML permet des opérations d’écriture de graphique d’objet pratique à partir de la combinaison d’une implémentation de writer d’objet XAML, sauvegarde système de type d’une technologie communiqués par le biais des informations d’assembly dans le contexte et le nœud XAML source. Pour plus d’informations sur le concept de schéma XAML. consultez [contexte de schéma XAML par défaut et contexte de schéma XAML WPF](default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Flux de nœud XAML, les lecteurs XAML et les Writers XAML  
 Pour comprendre le rôle joué par les Services XAML .NET Framework dans la relation entre le langage XAML et les technologies spécifiques qui utilisent XAML en tant que langage, il est utile de comprendre le concept d’un flux de nœud XAML et la manière qui influe sur l’API et terminologie. Le flux de nœud XAML est un intermédiaire conceptuel entre une représentation de langage XAML et le graphique d’objet qui représente le XAML ou le définit.  
  
- Un lecteur XAML est une entité qui traite le XAML dans une certaine forme et génère un flux de nœud XAML. Dans l’API, un lecteur XAML est représenté par la classe de base <xref:System.Xaml.XamlReader>.  
  
- Un writer XAML est une entité qui traite un flux de nœud XAML et produit une autre chose. Dans l’API, un writer XAML est représenté par la classe de base <xref:System.Xaml.XamlWriter>.  
  
 Les deux scénarios courants impliquant XAML sont le chargement XAML pour instancier un graphique d’objet et l’enregistrement d’un graphique d’objet à partir d’une application ou un outil et produire une représentation XAML (généralement sous forme de balisage enregistré en tant que fichier texte). Le chargement de XAML et la création d’un graphique d’objet sont souvent appelée dans cette documentation en tant que le chemin de chargement. L’enregistrement ou la sérialisation d’un graphique d’objet existant à XAML est souvent appelée dans cette documentation comme chemin d’accès.  
  
 Le type de chemin de chargement le plus courant peut être décrit comme suit :  
  
- Démarrez avec une représentation XAML, au format XML au format UTF et enregistré sous la forme d’un fichier texte.  
  
- Chargez ce XAML dans <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> est un <xref:System.Xaml.XamlReader> sous-classe.  
  
- Le résultat est un flux de nœud XAML. Vous pouvez accéder à des nœuds individuels du flux de nœud XAML à l’aide <xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> API. L’opération la plus classique ici est d’avancer dans le flux de nœud XAML, traitement de chaque nœud à l’aide d’un « enregistrement » métaphore.  
  
- Passez les nœuds obtenus à partir du flux de nœud XAML pour un <xref:System.Xaml.XamlObjectWriter> API. <xref:System.Xaml.XamlObjectWriter> est un <xref:System.Xaml.XamlWriter> sous-classe.  
  
- Le <xref:System.Xaml.XamlObjectWriter> écrit un graphique d’objet, un seul objet à la fois, conformément à la progression via le flux de nœud XAML source. Pour cela, avec l’aide d’un contexte de schéma XAML et une implémentation qui peut accéder aux assemblys et les types d’un système de type de stockage et le framework.  
  
- Appelez <xref:System.Xaml.XamlObjectWriter.Result%2A> à la fin du flux de nœud XAML pour obtenir l’objet racine du graphique d’objets.  
  
 Le type le plus courant de chemin d’enregistrement peut être décrit comme suit :  
  
- Démarrer avec le graphique d’objet d’une heure de l’ensemble de l’application s’exécuter, le contenu de l’interface utilisateur et l’état d’une durée d’exécution, ou un plus petit segment de la représentation d’objet d’une application globale en cours d’exécution.  
  
- À partir d’un objet de début logique, comme une racine de l’application ou de la racine du document, chargez les objets dans <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> est un <xref:System.Xaml.XamlReader> sous-classe.  
  
- Le résultat est un flux de nœud XAML. Vous pouvez accéder à des nœuds individuels du flux de nœud XAML à l’aide <xref:System.Xaml.XamlObjectReader> et <xref:System.Xaml.XamlReader> API. L’opération la plus classique ici est d’avancer dans le flux de nœud XAML, traitement de chaque nœud à l’aide d’un « enregistrement » métaphore.  
  
- Passez les nœuds obtenus à partir du flux de nœud XAML pour un <xref:System.Xaml.XamlXmlWriter> API. <xref:System.Xaml.XamlXmlWriter> est un <xref:System.Xaml.XamlWriter> sous-classe.  
  
- Le <xref:System.Xaml.XamlXmlWriter> écrit XAML dans un UTF XML encodage. Vous pouvez l’enregistrer comme un fichier texte, en tant que flux, ou dans d’autres formes.  
  
- Appelez <xref:System.Xaml.XamlXmlWriter.Flush%2A> pour obtenir la sortie finale.  
  
 Pour plus d’informations sur les concepts de flux de nœud XAML, consultez [Understanding XAML Node Stream Structures et des Concepts](understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>Classe XamlServices  
 Il n’est pas toujours nécessaire de traiter un flux de nœud XAML. Si vous souhaitez un chemin de chargement de base ou un chemin d’enregistrement de base, vous pouvez utiliser des API dans le <xref:System.Xaml.XamlServices> classe.  
  
- Diverses signatures de <xref:System.Xaml.XamlServices.Load%2A> implémenter un chemin de chargement. Vous pouvez charger un fichier ou un flux, ou encore un <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> ou <xref:System.Xaml.XamlReader> dans un wrapper votre entrée XAML en chargeant avec les API de ce lecteur.  
  
- Diverses signatures de <xref:System.Xaml.XamlServices.Save%2A> enregistrer un graphique d’objets et génère un résultat sous forme de flux, fichier, ou <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> instance.  
  
- <xref:System.Xaml.XamlServices.Transform%2A> convertit XAML en liant un chemin de chargement et l’enregistrer chemin d’accès comme une seule opération. Un contexte de schéma ou d’un système de type de stockage différent peut être utilisé pour <xref:System.Xaml.XamlReader> et <xref:System.Xaml.XamlWriter>, qui est l’élément qui influence la façon dont le XAML qui en résulte est transformé.  
  
 Pour plus d’informations sur l’utilisation <xref:System.Xaml.XamlServices>, consultez [classe XAMLServices et lecture de base XAML ou écriture](xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>Système de Type XAML  
 Le système de type XAML fournit les API qui sont requises pour fonctionner avec un nœud individuel donné d’un flux de nœud XAML.  
  
 <xref:System.Xaml.XamlType> est la représentation sous forme d’un objet - ce que vous traitez entre un nœud objet de début et un nœud objet de fin.  
  
 <xref:System.Xaml.XamlMember> est la représentation sous forme d’un membre d’un objet - ce que vous traitez entre un nœud membre de début et un nœud membre de fin.  
  
 API telles que <xref:System.Xaml.XamlType.GetAllMembers%2A> et <xref:System.Xaml.XamlType.GetMember%2A> et <xref:System.Xaml.XamlMember.DeclaringType%2A> signalent les relations entre un <xref:System.Xaml.XamlType> et <xref:System.Xaml.XamlMember>.  
  
 Le comportement par défaut du système de type XAML tel qu’implémenté par les Services XAML .NET Framework est basé sur le common language runtime (CLR) et analyse statique des types CLR dans les assemblys en utilisant la réflexion. Par conséquent, pour un type CLR spécifique, l’implémentation par défaut du système de type XAML peut exposer le schéma XAML de ce type et ses membres et le signaler en termes du système de type XAML. Dans le système de type XAML par défaut, le concept de l’assignabilité de types est mappé à l’héritage et les concepts des instances, les types valeur et ainsi de suite sont également mappés aux comportements et les fonctionnalités du CLR prise en charge.  
  
## <a name="reference-for-xaml-language-features"></a>Référence des fonctionnalités de langage XAML  
 Prise en charge XAML, les Services XAML .NET Framework fournit une implémentation spécifique des concepts du langage XAML tel que défini pour l’espace de noms XAML du langage XAML. Ces résultats sont décrits comme des pages de référence spécifique. Les fonctionnalités de langage sont documentées dans la perspective de la façon dont elles se comportent lorsqu’ils sont traités par un lecteur XAML ou un writer XAML défini par les Services XAML .NET Framework. Pour plus d’informations, consultez [XAML Namespace (x :)) Fonctionnalités de langage](xaml-namespace-x-language-features.md).
