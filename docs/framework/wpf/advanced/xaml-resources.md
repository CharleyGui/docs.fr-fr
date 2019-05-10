---
title: Ressources XAML
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: f92519ca1f960961f95722bce5c8e1f3b4419292
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662198"
---
# <a name="xaml-resources"></a>Ressources XAML
Une ressource est un objet pouvant être réutilisé à plusieurs endroits de votre application. Par exemple, les styles et les pinceaux sont des ressources. Cette vue d’ensemble décrit comment utiliser des ressources dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Vous pouvez également créer et accéder aux ressources à l’aide de code, ou en utilisant indifféremment entre code et [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Pour plus d’informations, consultez [ressources et Code](resources-and-code.md).  
  
> [!NOTE]
>  Les fichiers de ressources décrits dans cette rubrique sont différents que les fichiers de ressources décrits dans [ressource d’Application WPF, de contenu et de fichiers de données](../app-development/wpf-application-resource-content-and-data-files.md) ainsi que les ressources incorporées ou liées décrites dans [gérer Ressources d’application (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Utilisation des ressources en XAML  
 L’exemple suivant définit un <xref:System.Windows.Media.SolidColorBrush> en tant que ressource sur l’élément racine d’une page. L’exemple fait référence à la ressource, puis l’utilise pour définir les propriétés de plusieurs éléments enfants, y compris un <xref:System.Windows.Shapes.Ellipse>, un <xref:System.Windows.Controls.TextBlock>et un <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Chaque élément de niveau infrastructure (<xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>) a un <xref:System.Windows.FrameworkElement.Resources%2A> propriété, qui est la propriété qui contient les ressources (comme un <xref:System.Windows.ResourceDictionary>) qui définit une ressource. Vous pouvez définir les ressources sur n’importe quel élément. Toutefois, les ressources sont souvent définies sur l’élément racine, qui est <xref:System.Windows.Controls.Page> dans l’exemple.  
  
 Chaque ressource d’un dictionnaire de ressources doit avoir une clé unique. Lorsque vous définissez des ressources dans le balisage, vous affectez la clé unique via le [Directive x : Key](../../xaml-services/x-key-directive.md). Cette clé est généralement une chaîne, mais vous pouvez aussi la définir en tant qu’autres types d’objets en utilisant les extensions de balisage appropriées. Les clés pour les ressources sont utilisées par certaines fonctionnalités dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], notamment les styles, les ressources de composant et style des données.  
  
 Après avoir défini une ressource, vous pouvez faire référence à cette ressource que vous utilisez pour une valeur de propriété au moyen d’une syntaxe d’extension de balisage de ressource qui spécifie le nom de clé, par exemple :  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 Dans l’exemple précédent, lorsque le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] chargeur traite la valeur `{StaticResource MyBrush}` pour le <xref:System.Windows.Controls.Control.Background%2A> propriété sur <xref:System.Windows.Controls.Button>, la logique de recherche de ressources vérifie d’abord le dictionnaire de ressources pour le <xref:System.Windows.Controls.Button> élément. Si <xref:System.Windows.Controls.Button> n’a pas de définition de la clé de ressource `MyBrush` (il n’est pas le cas ; sa collection de ressources est vide), la recherche vérifie alors l’élément parent de <xref:System.Windows.Controls.Button>, c'est-à-dire <xref:System.Windows.Controls.Page>. Par conséquent, lorsque vous définissez une ressource sur le <xref:System.Windows.Controls.Page> élément racine, tous les éléments dans l’arborescence logique de la <xref:System.Windows.Controls.Page> peuvent y accéder, et vous pouvez réutiliser la même ressource pour définir la valeur de n’importe quelle propriété qui accepte le <xref:System.Type> que la ressource représente. Dans l’exemple précédent, le même `MyBrush` ressource définit deux propriétés différentes : la <xref:System.Windows.Controls.Control.Background%2A> d’un <xref:System.Windows.Controls.Button>et le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Ressources statiques et dynamiques  
 Une ressource peut être référencée comme ressource statique ou comme ressource dynamique. Cela à l’aide du [Extension de balisage StaticResource](staticresource-markup-extension.md) ou [Extension de balisage DynamicResource](dynamicresource-markup-extension.md). Une extension de balisage est une fonctionnalité de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui permet de spécifier une référence d’objet en ayant l’extension de balisage traite la chaîne d’attribut et retourne l’objet à un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] chargeur. Pour plus d’informations sur le comportement des extensions de balisage, consultez [Extensions de balisage et WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Quand vous utilisez une extension de balisage, vous fournissez généralement un ou plusieurs paramètres sous forme de chaînes, qui sont traités par cette même extension de balisage plutôt qu’évalués dans le contexte de la définition de la propriété. Le [Extension de balisage StaticResource](staticresource-markup-extension.md) traite une clé en recherchant la valeur de cette clé dans tous les dictionnaires de ressources disponibles. Cette opération s’effectue pendant le chargement, qui correspond au moment où le processus de chargement doit affecter la valeur de propriété qui prend la référence de ressource statique. Le [Extension de balisage DynamicResource](dynamicresource-markup-extension.md) à la place des processus une clé en créant une expression et cette expression reste sans évaluation jusqu'à ce que l’application soit effectivement exécutée, moment auquel l’expression est évaluée et fournit une valeur.  
  
 Quand vous faites référence à une ressource, les points suivants peuvent influer sur votre choix d’utiliser une référence de ressource statique ou à une ressource dynamique :  
  
- La conception globale de la façon dont vous créez les ressources pour votre application (par page, dans l’application, en libre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], dans un assembly de ressources uniquement).  
  
