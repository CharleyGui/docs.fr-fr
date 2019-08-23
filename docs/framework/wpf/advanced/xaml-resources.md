---
title: Ressources XAML
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: 738a4f397b1677b867126c7bb439b027f951baa0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958819"
---
# <a name="xaml-resources"></a>Ressources XAML
Une ressource est un objet pouvant être réutilisé à plusieurs endroits de votre application. Par exemple, les styles et les pinceaux sont des ressources. Cette vue d’ensemble décrit comment utiliser des [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ressources dans. Vous pouvez également créer des ressources et y accéder à l’aide de code, ou de façon [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]interchangeable entre le code et. Pour plus d’informations, consultez [ressources et code](resources-and-code.md).  
  
> [!NOTE]
> Les fichiers de ressources décrits dans cette rubrique sont différents des fichiers de ressources décrits dans les [fichiers de ressources, de contenu et de données de l’application WPF](../app-development/wpf-application-resource-content-and-data-files.md) et sont différents des ressources incorporées ou liées décrites dans gérer les ressources d' [application (.net). ](/visualstudio/ide/managing-application-resources-dotnet).  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Utilisation des ressources en XAML  
 L’exemple suivant définit une <xref:System.Windows.Media.SolidColorBrush> en tant que ressource sur l’élément racine d’une page. L’exemple référence ensuite la ressource et l’utilise pour définir les propriétés de plusieurs éléments enfants, y <xref:System.Windows.Shapes.Ellipse>compris un <xref:System.Windows.Controls.TextBlock>, un et <xref:System.Windows.Controls.Button>un.  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Chaque élément au niveau de l'<xref:System.Windows.FrameworkElement> infrastructure <xref:System.Windows.FrameworkContentElement>(ou) <xref:System.Windows.FrameworkElement.Resources%2A> a une propriété, qui est la <xref:System.Windows.ResourceDictionary>propriété qui contient les ressources (en tant que) qu’une ressource définit. Vous pouvez définir les ressources sur n’importe quel élément. Toutefois, les ressources sont le plus souvent définies sur l’élément racine, <xref:System.Windows.Controls.Page> qui est dans l’exemple.  
  
 Chaque ressource d’un dictionnaire de ressources doit avoir une clé unique. Quand vous définissez des ressources dans le balisage, vous assignez la clé unique par le biais de la [directive x:Key](../../xaml-services/x-key-directive.md). Cette clé est généralement une chaîne, mais vous pouvez aussi la définir en tant qu’autres types d’objets en utilisant les extensions de balisage appropriées. Les clés qui ne sont pas des chaînes pour les ressources sont [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]utilisées par certaines fonctionnalités dans, notamment pour les styles, les ressources de composant et le style des données.  
  
 Après avoir défini une ressource, vous pouvez faire référence à cette ressource que vous utilisez pour une valeur de propriété au moyen d’une syntaxe d’extension de balisage de ressource qui spécifie le nom de clé, par exemple :  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 Dans l’exemple précédent, lorsque le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] chargeur traite la valeur `{StaticResource MyBrush}` de la <xref:System.Windows.Controls.Control.Background%2A> propriété sur <xref:System.Windows.Controls.Button>, la logique de recherche de la ressource vérifie d’abord le dictionnaire <xref:System.Windows.Controls.Button> de ressources pour l’élément. Si <xref:System.Windows.Controls.Button> n’a pas de définition de la clé `MyBrush` de ressource (ce n’est pas le cas; sa collection de ressources est vide), la recherche vérifie <xref:System.Windows.Controls.Button>ensuite l’élément <xref:System.Windows.Controls.Page>parent de, qui est. Ainsi, lorsque vous définissez une ressource sur l' <xref:System.Windows.Controls.Page> élément racine, tous les éléments de l’arborescence logique <xref:System.Windows.Controls.Page> de peuvent y accéder, et vous pouvez réutiliser la même ressource pour définir la valeur d’une propriété qui accepte le <xref:System.Type> que la ressource correspond. Dans l’exemple précédent, la même `MyBrush` ressource définit deux propriétés différentes: le <xref:System.Windows.Controls.Control.Background%2A> d’un <xref:System.Windows.Controls.Button>et le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Ressources statiques et dynamiques  
 Une ressource peut être référencée comme ressource statique ou comme ressource dynamique. Cela s’effectue à l’aide de l' [extension de balisage StaticResource](staticresource-markup-extension.md) ou de l’extension de balisage [DynamicResource](dynamicresource-markup-extension.md). Une extension de balisage est une [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fonctionnalité de dans laquelle vous pouvez spécifier une référence d’objet en faisant en sorte que l’extension de balisage traite [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] la chaîne d’attribut et retourne l’objet à un chargeur. Pour plus d’informations sur le comportement de l’extension de balisage, consultez [extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 Quand vous utilisez une extension de balisage, vous fournissez généralement un ou plusieurs paramètres sous forme de chaînes, qui sont traités par cette même extension de balisage plutôt qu’évalués dans le contexte de la définition de la propriété. L' [extension de balisage StaticResource](staticresource-markup-extension.md) traite une clé en recherchant la valeur de cette clé dans tous les dictionnaires de ressources disponibles. Cette opération s’effectue pendant le chargement, qui correspond au moment où le processus de chargement doit affecter la valeur de propriété qui prend la référence de ressource statique. L' [extension de balisage DynamicResource](dynamicresource-markup-extension.md) traite à la place une clé en créant une expression, et cette expression reste non évaluée jusqu’à ce que l’application soit exécutée, auquel cas l’expression est évaluée et fournit une valeur.  
  
 Quand vous faites référence à une ressource, les points suivants peuvent influer sur votre choix d’utiliser une référence de ressource statique ou à une ressource dynamique :  
  
