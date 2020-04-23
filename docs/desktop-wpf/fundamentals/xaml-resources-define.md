---
title: Définir des ressources XAML
description: En savoir plus sur les ressources XAML dans WPF pour .NET Core. Comprendre les types de ressources XAML et apprendre à définir des ressources XAML.
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
# <a name="overview-of-xaml-resources"></a>Vue d’ensemble des ressources XAML

Une ressource est un objet qui peut être réutilisé à différents emplacements dans votre application. Par exemple, les styles et les pinceaux sont des ressources. Cette vue d’ensemble décrit comment utiliser des ressources en Extensible Application Markup Language (XAML). Vous pouvez également créer des ressources et y accéder à l’aide de code.

> [!NOTE]
> Les ressources XAML décrites dans cet article sont différentes des *ressources d’application* qui sont généralement des fichiers ajoutés à une application, tels que le contenu, les données ou les fichiers incorporés.

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>Utilisation de ressources en XAML

L’exemple suivant définit une <xref:System.Windows.Media.SolidColorBrush> en tant que ressource sur l’élément racine d’une page. L’exemple référence ensuite la ressource et l’utilise pour définir les propriétés de plusieurs éléments enfants, y <xref:System.Windows.Shapes.Ellipse>compris un <xref:System.Windows.Controls.TextBlock>, un et <xref:System.Windows.Controls.Button>un.

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

Chaque élément au niveau de l'<xref:System.Windows.FrameworkElement> infrastructure <xref:System.Windows.FrameworkContentElement>(ou) <xref:System.Windows.FrameworkElement.Resources%2A> a une propriété, qui <xref:System.Windows.ResourceDictionary> est un type qui contient des ressources définies. Vous pouvez définir des ressources sur n’importe quel élément, <xref:System.Windows.Controls.Button>tel qu’un. Toutefois, les ressources sont le plus souvent définies sur l’élément racine, <xref:System.Windows.Controls.Page> qui est dans l’exemple.

Chaque ressource d’un dictionnaire de ressources doit avoir une clé unique. Quand vous définissez des ressources dans le balisage, vous assignez la clé unique par le biais de la [directive x :Key](../xaml-services/xkey-directive.md). Cette clé est généralement une chaîne, mais vous pouvez aussi la définir en tant qu’autres types d’objets en utilisant les extensions de balisage appropriées. Les clés de non-chaîne pour les ressources sont utilisées par certaines fonctionnalités dans WPF, notamment pour les styles, les ressources de composant et le style de données.

Vous pouvez utiliser une ressource définie avec la syntaxe d’extension de balisage de ressource qui spécifie le nom de clé de la ressource. Par exemple, utilisez la ressource en tant que valeur d’une propriété sur un autre élément.

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

Dans l' `{StaticResource MyBrush}` exemple précédent, lorsque le chargeur XAML traite la valeur de la <xref:System.Windows.Controls.Control.Background%2A> propriété sur <xref:System.Windows.Controls.Button>, la logique de recherche de la ressource vérifie d’abord le dictionnaire <xref:System.Windows.Controls.Button> de ressources pour l’élément. Si <xref:System.Windows.Controls.Button> n’a pas de définition de la clé `MyBrush` de ressource (dans cet exemple, sa collection de ressources est vide), la recherche vérifie ensuite l’élément parent <xref:System.Windows.Controls.Button>de, qui <xref:System.Windows.Controls.Page>est. Si vous définissez une ressource sur l' <xref:System.Windows.Controls.Page> élément racine, tous les éléments de l’arborescence logique du <xref:System.Windows.Controls.Page> peuvent y accéder. Et vous pouvez réutiliser la même ressource pour définir la valeur d’une propriété qui accepte le même type que celui représenté par la ressource. Dans l’exemple précédent, la même `MyBrush` ressource définit deux propriétés différentes : le <xref:System.Windows.Controls.Control.Background%2A> d’un <xref:System.Windows.Controls.Button>et le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>.

## <a name="static-and-dynamic-resources"></a>Ressources statiques et dynamiques