- La fonctionnalité de l’application : la mise à jour des ressources en temps réel est-elle obligatoire dans votre application ?  
  
- Le comportement de recherche respectif de ce type de référence de ressource.  
  
- Le type de ressource ou de propriété spécifique et le comportement natif de ces types.  
  
### <a name="static-resources"></a>Ressources statiques  
 Les références de ressources statiques conviennent parfaitement dans les conditions suivantes :  
  
- La conception de votre application concentre la plupart de ses ressources dans des dictionnaires de ressources de niveau page ou application. Les références de ressources statiques ne sont pas réévaluées en fonction des comportements d’exécution (tels que le rechargement d’une page) et donc de meilleures performances peuvent être obtenues puisque de grandes quantités de références de ressources dynamiques sont évitées quand elles ne sont pas nécessaires à la conception de votre application ou de vos ressources.  
  
- Vous définissez la valeur d’une propriété qui n’est pas suite un <xref:System.Windows.DependencyObject> ou un <xref:System.Windows.Freezable>.  
  
- Vous créez un dictionnaire de ressources qui va être compilé dans une DLL et mis dans un package faisant partie de l’application, ou partagé entre plusieurs applications.  
  
- Vous créez un thème pour un contrôle personnalisé, puis définissez les ressources qui sont utilisées dans les thèmes. Dans ce cas, vous ne souhaitez généralement pas obtenir le comportement recherchant des références de ressources dynamiques, mais plutôt celui qui recherche des références de ressources statiques, afin que cette recherche soit prévisible et autonome dans le thème. Avec une référence de ressource dynamique, même une référence dans un thème est laissée sans évaluation jusqu’à l’exécution. Au moment de l’application d’un thème, un élément local risque de redéfinir une clé que votre thème essaie de référencer, si bien que l’élément local tombe avant le thème lui-même dans la recherche. Si cela se produit, votre thème ne se comporte pas comme prévu.  
  
- Vous utilisez des ressources pour définir un grand nombre de propriétés de dépendance. Les propriétés de dépendance disposent d’une mise en cache de la valeur réelle, comme le permet le système de propriétés. Par conséquent, si vous fournissez une valeur pour une propriété de dépendance qui peut être évaluée au moment du chargement, cette propriété de dépendance n’a pas à rechercher une expression réévaluée et peut retourner la dernière valeur effective. Cette technique peut s’avérer un gain de performances.  
  
