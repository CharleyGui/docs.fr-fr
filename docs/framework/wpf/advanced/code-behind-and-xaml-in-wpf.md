---
title: Code-behind et XAML dans WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: acd8c9ff0a4ff718dba272958a3e63820bcf1354
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401608"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Code-behind et XAML dans WPF
<a name="introduction"></a>Code-behind est un terme utilisé pour décrire le code joint aux objets définis par le balisage lorsqu’une [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page est compilée par balisage. Cette rubrique décrit la configuration requise pour code-behind, ainsi qu’un autre mécanisme de code inline [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]pour le code dans.  
  
 Cette rubrique contient les sections suivantes :  
  
- [Composants requis](#Prerequisites)  
  
- [Code-behind et langage XAML](#codebehind_and_the_xaml_language)  
  
- [Spécifications du code-behind, du gestionnaire d’événements et des classes partielles dans WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [Limitations du code inline](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique part du principe que vous avez lu la [vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md) et que vous avez une connaissance de base du CLR et de la programmation orientée objet.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Code-behind et langage XAML  
 Le langage XAML comprend des fonctionnalités au niveau du langage qui permettent d’associer des fichiers de code à des fichiers de balisage, du côté du fichier de balisage. Plus précisément, le langage XAML définit les fonctionnalités de langage [X:Class directive](../../xaml-services/x-class-directive.md), [la directive X:Subclass](../../xaml-services/x-subclass-directive.md)et [la directive x:ClassModifier](../../xaml-services/x-classmodifier-directive.md). La façon dont le code doit être généré, et comment intégrer le balisage et le code, ne fait pas partie de ce que spécifie le langage XAML. Il reste aux infrastructures telles que WPF pour déterminer comment intégrer le code, comment utiliser XAML dans l’application et les modèles de programmation, ainsi que les actions de génération ou d’autres prises en charge nécessaires.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Spécifications du code-behind, du gestionnaire d’événements et des classes partielles dans WPF  
  
- La classe partielle doit dériver du type qui stocke l’élément racine.  
  
- Notez que, sous le comportement par défaut des actions de génération de compilation du balisage, vous pouvez laisser la dérivation vide dans la définition de classe partielle du côté code-behind. Le résultat compilé supposera que le type de stockage de la racine de la page est la base de la classe partielle, même si elle n’est pas spécifiée. Toutefois, il n’est pas recommandé de s’appuyer sur ce comportement.  
  
- Les gestionnaires d’événements que vous écrivez dans le code-behind doivent être des méthodes d’instance et ne peuvent pas être des méthodes statiques. Ces méthodes doivent être définies par la classe partielle au sein de l’espace de `x:Class`noms CLR identifié par. Vous ne pouvez pas qualifier le nom d’un gestionnaire d’événements [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour demander à un processeur de rechercher un gestionnaire d’événements pour la connexion des événements dans une portée de classe différente.  
  
- Le gestionnaire doit correspondre au délégué pour l’événement approprié dans le système de type de stockage.  
  
- Pour le langage Microsoft Visual Basic spécifiquement, vous pouvez utiliser le mot clé propre `Handles` au langage pour associer des gestionnaires à des instances et des événements dans la déclaration de gestionnaire, au lieu d’attacher des [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]gestionnaires avec des attributs dans. Toutefois, cette technique présente certaines limitations, car le `Handles` mot clé ne peut pas prendre en charge toutes les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctionnalités spécifiques du système d’événements, telles que certains scénarios d’événements routés ou événements attachés. Pour plus d’informations, consultez [Visual Basic et gestion des événements WPF](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [x:code](../../xaml-services/x-code-intrinsic-xaml-type.md) est un élément de directive défini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]dans. Un `x:Code` élément directive peut contenir du code de programmation Inline. Le code qui est défini inline peut interagir avec le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sur la même page. L’exemple suivant illustre le code inline C# . Notez que le code se trouve à `x:Code` l’intérieur de l’élément et que le code doit `<CDATA[`être entouré par... [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]pour échapper le contenu de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], afin qu’un processeur (en interprétant le schéma ou le schéma) n’essaie pas d’interpréter le contenu comme. `]]>`  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Limitations du code inline  
 Vous devez envisager d’éviter ou de limiter l’utilisation du code inline. En termes d’architecture et de philosophie de codage, maintenir une séparation entre le balisage et le code-behind permet de conserver les rôles de concepteur et de développeur bien plus distincts. À un niveau plus technique, le code que vous écrivez pour le code inline peut être difficile à écrire, car vous écrivez toujours dans la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] classe partielle générée et vous pouvez uniquement utiliser les mappages d’espaces de noms XML par défaut. Étant donné que vous `using` ne pouvez pas ajouter d’instructions, vous devez qualifier entièrement un grand nombre des appels d’API que vous effectuez. Les mappages par défaut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] incluent la plupart des espaces de noms CLR qui sont présents dans les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblys, mais pas tous. vous devrez qualifier pleinement les appels aux types et aux membres contenus dans les autres espaces de noms CLR. Vous ne pouvez pas non plus définir d’élément au-delà de la classe partielle dans le code inline, et toutes les entités de code utilisateur que vous référencez doivent exister en tant que membre ou variable dans la classe partielle générée. D’autres fonctionnalités de programmation spécifiques au langage, telles que `#ifdef` les macros ou les variables globales ou les variables de build, ne sont pas non plus disponibles. Pour plus d’informations, consultez [type XAML intrinsèque x:code](../../xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md)
- [x:Code, type XAML intrinsèque](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [Génération d’une application WPF](../app-development/building-a-wpf-application-wpf.md)
- [Syntaxe XAML en détail](xaml-syntax-in-detail.md)