Une ressource peut être référencée en tant que valeur statique ou dynamique. Les références sont créées à l’aide de l' [extension de balisage StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md) ou de l' [extension de balisage DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md). Une extension de balisage est une fonctionnalité XAML qui vous permet de spécifier une référence d’objet en faisant en sorte que l’extension de balisage traite la chaîne d’attribut et retourne l’objet à un chargeur XAML. Pour plus d’informations sur le comportement de l’extension de balisage, consultez [extensions de balisage et XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

Lorsque vous utilisez une extension de balisage, vous fournissez généralement un ou plusieurs paramètres sous forme de chaîne qui sont traités par cette extension de balisage particulière. L' [extension de balisage StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md) traite une clé en recherchant la valeur de cette clé dans tous les dictionnaires de ressources disponibles. Le traitement se produit pendant le chargement, ce qui est le cas lorsque le processus de chargement doit assigner la valeur de la propriété. L' [extension de balisage DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md) traite à la place une clé en créant une expression, et cette expression reste non évaluée jusqu’à ce que l’application s’exécute, auquel cas l’expression est évaluée et fournit une valeur.

Quand vous faites référence à une ressource, les points suivants peuvent influer sur votre choix d’utiliser une référence de ressource statique ou à une ressource dynamique :

- Lorsque vous déterminez la conception globale de la façon dont vous créez les ressources pour votre application (par page, dans l’application, en XAML libre ou dans un assembly de ressources uniquement), tenez compte des points suivants :

- Fonctionnalités de l’application. Les ressources sont-elles mises à jour en temps réel dans le cadre des exigences de votre application ?
- Le comportement de recherche respectif de ce type de référence de ressource.
- Le type de ressource ou de propriété spécifique et le comportement natif de ces types.

## <a name="static-resources"></a>Ressources statiques

Les références de ressources statiques conviennent parfaitement dans les conditions suivantes :

- La conception de votre application concentre la plupart de ses ressources dans des dictionnaires de ressources de page ou d’application. Les références de ressources statiques ne sont pas réévaluées en fonction des comportements d’exécution, tels que le rechargement d’une page. Par conséquent, il peut y avoir des avantages en matière de performances pour éviter un grand nombre de références de ressources dynamiques lorsqu’elles ne sont pas nécessaires en fonction de la conception de vos ressources et de vos applications.

- Vous définissez la valeur d’une propriété qui n’est pas sur <xref:System.Windows.DependencyObject> un ou <xref:System.Windows.Freezable>un.

- Vous créez un dictionnaire de ressources qui sera compilé dans une DLL et empaqueté dans le cadre de l’application ou partagé entre les applications.

- Vous créez un thème pour un contrôle personnalisé et définissez des ressources utilisées dans les thèmes. Dans ce cas, vous ne souhaitez généralement pas le comportement de recherche de référence de ressource dynamique. vous souhaitez plutôt le comportement de référence de ressource statique afin que la recherche soit prévisible et autonome dans le thème. Avec une référence de ressource dynamique, même une référence dans un thème n’est pas évaluée jusqu’au moment de l’exécution. et il y a un risque que lorsque le thème est appliqué, un élément local redéfinit une clé que votre thème tente de référencer, et l’élément local se situe avant le thème lui-même dans la recherche. Si cela se produit, votre thème ne se comportera pas comme prévu.

- Vous utilisez des ressources pour définir un grand nombre de propriétés de dépendance. Les propriétés de dépendance ont une mise en cache de valeur effective activée par le système de propriétés. par conséquent, si vous fournissez une valeur pour une propriété de dépendance qui peut être évaluée au moment du chargement, la propriété de dépendance n’a pas besoin de rechercher une expression réévaluée et peut retourner la dernière valeur effective. Cette technique peut s’avérer un gain de performances.

- Vous souhaitez modifier la ressource sous-jacente pour tous les consommateurs, ou vous souhaitez conserver des instances accessibles en écriture distinctes pour chaque consommateur à l’aide de l' [attribut x :Shared](../xaml-services/xshared-attribute.md).

### <a name="static-resource-lookup-behavior"></a>Comportement de la recherche de ressources statiques

Les éléments suivants décrivent le processus de recherche qui se produit automatiquement lorsqu’une ressource statique est référencée par une propriété ou un élément :

01. Le processus de recherche recherche la clé demandée dans le dictionnaire de ressources qui est spécifié par l’élément définissant la propriété.

01. Le processus de recherche parcourt ensuite l’arborescence logique vers le haut jusqu’à l’élément parent et son dictionnaire de ressources. Ce processus se poursuit jusqu’à ce que l’élément racine soit atteint.

01. Les ressources de l’application sont vérifiées. Les ressources d’application sont les ressources du dictionnaire de ressources qui sont définies <xref:System.Windows.Application> par l’objet pour votre application WPF.

Les références de ressources statiques issues d’un dictionnaire de ressources doivent référencer une ressource qui a déjà été définie sur le plan lexical avant la référence de ressource. Les références anticipées ne peuvent pas être résolues par une référence de ressource statique. Pour cette raison, concevez votre structure de dictionnaire de ressources de sorte que les ressources soient définies au début ou à proximité du dictionnaire de ressources respectif.

La recherche de ressources statiques peut s’étendre aux thèmes ou aux ressources système, mais cette recherche est prise en charge uniquement parce que le chargeur XAML diffère la requête. Le report est nécessaire pour que le thème du Runtime au moment du chargement de la page s’applique correctement à l’application. Toutefois, les références de ressources statiques à des clés connues pour exister uniquement dans les thèmes ou en tant que ressources système ne sont pas recommandées, car ces références ne sont pas réévaluées si le thème est modifié par l’utilisateur en temps réel. Une référence de ressource dynamique est plus fiable quand vous demandez des ressources de système ou de thème. L’exception se présente lorsqu’un élément de thème lui-même demande une autre ressource. Ces références doivent être des références de ressources statiques pour les raisons mentionnées précédemment.

Le comportement d’exception si une référence de ressource statique est introuvable varie. Si la ressource a été différée, l’exception se produit lors de l’exécution. Si la ressource n’a pas été différée, l’exception se produit au moment du chargement.

## <a name="dynamic-resources"></a>Ressources dynamiques

Les ressources dynamiques fonctionnent mieux lorsque :

- La valeur de la ressource, y compris les ressources système ou les ressources qui sont autrement définissables par l’utilisateur, dépend des conditions qui ne sont pas connues jusqu’au moment de l’exécution. Par exemple, vous pouvez créer des valeurs d’accesseur Set qui font référence à <xref:System.Windows.SystemColors>des <xref:System.Windows.SystemFonts>propriétés système <xref:System.Windows.SystemParameters>telles qu’exposées par, ou. Ces valeurs sont véritablement dynamiques, car elles proviennent de l’environnement d’exécution de l’utilisateur et du système d’exploitation. Vous pouvez également avoir des thèmes de niveau application qui peuvent changer, où l’accès aux ressources de niveau page doit également capturer le changement.

- Vous créez ou référencez des styles de thème pour un contrôle personnalisé.

- Vous avez l’intention d’ajuster le contenu <xref:System.Windows.ResourceDictionary> d’un pendant une durée de vie d’application.

- Vous avez une structure de ressources complexe avec des interdépendances, où une référence anticipée peut être nécessaire. Les références de ressources statiques ne prennent pas en charge les références anticipées, mais les références de ressources dynamiques les prennent en charge, car la ressource n’a pas besoin d’être évaluée avant l’exécution, et les références anticipées ne sont donc pas un concept pertinent.

- Vous faites référence à une ressource qui est volumineuse du point de vue d’une compilation ou d’une plage de travail, et la ressource peut ne pas être utilisée immédiatement lors du chargement de la page. Les références de ressources statiques se chargent toujours à partir de XAML lors du chargement de la page. Toutefois, une référence de ressource dynamique ne se charge pas tant qu’elle n’est pas utilisée.

- Vous créez un style dans lequel les valeurs d’accesseur Set peuvent provenir d’autres valeurs qui sont influencées par des thèmes ou d’autres paramètres utilisateur.

- Vous appliquez des ressources aux éléments qui peuvent être reapparentés dans l’arborescence logique pendant la durée de vie de l’application. Le changement de parent peut aussi changer l’étendue de la recherche de ressources, donc si vous souhaitez que la ressource d’un élément réapparenté soit réévaluée en fonction de la nouvelle étendue, utilisez toujours une référence de ressource dynamique.

### <a name="dynamic-resource-lookup-behavior"></a>Comportement de la recherche de ressources dynamiques

Le comportement de recherche de ressources pour une référence de ressource dynamique correspond au comportement de recherche dans <xref:System.Windows.FrameworkElement.FindResource%2A> votre <xref:System.Windows.FrameworkElement.SetResourceReference%2A>code si vous appelez ou :

01. La recherche recherche la clé demandée dans le dictionnaire de ressources défini par l’élément qui définit la propriété :

    - Si l’élément définit une <xref:System.Windows.FrameworkElement.Style%2A> propriété, le <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName> <xref:System.Windows.Style.Resources> dictionnaire de l’élément est activé.

    - Si l’élément définit une <xref:System.Windows.Controls.Control.Template%2A> propriété, le <xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName> dictionnaire de l’élément est activé.

01. La recherche parcourt l’arborescence logique vers le haut jusqu’à l’élément parent et son dictionnaire de ressources. Ce processus se poursuit jusqu’à ce que l’élément racine soit atteint.

01. Les ressources de l’application sont vérifiées. Les ressources d’application sont les ressources du dictionnaire de ressources qui sont définies <xref:System.Windows.Application> par l’objet pour votre application WPF.

01. Le dictionnaire de ressources de thème est activé pour le thème actuellement actif. Si le thème change au moment de l’exécution, la valeur est réévaluée.

01. Les ressources du système sont recherchées.

Le comportement d’exception (le cas échéant) varie :

- Si une ressource a été demandée par <xref:System.Windows.FrameworkElement.FindResource%2A> un appel et qu’elle est introuvable, une exception est levée.

- Si une ressource a été demandée par <xref:System.Windows.FrameworkElement.TryFindResource%2A> un appel et qu’elle est introuvable, aucune exception n’est levée et `null`la valeur retournée est. Si la propriété qui est définie n' `null`accepte pas, il est toujours possible qu’une exception plus profonde soit levée, en fonction de la propriété individuelle définie.

- Si une ressource a été demandée par une référence de ressource dynamique en XAML et qu’elle est introuvable, le comportement dépend du système de propriétés général. Le comportement général est comme si aucune opération de définition de propriété ne s’est produite au niveau de l’emplacement où la ressource existe. Par exemple, si vous tentez de définir l’arrière-plan sur un élément de bouton individuel à l’aide d’une ressource qui n’a pas pu être évaluée, aucun résultat n’est défini, mais la valeur effective peut encore provenir d’autres participants dans le système de propriétés et la priorité de la valeur. Par exemple, la valeur d’arrière-plan peut encore provenir d’un style de bouton défini localement ou du style de thème. Pour les propriétés qui ne sont pas définies par les styles de thème, la valeur effective après l’échec d’une évaluation de ressource peut provenir de la valeur par défaut dans les métadonnées de propriété.

### <a name="restrictions"></a>Restrictions

Les références de ressources dynamiques présentent quelques restrictions notables. Au moins une des conditions suivantes doit être remplie :

- La propriété qui est définie doit être une propriété sur <xref:System.Windows.FrameworkElement> un <xref:System.Windows.FrameworkContentElement>ou un. Cette propriété doit être sauvegardée par un <xref:System.Windows.DependencyProperty>.

- La référence est pour une valeur dans un `StyleSetter`.

- La propriété qui est définie doit être une propriété sur <xref:System.Windows.Freezable> un qui est fourni en tant que valeur d' <xref:System.Windows.FrameworkElement> une <xref:System.Windows.FrameworkContentElement> propriété ou, ou <xref:System.Windows.Setter> d’une valeur.

Étant donné que la propriété qui est définie <xref:System.Windows.DependencyProperty> doit <xref:System.Windows.Freezable> être une propriété ou, la plupart des modifications de propriétés peuvent se propager à l’interface utilisateur, car une modification de propriété (la valeur de ressource dynamique modifiée) est reconnue par le système de propriétés. La plupart des contrôles incluent une logique qui force une autre disposition d’un <xref:System.Windows.DependencyProperty> contrôle si une modification et cette propriété peuvent affecter la disposition. Toutefois, toutes les propriétés qui ont une [extension de balisage DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md) comme valeur sont assurées de fournir des mises à jour en temps réel dans l’interface utilisateur. Cette fonctionnalité peut varier en fonction de la propriété, et en fonction du type qui possède la propriété, ou même de la structure logique de votre application.

## <a name="styles-datatemplates-and-implicit-keys"></a>Styles, DataTemplate et clés implicites

Bien que tous les éléments <xref:System.Windows.ResourceDictionary> d’un doivent avoir une clé, cela ne signifie pas que toutes les ressources `x:Key`doivent avoir un explicite. Plusieurs types d’objets prennent en charge une clé implicite lorsqu’elle est définie en tant que ressource, sachant que la valeur d’une clé est liée à la valeur d’une autre propriété. Ce type de clé est connu sous le nom de clé implicite `x:Key` , tandis qu’un attribut est une clé explicite. Vous pouvez remplacer une clé implicite en spécifiant une clé explicite.

Un scénario important pour les ressources est lorsque vous définissez <xref:System.Windows.Style>un. En fait, un <xref:System.Windows.Style> est presque toujours défini en tant qu’entrée dans un dictionnaire de ressources, car les styles sont par nature prévus pour être réutilisés. Pour plus d’informations sur les styles, consultez [stylisation et création de modèles](styles-templates-overview.md).

Des styles de contrôle peuvent être à la fois créés et référencés au moyen d’une clé implicite. Les styles de thème qui définissent l’apparence par défaut d’un contrôle s’appuient sur cette clé implicite. Du point de vue de la demande, la clé implicite <xref:System.Type> est le du contrôle lui-même. Du point de vue de la définition des ressources, la clé implicite est le <xref:System.Windows.Style.TargetType%2A> du style. Par conséquent, si vous créez des thèmes pour des contrôles personnalisés ou créez des styles qui interagissent avec les styles de thème existants, vous n’avez pas besoin <xref:System.Windows.Style>de spécifier une [directive x :Key](../xaml-services/xkey-directive.md) pour cela. Et si vous souhaitez utiliser les styles à thème, il n’est pas nécessaire de spécifier un style. Par exemple, la définition de style suivante fonctionne, même si <xref:System.Windows.Style> la ressource ne semble pas avoir une clé :

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

Ce style a vraiment une clé : la clé `typeof(System.Windows.Controls.Button)`implicite. Dans le balisage, vous pouvez <xref:System.Windows.Style.TargetType%2A> spécifier un directement comme nom de type (ou vous pouvez éventuellement utiliser [{x :type...}](../xaml-services/xtype-markup-extension.md) pour retourner un <xref:System.Type>.

Par le biais des mécanismes de style de thème par défaut utilisés par WPF, ce style est appliqué comme <xref:System.Windows.Controls.Button> style d’exécution d’un sur la <xref:System.Windows.Controls.Button> page, même si le lui <xref:System.Windows.FrameworkElement.Style%2A> -même ne tente pas de spécifier sa propriété ou une référence de ressource spécifique au style. Votre style défini dans la page est trouvé précédemment dans la séquence de recherche que le style du dictionnaire de thèmes, en utilisant la même clé que celle du style du dictionnaire de thèmes. Vous pouvez simplement spécifier `<Button>Hello</Button>` n’importe où dans la page, et le style que <xref:System.Windows.Style.TargetType%2A> vous `Button` avez défini avec la valeur s’applique à ce bouton. Si vous le souhaitez, vous pouvez toujours appliquer explicitement le style avec la même valeur de <xref:System.Windows.Style.TargetType%2A> type que pour clarifier la balise, mais cela est facultatif.

Les clés implicites pour les styles ne s’appliquent <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> pas `true`à un contrôle si est. (Notez également que <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> peut être défini dans le cadre du comportement natif de la classe de contrôle, plutôt que de manière explicite sur une instance du contrôle.) En outre, pour prendre en charge les clés implicites pour les scénarios de classe dérivée <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> , le contrôle doit se substituer (tous les contrôles existants fournis dans le cadre de WPF incluent ce remplacement). Pour plus d’informations sur les styles, les thèmes et la conception de contrôles, consultez [instructions pour la conception de contrôles stylisés](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md).

<xref:System.Windows.DataTemplate>a également une clé implicite. La clé implicite pour <xref:System.Windows.DataTemplate> un est <xref:System.Windows.DataTemplate.DataType%2A> la valeur de la propriété. <xref:System.Windows.DataTemplate.DataType%2A>peut également être spécifié en tant que nom du type au lieu d’utiliser explicitement [{x :type...}](../xaml-services/xtype-markup-extension.md). Pour plus d’informations, consultez [vue d’ensemble des modèles de données](../../framework/wpf/data/data-templating-overview.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.ResourceDictionary>
- [Ressources d’application](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Ressources et code](../../framework/wpf/advanced/resources-and-code.md)
- [Définir et référencer une ressource](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [Vue d’ensemble de la gestion des applications](../../framework/wpf/app-development/application-management-overview.md)
- [x :Type (extension de balisage)](../xaml-services/xtype-markup-extension.md)
- [StaticResource, extension de balisage](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [DynamicResource, extension de balisage](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