- Vous souhaitez modifier la ressource sous-jacente pour tous les consommateurs ou vous souhaitez maintenir des instances accessibles en écriture distinctes pour chaque consommateur à l’aide de la [x : Shared Attribute](../../xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Comportement de la recherche de ressources statiques  
  
1. Le processus de recherche recherche la clé demandée dans le dictionnaire de ressources qui est spécifié par l’élément définissant la propriété.  
  
2. Il remonte ensuite dans l’arborescence logique jusqu’à l’élément parent et son dictionnaire de ressources. Ce processus se poursuit jusqu’à ce que l’élément racine soit atteint.  
  
3. Ensuite, les ressources de l’application sont recherchées. Ressources d’application sont les ressources dans le dictionnaire de ressources défini par le <xref:System.Windows.Application> de l’objet pour votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.  
  
 Les références de ressources statiques issues d’un dictionnaire de ressources doivent référencer une ressource qui a déjà été définie sur le plan lexical avant la référence de ressource. Les références anticipées ne peuvent pas être résolues par une référence de ressource statique. Ainsi, si vous utilisez des références de ressources statiques, vous devez concevoir votre structure de dictionnaires de ressources de telle sorte que les ressources destinées à une utilisation par ressource soient définies au début ou près du début de chaque dictionnaire de ressources respectif.  
  
 Recherche de ressources statiques peut s’étendre aux thèmes, ou dans les ressources système, mais cela est pris en charge uniquement parce que le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] chargeur diffère de la requête. Le report est nécessaire pour que le thème d’exécution lors du chargement de la page s’applique correctement à l’application. Toutefois, les références de ressources statiques aux clés, connues pour exister seulement dans les thèmes ou en tant que ressources système, ne sont pas recommandées. La raison en est que de telles références ne sont pas réévaluées si l’utilisateur change le thème en temps réel. Une référence de ressource dynamique est plus fiable quand vous demandez des ressources de système ou de thème. L’exception se présente lorsqu’un élément de thème lui-même demande une autre ressource. Ces références doivent être des références de ressources statiques pour les raisons mentionnées précédemment.  
  
 Le comportement d’exception, en cas de référence de ressource statique introuvable, varie. Si la ressource a été différée, l’exception se produit lors de l’exécution. Si la ressource n’a pas été différée, l’exception se produit au moment du chargement.  
  
### <a name="dynamic-resources"></a>Ressources dynamiques  
 Les ressources dynamiques fonctionnent parfaitement dans les circonstances suivantes :  
  
- La valeur de la ressource dépend de conditions qui ne sont pas connues avant l’exécution comme les ressources du système ou des ressources qui sont paramétrables par l’utilisateur. Par exemple, vous pouvez créer des valeurs setter qui font référence aux propriétés du système, comme exposé par <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>, ou <xref:System.Windows.SystemParameters>. Ces valeurs sont véritablement dynamiques, car elles proviennent de l’environnement d’exécution de l’utilisateur et du système d’exploitation. Vous pouvez également avoir des thèmes de niveau application qui peuvent changer, où l’accès aux ressources de niveau page doit également capturer le changement.  
  
- Vous créez ou référencez des styles de thème pour un contrôle personnalisé.  
  
- Vous envisagez d’ajuster le contenu d’un <xref:System.Windows.ResourceDictionary> pendant une durée de vie d’application.  
  
- Vous avez une structure de ressources complexe avec des interdépendances, où une référence anticipée peut être nécessaire. Références de ressources statiques ne prennent pas en charge les références anticipées, mais les références de ressources dynamiques prennent en charge les car la ressource n’a pas besoin d’être évaluée avant l’exécution et les références anticipées ne sont donc pas un concept pertinent.  
  
- Vous référencez une ressource particulièrement grande pour une compilation ou une plage de travail et vous ne pouvez pas l’utiliser immédiatement lorsque la page se charge. Références de ressources statiques se chargent toujours à partir de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lorsque la page se charge ; Toutefois, une référence de ressource dynamique ne se charge pas jusqu'à ce qu’il est réellement utilisé.  
  
- Vous créez un style où les valeurs setter peuvent provenir d’autres valeurs qui sont influencées par des thèmes ou d’autres paramètres utilisateur.  
  
- Vous appliquez des ressources à des éléments susceptibles d’être réapparentés dans l’arborescence logique pendant la durée de vie d’une application. Le changement de parent peut aussi changer l’étendue de la recherche de ressources, donc si vous souhaitez que la ressource d’un élément réapparenté soit réévaluée en fonction de la nouvelle étendue, utilisez toujours une référence de ressource dynamique.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Comportement de la recherche de ressources dynamiques  
 Comportement de recherche pour une référence de ressource dynamique correspond au comportement de recherche dans votre code si vous appelez <xref:System.Windows.FrameworkElement.FindResource%2A> ou <xref:System.Windows.FrameworkElement.SetResourceReference%2A>.  
  
1. Le processus de recherche recherche la clé demandée dans le dictionnaire de ressources qui est spécifié par l’élément définissant la propriété.  
  
    - Si l’élément définit un <xref:System.Windows.FrameworkElement.Style%2A> propriété, le <xref:System.Windows.Style.Resources%2A> dictionnaire dans le <xref:System.Windows.Style> est activée.  
  
    - Si l’élément définit un <xref:System.Windows.Controls.Control.Template%2A> propriété, le <xref:System.Windows.FrameworkTemplate.Resources%2A> dictionnaire dans le <xref:System.Windows.FrameworkTemplate> est activée.  
  
