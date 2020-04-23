---
title: Décrivez les ressources XAML
description: En savoir plus sur les ressources XAML dans WPF pour .NET Core. Comprendre les types de ressources XAML et apprendre à définir les ressources XAML.
author: thraka
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: b278bb92afc308578d60e347871e0150b26a95db
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "82071282"
---
# <a name="overview-of-xaml-resources"></a>Aperçu des ressources XAML

Une ressource est un objet qui peut être réutilisé à différents endroits de votre application. Par exemple, les styles et les pinceaux sont des ressources. Cette vue d’ensemble décrit comment utiliser les ressources dans Extensible Application Markup Language (XAML). Vous pouvez également créer et accéder aux ressources en utilisant du code.

> [!NOTE]
> Les ressources XAML décrites dans cet article sont différentes des *ressources d’applications* qui sont généralement des fichiers ajoutés à une application, telles que le contenu, les données ou les fichiers intégrés.

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>Utilisation des ressources dans XAML

L’exemple suivant <xref:System.Windows.Media.SolidColorBrush> définit une ressource sur l’élément racine d’une page. L’exemple fait ensuite référence à la ressource et l’utilise <xref:System.Windows.Controls.TextBlock>pour <xref:System.Windows.Controls.Button>définir les propriétés de plusieurs éléments pour enfants, y compris un <xref:System.Windows.Shapes.Ellipse>, a , et a .

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

Chaque élément de<xref:System.Windows.FrameworkElement> niveau <xref:System.Windows.FrameworkContentElement>cadre <xref:System.Windows.FrameworkElement.Resources%2A> ( ou ) <xref:System.Windows.ResourceDictionary> a une propriété, qui est un type qui contient des ressources définies. Vous pouvez définir des ressources sur <xref:System.Windows.Controls.Button>n’importe quel élément, comme un . Cependant, les ressources sont le plus souvent <xref:System.Windows.Controls.Page> définies sur l’élément racine, ce qui est dans l’exemple.

Chaque ressource d’un dictionnaire de ressources doit avoir une clé unique. Lorsque vous définissez les ressources en marge, vous attribuez la clé unique par le biais de la [directive x:Key](../xaml-services/xkey-directive.md). Cette clé est généralement une chaîne, mais vous pouvez aussi la définir en tant qu’autres types d’objets en utilisant les extensions de balisage appropriées. Les clés non-cordes pour les ressources sont utilisées par certaines zones de fonctionnalités dans WPF, notamment pour les styles, les ressources de composants et le style de données.

Vous pouvez utiliser une ressource définie avec la syntaxe d’extension de balisage des ressources qui spécifie le nom clé de la ressource. Par exemple, utilisez la ressource comme valeur d’une propriété sur un autre élément.

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

Dans l’exemple précédent, lorsque le chargeur `{StaticResource MyBrush}` XAML traite la valeur de la <xref:System.Windows.Controls.Control.Background%2A> propriété sur <xref:System.Windows.Controls.Button>, la logique de recherche de ressources vérifie d’abord le dictionnaire de ressources pour l’élément. <xref:System.Windows.Controls.Button> Si <xref:System.Windows.Controls.Button> elle n’a pas de `MyBrush` définition de la clé de ressources (dans cet exemple, elle n’en a pas; sa collecte de ressources est vide), la prochaine vérification de l’élément parent de <xref:System.Windows.Controls.Button>, qui est <xref:System.Windows.Controls.Page>. Si vous définissez <xref:System.Windows.Controls.Page> une ressource sur l’élément racine, <xref:System.Windows.Controls.Page> tous les éléments de l’arbre logique de la peut y accéder. Et vous pouvez réutiliser la même ressource pour définir la valeur de toute propriété qui accepte le même type que la ressource représente. Dans l’exemple précédent, `MyBrush` la même ressource <xref:System.Windows.Controls.Control.Background%2A> définit <xref:System.Windows.Controls.Button>deux <xref:System.Windows.Shapes.Shape.Fill%2A> propriétés différentes: l’un , et le d’un <xref:System.Windows.Shapes.Rectangle>.

## <a name="static-and-dynamic-resources"></a>Ressources statiques et dynamiques

