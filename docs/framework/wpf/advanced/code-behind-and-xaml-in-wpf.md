---
title: Code-behind et XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 212a37fb7fbcb7e66a669d96671333be793956df
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738092"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Code-behind et XAML dans WPF
<a name="introduction"></a>Code-behind est un terme utilisé pour décrire le code joint aux objets définis par le balisage, quand une page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est compilée par balisage. Cette rubrique décrit la configuration requise pour code-behind, ainsi qu’un autre mécanisme de code inline pour le code dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Cette rubrique contient les sections suivantes :  
  
- [Conditions préalables](#Prerequisites)  
  
- [Code-behind et langage XAML](#codebehind_and_the_xaml_language)  
  
- [Spécifications du code-behind, du gestionnaire d’événements et des classes partielles dans WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [Limitations du code inline](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Cette rubrique part du principe que vous avez lu la [vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) et que vous avez une connaissance de base du CLR et de la programmation orientée objet.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Code-behind et langage XAML  
 Le langage XAML comprend des fonctionnalités au niveau du langage qui permettent d’associer des fichiers de code à des fichiers de balisage, du côté du fichier de balisage. Plus précisément, le langage XAML définit les fonctionnalités de langage [X :Class directive](../../../desktop-wpf/xaml-services/xclass-directive.md), [la directive X :Subclass](../../../desktop-wpf/xaml-services/xsubclass-directive.md)et [la directive x :ClassModifier](../../../desktop-wpf/xaml-services/xclassmodifier-directive.md). La façon dont le code doit être généré, et comment intégrer le balisage et le code, ne fait pas partie de ce que spécifie le langage XAML. Il reste aux infrastructures telles que WPF pour déterminer comment intégrer le code, comment utiliser XAML dans l’application et les modèles de programmation, ainsi que les actions de génération ou d’autres prises en charge nécessaires.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Spécifications du code-behind, du gestionnaire d’événements et des classes partielles dans WPF  
  
- La classe partielle doit dériver du type qui stocke l’élément racine.  
  
- Notez que, sous le comportement par défaut des actions de génération de compilation du balisage, vous pouvez laisser la dérivation vide dans la définition de classe partielle du côté code-behind. Le résultat compilé supposera que le type de stockage de la racine de la page est la base de la classe partielle, même si elle n’est pas spécifiée. Toutefois, il n’est pas recommandé de s’appuyer sur ce comportement.  
  
- Les gestionnaires d’événements que vous écrivez dans le code-behind doivent être des méthodes d’instance et ne peuvent pas être des méthodes statiques. Ces méthodes doivent être définies par la classe partielle au sein de l’espace de noms CLR identifié par `x:Class`. Vous ne pouvez pas qualifier le nom d’un gestionnaire d’événements pour demander à un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur de rechercher un gestionnaire d’événements pour la connexion des événements dans une portée de classe différente.  
  
- Le gestionnaire doit correspondre au délégué pour l’événement approprié dans le système de type de stockage.  
  
- Pour le langage Microsoft Visual Basic spécifiquement, vous pouvez utiliser le mot clé `Handles` spécifique au langage pour associer des gestionnaires à des instances et des événements dans la déclaration de gestionnaire, au lieu d’attacher des gestionnaires avec des attributs dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Toutefois, cette technique présente certaines limitations, car le mot clé `Handles` ne peut pas prendre en charge toutes les fonctionnalités spécifiques du système d’événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], telles que certains scénarios d’événements routés ou événements attachés. Pour plus d’informations, consultez [Visual Basic et gestion des événements WPF](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [x :code](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md) est un élément de directive défini dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Un élément de directive `x:Code` peut contenir du code de programmation Inline. Le code qui est défini inline peut interagir avec le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sur la même page. L’exemple suivant illustre le code inline C# . Notez que le code se trouve à l’intérieur de l’élément `x:Code` et que le code doit être entouré par des `<CDATA[`...`]]>` pour échapper le contenu de XML, afin qu’un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (en interprétant le schéma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou le schéma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) n’essaie pas d’interpréter le contenu littéralement comme XML.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Limitations du code inline  
 Vous devez envisager d’éviter ou de limiter l’utilisation du code inline. En termes d’architecture et de philosophie de codage, maintenir une séparation entre le balisage et le code-behind permet de conserver les rôles de concepteur et de développeur bien plus distincts. À un niveau plus technique, le code que vous écrivez pour le code inline peut être difficile à écrire, car vous écrivez toujours dans le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] classe partielle générée et vous pouvez uniquement utiliser les mappages d’espaces de noms XML par défaut. Étant donné que vous ne pouvez pas ajouter de `using` instructions, vous devez qualifier entièrement un grand nombre des appels d’API que vous effectuez. Les mappages de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut incluent la plupart des espaces de noms CLR présents dans les assemblys de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mais pas tous. vous devrez qualifier pleinement les appels aux types et aux membres contenus dans les autres espaces de noms CLR. Vous ne pouvez pas non plus définir d’élément au-delà de la classe partielle dans le code inline, et toutes les entités de code utilisateur que vous référencez doivent exister en tant que membre ou variable dans la classe partielle générée. D’autres fonctionnalités de programmation spécifiques au langage, telles que des macros ou des `#ifdef` par rapport à des variables globales ou des variables de build, ne sont pas non plus disponibles. Pour plus d’informations, consultez [type XAML intrinsèque x :code](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [x:Code, type XAML intrinsèque](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)
- [Génération d’une application WPF](../app-development/building-a-wpf-application-wpf.md)
- [Syntaxe XAML en détail](xaml-syntax-in-detail.md)