2. Le processus de recherche remonte ensuite dans l’arborescence logique jusqu’à l’élément parent et son dictionnaire de ressources. Ce processus se poursuit jusqu’à ce que l’élément racine soit atteint.  
  
3. Ensuite, les ressources de l’application sont recherchées. Ressources d’application sont les ressources dans le dictionnaire de ressources défini par le <xref:System.Windows.Application> de l’objet pour votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.  
  
4. Le thème actif est recherché dans le dictionnaire de ressources de thèmes. Si le thème change au moment de l’exécution, la valeur est réévaluée.  
  
5. Les ressources du système sont recherchées.  
  
 Le comportement d’exception (le cas échéant) varie :  
  
- Si une ressource a été demandée par un <xref:System.Windows.FrameworkElement.FindResource%2A> appeler et est introuvable, une exception est levée.  
  
- Si une ressource a été demandée par un <xref:System.Windows.FrameworkElement.TryFindResource%2A> appeler et est introuvable, aucune exception n’est levée, mais la valeur retournée est `null`. Si la valeur de propriété n’accepte pas `null`, il est toujours possible qu’une exception plus profonde soit levée (Cela dépend de la propriété définie).  
  
- Si une ressource a été demandée par une référence de ressource dynamique dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]et n’a été trouvée, alors le comportement varie selon le système de propriétés général, mais le comportement général agit comme si aucune opération de définition de propriété s’est produite au niveau où la ressource existe. Par exemple, si vous essayez de définir l’arrière-plan d’un élément bouton à l’aide d’une ressource qui ne peut pas être déterminée, aucune définition de valeur n’en résulte alors, mais la valeur réelle peut quand même provenir d’autres participants selon la priorité de la valeur et du système de propriétés. Par exemple, la valeur de l’arrière-plan peut quand même provenir d’un style de bouton défini localement ou du style du thème. Pour les propriétés qui ne sont pas définies par les styles du thème, la valeur réelle, après l’échec d’une évaluation des ressources, peut provenir de la valeur par défaut des métadonnées de propriétés.  
  
#### <a name="restrictions"></a>Restrictions  
 Les références de ressources dynamiques présentent quelques restrictions notables. Au moins une des limitations suivantes doit se vérifier :  
  
- La propriété définie doit être une propriété sur un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. Que la propriété doit être stockée par un <xref:System.Windows.DependencyProperty>.  
  
- La référence est une valeur d’un <xref:System.Windows.Style> <xref:System.Windows.Setter>.  
  
