---
title: Classe XAMLServices et lecture ou écriture XAML de base
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: 264a8c4abcf9a7efceb7c7accd786495d35476e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071877"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>Classe XAMLServices et lecture ou écriture XAML de base

<xref:System.Xaml.XamlServices>est une classe fournie par .NET qui peut être utilisé pour répondre aux scénarios XAML qui ne nécessitent pas un accès spécifique au flux de nœuds XAML ou à des informations système de type XAML obtenues à partir de ces nœuds. <xref:System.Xaml.XamlServices>L’API peut être `Load` résumée comme suit : `Parse` ou `Save` pour prendre en charge un `Transform` chemin de charge XAML, pour prendre en charge un chemin d’enregistrement XAML, et pour fournir une technique qui relie un chemin de charge et de sauver le chemin. `Transform` peut être utilisé pour passer d'un schéma XAML à un autre. Cette rubrique résume chacune de ces classifications d'API et décrit les différences qui existent entre des surcharges de méthode particulières.

## <a name="load"></a>Load

Différentes surcharges de <xref:System.Xaml.XamlServices.Load%2A> implémentent la logique complète d'un chemin de chargement. Le chemin de chargement utilise du code XAML sous une certaine forme et exporte un flux de nœud XAML. La plupart de ces chemins de chargement utilise du code XAML sous la forme d'un fichier texte XML encodé. Toutefois, vous pouvez aussi charger un flux général ou une source XAML préchargée qui est déjà contenue dans une implémentation de <xref:System.Xaml.XamlReader> différente.

La surcharge la plus simple pour la plupart des scénarios est <xref:System.Xaml.XamlServices.Load%28System.String%29>. Cette surcharge possède un paramètre `fileName` qui correspond simplement au nom d'un fichier texte contenant le code XAML à charger. Elle convient particulièrement aux scénarios d'application comme pour les applications de confiance totale qui ont précédemment sérialisé l'état ou les données sur l'ordinateur local. Elle est également utile pour les infrastructures dans lesquelles vous définissez le modèle d'application et souhaitez charger l'un des fichiers standard qui définit le comportement de l'application, en démarrant l'interface utilisateur ou d'autres fonctions définies par l'infrastructure qui utilisent XAML.

<xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29> dispose de scénarios similaires. Cette surcharge peut s'avérer utile si l'utilisateur choisit les fichiers à charger, car un <xref:System.IO.Stream> est une sortie fréquente d'autres API <xref:System.IO> qui peuvent accéder à un système de fichiers. Vous pouvez également accéder aux sources XAML par le biais de téléchargements asynchrones ou d'autres techniques de réseau qui fournissent également un flux. (Le chargement d'un flux de données ou d'une source choisie par l'utilisateur peut avoir des conséquences sur la sécurité. Pour plus d’informations, consultez [XAML Security Considerations](security-considerations.md).)

<xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29>et <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> sont des surcharges qui s’appuient sur les lecteurs de formats de versions précédentes de .NET. Pour utiliser ces surcharges, vous devriez avoir déjà `Create` créé une instance de lecteur et utiliser son API pour charger le XAML sous la forme pertinente (texte ou XML). Si vous avez déjà déplacé des pointeurs d'enregistrement dans les autres lecteurs ou exécuté d'autres opérations les concernant, cela ne pose aucun problème. La logique du chemin de chargement de <xref:System.Xaml.XamlServices.Load%2A> traite toujours l'entrée XAML entière à partir de la racine. Les scénarios suivants pourraient justifier l’utilisation de ces surcharges :

- les aires de conception dans lesquelles vous fournissez des fonctions d'édition XAML simples à partir d'un éditeur de texte XML existant ;

- les variantes des scénarios <xref:System.IO> de base dans lesquels vous utilisez les lecteurs dédiés pour ouvrir des fichiers ou des flux. Votre logique procède à un contrôle ou un traitement rudimentaire du contenu avant de tenter de le charger en tant que code XAML.

Vous pouvez charger un fichier ou un <xref:System.Xml.XmlReader>flux, ou vous pouvez charger un , , <xref:System.IO.TextReader>ou <xref:System.Xaml.XamlReader> qui enveloppe votre entrée XAML en chargeant avec les API du lecteur.

En interne, chacune des surcharges précédentes correspond finalement à <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>, avec le <xref:System.Xml.XmlReader> passé qui est utilisé pour créer un <xref:System.Xaml.XamlXmlReader>.

La signature `Load` permettant des scénarios plus avancés est <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>. Vous pouvez utiliser cette signature pour l'un des cas suivants :

- Vous avez défini votre propre <xref:System.Xaml.XamlReader>implémentation d’un .

- Vous devez spécifier des paramètres pour <xref:System.Xaml.XamlReader> qui diffèrent des paramètres par défaut.

Exemples de paramètres non par défaut :

<xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>\
<xref:System.Xaml.XamlReaderSettings.BaseUri%2A>\
<xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>\
<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>\
<xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>.

Le lecteur par défaut de <xref:System.Xaml.XamlServices> est <xref:System.Xaml.XamlXmlReader>. Si vous fournissez vos propres <xref:System.Xaml.XamlXmlReader> paramètres, ce qui <xref:System.Xaml.XamlXmlReaderSettings>suit sont des propriétés à définir non-default :

<xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>

## <a name="parse"></a>Analyser

<xref:System.Xaml.XamlServices.Parse%2A> s'apparente à `Load` en ce sens que c'est une API de chemin de chargement qui crée un flux de nœud XAML à partir de l'entrée XAML. Toutefois, dans ce cas, l'entrée XAML est fournie directement sous la forme d'une chaîne qui contient tout le code XAML à charger. <xref:System.Xaml.XamlServices.Parse%2A> est une approche légère plus appropriée pour les scénarios d'application que les scénarios d'infrastructure. Pour plus d’informations, consultez <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A>n’est <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> qu’un <xref:System.IO.StringReader> appel enveloppé qui implique un interne.

## <a name="save"></a>Enregistrer

Diverses surcharges <xref:System.Xaml.XamlServices.Save%2A> d’implémenter le chemin d’enregistrement. Les méthodes <xref:System.Xaml.XamlServices.Save%2A> ont toutes un graphique d'objets comme entrée et génère un flux, un fichier ou une instance <xref:System.Xml.XmlWriter>/<xref:System.IO.TextWriter> comme sortie.

L'objet en entrée est supposé être l'objet racine d'une représentation d'objet. Il peut s'agir de la racine unique d'un objet métier, de la racine d'une arborescence d'objets pour la page d'un scénario d'interface utilisateur, de la surface de modification active d'un outil de conception ou encore d'autres concepts d'objet racine appropriés pour les scénarios.

Dans de nombreux scénarios, l’arbre objet que vous enregistrez est <xref:System.Xaml.XamlServices.Load%2A> lié à une opération originale qui a chargé XAML avec ou avec d’autres API mis en œuvre par un modèle de cadre/application. Il peut y avoir des différences capturées dans l'arborescence d'objets dues à des modifications d'état, des modifications dans lesquelles votre application a capturé des paramètres d'exécution auprès d'un utilisateur, du code XAML modifié car votre application est une aire de conception XAML, etc. Avec ou sans modification, le concept consistant à d'abord charger le code XAML à partir du balisage, puis à le réenregistrer et à comparer les deux formes de balisage XAML est parfois appelé représentation « aller-retour » du code XAML.

Le défi lié à l'enregistrement et à la sérialisation d'un objet complexe qui est défini dans une forme de balisage réside dans l'obtention d'un équilibre entre une représentation complète sans perte d'informations et un excès de commentaires rendant le code XAML moins explicite. De plus, différents clients pour XAML peuvent avoir des définitions ou des attentes différentes concernant la définition de l'équilibre. Les API <xref:System.Xaml.XamlServices.Save%2A> représentent une définition de cet équilibre. Les API <xref:System.Xaml.XamlServices.Save%2A> utilisent un contexte de schéma XAML disponible et les caractéristiques CLR par défaut de <xref:System.Xaml.XamlType>, de <xref:System.Xaml.XamlMember>et d'autres concepts d'intrinsèque XAML et de système de type XAML pour déterminer si certaines constructions de flux de nœud XAML peuvent être optimisées lorsqu'elles sont réenregistrées dans le balisage. Par exemple, les chemins d'enregistrement <xref:System.Xaml.XamlServices> peuvent utiliser un contexte de schéma XAML par défaut basé sur CLR pour résoudre <xref:System.Xaml.XamlType> pour des objets, déterminer une propriété <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>, puis omettre des balises d'éléments de propriété lors de l'écriture de la propriété dans le contenu XAML de cet objet.

<a name="transform"></a>
## <a name="transform"></a>Transformer

<xref:System.Xaml.XamlServices.Transform%2A> convertit ou transforme le code XAML en associant un chemin de chargement et un chemin d'enregistrement dans le cadre d'une seule opération. Un contexte de schéma ou un système de types de stockage différent peut être utilisé pour <xref:System.Xaml.XamlReader> et <xref:System.Xaml.XamlWriter>, ce qui est l'élément qui influence le mode de transformation du code XAML obtenu. Cela fonctionne bien pour les opérations de transformation générales.

Pour les opérations qui reposent sur l'examen de chaque nœud dans un flux de nœud XAML, vous n'utiliseriez généralement pas <xref:System.Xaml.XamlServices.Transform%2A>. Au lieu de cela, vous devez définir votre propre série d'opérations chemin de chargement-chemin d'enregistrement et lancer votre propre logique. Dans l'un des chemins, utilisez une paire lecteur XAML/writer XAML autour de votre propre boucle de nœud. Par exemple, chargez le code XAML initial à l'aide de <xref:System.Xaml.XamlXmlReader> et entrez dans les nœuds avec des appels à <xref:System.Xaml.XamlXmlReader.Read%2A> successifs. En opérant au niveau du flux de nœud XAML, vous pouvez maintenant ajuster des nœuds individuels (types, membres ou autres nœuds) pour appliquer une transformation ou laisser le nœud en l'état. Envoyez ensuite le nœud à l'API `Write` pertinente d'un <xref:System.Xaml.XamlObjectWriter> et écrivez l'objet. Pour plus d'informations, consultez [Understanding XAML Node Stream Structures and Concepts](understanding-xaml-node-stream-structures-and-concepts.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Xaml.XamlObjectWriter>
- <xref:System.Xaml.XamlServices>
- [Services XAML](../../../api/index.md)
