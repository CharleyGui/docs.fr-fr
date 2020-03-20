---
title: Namescopes XAML
ms.date: 03/30/2017
helpviewer_keywords:
- namescopes [WPF]
- styles [WPF], namescopes in
- templates [WPF], namescopes in
- APIs [WPF], name-related
- name-related APIs
- XAML [WPF], namescopes
- classes [WPF], FrameworkContentElement
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
ms.openlocfilehash: f9d4439c6b102d0d430b5201e3649985daee0b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186270"
---
# <a name="wpf-xaml-namescopes"></a>Portées de nom XAML WPF
Les portées de nom XAML correspondent à un concept qui identifie des objets définis en XAML. Les noms dans une portée de nom XAML peuvent être utilisés pour établir des relations entre les noms définis en XAML des objets et leurs instances équivalentes dans une arborescence d’objets. En règle générale, les portées de nom XAML dans du code managé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont créées lors du chargement des racines d’une page XAML spécifique pour une application XAML. Les namescopes XAML comme objet <xref:System.Windows.Markup.INameScope> de programmation sont définis <xref:System.Windows.NameScope>par l’interface et sont également implémenté par la classe pratique.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>
## <a name="namescopes-in-loaded-xaml-applications"></a>Portées de nom dans les applications XAML chargées  
 Dans un contexte plus large de programmation ou d’informatique, les concepts de programmation incluent souvent le principe d’un identificateur ou d’un nom unique, qui peut être utilisé pour accéder à un objet. Pour les systèmes qui utilisent des identificateurs ou des noms, la portée de nom définit les limites à l’intérieur desquelles un processus ou une technique recherche si un objet de ce nom est demandé, ou les limites dans lesquelles l’unicité des noms qui identifient est appliquée. Ces principes généraux sont vrais pour les portées de nom XAML. Dans WPF, les portées de nom XAML sont créées sur l’élément racine d’une page XAML quand la page est chargée. Chaque nom spécifié dans la page XAML en commençant à la racine de la page est ajouté à une portée de nom XAML pertinente.  
  
 Dans WPF XAML, les éléments qui <xref:System.Windows.Controls.Page>sont <xref:System.Windows.Window>des éléments racinaires communs (tels que , et ) contrôlent toujours un namescope XAML. Si un élément <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> tel que ou est l’élément [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] racine de <xref:System.Windows.Controls.Page> la page dans <xref:System.Windows.Controls.Page> le balisage, un processeur ajoute une racine implicitement de sorte que le peut fournir un namescope XAML de travail.  
  
> [!NOTE]
> Les actions de génération WPF créent une portée de nom XAML pour une production XAML même si aucun attribut `Name` ou `x:Name` n’est défini sur les éléments dans la balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Si vous essayez d’utiliser deux fois le même nom dans une portée de nom XAML, une exception est levée. Pour du XAML WPF qui a du code-behind et qui fait partie d’une application compilée, l’exception est levée au moment de la génération par les actions de génération WPF, lors de la création de la classe générée pour la page pendant la compilation initiale du balisage. Pour le XAML qui n’est compilé par balisage par aucune action de génération, des exceptions liées aux problèmes de portée de nom XAML peuvent être déclenchées lors du chargement du XAML. Les concepteurs XAML peuvent également anticiper les problèmes de portée de nom XAML au moment du design.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Ajout d’objets à des arborescences d’objets d’exécution  
 Le moment où le XAML est analysé correspond au moment une portée de nom XAML WPF est créée et définie. Si vous ajoutez un objet à une arborescence d’objets après l’analyse du code XAML ayant généré cette arborescence, une valeur `Name` ou `x:Name` sur le nouvel objet ne met pas automatiquement à jour les informations contenues dans une portée de nom XAML. Pour ajouter un nom pour un objet dans un namescope WPF XAML après <xref:System.Windows.Markup.INameScope.RegisterName%2A> le chargement de XAML, vous devez appeler la mise en œuvre appropriée de l’objet qui définit le namescope XAML, qui est généralement la racine de page XAML. Si le nom n’est pas enregistré, l’objet ajouté <xref:System.Windows.FrameworkElement.FindName%2A>ne peut pas être référencé par son nom par des méthodes telles que , et vous ne pouvez pas utiliser ce nom pour le ciblage d’animation.  
  
 Le scénario le plus courant pour <xref:System.Windows.FrameworkElement.RegisterName%2A> les développeurs d’applications est que vous utiliserez pour enregistrer des noms dans le namescope XAML sur la racine actuelle de la page. <xref:System.Windows.FrameworkElement.RegisterName%2A>fait partie d’un scénario important pour les storyboards qui ciblent les objets pour les animations. Pour plus d’informations, consultez [Vue d’ensemble des plans conceptuels](../graphics-multimedia/storyboards-overview.md).  
  
 Si vous <xref:System.Windows.FrameworkElement.RegisterName%2A> appelez un objet autre que l’objet qui définit le namescope XAML, le nom est toujours enregistré sur le <xref:System.Windows.FrameworkElement.RegisterName%2A> namescope XAML que l’objet d’appel est tenu à l’intérieur, comme si vous aviez appelé sur l’objet de définition XAML namescope.  
  