- La propriété définie doit être une propriété sur un <xref:System.Windows.Freezable> qui est fourni en tant que valeur de l’un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> propriété, ou un <xref:System.Windows.Setter> valeur.  
  
 Étant donné que la propriété définie doit être un <xref:System.Windows.DependencyProperty> ou <xref:System.Windows.Freezable> propriété, la plupart des modifications de propriété peuvent se propager à l’interface utilisateur, car une modification de propriété (la valeur de ressource dynamique modifiée) est reconnue par le système de propriétés. La plupart des contrôles incluent la logique qui forcera une autre disposition d’un contrôle si un <xref:System.Windows.DependencyProperty> modifications et la propriété peut affecter la disposition. Toutefois, pas toutes les propriétés qui ont un [Extension de balisage DynamicResource](dynamicresource-markup-extension.md) en tant que leur valeur sont assurées de fournir la valeur de manière à ce qu’ils mettent à jour en temps réel dans l’interface utilisateur. Cette fonctionnalité peut varier en fonction de la propriété, du type de propriétaire de la propriété ou même de la structure logique de votre application.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Styles, modèles de données et clés implicites  
 Plus haut, il a été indiqué que tous les éléments dans un <xref:System.Windows.ResourceDictionary> doit avoir une clé. Toutefois, cela ne signifie pas que toutes les ressources doivent avoir explicite `x:Key`. Plusieurs types d’objets prennent en charge une clé implicite lorsqu’elle est définie en tant que ressource, sachant que la valeur d’une clé est liée à la valeur d’une autre propriété. Il s’agit une clé implicite, alors qu’un `x:Key` attribut est une clé explicite. Vous pouvez remplacer une clé implicite en spécifiant une clé explicite.  
  
 Un scénario très important pour les ressources est lorsque vous définissez un <xref:System.Windows.Style>. En fait, un <xref:System.Windows.Style> est presque toujours défini en tant qu’entrée dans un dictionnaire de ressources, car les styles sont par nature prévus pour être réutilisés. Pour plus d’informations sur les styles, consultez [Styling and Templating](../controls/styling-and-templating.md).  
  
 Des styles de contrôle peuvent être à la fois créés et référencés au moyen d’une clé implicite. Les styles de thème qui définissent l’apparence par défaut d’un contrôle s’appuient sur cette clé implicite. La clé implicite du point de vue de sa requête est le <xref:System.Type> du contrôle lui-même. La clé implicite du point de vue de la définition de la ressource est le <xref:System.Windows.Style.TargetType%2A> du style. Par conséquent, si vous créez des thèmes de contrôles personnalisés, créant des styles qui interagissent avec les styles de thème existants, il est inutile de spécifier un [Directive x : Key](../../xaml-services/x-key-directive.md) pour qui <xref:System.Windows.Style>. Et si vous souhaitez utiliser les styles à thème, il n’est pas nécessaire de spécifier un style. Par exemple, la définition de style suivante fonctionne, même si le <xref:System.Windows.Style> ressource ne semble pas avoir une clé :  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Que style a vraiment une clé : la clé implicite `typeof(` <xref:System.Windows.Controls.Button> `)`. Dans le balisage, vous pouvez spécifier un <xref:System.Windows.Style.TargetType%2A> directement en tant que le type de nom (ou vous pouvez éventuellement utiliser [{x : Type...}](../../xaml-services/x-type-markup-extension.md) pour retourner un <xref:System.Type>.  
  
 Par le biais des mécanismes de style de thème par défaut utilisés par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ce style est appliqué en tant que style d’exécution d’un <xref:System.Windows.Controls.Button> sur la page, même si le <xref:System.Windows.Controls.Button> lui-même ne tente pas de spécifier son <xref:System.Windows.FrameworkElement.Style%2A> propriété ou une ressource spécifique faire référence au style. Votre style défini dans la page est située plus haut dans la séquence de recherche que le style de dictionnaire de thème, à l’aide de la même clé que celle qui a le style de dictionnaire du thème. Vous pouvez simplement spécifier `<Button>Hello</Button>` n’importe où dans la page et le style que vous avez défini avec <xref:System.Windows.Style.TargetType%2A> de `Button` s’appliquera à ce bouton. Si vous le souhaitez, vous pouvez toujours indexer explicitement le style avec la même valeur de type en tant que <xref:System.Windows.Style.TargetType%2A>pour plus de clarté dans votre balisage, mais qui est facultatif.  
  
 Les clés implicites pour les styles ne s’appliquent pas sur un contrôle si <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> est `true` (Notez également que <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> peut être défini en tant que partie du comportement natif pour la classe de contrôle, plutôt qu’explicitement sur une instance du contrôle). En outre, pour prendre en charge les clés implicites pour les scénarios de classe dérivée, le contrôle doit remplacer <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (tous les contrôles existants fournis dans le cadre de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cela). Pour plus d’informations sur les styles, thèmes et la conception du contrôle, consultez [instructions pour la conception des contrôles d’appliquer un style](../controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate> a également une clé implicite. La clé implicite d’un <xref:System.Windows.DataTemplate> est la <xref:System.Windows.DataTemplate.DataType%2A> valeur de propriété. <xref:System.Windows.DataTemplate.DataType%2A> peut également être spécifié comme le nom du type, plutôt que d’utiliser explicitement [{x : Type...} ](../../xaml-services/x-type-markup-extension.md). Pour plus d’informations, consultez [vue d’ensemble de la création de modèles de données](../data/data-templating-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.ResourceDictionary>
- [Ressources d'application](optimizing-performance-application-resources.md)
- [Ressources et code](resources-and-code.md)
- [Définir et référencer une ressource](how-to-define-and-reference-a-resource.md)
- [Vue d’ensemble de la gestion d’applications](../app-development/application-management-overview.md)
- [x:Type, extension de balisage](../../xaml-services/x-type-markup-extension.md)
- [StaticResource, extension de balisage](staticresource-markup-extension.md)
- [Extension de balisage DynamicResource](dynamicresource-markup-extension.md)