- La conception globale de la façon dont vous créez les ressources pour votre application (par page, dans l’application, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]en libre dans un assembly de ressources uniquement).  
  
- La fonctionnalité de l’application : la mise à jour des ressources en temps réel est-elle obligatoire dans votre application ?  
  
- Le comportement de recherche respectif de ce type de référence de ressource.  
  
- Le type de ressource ou de propriété spécifique et le comportement natif de ces types.  
  
### <a name="static-resources"></a>Ressources statiques  
 Les références de ressources statiques conviennent parfaitement dans les conditions suivantes :  
  
- La conception de votre application concentre la plupart de ses ressources dans des dictionnaires de ressources de niveau page ou application. Les références de ressources statiques ne sont pas réévaluées en fonction des comportements d’exécution (tels que le rechargement d’une page) et donc de meilleures performances peuvent être obtenues puisque de grandes quantités de références de ressources dynamiques sont évitées quand elles ne sont pas nécessaires à la conception de votre application ou de vos ressources.  
  
- Vous définissez la valeur d’une propriété qui ne se trouve pas sur <xref:System.Windows.DependencyObject> <xref:System.Windows.Freezable>ou.  
  
- Vous créez un dictionnaire de ressources qui va être compilé dans une DLL et mis dans un package faisant partie de l’application, ou partagé entre plusieurs applications.  
  
- Vous créez un thème pour un contrôle personnalisé, puis définissez les ressources qui sont utilisées dans les thèmes. Dans ce cas, vous ne souhaitez généralement pas obtenir le comportement recherchant des références de ressources dynamiques, mais plutôt celui qui recherche des références de ressources statiques, afin que cette recherche soit prévisible et autonome dans le thème. Avec une référence de ressource dynamique, même une référence dans un thème est laissée sans évaluation jusqu’à l’exécution. Au moment de l’application d’un thème, un élément local risque de redéfinir une clé que votre thème essaie de référencer, si bien que l’élément local tombe avant le thème lui-même dans la recherche. Si cela se produit, votre thème ne se comporte pas comme prévu.  
  
- Vous utilisez des ressources pour définir un grand nombre de propriétés de dépendance. Les propriétés de dépendance disposent d’une mise en cache de la valeur réelle, comme le permet le système de propriétés. Par conséquent, si vous fournissez une valeur pour une propriété de dépendance qui peut être évaluée au moment du chargement, cette propriété de dépendance n’a pas à rechercher une expression réévaluée et peut retourner la dernière valeur effective. Cette technique peut s’avérer un gain de performances.  
  
- Vous souhaitez modifier la ressource sous-jacente pour tous les consommateurs, ou vous souhaitez conserver des instances accessibles en écriture distinctes pour chaque consommateur à l’aide de l' [attribut x:Shared](../../xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Comportement de la recherche de ressources statiques  
  
1. Le processus de recherche recherche la clé demandée dans le dictionnaire de ressources qui est spécifié par l’élément définissant la propriété.  
  
2. Il remonte ensuite dans l’arborescence logique jusqu’à l’élément parent et son dictionnaire de ressources. Ce processus se poursuit jusqu’à ce que l’élément racine soit atteint.  
  
