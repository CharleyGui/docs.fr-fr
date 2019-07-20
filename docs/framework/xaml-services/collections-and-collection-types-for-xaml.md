---
title: Collections et types de collections pour XAML
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 63f6346837f77dbdbdcb4a90ec5af725be69ee02
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364341"
---
# <a name="collections-and-collection-types-for-xaml"></a>Collections et types de collections pour XAML

Cette rubrique explique comment définir des propriétés de types qui sont destinées à prendre en charge une collection et comment prendre en charge la syntaxe XAML pour instancier des éléments de collection en tant qu’éléments enfants d’un élément objet parent ou d’un élément de propriété.

## <a name="xaml-collection-concepts"></a>Concepts de la collection XAML

Conceptuellement, toute relation en XAML dans laquelle il y a plusieurs éléments enfants dans la portée d’un élément objet XAML ou d’un élément de propriété XAML doit être implémentée en tant que collection. Cette collection doit être associée à une propriété XAML particulière du type XAML qui est le parent dans cette relation. La propriété doit être une collection, car un processeur XAML s’attend à attribuer à chaque élément du balisage un élément récemment ajouté à la propriété de collection de stockage.

Au niveau du langage XAML, les spécifications exactes de la prise en charge des collections ne sont pas entièrement définies. Le concept qu’une collection peut être une liste ou un dictionnaire (mais pas les deux) est défini au niveau du langage XAML, mais les types de stockage représentant des listes ou des dictionnaires ne sont pas définis par le langage XAML.

Dans .NET Framework services XAML, le concept de prise en charge de la collection XAML est plus clairement défini en termes de types de stockage .NET Framework. Plus précisément, la prise en charge XAML pour les collections est basée sur plusieurs concepts de .NET Framework et API utilisés pour les listes et les dictionnaires en général .NET Framework la programmation.

1. L' <xref:System.Collections.IList> interface indique une collection de listes.

2. L' <xref:System.Collections.IDictionary> interface indique une collection de dictionnaires.

3. <xref:System.Array>représente un tableau et un tableau prend en <xref:System.Collections.IList> charge les méthodes.

Dans chacun de ces concepts de collection, un .NET Framework processeur XAML des services XAML s’attend à `Add` appeler la méthode sur une instance spécifique du type de la propriété de collection. Ou, dans un scénario de sérialisation, un processeur XAML produit des instances de type XAML discrètes pour chaque élément trouvé dans la liste, le dictionnaire ou le tableau en fonction du concept spécifique de chaque collection d’éléments. Il s’agit <xref:System.Collections.IList.Item%2A>des éléments suivants:; <xref:System.Collections.IDictionary.Item%2A>; Explicit<xref:System.Array.System%23Collections%23IList%23Item%2A> pour .<xref:System.Array>

## <a name="generic-collections"></a>Collections génériques

Les collections génériques peuvent être utiles pour la programmation .NET Framework générale et peuvent également être utilisées pour les propriétés de collection XAML. Toutefois <xref:System.Collections.Generic.IList%601> , les interfaces génériques et <xref:System.Collections.Generic.IDictionary%602> ne sont pas identifiées par .NET Framework les processeurs XAML des services XAML comme équivalents à la ou <xref:System.Collections.IDictionary>non générique <xref:System.Collections.IList> . Au lieu d’implémenter les interfaces, une approche recommandée pour les types de propriété de collection générique consiste <xref:System.Collections.Generic.List%601> à <xref:System.Collections.Generic.Dictionary%602>dériver des classes ou. Ces classes implémentent les interfaces non génériques et incluent donc la prise en charge attendue pour les collections XAML dans l’implémentation de base.

## <a name="read-only-collections-and-initialization-logic"></a>Collections en lecture seule et logique d’initialisation

Dans .NET Framework programmation, il s’agit d’un modèle de conception courant pour faire de toute propriété qui contient une valeur d’une collection sous la forme d’une collection en lecture seule. Ce modèle permet à l’instance qui possède la propriété de collection de mieux contrôler ce qui arrive à la collection. Plus précisément, le modèle empêche le remplacement accidentel de l’intégralité de la collection préexistante en définissant la propriété. Dans ce modèle, tout accès à la collection par les appelants doit plutôt être effectué en appelant les méthodes ou les propriétés prises en charge par le type de collection et/ou les <xref:System.Collections.IList>interfaces de collection pertinentes telles que.

L’utilisation de ce modèle implique que toute classe qui expose une propriété de collection en lecture seule doit d’abord initialiser cette propriété pour contenir une collection vide. En général, l’initialisation est effectuée dans le cadre du comportement de construction de la classe. Pour être utile pour XAML, il est important que cette logique soit toujours référencée par le constructeur sans paramètre, car XAML appelle généralement le constructeur sans paramètre avant de traiter les propriétés (propriétés de collection ou autre).

## <a name="xaml-type-system-support-and-collections"></a>Prise en charge et collections du système de type XAML

Au-delà des mécanismes de base de l’analyse du code XAML et du remplissage ou de la sérialisation des propriétés de collection, le système de type XAML implémenté dans .NET Framework services XAML comprend plusieurs fonctionnalités de conception qui se rapportent aux collections en XAML.

1. <xref:System.Xaml.XamlType.IsCollection%2A>retourne la valeur true si le type XAML est stocké par un type qui fournit la prise en charge de la collection XAML.

2. <xref:System.Xaml.XamlType.IsDictionary%2A>et <xref:System.Xaml.XamlType.IsArray%2A> peuvent identifier plus précisément le mode de collecte pris en charge par le type XAML. Pour les processeurs XAML personnalisés basés sur .NET Framework les services XAML et le système de type XAML, mais non <xref:System.Xaml.XamlWriter> basés sur des implémentations existantes, il peut être nécessaire de savoir quel mode de collecte est utilisé pour savoir quelle méthode appeler pour traitement de la collection.

3. Chacune des valeurs de propriété précédentes est potentiellement influencée par les substitutions <xref:System.Xaml.XamlType.LookupCollectionKind%2A> de sur un type XAML.
