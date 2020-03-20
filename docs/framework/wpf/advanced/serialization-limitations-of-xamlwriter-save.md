---
title: Limitations de sérialisation de XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 96e917898320fb5d49f4e7dfc27daa7750af9d41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174366"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Limitations de sérialisation de XamlWriter.Save
L’API <xref:System.Windows.Markup.XamlWriter.Save%2A> peut être utilisée pour [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sérialiser le contenu d’une application en tant [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que fichier. Toutefois, il existe quelques limitations importantes dans ce qui peut être sérialisé. Ces restrictions et certaines considérations d’ordre général sont abordées dans cette rubrique.  

<a name="Run_Time__Not_Design_Time_Representation"></a>
## <a name="run-time-not-design-time-representation"></a>Représentation au moment de l’exécution, et non du design  
 La philosophie de base de ce <xref:System.Windows.Markup.XamlWriter.Save%2A> qui est sérialisé par un appel à est que le résultat sera une représentation de l’objet en cours de sérialisation, à l’heure de pointe. De nombreuses propriétés de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] conception-temps du fichier d’origine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] peuvent déjà être optimisées ou perdues au <xref:System.Windows.Markup.XamlWriter.Save%2A> moment où le chargement comme objets en mémoire, et ne sont pas conservés lorsque vous appelez à sérialiser. Le résultat sérialisé est une représentation effective de l’arborescence logique construite de l’application, mais pas nécessairement du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d’origine qui l’a produite. Ces problèmes font qu’il <xref:System.Windows.Markup.XamlWriter.Save%2A> est extrêmement difficile [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d’utiliser la sérialisation dans le cadre d’une vaste surface de conception.  
  
<a name="Serialization_is_Self_Contained"></a>
## <a name="serialization-is-self-contained"></a>La sérialisation est autonome  
 La sortie sérialisée de <xref:System.Windows.Markup.XamlWriter.Save%2A> est autonome; tout ce qui est sérialisé est contenu à l’intérieur d’une [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] seule page, avec un seul élément racine, et aucune référence externe autre que les URL. Par exemple, si votre page référence des ressources d’application, celles-ci apparaissent comme un composant de la page en cours de sérialisation.  
  
<a name="Extension_References_are_Dereferenced"></a>
## <a name="extension-references-are-dereferenced"></a>Les références d’extension sont déréférencées  
 Les références d’objets communes effectuées dans divers formats d’extension de balisage, tels que `StaticResource` ou `Binding`, seront déréférencées par le processus de sérialisation. Ceux-ci étaient déjà déreférés à l’époque où des <xref:System.Windows.Markup.XamlWriter.Save%2A> objets en mémoire [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ont été créés par l’exécution de l’application, et la logique ne revisite pas l’original pour restaurer de telles références à la sortie sérialisée. Ceci peut forcer l’utilisation d’une valeur liée aux données ou obtenue par des ressources comme dernière valeur utilisée par la représentation au moment de l’exécution, avec seulement une possibilité limitée ou indirecte de distinguer cette valeur des autres valeurs définies localement. Les images sont également sérialisées comme références d’objets aux images telles qu’elles existent dans le projet, plutôt que comme références sources originales, perdant n’importe quel nom de fichier ou URI a été initialement référencé. Même les ressources déclarées au sein de la même page sont sérialisées à l’endroit où elles étaient référencées, au lieu d’être conservées en tant que clé d’une collection de ressources.  
  
<a name="Event_Handling_is_Not_Preserved"></a>
## <a name="event-handling-is-not-preserved"></a>La gestion des événements n’est pas conservée  
 Lorsque les gestionnaires d’événements qui sont ajoutés via [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sont sérialisés, ils ne sont pas conservés. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sans code-behind (et sans le mécanisme x:Code associé) n’a aucun moyen de sérialiser la logique procédurale du runtime. Étant donné que la sérialisation est autonome et limitée à l’arborescence logique, il n’existe aucun mécanisme permettant de stocker les gestionnaires d’événements. Par conséquent, les attributs de gestionnaire d’événements, l’attribut lui-même et la valeur de chaîne qui nomme le gestionnaire sont supprimés de la sortie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Scénarios réalistes d’utilisation de XAMLWriter.Save  
 Bien que les limites énumérées ici soient assez <xref:System.Windows.Markup.XamlWriter.Save%2A> importantes, il existe encore plusieurs scénarios appropriés pour l’utilisation pour la sérialisation.  
  
- Sortie de vecteurs ou de graphiques : la sortie de la zone de rendu peut être utilisée pour reproduire les mêmes vecteurs ou graphiques lors du rechargement.  
  
- Documents dynamiques et au format RTF : le texte, ainsi que toutes les mises en forme et imbrications des éléments qu’ils contiennent sont conservés dans la sortie. Ceci peut être utile pour les mécanismes qui se rapprochent de la fonctionnalité de Presse-papiers.  
  
- Préserver les données des objets d’affaires : Si vous avez stocké des données dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] des éléments personnalisés, tels que les données XML, tant que vos objets d’entreprise suivent des règles de base telles que la fourniture de constructeurs personnalisés et la conversion pour les valeurs des propriétés de référence, ces objets d’affaires peuvent être perpétués par la sérialisation.
