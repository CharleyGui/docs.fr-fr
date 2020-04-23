---
title: Traitement des espaces blancs en XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 05f28c9115326424164b92e1b704c52bba31cf35
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071604"
---
# <a name="white-space-processing-in-xaml"></a>Traitement des espaces blancs en XAML

Les règles linguistiques pour XAML stipulent que [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] l’espace blanc important doit être traité par une mise en œuvre du processeur. Cet article documente ces règles linguistiques XAML. Il documente également la manipulation supplémentaire [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] de l’espace blanc qui est définie par la mise en œuvre du processeur XAML et l’auteur XAML pour la sérialisation.

## <a name="white-space-definition"></a>Définition de l’espace blanc

Conformément à XML, les [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] caractères de l’espace blanc sont l’espace, l’alimentation en ligne et l’onglet. Celles-ci correspondent aux valeurs Unicode 0020, 000A et 0009 respectivement.

## <a name="white-space-normalization"></a>Normalisation de l’espace blanc

Par défaut, la normalisation de l’espace blanc suivant se produit lorsqu’un [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processeur traite un [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] fichier :

1. Les caractères de saut de ligne entre les caractères d'Extrême-Orient sont supprimés. Consultez la section « Caractères d'Extrême-Orient », plus loin dans cette rubrique, pour obtenir une définition de ce terme.

2. Tous les caractères de l’espace blanc (espace, fil de ligne, onglet) sont convertis en espaces.

3. Tous les espaces consécutifs sont supprimés et remplacés par un espace.

4. Un espace qui suit immédiatement la balise de début est supprimé.

5. Un espace qui précède immédiatement la balise de fin est supprimé.

La « valeur par défaut » correspond à l'état désigné par la valeur par défaut de l'attribut [xml:space](xml-space-handling.md) .

## <a name="white-space-in-inner-text-and-string-primitives"></a>Espace blanc dans le texte intérieur, et primitives de chaîne

Les règles de normalisation précédentes s'appliquent au texte interne que l'on trouve dans les éléments XAML. Après la normalisation, un processeur XAML convertit tout texte interne en un type approprié, comme suit :

- Si le type de la propriété n'est pas une collection, mais n'est pas directement un type <xref:System.Object> , le processeur XAML tente de convertir en ce type à l'aide de son convertisseur de type. En cas d'échec de la conversion, une erreur de compilation survient.

- Si le type de la propriété est une collection et que le texte interne est contigu (aucune balise d'élément intermédiaire), le texte interne est analysé comme un élément <xref:System.String>String. Si le type de collection ne peut pas accepter <xref:System.String>, une erreur de compilation est également générée.

- Si le type de la propriété est <xref:System.Object>, le texte interne est analysé comme un objet <xref:System.String>unique. En cas de balises d'élément intermédiaires, une erreur de compilation est générée car le type <xref:System.Object> implique un objet unique (<xref:System.String> ou autre).

- Si le type de la propriété est une collection et que le texte interne n'est pas contigu, la première sous-chaîne est convertie en <xref:System.String> et ajoutée en tant qu'élément de collection, l'élément intermédiaire est ajouté en tant qu'élément de collection et la sous-chaîne de fin (le cas échéant) est ajoutée à la collection comme troisième élément <xref:System.String> .

## <a name="preserving-white-space"></a>Préserver l’espace blanc

Il existe plusieurs techniques pour préserver [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] l’espace blanc dans [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] la source pour une présentation éventuelle qui ne sont pas affectées par la normalisation de l’espace blanc processeur.

**xml:space"preserve"**: Spécifier cet attribut au niveau de l’élément où la préservation de l’espace blanc est souhaitée. Cela permet de conserver l'ensemble de l'espace blanc, ce qui inclut les espaces pouvant être ajoutés par des applications d'édition de code pour imprimer correctement des éléments comme une imbrication visuellement intuitive. Toutefois, le rendu de ces espaces est déterminé par le modèle de contenu pour l'élément conteneur. Évitez de `xml:space="preserve"` spécifier au niveau de la racine parce que la plupart des modèles d’objets ne considèrent pas l’espace blanc comme significatif indépendamment de la façon dont vous définissez l’attribut. Le fait de définir `xml:space` de façon globale peut avoir des conséquences sur les performances de traitement XAML (en particulier, la sérialisation) dans certaines implémentations. Il est préférable de ne définir l’attribut spécifiquement qu’au niveau des éléments qui rendent l’espace blanc dans les cordes, ou sont des collections importantes en espace blanc.

**Entités et espaces non cassés**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] prend en charge le placement de toute entité Unicode dans un modèle d’objet texte. Vous pouvez utiliser des entités dédiées telles que \#l’espace non-rupture (&160; dans l’encodage UTF-8). Vous pouvez également utiliser des contrôles de texte enrichi qui prennent en charge les caractères d'espace insécable. Soyez prudent lorsque vous utilisez des entités pour simuler des caractéristiques de mise en page telles que la mise en retrait, car la sortie à l'exécution des entités variera suivant que le nombre de facteurs est plus élevé que les fonctionnalités de mise en page générales, telles que l'utilisation appropriée de panneaux et de marges. Par exemple, les entités sont mappées aux polices et peuvent changer de taille en fonction de la police sélectionnée par l'utilisateur.

## <a name="east-asian-characters"></a>Personnages d’Asie de l’Est

Les « caractères d’Asie de l’Est » sont définis comme un ensemble de gammes de caractères Unicode de U-20000 à U-2FFFD et U-30000 à U-3FFFD. Ce sous-ensemble est parfois également appelé « idéogrammes CJK ». Pour plus d’informations, consultez <https://www.unicode.org>.

## <a name="white-space-and-text-content-models"></a>Modèles de contenu d’espace blanc et de texte

Dans la pratique, la préservation de l’espace blanc ne concerne qu’un sous-ensemble de tous les modèles de contenu possibles. Ce sous-ensemble se compose des modèles de contenu qui peuvent prendre un type <xref:System.String> singleton d'une certaine manière, une collection <xref:System.String> dédiée ou un mélange de <xref:System.String> et d'autres types dans une collection <xref:System.Collections.IList> ou <xref:System.Collections.Generic.ICollection%601> .

### <a name="white-space-and-text-content-models-in-wpf"></a>Modèles de contenu d’espace blanc et de texte dans WPF

À des fins d'illustration, le reste de cette section référence des types particuliers définis par WPF. Les caractéristiques de manipulation de l’espace blanc qui sont décrites dans cet article sont pertinentes à la fois pour .NET XAML Services et WPF. Pour voir ce comportement en action, il peut se révéler utile d'expérimenter des balises XAML WPF et de consulter les résultats dans un graphique d'objets, puis de procéder une nouvelle fois à une désérialisation en balises.

Même pour les modèles de contenu qui peuvent prendre des chaînes, le comportement par défaut dans ces modèles de contenu est que tout espace blanc qui reste n’est pas traité comme significatif. Par exemple, <xref:System.Windows.Controls.ListBox> <xref:System.Collections.IList>prend un , mais l’espace blanc <xref:System.Windows.Controls.ListBoxItem>(comme les filoires entre chaque ) n’est pas conservé et non rendu. Si vous tentez d'utiliser des sauts de ligne comme séparateurs entre des chaînes pour les éléments <xref:System.Windows.Controls.ListBoxItem> , cela ne fonctionne pas du tout ; les chaînes séparées par des sauts de ligne sont traitées comme une chaîne et un élément.

Les collections qui traitent l’espace blanc comme significative font généralement partie du modèle de document de flux. La collection principale qui soutient le <xref:System.Windows.Documents.InlineCollection>comportement de préservation de l’espace blanc est . Cette classe de collecte <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>est déclarée avec le ; lorsque cet attribut est [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] trouvé, le processeur traitera l’espace blanc dans la collection comme significatif. La combinaison `xml:space="preserve"` de l’espace blanc et dans une <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> collection dénotée est que tout l’espace blanc est préservé et rendu. La combinaison `xml:space="default"` et l’espace blanc dans un <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> provoque la normalisation initiale de l’espace blanc décrite plus tôt, ce qui laisse un espace dans certaines positions, et ces espaces sont préservés et rendus. À vous de déterminer le comportement souhaité et d'utiliser `xml:space` de manière sélective pour activer le comportement de votre choix.

En outre, certains éléments en ligne qui évoquent une rupture de ligne dans un modèle de document de flux ne devraient délibérément pas introduire un espace supplémentaire, même dans une collection significative d’espace blanc. Par exemple, <xref:System.Windows.Documents.LineBreak> l’élément a \<le même but que l’étiquette BR/> en HTML, et pour la lisibilité dans la balisage, généralement a <xref:System.Windows.Documents.LineBreak> est séparé de tout texte ultérieur par un fil de ligne rédigé. Ce saut de ligne ne doit pas être normalisé pour devenir un espace de début dans la ligne suivante. Pour permettre ce comportement, la <xref:System.Windows.Documents.LineBreak> définition <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>de classe pour l’élément applique le , qui est ensuite interprété par le processeur pour signifier que l’espace [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] blanc entourant <xref:System.Windows.Documents.LineBreak> est toujours coupé.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble XAML (WPF)](../fundamentals/xaml.md)
- [Entités de caractère XML et XAML](xml-character-entities.md)
- [xml: manipulation de l’espace dans XAML](xml-space-handling.md)