3. Ensuite, les ressources de l’application sont recherchées. Les ressources d’application sont les ressources du dictionnaire de ressources qui sont définies <xref:System.Windows.Application> par l’objet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour votre application.  
  
 Les références de ressources statiques issues d’un dictionnaire de ressources doivent référencer une ressource qui a déjà été définie sur le plan lexical avant la référence de ressource. Les références anticipées ne peuvent pas être résolues par une référence de ressource statique. Ainsi, si vous utilisez des références de ressources statiques, vous devez concevoir votre structure de dictionnaires de ressources de telle sorte que les ressources destinées à une utilisation par ressource soient définies au début ou près du début de chaque dictionnaire de ressources respectif.  
  
 La recherche de ressources statiques peut s’étendre à des thèmes ou à des ressources système, mais cela [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est pris en charge uniquement parce que le chargeur diffère la demande. Le report est nécessaire pour que le thème d’exécution lors du chargement de la page s’applique correctement à l’application. Toutefois, les références de ressources statiques aux clés, connues pour exister seulement dans les thèmes ou en tant que ressources système, ne sont pas recommandées. La raison en est que de telles références ne sont pas réévaluées si l’utilisateur change le thème en temps réel. Une référence de ressource dynamique est plus fiable quand vous demandez des ressources de système ou de thème. L’exception se présente lorsqu’un élément de thème lui-même demande une autre ressource. Ces références doivent être des références de ressources statiques pour les raisons mentionnées précédemment.  
  
 Le comportement d’exception, en cas de référence de ressource statique introuvable, varie. Si la ressource a été différée, l’exception se produit lors de l’exécution. Si la ressource n’a pas été différée, l’exception se produit au moment du chargement.  
  
### <a name="dynamic-resources"></a>Ressources dynamiques  
 Les ressources dynamiques fonctionnent parfaitement dans les circonstances suivantes :  
  
- La valeur de la ressource dépend de conditions qui ne sont pas connues avant l’exécution comme les ressources du système ou des ressources qui sont paramétrables par l’utilisateur. Par exemple, vous pouvez créer des valeurs d’accesseur Set qui font référence à des <xref:System.Windows.SystemColors>propriétés <xref:System.Windows.SystemFonts>système, <xref:System.Windows.SystemParameters>telles qu’elles sont exposées par, ou. Ces valeurs sont véritablement dynamiques, car elles proviennent de l’environnement d’exécution de l’utilisateur et du système d’exploitation. Vous pouvez également avoir des thèmes de niveau application qui peuvent changer, où l’accès aux ressources de niveau page doit également capturer le changement.  
  
- Vous créez ou référencez des styles de thème pour un contrôle personnalisé.  
  
- Vous avez l’intention d’ajuster le contenu <xref:System.Windows.ResourceDictionary> d’un pendant la durée de vie d’une application.  
  
- Vous avez une structure de ressources complexe avec des interdépendances, où une référence anticipée peut être nécessaire. Les références de ressources statiques ne prennent pas en charge les références anticipées, mais les références de ressources dynamiques les prennent en charge, car la ressource n’a pas besoin d’être évaluée avant l’exécution, et les références anticipées ne sont donc pas un concept pertinent.  
  
- Vous référencez une ressource particulièrement grande pour une compilation ou une plage de travail et vous ne pouvez pas l’utiliser immédiatement lorsque la page se charge. Les références de ressources statiques [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se chargent toujours à partir de lors du chargement de la page; Toutefois, une référence de ressource dynamique n’est pas chargée tant qu’elle n’est pas réellement utilisée.  
  
- Vous créez un style où les valeurs setter peuvent provenir d’autres valeurs qui sont influencées par des thèmes ou d’autres paramètres utilisateur.  
  
- Vous appliquez des ressources à des éléments susceptibles d’être réapparentés dans l’arborescence logique pendant la durée de vie d’une application. Le changement de parent peut aussi changer l’étendue de la recherche de ressources, donc si vous souhaitez que la ressource d’un élément réapparenté soit réévaluée en fonction de la nouvelle étendue, utilisez toujours une référence de ressource dynamique.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Comportement de la recherche de ressources dynamiques  
 Le comportement de recherche de ressources pour une référence de ressource dynamique correspond au comportement de recherche dans <xref:System.Windows.FrameworkElement.FindResource%2A> votre <xref:System.Windows.FrameworkElement.SetResourceReference%2A>code si vous appelez ou.  
  
1. Le processus de recherche recherche la clé demandée dans le dictionnaire de ressources qui est spécifié par l’élément définissant la propriété.  
  
    - Si l’élément définit une <xref:System.Windows.FrameworkElement.Style%2A> propriété, le <xref:System.Windows.Style.Resources%2A> dictionnaire dans le <xref:System.Windows.Style> est activé.  
  
    - Si l’élément définit une <xref:System.Windows.Controls.Control.Template%2A> propriété, le <xref:System.Windows.FrameworkTemplate.Resources%2A> dictionnaire dans le <xref:System.Windows.FrameworkTemplate> est activé.  
  
2. Le processus de recherche remonte ensuite dans l’arborescence logique jusqu’à l’élément parent et son dictionnaire de ressources. Ce processus se poursuit jusqu’à ce que l’élément racine soit atteint.  
  
3. Ensuite, les ressources de l’application sont recherchées. Les ressources d’application sont les ressources du dictionnaire de ressources qui sont définies <xref:System.Windows.Application> par l’objet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour votre application.  
  
4. Le thème actif est recherché dans le dictionnaire de ressources de thèmes. Si le thème change au moment de l’exécution, la valeur est réévaluée.  
  
5. Les ressources du système sont recherchées.  
  
 Le comportement d’exception (le cas échéant) varie :  
  
- Si une ressource a été demandée par <xref:System.Windows.FrameworkElement.FindResource%2A> un appel et qu’elle est introuvable, une exception est levée.  
  
- Si une ressource a été demandée par <xref:System.Windows.FrameworkElement.TryFindResource%2A> un appel et qu’elle est introuvable, aucune exception n’est levée, mais `null`la valeur retournée est. Si la propriété qui est définie n’accepte `null`pas, il est toujours possible qu’une exception plus profonde soit levée (cela dépend de la propriété individuelle définie).  
  
- Si une ressource a été demandée par une référence de ressource [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]dynamique dans, et qu’elle est introuvable, le comportement dépend du système de propriétés général, mais le comportement général est comme si aucune opération de définition de propriété ne s’est produite au niveau de l’emplacement où la ressource existe. Par exemple, si vous essayez de définir l’arrière-plan d’un élément bouton à l’aide d’une ressource qui ne peut pas être déterminée, aucune définition de valeur n’en résulte alors, mais la valeur réelle peut quand même provenir d’autres participants selon la priorité de la valeur et du système de propriétés. Par exemple, la valeur de l’arrière-plan peut quand même provenir d’un style de bouton défini localement ou du style du thème. Pour les propriétés qui ne sont pas définies par les styles du thème, la valeur réelle, après l’échec d’une évaluation des ressources, peut provenir de la valeur par défaut des métadonnées de propriétés.  
  
#### <a name="restrictions"></a>Restrictions  
 Les références de ressources dynamiques présentent quelques restrictions notables. Au moins une des limitations suivantes doit se vérifier :  
  
- La propriété qui est définie doit être une propriété sur <xref:System.Windows.FrameworkElement> un <xref:System.Windows.FrameworkContentElement>ou un. Cette propriété doit être sauvegardée par un <xref:System.Windows.DependencyProperty>.  
  
- La référence est pour une valeur dans un <xref:System.Windows.Style>. <xref:System.Windows.Setter>  
  
- La propriété qui est définie doit être une propriété sur <xref:System.Windows.Freezable> un qui est fourni en tant que valeur d' <xref:System.Windows.FrameworkElement> une <xref:System.Windows.FrameworkContentElement> propriété ou, ou <xref:System.Windows.Setter> d’une valeur.  
  
 Étant donné que la propriété qui est définie <xref:System.Windows.DependencyProperty> doit <xref:System.Windows.Freezable> être une propriété ou, la plupart des modifications de propriétés peuvent se propager à l’interface utilisateur, car une modification de propriété (la valeur de ressource dynamique modifiée) est reconnue par le système de propriétés. La plupart des contrôles incluent une logique qui force une autre disposition d’un <xref:System.Windows.DependencyProperty> contrôle si une modification et cette propriété peuvent affecter la disposition. Toutefois, toutes les propriétés qui ont une [extension de balisage DynamicResource](dynamicresource-markup-extension.md) comme valeur sont assurées de fournir la valeur de sorte qu’elles soient mises à jour en temps réel dans l’interface utilisateur. Cette fonctionnalité peut varier en fonction de la propriété, du type de propriétaire de la propriété ou même de la structure logique de votre application.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Styles, modèles de données et clés implicites  
 Précédemment, il a été indiqué que tous les éléments <xref:System.Windows.ResourceDictionary> d’un doivent avoir une clé. Toutefois, cela ne signifie pas que toutes les ressources doivent avoir un `x:Key`explicite. Plusieurs types d’objets prennent en charge une clé implicite lorsqu’elle est définie en tant que ressource, sachant que la valeur d’une clé est liée à la valeur d’une autre propriété. C’est ce qu’on appelle une clé implicite `x:Key` , tandis qu’un attribut est une clé explicite. Vous pouvez remplacer une clé implicite en spécifiant une clé explicite.  
  
 Un scénario très important pour les ressources est lorsque vous définissez <xref:System.Windows.Style>un. En fait, un <xref:System.Windows.Style> est presque toujours défini en tant qu’entrée dans un dictionnaire de ressources, car les styles sont par nature prévus pour être réutilisés. Pour plus d’informations sur les styles, consultez [stylisation et création de modèles](../controls/styling-and-templating.md).  
  
 Des styles de contrôle peuvent être à la fois créés et référencés au moyen d’une clé implicite. Les styles de thème qui définissent l’apparence par défaut d’un contrôle s’appuient sur cette clé implicite. La clé implicite du point de vue de la demande <xref:System.Type> est le du contrôle lui-même. La clé implicite du point de vue de la définition de <xref:System.Windows.Style.TargetType%2A> la ressource est le du style. Par conséquent, si vous créez des thèmes pour des contrôles personnalisés, en créant des styles qui interagissent avec les styles de thème existants, vous n’avez pas <xref:System.Windows.Style>besoin de spécifier une [directive x:Key](../../xaml-services/x-key-directive.md) pour cela. Et si vous souhaitez utiliser les styles à thème, il n’est pas nécessaire de spécifier un style. Par exemple, la définition de style suivante fonctionne, même si <xref:System.Windows.Style> la ressource ne semble pas avoir une clé:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Ce style a vraiment une clé: la clé `typeof(` <xref:System.Windows.Controls.Button> `)`implicite. Dans le balisage, vous pouvez <xref:System.Windows.Style.TargetType%2A> spécifier un directement comme nom de type (ou vous pouvez éventuellement utiliser [{x:type...}](../../xaml-services/x-type-markup-extension.md) pour retourner un <xref:System.Type>.  
  
 Par le biais des mécanismes de style de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]thème par défaut utilisés par, ce style est appliqué comme <xref:System.Windows.Controls.Button> style d’exécution d’un sur la <xref:System.Windows.Controls.Button> page, même si le lui- <xref:System.Windows.FrameworkElement.Style%2A> même ne tente pas de spécifier sa propriété ou une ressource spécifique. référence au style. Votre style défini dans la page est trouvé précédemment dans la séquence de recherche que le style du dictionnaire de thèmes, en utilisant la même clé que celle du style du dictionnaire de thèmes. Vous pouvez simplement spécifier `<Button>Hello</Button>` n’importe où dans la page, et le style que <xref:System.Windows.Style.TargetType%2A> vous `Button` avez défini avec la valeur s’applique à ce bouton. Si vous le souhaitez, vous pouvez toujours définir explicitement le style avec la même valeur de <xref:System.Windows.Style.TargetType%2A>type que, pour plus de clarté dans votre balisage, mais cela est facultatif.  
  
 Les clés implicites pour les styles ne s’appliquent <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> pas `true` à un contrôle si <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> a la valeur (Notez également que peut être défini dans le cadre du comportement natif de la classe de contrôle, plutôt que de manière explicite sur une instance du contrôle). En outre, pour prendre en charge les clés implicites pour les scénarios de classe dérivée <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> , le contrôle doit se substituer ( [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tous les contrôles existants fournis dans le cadre de cette opération). Pour plus d’informations sur les styles, les thèmes et la conception de contrôles, consultez [instructions pour la conception de contrôles stylisés](../controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate>a également une clé implicite. La clé implicite pour <xref:System.Windows.DataTemplate> un est <xref:System.Windows.DataTemplate.DataType%2A> la valeur de la propriété. <xref:System.Windows.DataTemplate.DataType%2A>peut également être spécifié en tant que nom du type au lieu d’utiliser explicitement [{x:type...}](../../xaml-services/x-type-markup-extension.md). Pour plus d’informations, consultez [vue d’ensemble des modèles de données](../data/data-templating-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.ResourceDictionary>
- [Ressources d'application](optimizing-performance-application-resources.md)
- [Ressources et code](resources-and-code.md)
- [Définir et référencer une ressource](how-to-define-and-reference-a-resource.md)
- [Vue d’ensemble de la gestion d’applications](../app-development/application-management-overview.md)
- [x:Type, extension de balisage](../../xaml-services/x-type-markup-extension.md)
- [StaticResource, extension de balisage](staticresource-markup-extension.md)
- [Extension de balisage DynamicResource](dynamicresource-markup-extension.md)
