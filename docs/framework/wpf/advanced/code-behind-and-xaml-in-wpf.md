---
title: Code-Behind et XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 32283d5b81bf92999a97711ded13a8b533ae3028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145343"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Code-behind et XAML dans WPF
<a name="introduction"></a>Code-derrière est un terme utilisé pour décrire le code qui est [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] joint avec des objets définis par le balisage, quand une page est compilée de balisage. Ce sujet décrit les exigences pour code-derrière ainsi qu’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]mécanisme alternatif de code inline pour le code dans .  
  
 Cette rubrique contient les sections suivantes :  
  
- [Conditions préalables](#Prerequisites)  
  
- [Code-Behind et la langue XAML](#codebehind_and_the_xaml_language)  
  
- [Code-derrière, gestionnaire d’événements, et les exigences partielles de classe dans WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [Inline Code Limitations](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Ce sujet suppose que vous avez lu le [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md) et que vous avez une certaine connaissance de base de la programmation CLR et orientée objet.  
  
<a name="codebehind_and_the_xaml_language"></a>
## <a name="code-behind-and-the-xaml-language"></a>Code-Behind et la langue XAML  
 La langue XAML inclut des fonctionnalités de niveau linguistique qui permettent d’associer des fichiers de code avec des fichiers de balisage, du côté du fichier de balisage. Plus précisément, la langue XAML définit les caractéristiques linguistiques [x:Class Directive](../../../desktop-wpf/xaml-services/xclass-directive.md), [x:Subclass Directive](../../../desktop-wpf/xaml-services/xsubclass-directive.md), et [x:ClassModifier Directive](../../../desktop-wpf/xaml-services/xclassmodifier-directive.md). La façon exacte dont le code doit être produit et la façon d’intégrer le balisage et le code ne fait pas partie de ce que la langue XAML précise. Il appartient à des cadres tels que WPF de déterminer comment intégrer le code, comment utiliser XAML dans les modèles d’application et de programmation, et les actions de construction ou tout autre support que tout cela nécessite.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Code-derrière, gestionnaire d’événements, et les exigences partielles de classe dans WPF  
  
- La classe partielle doit dériver du type qui soutient l’élément racine.  
  
- Notez que, selon le comportement par défaut de la compilation de balisage des actions de construction, vous pouvez laisser la dérivation vide dans la définition de classe partielle sur le côté code-derrière. Le résultat compilé supposera que le type de support de la racine de la page sera la base de la classe partielle, même si elle n’est pas spécifiée. Cependant, s’appuyer sur ce comportement n’est pas une pratique exemplaire.  
  
- Les gestionnaires d’événements que vous écrivez dans le code-derrière doivent être des méthodes d’instance et ne peuvent pas être des méthodes statiques. Ces méthodes doivent être définies par la classe `x:Class`partielle dans l’espace nom CLR identifié par . Vous ne pouvez pas qualifier le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nom d’un gestionnaire d’événements pour demander à un transformateur de rechercher un gestionnaire d’événements pour le câblage d’événements dans une portée de classe différente.  
  
- Le gestionnaire doit faire correspondre le délégué pour l’événement approprié dans le système de type d’accompagnement.  
  
- Pour la langue Microsoft Visual Basic en particulier, vous pouvez utiliser le mot clé spécifique `Handles` à la langue pour [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]associer les gestionnaires avec les instances et les événements dans la déclaration de gestionnaire, au lieu d’attacher des gestionnaires avec des attributs dans . Cependant, cette technique a certaines `Handles` limites parce que le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mot clé ne peut pas prendre en charge toutes les fonctionnalités spécifiques du système d’événements, telles que certains scénarios d’événements acheminés ou des événements ci-joints. Pour plus de détails, voir [Visual Basic et WPF Event Handling](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>
## <a name="xcode"></a>x:Code  
 [x:Code](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md) est un élément [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]de directive défini dans . Un `x:Code` élément directive peut contenir du code de programmation en ligne. Le code défini en ligne peut [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] interagir avec le sur la même page. L’exemple suivant illustre le code inline C. Notez que le `x:Code` code est à l’intérieur `<CDATA[`de l’élément et que le code doit être entouré par ... `]]>` pour échapper au contenu pour XML, de sorte qu’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur (interprétant soit le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schéma ou le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] schéma) ne sera pas essayer d’interpréter le contenu littéralement comme XML.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>
## <a name="inline-code-limitations"></a>Inline Code Limitations  
 Vous devriez envisager d’éviter ou de limiter l’utilisation du code inline. En termes d’architecture et de philosophie de codage, le maintien d’une séparation entre la majoration et le code-derrière maintient les rôles de concepteur et de développeur beaucoup plus distincts. Sur un plan plus technique, le code que vous écrivez pour le code [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en ligne peut être gênant à écrire, parce que vous êtes toujours écrire dans la classe partielle générée, et ne peut utiliser les cartes par défaut XML namespace. Étant donné `using` que vous ne pouvez pas ajouter de déclarations, vous devez être pleinement admissible à bon nombre des appels de l’API que vous faites. Les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cartes par défaut comprennent la plupart mais pas tous [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les espaces de noms CLR qui sont présents dans les assemblées; vous devrez entièrement qualifier les appels vers les types et les membres contenus dans les autres espaces nominaux CLR. Vous ne pouvez pas non plus définir quoi que ce soit au-delà de la classe partielle dans le code inline, et toutes les entités de code utilisateur que vous référencez doivent exister en tant que membre ou variable au sein de la classe partielle générée. D’autres fonctionnalités de programmation `#ifdef` spécifiques à la langue, telles que des macros ou contre des variables globales ou des variables de construction, ne sont pas non plus disponibles. Pour plus d’informations, voir [x:Code Intrinsic XAML Type](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [x:Code, type XAML intrinsèque](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)
- [Génération d'une application WPF](../app-development/building-a-wpf-application-wpf.md)
- [Syntaxe XAML en détail](xaml-syntax-in-detail.md)