### <a name="xaml-namescopes-in-code"></a>Portées de nom XAML dans du code  
 Vous pouvez créer et ensuite utiliser des portées de nom XAML dans du code. Les API et les concepts impliqués dans la création de portée de nom XAML sont les mêmes, même pour une utilisation du code pure, car le processeur XAML pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise ces API et concepts quand il traite le XAML lui-même. Les concepts et l’API existent principalement pour pouvoir rechercher des objets par nom dans une arborescence d’objets définie partiellement ou entièrement en XAML.  
  
 Pour les applications qui sont créées programmatiquement, et non à partir de XAML <xref:System.Windows.Markup.INameScope>chargé, <xref:System.Windows.FrameworkElement> l’objet qui définit un namescope XAML doit implémenter, ou être une classe ou <xref:System.Windows.FrameworkContentElement> dérivée, afin de soutenir la création d’un namescope XAML sur ses instances.  
  
 De même, pour tout élément qui n’est pas chargé et traité par un processeur XAML, la portée de nom XAML pour l’objet n’est pas créée ou initialisée par défaut. Vous devez créer explicitement une nouvelle portée de nom XAML pour tout objet dans lequel vous prévoyez d’inscrire des noms par la suite. Pour créer un namescope XAML, <xref:System.Windows.NameScope.SetNameScope%2A> vous appelez la méthode statique. Spécifier l’objet `dependencyObject` qui le possédera comme paramètre, et un nouvel <xref:System.Windows.NameScope.%23ctor%2A> appel constructeur comme `value` paramètre.  
  
 Si l’objet `dependencyObject` <xref:System.Windows.NameScope.SetNameScope%2A> fourni quant <xref:System.Windows.Markup.INameScope> à <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>tel <xref:System.Windows.FrameworkElement.RegisterName%2A> n’est pas une implémentation, ou, faire appel à des éléments enfant n’aura aucun effet. Si vous ne créez pas explicitement le nouveau namescope XAML, les appels à <xref:System.Windows.FrameworkElement.RegisterName%2A> soulever une exception.  
  
 Pour obtenir un exemple d’utilisation des API de portée de nom XAML dans du code, consultez [Définir une portée de nom](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>
## <a name="xaml-namescopes-in-styles-and-templates"></a>Portées de nom XAML dans les styles et les modèles  
 Les styles et les modèles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permettent de réutiliser et de réappliquer le contenu d’une manière simple. Toutefois, les styles et les modèles peuvent également inclure des éléments avec des noms XAML définis au niveau d’un modèle. Ce même modèle peut être utilisé plusieurs fois dans une page. Pour cette raison, les styles et les modèles définissent tous deux leurs propres portées de nom XAML, indépendamment de l’emplacement où le style ou le modèle est appliqué dans une arborescence d’objets.  
  
 Prenons l’exemple suivant :  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Ici, le même modèle est appliqué à deux boutons différents. Si les modèles n’avaient pas de portées de nom XAML discrètes, le nom `TheBorder` utilisé dans le modèle provoquerait un conflit de noms dans la portée de nom XAML. Chaque instanciation du modèle a sa propre portée de nom XAML. Ainsi, dans cet exemple, la portée de nom XAML de chaque modèle instancié contient un et un seul nom.  
  
 Les styles définissent également leur propre portée de nom XAML, principalement pour que des noms particuliers puissent être affectés aux différentes parties des plans conceptuels. Ces noms activent des comportements spécifiques des contrôles qui ciblent les éléments de ce nom, même si le modèle a été redéfini dans le cadre de la personnalisation du contrôle.  
  
 En raison des portées de nom XAML distinctes, rechercher des éléments nommés dans un modèle est plus difficile que rechercher dans une page un élément nommé non basé sur un modèle. Vous devez d’abord déterminer le <xref:System.Windows.Controls.Control.Template%2A> modèle appliqué, en obtenant la valeur de propriété du contrôle où le modèle est appliqué. Ensuite, vous appelez la <xref:System.Windows.FrameworkTemplate.FindName%2A>version modèle de , en passant le contrôle où le modèle a été appliqué comme le deuxième paramètre.  
  
 Si vous êtes un auteur de contrôle et que vous généez une convention où un élément nommé particulier <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> dans un modèle appliqué est la cible d’un comportement qui est défini par le contrôle lui-même, vous pouvez utiliser la méthode à partir de votre code d’implémentation de contrôle. La <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> méthode est protégée, de sorte que seul l’auteur de contrôle y a accès.  
  
 Si vous travaillez à partir d’un modèle, et ont besoin d’obtenir le <xref:System.Windows.FrameworkElement.TemplatedParent%2A>namescope XAML où le modèle est appliqué, obtenir la valeur de , et ensuite appeler <xref:System.Windows.FrameworkElement.FindName%2A> là-bas. Un exemple de travail à l’intérieur du modèle est l’écriture de l’implémentation du gestionnaire d’événements là où l’événement est déclenché à partir d’un élément dans un modèle appliqué.  
  
<a name="Namescopes_and_Name_related_APIs"></a>
## <a name="xaml-namescopes-and-name-related-apis"></a>Portées de nom XAML et API relatives aux noms  
 <xref:System.Windows.FrameworkElement>a <xref:System.Windows.FrameworkElement.FindName%2A> <xref:System.Windows.FrameworkElement.RegisterName%2A> , <xref:System.Windows.FrameworkElement.UnregisterName%2A> et les méthodes. Si l’objet sur lequel vous appelez ces méthodes a une portée de nom XAML, les méthodes font les appels au sein des méthodes de la portée de nom XAML appropriée. Sinon, l’élément parent est vérifié pour voir s’il détient une portée de nom XAML, et ce processus continue de manière récursive jusqu’à ce qu’une portée de nom XAML soit trouvée (en raison du comportement du processeur XAML, la présence d’une portée de nom XAML à la racine est garantie). <xref:System.Windows.FrameworkContentElement>a des comportements analogues, à <xref:System.Windows.FrameworkContentElement> l’exception qu’aucun ne sera jamais propriétaire d’un namescope XAML. Les méthodes <xref:System.Windows.FrameworkContentElement> existent pour que les appels puissent <xref:System.Windows.FrameworkElement> éventuellement être transmis à un élément parent.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>est utilisé pour cartographier un nouveau namescope XAML à un objet existant. Vous pouvez <xref:System.Windows.NameScope.SetNameScope%2A> appeler plus d’une fois afin de réinitialiser ou effacer le namescope XAML, mais ce n’est pas une utilisation courante. En <xref:System.Windows.NameScope.GetNameScope%2A> outre, n’est généralement pas utilisé à partir du code.  
  
### <a name="xaml-namescope-implementations"></a>Implémentations de portée de nom XAML  
 Les classes <xref:System.Windows.Markup.INameScope> suivantes mettent en œuvre directement :  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>n’utilise pas de noms ou de namescopes XAML ; il utilise des clés à la place, parce qu’il s’agit d’une implémentation de dictionnaire. La seule <xref:System.Windows.ResourceDictionary> raison <xref:System.Windows.Markup.INameScope> pour laquelle les implémentations est de sorte qu’il peut soulever <xref:System.Windows.ResourceDictionary> des exceptions au code utilisateur qui aident à clarifier la <xref:System.Windows.ResourceDictionary> distinction entre un vrai namescope XAML et comment un poignées clés, et aussi pour s’assurer que les namescopes XAML ne sont pas appliqués à un par les éléments parent.  
  
 <xref:System.Windows.FrameworkTemplate>et <xref:System.Windows.Style> <xref:System.Windows.Markup.INameScope> implémenter par des définitions d’interface explicites. Les implémentations explicites permettent à ces namescopes XAML de se comporter de façon conventionnelle lorsqu’ils sont accessibles via l’interface, c’est ainsi que les <xref:System.Windows.Markup.INameScope> namescopes XAML sont communiqués par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des processus internes. Mais les définitions d’interface explicite ne font <xref:System.Windows.FrameworkTemplate> <xref:System.Windows.Style>pas partie de la <xref:System.Windows.Markup.INameScope> surface <xref:System.Windows.FrameworkTemplate> aPI conventionnelle de et , parce que vous avez rarement besoin d’appeler les méthodes sur et <xref:System.Windows.Style> directement, et à la place utiliserait d’autres API tels que <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Les classes suivantes définissent leur propre namescope <xref:System.Windows.NameScope?displayProperty=nameWithType> XAML, en utilisant la classe d’aide <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> et en se connectant à sa mise en œuvre de namescope XAML via la propriété ci-jointe :  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Voir aussi

- [Espaces de noms XAML et mappage d'espace de noms pour XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name, directive](../../../desktop-wpf/xaml-services/xname-directive.md)