Une ressource peut être référencée comme statique ou dynamique. Les références sont créées en utilisant soit [l’extension de balisage StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md) ou l’extension [De Markup DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md). Une extension de balisage est une fonctionnalité XAML qui vous permet de spécifier une référence d’objet en ayant le processus d’extension de balisage de la chaîne d’attribut et de retourner l’objet à un chargeur XAML. Pour plus d’informations sur le comportement d’extension de balisage, voir [Extensions Markup et WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

Lorsque vous utilisez une extension de balisage, vous fournissez généralement un ou plusieurs paramètres sous forme de chaîne qui sont traités par cette extension de balisage particulière. [L’extension De Markup StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md) traite une clé en recherchant la valeur de cette clé dans tous les dictionnaires de ressources disponibles. Le traitement se produit pendant la charge, c’est-à-dire lorsque le processus de chargement doit attribuer la valeur de la propriété. [L’extension DynamicResource Markup](../../framework/wpf/advanced/dynamicresource-markup-extension.md) traite plutôt une clé en créant une expression, et cette expression reste non évaluée jusqu’à ce que l’application s’exécute, date à laquelle l’expression est évaluée et fournit une valeur.

Quand vous faites référence à une ressource, les points suivants peuvent influer sur votre choix d’utiliser une référence de ressource statique ou à une ressource dynamique :

- Lorsque vous déterminez la conception globale de la façon dont vous créez les ressources de votre application (par page, dans l’application, en XAML en vrac ou dans un assemblage uniquement de ressources), considérez ce qui suit :

- La fonctionnalité de l’application. Les ressources mises à jour en temps réel sont-elles une partie des exigences de votre application ?
- Le comportement de recherche respectif de ce type de référence de ressource.
- Le type de ressource ou de propriété spécifique et le comportement natif de ces types.

## <a name="static-resources"></a>Ressources statiques

Les références de ressources statiques conviennent parfaitement dans les conditions suivantes :

- La conception de votre application concentre la plupart de ses ressources dans des dictionnaires de ressources de page ou de niveau d’application. Les références de ressources statiques ne sont pas réévaluées en fonction des comportements en temps d’exécution, tels que le rechargement d’une page. Ainsi, il peut y avoir un certain avantage de performance à éviter un grand nombre de références de ressources dynamiques quand elles ne sont pas nécessaires en fonction de votre ressource et la conception d’applications.

- Vous définissez la valeur d’une propriété <xref:System.Windows.DependencyObject> qui <xref:System.Windows.Freezable>n’est pas sur un ou un .

- Vous créez un dictionnaire de ressources qui sera compilé dans un DLL et emballé dans le cadre de l’application ou partagé entre les applications.

- Vous créez un thème pour un contrôle personnalisé et définissez les ressources qui sont utilisées dans les thèmes. Pour ce cas, vous ne voulez généralement pas le comportement dynamique de recherche de référence de ressource ; vous voulez plutôt le comportement statique de référence de ressource de sorte que le lookup est prévisible et autonome au thème. Avec une référence dynamique des ressources, même une référence dans un thème n’est pas évaluée jusqu’à la durée de la course. et il ya une chance que lorsque le thème est appliqué, un élément local redéfinira une clé que votre thème essaie de référence, et l’élément local tombera avant le thème lui-même dans le lookup. Si cela se produit, votre thème ne se comportera pas comme prévu.

- Vous utilisez les ressources pour définir un grand nombre de propriétés de dépendance. Propriétés de dépendance ont la mise en cache de valeur efficace comme activé par le système de propriété, ainsi si vous fournissez une valeur pour une propriété de dépendance qui peut être évaluée au moment de charge, la propriété de dépendance n’a pas à vérifier pour une expression réévaluée et peut retourner la dernière valeur effective. Cette technique peut s’avérer un gain de performances.

- Vous souhaitez modifier la ressource sous-jacente pour tous les consommateurs, ou vous souhaitez maintenir des instances brefes distinctes pour chaque consommateur en utilisant le [x:Shared Attribute](../xaml-services/xshared-attribute.md).

### <a name="static-resource-lookup-behavior"></a>Comportement de la recherche de ressources statiques

Ce qui suit décrit le processus de recherche qui se produit automatiquement lorsqu’une ressource statique est référencée par une propriété ou un élément :

01. Le processus de recherche recherche la clé demandée dans le dictionnaire de ressources qui est spécifié par l’élément définissant la propriété.

01. Le processus de recherche traverse alors l’arbre logique vers le haut à l’élément parent et son dictionnaire de ressources. Ce processus se poursuit jusqu’à ce que l’élément racine soit atteint.

01. Les ressources de l’application sont vérifiées. Les ressources d’applications sont les ressources <xref:System.Windows.Application> du dictionnaire des ressources qui est définie par l’objet de votre application WPF.

Les références de ressources statiques issues d’un dictionnaire de ressources doivent référencer une ressource qui a déjà été définie sur le plan lexical avant la référence de ressource. Les références anticipées ne peuvent pas être résolues par une référence de ressource statique. Pour cette raison, concevez votre structure de dictionnaire de ressources de telle sorte que les ressources soient définies au début ou vers le début de chaque dictionnaire de ressources respectif.

La recherche statique des ressources peut s’étendre en thèmes ou en ressources système, mais cette recherche n’est prise en charge que parce que le chargeur XAML reporte la demande. Le report est nécessaire de sorte que le thème de l’heure d’exécution au moment où la page se charge s’applique correctement à l’application. Cependant, les références statiques de ressources aux touches qui sont connues pour exister seulement dans les thèmes ou comme ressources système ne sont pas recommandées, parce que ces références ne sont pas réévaluées si le thème est changé par l’utilisateur en temps réel. Une référence de ressource dynamique est plus fiable quand vous demandez des ressources de système ou de thème. L’exception se présente lorsqu’un élément de thème lui-même demande une autre ressource. Ces références doivent être des références de ressources statiques pour les raisons mentionnées précédemment.

Le comportement d’exception si une référence de ressource statique n’est pas trouvée varie. Si la ressource a été différée, l’exception se produit lors de l’exécution. Si la ressource n’a pas été différée, l’exception se produit au moment du chargement.

## <a name="dynamic-resources"></a>Ressources dynamiques

Les ressources dynamiques fonctionnent mieux lorsque :

- La valeur de la ressource, y compris les ressources système, ou les ressources qui sont autrement définis par l’utilisateur, dépend de conditions qui ne sont pas connues avant l’exécution. Par exemple, vous pouvez créer des valeurs de <xref:System.Windows.SystemColors>setter qui se réfèrent aux propriétés du système telles qu’exposées par , <xref:System.Windows.SystemFonts>, ou <xref:System.Windows.SystemParameters>. Ces valeurs sont véritablement dynamiques, car elles proviennent de l’environnement d’exécution de l’utilisateur et du système d’exploitation. Vous pouvez également avoir des thèmes de niveau application qui peuvent changer, où l’accès aux ressources de niveau page doit également capturer le changement.

- Vous créez ou faites référence à des styles thématiques pour un contrôle personnalisé.

- Vous avez l’intention <xref:System.Windows.ResourceDictionary> d’ajuster le contenu d’une durée de vie dans une application.

- Vous avez une structure de ressources complexe avec des interdépendances, où une référence anticipée peut être nécessaire. Les références statiques des ressources ne prennent pas en charge les références avancées, mais les références dynamiques en matière de ressources les soutiennent parce que la ressource n’a pas besoin d’être évaluée avant l’exécution, et les références avancées ne sont donc pas un concept pertinent.

- Vous faites référence à une ressource qui est grande du point de vue d’une compilation ou d’un ensemble de travail, et la ressource pourrait ne pas être utilisée immédiatement lorsque la page se charge. Les références de ressources statiques se chargent toujours de XAML lorsque la page se charge. Cependant, une référence dynamique des ressources ne se charge pas tant qu’elle n’est pas utilisée.

- Vous créez un style où les valeurs de setter peuvent provenir d’autres valeurs qui sont influencées par des thèmes ou d’autres paramètres de l’utilisateur.

- Vous appliquez des ressources à des éléments qui pourraient être réparentés dans l’arbre logique pendant la durée de vie de l’application. Le changement de parent peut aussi changer l’étendue de la recherche de ressources, donc si vous souhaitez que la ressource d’un élément réapparenté soit réévaluée en fonction de la nouvelle étendue, utilisez toujours une référence de ressource dynamique.

### <a name="dynamic-resource-lookup-behavior"></a>Comportement de la recherche de ressources dynamiques

Le comportement de recherche de ressources pour une référence dynamique de <xref:System.Windows.FrameworkElement.FindResource%2A> <xref:System.Windows.FrameworkElement.SetResourceReference%2A>ressource parallèle au comportement de recherche dans votre code si vous appelez ou :

01. Les vérifications de recherche de la clé demandée dans le dictionnaire des ressources définies par l’élément qui définit la propriété :

    - Si l’élément <xref:System.Windows.FrameworkElement.Style%2A> définit une <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName> propriété, l’élément fait vérifier son <xref:System.Windows.Style.Resources> dictionnaire.

    - Si l’élément <xref:System.Windows.Controls.Control.Template%2A> définit une <xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName> propriété, le dictionnaire de l’élément est vérifié.

01. La recherche traverse l’arbre logique vers le haut à l’élément parent et son dictionnaire de ressources. Ce processus se poursuit jusqu’à ce que l’élément racine soit atteint.

01. Les ressources de l’application sont vérifiées. Les ressources d’applications sont les ressources <xref:System.Windows.Application> du dictionnaire des ressources qui sont définies par l’objet de votre application WPF.

01. Le dictionnaire des ressources thématiques est vérifié pour le thème actuellement actif. Si le thème change au moment de l’exécution, la valeur est réévaluée.

01. Les ressources du système sont recherchées.

Le comportement d’exception (le cas échéant) varie :

- Si une ressource a <xref:System.Windows.FrameworkElement.FindResource%2A> été demandée par un appel et n’a pas été trouvée, une exception est lancée.

- Si une ressource a <xref:System.Windows.FrameworkElement.TryFindResource%2A> été demandée par un appel et n’a pas été trouvée, aucune exception n’est jetée, et la valeur retournée est `null`. Si la propriété étant définie `null`n’accepte pas, alors il est toujours possible qu’une exception plus profonde sera jetée, selon la propriété individuelle étant définie.

- Si une ressource a été demandée par une référence dynamique de ressource dans XAML et n’a pas été trouvée, alors le comportement dépend du système général de propriété. Le comportement général est comme si aucune opération de réglage de propriété n’a eu lieu au niveau où la ressource existe. Par exemple, si vous essayez de définir l’arrière-plan sur un élément de bouton individuel à l’aide d’une ressource qui n’a pas pu être évaluée, alors aucun résultat de jeu de valeur, mais la valeur effective peut encore provenir d’autres participants au système de propriété et la préséance de valeur. Par exemple, la valeur de fond peut encore provenir d’un style de bouton défini localement ou du style thème. Pour les propriétés qui ne sont pas définies par les styles thématiques, la valeur effective après une évaluation des ressources a échoué pourrait provenir de la valeur par défaut dans les métadonnées de propriété.

### <a name="restrictions"></a>Restrictions

Les références de ressources dynamiques présentent quelques restrictions notables. Au moins une des conditions suivantes doit être vraie :

- La propriété en cours d’établissement doit être une propriété sur un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. Cette propriété doit être <xref:System.Windows.DependencyProperty>soutenue par un .

- La référence est pour `StyleSetter`une valeur dans un .

- La propriété en cours d’établissement doit être une propriété sur un <xref:System.Windows.Freezable> qui est fourni comme une valeur d’un ou <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> d’une propriété, ou une <xref:System.Windows.Setter> valeur.

Étant donné que la <xref:System.Windows.DependencyProperty> propriété <xref:System.Windows.Freezable> étant définie doit être une propriété ou une propriété, la plupart des changements de propriété peuvent se propager à l’assurance-chômage parce qu’un changement de propriété (la valeur de ressource dynamique changée) est reconnu par le système de propriété. La plupart des contrôles comprennent la logique <xref:System.Windows.DependencyProperty> qui forcera une autre disposition d’un contrôle si un changement et que la propriété pourrait affecter la disposition. Cependant, toutes les propriétés qui ont une [extension De Markup DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md) que leur valeur sont garantis pour fournir des mises à jour en temps réel dans l’interface utilisateur. Cette fonctionnalité peut encore varier en fonction de la propriété, ainsi que selon le type qui possède la propriété, ou même la structure logique de votre application.

## <a name="styles-datatemplates-and-implicit-keys"></a>Styles, DataTemplates et touches implicites

Bien que tous <xref:System.Windows.ResourceDictionary> les éléments dans un doit avoir une clé, `x:Key`cela ne signifie pas que toutes les ressources doivent avoir un explicite . Plusieurs types d’objets prennent en charge une clé implicite lorsqu’elle est définie en tant que ressource, sachant que la valeur d’une clé est liée à la valeur d’une autre propriété. Ce type de clé est connu comme `x:Key` une clé implicite, alors qu’un attribut est une clé explicite. Vous pouvez remplacer une clé implicite en spécifiant une clé explicite.

Un scénario important pour les <xref:System.Windows.Style>ressources est lorsque vous définissez un . En fait, <xref:System.Windows.Style> a est presque toujours défini comme une entrée dans un dictionnaire de ressources, parce que les styles sont intrinsèquement destinés à la réutilisation. Pour plus d’informations sur les styles, voir [Styling et Templating](styles-templates-overview.md).

Des styles de contrôle peuvent être à la fois créés et référencés au moyen d’une clé implicite. Les styles de thème qui définissent l’apparence par défaut d’un contrôle s’appuient sur cette clé implicite. Du point de vue de sa demande, la clé implicite est le <xref:System.Type> contrôle lui-même. Du point de vue de la définition <xref:System.Windows.Style.TargetType%2A> des ressources, la clé implicite est le style. Par conséquent, si vous créez des thèmes pour des contrôles personnalisés ou la création de styles <xref:System.Windows.Style>qui interagissent avec les styles de thème existants, vous n’avez pas besoin de spécifier une [directive x:Key](../xaml-services/xkey-directive.md) pour cela . Et si vous souhaitez utiliser les styles à thème, il n’est pas nécessaire de spécifier un style. Par exemple, la définition de style <xref:System.Windows.Style> suivante fonctionne, même si la ressource ne semble pas avoir une clé :

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

Ce style a vraiment une clé: la clé `typeof(System.Windows.Controls.Button)`implicite . Dans le balisage, <xref:System.Windows.Style.TargetType%2A> vous pouvez spécifier un directement comme nom de type (ou vous pouvez utiliser optionnellement [x:Type...](../xaml-services/xtype-markup-extension.md) pour retourner <xref:System.Type>un .

Grâce aux mécanismes de style thème par défaut utilisés par WPF, ce style est appliqué comme le style de temps d’exécution d’un <xref:System.Windows.Controls.Button> sur la page, même si le <xref:System.Windows.Controls.Button> lui-même ne tente pas de spécifier sa <xref:System.Windows.FrameworkElement.Style%2A> propriété ou une référence de ressource spécifique au style. Votre style défini dans la page se trouve plus tôt dans la séquence de recherche que le style de dictionnaire de thème, en utilisant la même clé que le style de dictionnaire de thème a. Vous pouvez `<Button>Hello</Button>` simplement spécifier n’importe <xref:System.Windows.Style.TargetType%2A> où dans la page, et le style que vous définissez avec de `Button` s’appliquerait à ce bouton. Si vous voulez, vous pouvez toujours explicitement la <xref:System.Windows.Style.TargetType%2A> clé du style avec la même valeur de type que pour la clarté dans votre balisage, mais qui est facultatif.

Les touches implicites pour les <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> styles `true`ne s’appliquent pas sur un contrôle si c’est . (Notez <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> également que pourrait être défini dans le cadre du comportement natif pour la classe de contrôle, plutôt que explicitement sur une instance du contrôle.) En outre, afin de prendre en charge les clés <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> implicites pour les scénarios de classe dérivés, le contrôle doit l’emporter (tous les contrôles existants fournis dans le cadre de WPF comprennent cette dérogation). Pour plus d’informations sur les styles, les thèmes et la conception de contrôle, voir [Lignes directrices pour la conception des contrôles stylables](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md).

<xref:System.Windows.DataTemplate>a également une clé implicite. La clé implicite <xref:System.Windows.DataTemplate> pour <xref:System.Windows.DataTemplate.DataType%2A> un est la valeur de la propriété. <xref:System.Windows.DataTemplate.DataType%2A>peut également être spécifié comme le nom du type plutôt que d’utiliser explicitement [x:Type ...](../xaml-services/xtype-markup-extension.md). Pour plus de détails, voir [Data Templating Overview](../../framework/wpf/data/data-templating-overview.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.ResourceDictionary>
- [Ressources d’application](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Ressources et code](../../framework/wpf/advanced/resources-and-code.md)
- [Définir et faire référence à une ressource](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [Aperçu de la gestion des applications](../../framework/wpf/app-development/application-management-overview.md)
- [x: Extension de balisage de type](../xaml-services/xtype-markup-extension.md)
- [Extension de balisage StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [Extension de balisage DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
