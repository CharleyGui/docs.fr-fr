---
title: Limitations de sérialisation de XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: f743f3de505904854be8aab59e9d3ad14ee64581
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238620"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Limitations de sérialisation de XamlWriter.Save
L’API <xref:System.Windows.Markup.XamlWriter.Save%2A> peut être utilisé pour sérialiser le contenu d’un [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application comme un [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier. Toutefois, il existe quelques limitations importantes dans ce qui peut être sérialisé. Ces restrictions et certaines considérations d’ordre général sont abordées dans cette rubrique.  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Représentation au moment de l’exécution, et non du design  
 La philosophie de base de ce qui est sérialisé par un appel à <xref:System.Windows.Markup.XamlWriter.Save%2A> est que le résultat sera une représentation de l’objet sérialisé, au moment de l’exécution. Plusieurs propriétés au moment du design de l’original [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier peut déjà être optimisé ou perdu au moment qui le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est chargé en tant qu’objets en mémoire et ne sont pas conservées lorsque vous appelez <xref:System.Windows.Markup.XamlWriter.Save%2A> à sérialiser. Le résultat sérialisé est une représentation effective de l’arborescence logique construite de l’application, mais pas nécessairement du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d’origine qui l’a produite. Ces problèmes rendent extrêmement difficile à utiliser le <xref:System.Windows.Markup.XamlWriter.Save%2A> sérialisation dans le cadre d’une étendue [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aire de conception.  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>La sérialisation est autonome  
 Le résultat sérialisé de <xref:System.Windows.Markup.XamlWriter.Save%2A> est autonome ; tout ce qui est sérialisé est contenu à l’intérieur d’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page unique, avec un seul élément racine et aucune autre référence externe que [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]. Par exemple, si votre page référence des ressources d’application, celles-ci apparaissent comme un composant de la page en cours de sérialisation.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Les références d’extension sont déréférencées  
 Les références d’objets communes effectuées dans divers formats d’extension de balisage, tels que `StaticResource` ou `Binding`, seront déréférencées par le processus de sérialisation. Elles étaient déjà déréférencées au moment où les objets en mémoire ont été créés par le runtime de l’application, et le <xref:System.Windows.Markup.XamlWriter.Save%2A> logique ne revient pas sur la version d’origine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à restaurer de telles références dans la sortie sérialisée. Ceci peut forcer l’utilisation d’une valeur liée aux données ou obtenue par des ressources comme dernière valeur utilisée par la représentation au moment de l’exécution, avec seulement une possibilité limitée ou indirecte de distinguer cette valeur des autres valeurs définies localement. Les images sont également sérialisées en tant que références d’objets en images telles qu’elles existent dans le projet, plutôt que comme des références sources d’origine, perdant ainsi le nom de fichier ou le [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] référencé à l’origine. Même les ressources déclarées au sein de la même page sont sérialisées à l’endroit où elles étaient référencées, au lieu d’être conservées en tant que clé d’une collection de ressources.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>La gestion des événements n’est pas conservée  
 Lorsque les gestionnaires d’événements qui sont ajoutés via [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sont sérialisés, ils ne sont pas conservés. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sans code-behind (et sans le mécanisme x:Code associé) n’a aucun moyen de sérialiser la logique procédurale du runtime. Étant donné que la sérialisation est autonome et limitée à l’arborescence logique, il n’existe aucun mécanisme permettant de stocker les gestionnaires d’événements. Par conséquent, les attributs de gestionnaire d’événements, l’attribut lui-même et la valeur de chaîne qui nomme le gestionnaire sont supprimés de la sortie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Scénarios réalistes d’utilisation de XAMLWriter.Save  
 Si les limitations énumérées ici sont importantes, il reste toutefois plusieurs scénarios appropriés pour l’utilisation de <xref:System.Windows.Markup.XamlWriter.Save%2A> pour la sérialisation.  
  
- Sortie vecteur ou graphique : La sortie de la zone de rendu peut être utilisée pour reproduire les mêmes vecteurs ou graphiques lors du rechargement.  
  
- Documents texte et flux riches : Texte et tout élément mise en forme et élément relation contenant-contenu qu’il contient sont conservés dans la sortie. Ceci peut être utile pour les mécanismes qui se rapprochent de la fonctionnalité de Presse-papiers.  
  
- Conservation des données d’objet métier : Si vous avez stocké des données dans des éléments personnalisés, tels que [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] données, tant que vos objets métier suivent base [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] règles telles que la fourniture de constructeurs personnalisés et conversion pour les valeurs de propriété par référence, ces objets métier peuvent être conservés après la sérialisation.
