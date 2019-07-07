---
title: Code-behind et XAML dans WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 6a47f5a93cb161c9a87df25403cc86247619cd81
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610533"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Code-behind et XAML dans WPF
<a name="introduction"></a> Code-behind est un terme utilisé pour décrire le code joint avec les objets définis par le balisage, quand un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page est compilé par balisage. Cette rubrique décrit la configuration requise pour le code-behind ainsi qu’un mécanisme alternatif incorporé code pour le code dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Cette rubrique contient les sections suivantes :  
  
- [Composants requis](#Prerequisites)  
  
- [Code-Behind et le langage XAML](#codebehind_and_the_xaml_language)  
  
- [Code-behind, gestionnaire d’événements et spécifications de la classe partielle dans WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [Limitations de Code inline](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique suppose que vous avez lu la [vue d’ensemble de XAML (WPF)](xaml-overview-wpf.md) et avoir des connaissances de base de la [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et la programmation orientée objet.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Code-Behind et le langage XAML  
 Le langage XAML inclut des fonctionnalités au niveau du langage qui le rendent possible d’associer des fichiers de code avec des fichiers de balisage, du côté du fichier de balisage. Plus précisément, le langage XAML définit les fonctionnalités de langage [x : Class Directive](../../xaml-services/x-class-directive.md), [x : Subclass Directive](../../xaml-services/x-subclass-directive.md), et [x : ClassModifier, Directive](../../xaml-services/x-classmodifier-directive.md). Exactement comment le code doit être généré et comment intégrer le balisage et le code ne fait pas partie de ce qui spécifie le langage XAML. Il incombe aux infrastructures telles que WPF pour déterminer comment intégrer le code, comment utiliser XAML dans l’application et de modèles de programmation et de la build actions ou l’autre prend en charge que tout ceci requiert.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Code-behind, gestionnaire d’événements et spécifications de la classe partielle dans WPF  
  
- La classe partielle doit dériver du type qui stocke l’élément racine.  
  
- Notez que sous le comportement par défaut des actions de génération de compilation de balisage, vous pouvez laisser la dérivation vide dans la définition de classe partielle sur le côté du code-behind. Le résultat compilé supposera type de sauvegarde de la racine de la page pour servir de base à la classe partielle, même si elle pas spécifiée. Toutefois, s’appuyer sur ce comportement n’est pas une bonne pratique.  
  
- Les gestionnaires d’événements que vous écrivez dans le code-behind doivent être des méthodes d’instance et ne peut pas être des méthodes statiques. Ces méthodes doivent être définies par la classe partielle dans l’espace de noms CLR identifié par `x:Class`. Vous ne pouvez pas qualifier le nom d’un gestionnaire d’événements pour demander à un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur à rechercher un gestionnaire d’événements pour la connexion d’événements dans une portée de classe différente.  
  
- Le gestionnaire doit correspondre le délégué pour l’événement approprié dans le système de type de stockage.  
  
- Pour le langage Microsoft Visual Basic, vous pouvez utiliser spécifique au langage `Handles` mot clé à associer les gestionnaires d’instances et des événements dans la déclaration de gestionnaire, au lieu d’attacher des gestionnaires avec des attributs dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Toutefois, cette technique a certaines limitations, car le `Handles` mot clé ne peut pas prendre en charge toutes les fonctionnalités spécifiques de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système de l’événement, comme dans certains scénarios d’événements routés ou événements attachés. Pour plus d’informations, consultez [Visual Basic et la gestion des événements de WPF](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [x : Code](../../xaml-services/x-code-intrinsic-xaml-type.md) est un élément de directive défini dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Un `x:Code` la directive de l’élément peut contenir du code de programmation inline. Le code défini en ligne peut interagir avec le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sur la même page. L’exemple suivant illustre le code inline c#. Notez que le code se trouve dans le `x:Code` élément et que le code doit être entouré de `<CDATA[`... `]]>` pour échapper le contenu pour [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], de sorte qu’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur (interprétant le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schéma ou la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] schéma) n’essaie pas d’interpréter le contenu littéralement en tant que [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Limitations de Code inline  
 Vous devez envisager d’éviter ou de limiter l’utilisation de code inline. En termes d’architecture et de philosophie du codage, la séparation entre le balisage et code-behind conserve les concepteurs et les développeurs rôles bien distincts. À un niveau plus technique, le code que vous écrivez pour le code inline peut être plus difficile à écrire, étant donné que vous écrivez toujours dans la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] classe partielle générée et pouvez utiliser uniquement les mappages d’espace de noms XML par défaut. Étant donné que vous ne pouvez pas ajouter `using` instructions, vous devez qualifier complètement beaucoup d’appels API que vous apportez. La valeur par défaut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mappages incluent la plupart mais pas tout [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] espaces de noms qui sont présents dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblys ; vous devez qualifier complètement les appels aux types et membres contenus dans les autres espaces de noms CLR. Vous également ne peut pas définir n’importe quoi au-delà de la classe partielle dans le code inline, et toutes les entités de code utilisateur que vous référencez doivent exister en tant que membre ou variable dans la classe partielle générée. Autres langage spécifique fonctionnalités de programmation, tels que des macros ou `#ifdef` par rapport à des variables globales ou des variables de génération, ne sont pas disponibles. Pour plus d’informations, consultez [x : Code de Type XAML intrinsèque](../../xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md)
- [x:Code, type XAML intrinsèque](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [Génération d’une application WPF](../app-development/building-a-wpf-application-wpf.md)
- [Syntaxe XAML en détail](xaml-syntax-in-detail.md)
