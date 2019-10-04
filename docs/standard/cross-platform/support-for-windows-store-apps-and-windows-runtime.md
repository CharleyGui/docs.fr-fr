---
title: Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Windows Store apps, .NET Framework support for
- Windows Runtime, .NET Framework support for
- .NET for Windows Store apps
- .NET Framework, and Windows Store apps
- .NET Framework, and Windows Runtime
ms.assetid: 6fa7d044-ae12-4c54-b8ee-50915607a565
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f46d21123ecfda4bd336edbbd79fabf01e002a4
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835325"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime

Le .NET Framework 4,5 prend en charge un certain nombre de scénarios de développement logiciel avec le Windows Runtime. Ces scénarios se répartissent en trois catégories :

- Développement d’applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] avec des contrôles XAML, comme décrit dans la feuille [de route C# pour les applications du Windows Store à l’aide de ou de Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [Comment les OT (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))et [.net pour les applications du Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- Développement de bibliothèques de classes à utiliser dans les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] que vous créez avec le .NET Framework.

- Développement de composants Windows Runtime, empaquetés dans. Fichiers WinMD, qui peuvent être utilisés par n’importe quel langage de programmation prenant en charge l’Windows Runtime. Par exemple, consultez [création de composants Windows Runtime C# dans et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

Cette rubrique décrit la prise en charge fournie par le .NET Framework pour les trois catégories, et décrit les scénarios pour les composants Windows Runtime. La première section contient des informations de base sur la relation entre le .NET Framework et le Windows Runtime, et explique certains singularités que vous pouvez rencontrer dans le système d’aide et l’IDE. La [deuxième section](#WindowsRuntimeComponents) décrit des scénarios de développement de composants Windows Runtime.

## <a name="the-basics"></a>Principes de base

Le .NET Framework prend en charge les trois scénarios de développement répertoriés précédemment en fournissant [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] et en prenant en charge le Windows Runtime lui-même.

- Les [espaces de noms .NET Framework et Windows Runtime](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) fournissent une vue simplifiée des bibliothèques de classes .NET Framework et incluent uniquement les types et les membres que vous pouvez utiliser pour créer des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] et des composants Windows Runtime.

  - Quand vous utilisez Visual Studio (Visual Studio 2012 ou version ultérieure) pour développer une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ou un composant Windows Runtime, un ensemble d’assemblys de référence garantit que seuls les types et membres pertinents sont visibles.

  - Ce jeu d’API rationalisé est simplifié par la suppression des fonctionnalités qui sont dupliquées dans le .NET Framework ou qui dupliquent des fonctionnalités Windows Runtime. Par exemple, il contient uniquement les versions génériques des types de collection et le modèle d’objet de document XML est éliminé en faveur de l’ensemble d’API XML Windows Runtime.

  - Les fonctionnalités qui encapsulent simplement l’API du système d’exploitation sont également supprimées, car le Windows Runtime est facile à appeler à partir du code managé.

  Pour en savoir plus sur le [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], consultez la [vue d’ensemble de .net pour les applications du Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Pour en savoir plus sur le processus de sélection d’API, consultez l’entrée [.net for Metro style Apps](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) dans le blog .net.

- Le [Windows Runtime](/uwp/api/) fournit les éléments d’interface utilisateur pour la génération d’applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], et fournit l’accès aux fonctionnalités du système d’exploitation. À l’instar de la .NET Framework, le Windows Runtime a C# des métadonnées qui permettent aux compilateurs et Visual Basic d’utiliser le Windows Runtime la manière dont ils utilisent les bibliothèques de classes .NET Framework. Le .NET Framework simplifie l’utilisation du Windows Runtime en masquant certaines différences :

  - Certaines différences dans les modèles de programmation entre le .NET Framework et le Windows Runtime, comme le modèle pour l’ajout et la suppression de gestionnaires d’événements, sont masquées. Vous utilisez simplement le modèle .NET Framework.

  - Certaines différences dans les types couramment utilisés (par exemple les collections et les types primitifs) sont masquées. Vous utilisez simplement le type de .NET Framework, comme indiqué dans [différences visibles dans l’IDE](#DifferencesVisibleInIDE), plus loin dans cet article.

La plupart du temps, la prise en charge .NET Framework pour le Windows Runtime est transparente. La section suivante présente certaines des différences évidentes entre le code managé et le Windows Runtime.

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>La .NET Framework et la documentation de référence Windows Runtime

Les Windows Runtime et les ensembles de documentation .NET Framework sont distincts. Si vous appuyez sur F1 pour afficher l’aide sur un type ou un membre, la documentation de référence de l’ensemble approprié s’affiche. Toutefois, si vous parcourez la [référence Windows Runtime](/uwp/api/) , vous pouvez rencontrer des exemples qui semblent curieuse :

- Les rubriques telles que l’interface <xref:Windows.Foundation.Collections.IIterable%601> n’ont pas de syntaxe de C#déclaration pour Visual Basic ou. Au lieu de cela, une remarque s’affiche au-dessus de la section syntaxe (dans le cas présent, «.NET : Cette interface apparaît en tant que System. Collections. Generic. IEnumerable @ no__t-0T >»). Cela est dû au fait que les .NET Framework et le Windows Runtime offrent des fonctionnalités similaires avec des interfaces différentes. En outre, il existe des différences de comportement : `IIterable` a une méthode `First` plutôt qu’une méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> pour retourner l’énumérateur. Au lieu de vous forcer à apprendre une autre façon d’effectuer une tâche courante, le .NET Framework prend en charge le Windows Runtime en faisant apparaître votre code managé afin d’utiliser le type que vous connaissez. Vous ne verrez pas l’interface `IIterable` dans l’IDE. par conséquent, le seul moyen de le rencontrer dans la documentation de référence de Windows Runtime consiste à parcourir directement cette documentation.

- La documentation <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> illustre un problème étroitement lié : Ses types de paramètres semblent être différents selon les langages. Pour C# et Visual Basic, les types de paramètres sont <xref:System.String?displayProperty=nameWithType> et <xref:System.Uri?displayProperty=nameWithType>. Là encore, c’est parce que le .NET Framework a ses propres types `String` et `Uri`, et pour ces types couramment utilisés, il est inutile d’obliger les utilisateurs du .NET Framework à apprendre une autre manière de faire les choses. Dans l’IDE, le .NET Framework masque les types de Windows Runtime correspondants.

- Dans certains cas, tels que la structure <xref:Windows.UI.Xaml.GridLength>, le .NET Framework fournit un type avec le même nom, mais davantage de fonctionnalités. Par exemple, un ensemble de rubriques sur les constructeurs et les propriétés sont associées à `GridLength`, mais elles ont des blocs de syntaxe uniquement pour Visual Basic et C#, car les membres sont disponibles uniquement dans le code managé. Dans le Windows Runtime, les structures ont uniquement des champs. La structure Windows Runtime nécessite une classe d’assistance, <xref:Windows.UI.Xaml.GridLengthHelper>, pour fournir des fonctionnalités équivalentes. Vous ne verrez par cette classe d’assistance dans l’IDE quand vous écrirez du code managé.

- Dans l’IDE, les types de Windows Runtime semblent dériver de <xref:System.Object?displayProperty=nameWithType>. Ils semblent avoir des membres hérités de <xref:System.Object>, tels que <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Ces membres fonctionnent comme si les types étaient réellement hérités de <xref:System.Object>, et les types de Windows Runtime peuvent être castés en <xref:System.Object>. Cette fonctionnalité fait partie de la prise en charge fournie par le .NET Framework pour le Windows Runtime. Toutefois, si vous affichez les types dans la documentation de référence Windows Runtime, ces membres ne s’affichent pas. La documentation sur ces membres hérités apparents est fournie par la documentation de référence sur <xref:System.Object?displayProperty=nameWithType>.

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>Différences visibles dans l’IDE

Dans des scénarios de programmation plus avancés, tels que l’utilisation d’un C# Windows Runtime composant écrit dans pour fournir la logique d’application pour une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] générée pour Windows à l’aide de JavaScript, ces différences sont apparentes dans l’IDE et dans la documentation. Lorsque votre composant retourne un `IDictionary<int, string>` à JavaScript et que vous l’examinez dans le débogueur JavaScript, vous verrez les méthodes de `IMap<int, string>`, car JavaScript utilise le type de Windows Runtime. Certains types de collections fréquemment utilisés dont l’apparence est différente dans les deux langages sont répertoriés dans le tableau suivant :

|Type Windows Runtime|Type .NET Framework correspondant|
|--------------------------------------------------------------|---------------------------------------|
|`IIterable<T>`|`IEnumerable<T>`|
|`IIterator<T>`|`IEnumerator<T>`|
|`IVector<T>`|`IList<T>`|
|`IVectorView<T>`|`IReadOnlyList<T>`|
|`IMap<K, V>`|`IDictionary<TKey, TValue>`|
|`IMapView<K, V>`|`IReadOnlyDictionary<TKey, TValue>`|
|`IBindableIterable`|`IEnumerable`|
|`IBindableVector`|`IList`|
|`Windows.UI.Xaml.Data.INotifyPropertyChanged`|`System.ComponentModel.INotifyPropertyChanged`|
|`Windows.UI.Xaml.Data.PropertyChangedEventHandler`|`System.ComponentModel.PropertyChangedEventHandler`|
|`Windows.UI.Xaml.Data.PropertyChangedEventArgs`|`System.ComponentModel.PropertyChangedEventArgs`|

Dans le Windows Runtime, `IMap<K, V>` et `IMapView<K, V>` sont itérés à l’aide de `IKeyValuePair`. Lorsque vous les passez au code managé, ils apparaissent comme `IDictionary<TKey, TValue>` et `IReadOnlyDictionary<TKey, TValue>`, donc bien sûr vous utilisez `System.Collections.Generic.KeyValuePair<TKey, TValue>` pour les énumérer.

La façon dont les interfaces apparaissent dans le code managé affecte la façon dont les types qui implémentent ces interfaces apparaissent. Par exemple, la classe `PropertySet` implémente `IMap<K, V>`, qui s'affiche dans le code managé sous la forme `IDictionary<TKey, TValue>`. `PropertySet` apparaît comme ayant implémenté `IDictionary<TKey, TValue>` au lieu de `IMap<K, V>`, donc en code managé une méthode `Add` semble se comporter comme la méthode `Add` sur les dictionnaires .NET Framework. Il ne semble pas avoir de méthode `Insert`.

Pour plus d’informations sur l’utilisation de l' .NET Framework pour créer un composant Windows Runtime et pour obtenir une procédure pas à pas qui montre comment utiliser ce composant avec JavaScript, consultez [création de composants Windows Runtime C# dans et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>Types primitifs

Pour permettre l’utilisation naturelle de l’Windows Runtime dans du code managé, .NET Framework types primitifs apparaissent au lieu de Windows Runtime types primitifs dans votre code. Dans le .NET Framework, les types primitifs, comme la structure `Int32` ont de nombreuses propriétés et méthodes utiles, telles que la méthode `Int32.TryParse`. En revanche, les types primitifs et les structures dans le Windows Runtime ont uniquement des champs. Quand vous utilisez des primitives dans du code managé, elles semblent être des types .NET Framework, et vous pouvez en utiliser les propriétés et les méthodes comme vous le faites habituellement. La liste suivante fournit un résumé :

- Pour les Windows Runtime primitives `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (collection immuable de caractères Unicode), `Enum`, `UInt32`, `UInt64` et `Guid`, utilisez le type du même nom dans l’espace de noms 0.

- Pour `UInt8`, utilisez `System.Byte`.

- Pour `Char16`, utilisez `System.Char`.

- Pour l'interface `IInspectable`, utilisez `System.Object`.

- Pour `HRESULT`, utilisez une structure avec un membre `System.Int32`.

Comme avec les types d’interfaces, le seul moment où vous pouvez voir la preuve de cette représentation est lorsque votre projet .NET Framework est un composant Windows Runtime utilisé par une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] créée à l’aide de JavaScript.

D’autres types de Windows Runtime couramment utilisés qui apparaissent dans du code managé comme leurs équivalents .NET Framework incluent la structure `Windows.Foundation.DateTime`, qui apparaît dans le code managé comme structure <xref:System.DateTimeOffset?displayProperty=nameWithType>, et la structure `Windows.Foundation.TimeSpan`, qui apparaît comme <xref:System.TimeSpan?displayProperty=nameWithType> arborescence.

### <a name="other-differences"></a>Autres différences

Dans certains cas, le fait que les types de .NET Framework apparaissent dans votre code au lieu des types de Windows Runtime nécessite une action de votre part. Par exemple, la classe <xref:Windows.Foundation.Uri?displayProperty=nameWithType> apparaît comme <xref:System.Uri?displayProperty=nameWithType> dans .NET Framework code. <xref:System.Uri?displayProperty=nameWithType> autorise un URI relatif, mais <xref:Windows.Foundation.Uri?displayProperty=nameWithType> requiert un URI absolu. Par conséquent, lorsque vous transmettez un URI à une méthode Windows Runtime, vous devez vous assurer qu’il est absolu. Consultez [transmission d’un URI au Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>Scénarios pour le développement de composants Windows Runtime

Les scénarios pris en charge pour les composants de Windows Runtime gérés dépendent des principes généraux suivants :

- Windows Runtime composants générés à l’aide du .NET Framework n’ont aucune différence apparente par rapport aux autres Runtimelibraries Windows. Par exemple, si vous implémentez à nouveau un composant Windows Runtime natif à l’aide de code managé, les deux composants sont impossibles à distinguer dans le sens inverse. Le fait que votre composant soit écrit en code managé est invisible pour le code qui l’utilise, même si celui-ci est managé. Cependant, en interne, votre composant constitue du vrai code managé et s’exécute sur le Common Language Runtime (CLR).

- Les composants peuvent contenir des types qui implémentent une logique d’application, des contrôles d’interface utilisateur [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ou les deux.

  > [!NOTE]
  > Nous vous recommandons de séparer les éléments d’interface utilisateur de la logique d’application. De plus, vous ne pouvez pas utiliser de contrôles d’interface utilisateur [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] conçue pour Windows à l’aide de JavaScript et HTML.

- Un composant peut être un projet dans une solution Visual Studio pour une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], ou un composant réutilisable que vous pouvez ajouter à plusieurs solutions.

  > [!NOTE]
  > Si votre composant est utilisé uniquement avec C# ou Visual Basic, il n’y a aucune raison d’en faire un composant Windows Runtime. Si vous en faites une bibliothèque de classes de .NET Framework ordinaire, vous n’êtes pas obligé de limiter sa surface d’API publique aux types de Windows Runtime.

- Vous pouvez libérer des versions de composants réutilisables à l’aide de l’attribut Windows Runtime <xref:Windows.Foundation.Metadata.VersionAttribute> pour identifier les types (et les membres d’un type) qui ont été ajoutés dans différentes versions.

- Les types de votre composant peuvent dériver des types de Windows Runtime. Les contrôles peuvent dériver des types de contrôles primitifs de l’espace de noms <xref:Windows.UI.Xaml.Controls.Primitives> ou de contrôles plus finis, tels que <xref:Windows.UI.Xaml.Controls.Button>.

  > [!IMPORTANT]
  > À partir de [!INCLUDE[win8](../../../includes/win8-md.md)] et du .NET Framework 4,5, tous les types publics dans un composant Windows Runtime managé doivent être sealed. Un type dans un autre composant de Windows Runtime ne peut pas en dériver. Si vous souhaitez fournir un comportement polymorphe dans votre composant, vous pouvez créer une interface et l’implémenter dans les types polymorphes.

- Tous les types de paramètre et de retour sur les types publics de votre composant doivent être des types de Windows Runtime (y compris les types de Windows Runtime que votre composant définit).

Les sections suivantes fournissent des exemples de scénarios courants.

### <a name="application-logic-for-a-includewin8_appname_longincludeswin8-appname-long-mdmd-app-with-javascript"></a>Logique d’application pour une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] avec JavaScript

Quand vous développez une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] pour Windows à l’aide de JavaScript, vous constaterez peut-être que certaines parties de la logique d’application sont plus performantes (ou plus faciles à développer) dans du code managé. JavaScript ne peut pas utiliser les bibliothèques de classes .NET Framework directement, mais vous pouvez faire de la bibliothèque de classes un fichier .WinMD. Dans ce scénario, le composant Windows Runtime fait partie intégrante de l’application. il n’est donc pas judicieux de fournir des attributs de version.

### <a name="reusable-includewin8_appname_longincludeswin8-appname-long-mdmd-ui-controls"></a>Contrôles d’interface utilisateur [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] réutilisables

Vous pouvez empaqueter un ensemble de contrôles d’interface utilisateur associés dans un composant Windows Runtime réutilisable. Le composant peut être commercialisé seul ou utilisé comme élément dans les applications que vous créez. Dans ce scénario, il est logique d’utiliser l’attribut Windows Runtime <xref:Windows.Foundation.Metadata.VersionAttribute> pour améliorer la compatibilité.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Logique d’application réutilisable à partir d’applications .NET Framework existantes

Vous pouvez empaqueter du code managé à partir de vos applications de bureau existantes en tant que composant Windows Runtime autonome. Cela vous permet d’utiliser le composant dans des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] générées à l’aide de C++ ou JavaScript, ainsi que dans des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] générées à l’aide de C# ou Visual Basic. Le contrôle de version est une option s’il existe plusieurs scénarios de réutilisation du code.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Vue d’ensemble de .NET pour les applications Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|Décrit les types de .NET Framework et les membres que vous pouvez utiliser pour créer des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] et des RuntimeComponents Windows. (Dans le Centre de développement Windows.)|
|[Feuille de route pour les applications C# du Windows Store utilisant ou Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Fournit des ressources clés pour vous aider à commencer à développer des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] à l’aide de C# ou Visual Basic, notamment de nombreuses rubriques de démarrage rapide, des instructions et des bonnes pratiques. (Dans le Centre de développement Windows.)|
|[Procédures (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Fournit des ressources clés pour vous aider à commencer à développer des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] à l’aide de C# ou Visual Basic, notamment de nombreuses rubriques de démarrage rapide, des instructions et des bonnes pratiques. (Dans le Centre de développement Windows.)|
|[Création de composants Windows Runtime en C# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|Décrit comment créer un composant Windows Runtime à l’aide du .NET Framework, explique comment l’utiliser dans le cadre d’une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] générée pour Windows à l’aide de JavaScript et décrit comment déboguer la combinaison avec Visual Studio. (Dans le Centre de développement Windows.)|
|[Référence Windows Runtime](/uwp/api/)|La documentation de référence pour le Windows Runtime. (Dans le Centre de développement Windows.)|
|[Passage d’un URI au Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Décrit un problème qui peut se produire quand vous transmettez un URI à partir du code managé à la Windows Runtime, et comment l’éviter.|
