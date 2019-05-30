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
ms.openlocfilehash: 45e28ebb9319447f2e1ae98f1de883f90840720f
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378295"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime
Le .NET Framework 4.5 prend en charge un nombre de scénarios de développement de logiciel avec le [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Ces scénarios se répartissent en trois catégories :

- Développement [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] avec les contrôles XAML, comme décrit dans les applications [des applications de feuille de route pour Windows Store à l’aide de c# ou Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [comment Ot (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10)), et [vue d’ensemble des applications .NET pour Windows Store ](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- Développement de bibliothèques de classes à utiliser dans les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] que vous créez avec le .NET Framework.

- Développement de composants [!INCLUDE[wrt](../../../includes/wrt-md.md)], empaquetés dans des fichiers .WinMD, qui peuvent être utilisés par n’importe quel langage de programmation qui prend en charge le [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Par exemple, consultez [création de composants Windows Runtime en c# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

 Cette rubrique décrit la prise en charge fournie par le .NET Framework pour ces trois catégories, et décrit les scénarios pour les composants [!INCLUDE[wrt](../../../includes/wrt-md.md)]. La première section comprend des informations de base sur la relation entre le .NET Framework et le [!INCLUDE[wrt](../../../includes/wrt-md.md)], et explique certaines singularités que vous pouvez rencontrer dans le système d’aide et l’IDE. Le [deuxième section](#WindowsRuntimeComponents) décrit des scénarios de développement [!INCLUDE[wrt](../../../includes/wrt-md.md)] composants.

## <a name="the-basics"></a>Principes de base
 Le .NET Framework prend en charge les trois scénarios de développement répertoriés précédemment en fournissant [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], et en prenant en charge le [!INCLUDE[wrt](../../../includes/wrt-md.md)] proprement dit.

- [Espaces de noms .NET framework et Windows Runtime](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) fournit une vue simplifiée des bibliothèques de classes .NET Framework et incluent uniquement les types et membres que vous pouvez utiliser pour créer [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications et [!INCLUDE[wrt](../../../includes/wrt-md.md)] composants.

    - Lorsque vous utilisez Visual Studio (Visual Studio 2012 ou version ultérieure) pour développer un [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] application ou un [!INCLUDE[wrt](../../../includes/wrt-md.md)] composant, un jeu d’assemblys de référence permet de s’assurer que vous voyez uniquement les types pertinents et les membres.

    - Cet ensemble d’API est davantage simplifié par la suppression de fonctionnalités qui sont dupliquées dans le .NET Framework ou qui dupliquent des fonctionnalités [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Par exemple, il contient uniquement les versions génériques des types de collections, et le modèle objet de document XML est éliminé en faveur de l’ensemble d’API XML [!INCLUDE[wrt](../../../includes/wrt-md.md)].

    - Les fonctionnalités qui ne font qu’envelopper l’API du système d’exploitation sont également supprimées, car le [!INCLUDE[wrt](../../../includes/wrt-md.md)] est facile à appeler à partir du code managé.

     Pour en savoir plus sur la [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], consultez le [vue d’ensemble des applications .NET pour Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Pour en savoir plus sur le processus de sélection d’API, consultez le [.NET pour les applications de style Metro](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) entrée dans le blog .NET.

- Le [Windows Runtime](/uwp/api/) fournit des éléments d’interface de l’utilisateur pour la création de [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications et donne accès aux fonctionnalités du système d’exploitation. Comme le .NET Framework, le [!INCLUDE[wrt](../../../includes/wrt-md.md)] a des métadonnées qui permettent aux compilateurs C# et Visual Basic d’utiliser les bibliothèques de classes [!INCLUDE[wrt](../../../includes/wrt-md.md)] de la même façon que les bibliothèques de classes .NET Framework. Le .NET Framework simplifie l’utilisation du [!INCLUDE[wrt](../../../includes/wrt-md.md)] en masquant certaines différences :

    - Certaines différences dans les modèles de programmation entre le .NET Framework et le [!INCLUDE[wrt](../../../includes/wrt-md.md)], tels que le modèle pour ajouter et supprimer des gestionnaires d’événements, sont masquées. Vous utilisez simplement le modèle .NET Framework.

    - Certaines différences dans les types couramment utilisés (par exemple les collections et les types primitifs) sont masquées. Vous utilisez simplement le type .NET Framework, comme indiqué dans [différences visibles dans l’IDE](#DifferencesVisibleInIDE), plus loin dans cet article.

 La plupart du temps, la prise en charge du [!INCLUDE[wrt](../../../includes/wrt-md.md)] par le .NET Framework est transparente. La section suivante décrit certaines des différences apparentes entre le code managé et le [!INCLUDE[wrt](../../../includes/wrt-md.md)].

<a name="AboutReferenceDocumentation"></a>
### <a name="the-net-framework-and-the-includewrtincludeswrt-mdmd-reference-documentation"></a>Le .NET Framework et la documentation de référence du [!INCLUDE[wrt](../../../includes/wrt-md.md)]
 Le Runtime Windows et les jeux de documentation de .NET Framework sont séparés. Si vous appuyez sur F1 pour afficher l’aide sur un type ou un membre, la documentation de référence de l’ensemble approprié s’affiche. Toutefois, si vous parcourez le [de référence Windows Runtime](/uwp/api/) vous rencontrerez des exemples qui pourront vous sembler étranges :

- Rubriques telles que le <xref:Windows.Foundation.Collections.IIterable%601> interface n’avez pas la syntaxe de déclaration pour Visual Basic ou c#. Au lieu de cela, une note apparaît au-dessus de la section syntaxe (dans ce cas, « .NET : Cette interface s’affiche sous forme de System.Collections.Generic.IEnumerable\<T > »). Cela est dû au fait que le .NET Framework et le [!INCLUDE[wrt](../../../includes/wrt-md.md)] fournissent une fonctionnalité similaire avec des interfaces différentes. En outre, il existe des différences de comportement : `IIterable` a une méthode `First` plutôt qu’une méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> pour retourner l’énumérateur. Au lieu de vous contraindre à apprendre une autre manière d’effectuer une tâche courante, le .NET Framework prend en charge le [!INCLUDE[wrt](../../../includes/wrt-md.md)] en donnant l’apparence que votre code managé utilise le type que vous connaissez. Vous ne verrez pas l’interface `IIterable` dans l’IDE. Ainsi, la seule façon dont vous pouvez la rencontrer dans la documentation de référence [!INCLUDE[wrt](../../../includes/wrt-md.md)] est en parcourant directement cette documentation.

- Le <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> documentation illustre un problème étroitement lié : Ses types de paramètres semblent différents pour différentes langues. Pour C# et Visual Basic, les types de paramètres sont <xref:System.String?displayProperty=nameWithType> et <xref:System.Uri?displayProperty=nameWithType>. Là encore, c’est parce que le .NET Framework a ses propres types `String` et `Uri`, et pour ces types couramment utilisés, il est inutile d’obliger les utilisateurs du .NET Framework à apprendre une autre manière de faire les choses. Dans l’IDE, le .NET Framework masque les types [!INCLUDE[wrt](../../../includes/wrt-md.md)] correspondants.

- Dans certains cas, comme le <xref:Windows.UI.Xaml.GridLength> structure, le .NET Framework fournit un type avec le même nom mais davantage de fonctionnalités. Par exemple, un ensemble de rubriques sur les constructeurs et les propriétés sont associées à `GridLength`, mais elles ont des blocs de syntaxe uniquement pour Visual Basic et C#, car les membres sont disponibles uniquement dans le code managé. Dans le [!INCLUDE[wrt](../../../includes/wrt-md.md)], les structures ont uniquement des champs. Le [!INCLUDE[wrt](../../../includes/wrt-md.md)] structure requiert une classe d’assistance, <xref:Windows.UI.Xaml.GridLengthHelper>, pour fournir des fonctionnalités équivalentes. Vous ne verrez par cette classe d’assistance dans l’IDE quand vous écrirez du code managé.

- Dans l’IDE, les types [!INCLUDE[wrt](../../../includes/wrt-md.md)] semblent dériver de <xref:System.Object?displayProperty=nameWithType>. Ils semblent avoir des membres hérités de <xref:System.Object>, tels que <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Ces membres fonctionnent comme si les types héritaient réellement de <xref:System.Object>, et les types [!INCLUDE[wrt](../../../includes/wrt-md.md)] peuvent être convertis en <xref:System.Object>. Cette fonctionnalité fait partie de la prise en charge fournie par le .NET Framework pour le [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Toutefois, si vous affichez les types dans la documentation de référence du [!INCLUDE[wrt](../../../includes/wrt-md.md)], aucun membre n’apparaît. La documentation sur ces membres hérités apparents est fournie par la documentation de référence sur <xref:System.Object?displayProperty=nameWithType>.

<a name="DifferencesVisibleInIDE"></a>
### <a name="differences-that-are-visible-in-the-ide"></a>Différences visibles dans l’IDE
 Dans les scénarios de programmation avancés, comme lors de l’utilisation d’un composant [!INCLUDE[wrt](../../../includes/wrt-md.md)] écrit en C# pour fournir la logique d’application pour une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] conçue pour Windows à l’aide de JavaScript, ces différences sont visibles dans l’IDE et dans la documentation. Quand votre composant retourne un `IDictionary<int, string>` à JavaScript et que vous l’observez dans le débogueur JavaScript, les méthodes de `IMap<int, string>` sont visibles car JavaScript utilise le type [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Certains types de collections fréquemment utilisés dont l’apparence est différente dans les deux langages sont répertoriés dans le tableau suivant :

|Type [!INCLUDE[wrt](../../../includes/wrt-md.md)]|Type .NET Framework correspondant|
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

 Dans le [!INCLUDE[wrt](../../../includes/wrt-md.md)], `IMap<K, V>` et `IMapView<K, V>` sont itérés à l’aide de `IKeyValuePair`. Lorsque vous les passez au code managé, ils apparaissent comme `IDictionary<TKey, TValue>` et `IReadOnlyDictionary<TKey, TValue>`, donc bien sûr vous utilisez `System.Collections.Generic.KeyValuePair<TKey, TValue>` pour les énumérer.

 La façon dont les interfaces apparaissent dans le code managé affecte la façon dont les types qui implémentent ces interfaces apparaissent. Par exemple, la classe `PropertySet` implémente `IMap<K, V>`, qui s'affiche dans le code managé sous la forme `IDictionary<TKey, TValue>`. `PropertySet` apparaît comme ayant implémenté `IDictionary<TKey, TValue>` au lieu de `IMap<K, V>`, donc en code managé une méthode `Add` semble se comporter comme la méthode `Add` sur les dictionnaires .NET Framework. Il ne semble pas avoir de méthode `Insert`.

 Pour plus d’informations sur l’utilisation de .NET Framework pour créer un [!INCLUDE[wrt](../../../includes/wrt-md.md)] composant et une procédure pas à pas qui montre comment utiliser un tel composant avec JavaScript, consultez [création de composants Windows Runtime en c# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>Types primitifs
 Pour permettre l’utilisation naturelle du [!INCLUDE[wrt](../../../includes/wrt-md.md)] dans le code managé, les types primitifs .NET Framework s’affichent au lieu des types primitifs [!INCLUDE[wrt](../../../includes/wrt-md.md)] dans votre code. Dans le .NET Framework, les types primitifs, comme la structure `Int32` ont de nombreuses propriétés et méthodes utiles, telles que la méthode `Int32.TryParse`. En revanche, les types primitifs et les structures dans le [!INCLUDE[wrt](../../../includes/wrt-md.md)] ont uniquement des champs. Quand vous utilisez des primitives dans du code managé, elles semblent être des types .NET Framework, et vous pouvez en utiliser les propriétés et les méthodes comme vous le faites habituellement. La liste suivante fournit un résumé :

- Pour les primitives [!INCLUDE[wrt](../../../includes/wrt-md.md)]`Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (une collection immuables de caractères Unicode), `Enum`, `UInt32`, `UInt64` et `Guid`, utilisez le type portant le même nom que dans l'espace de noms `System`.

- Pour `UInt8`, utilisez `System.Byte`.

- Pour `Char16`, utilisez `System.Char`.

- Pour l'interface `IInspectable`, utilisez `System.Object`.

- Pour `HRESULT`, utilisez une structure avec un membre `System.Int32`.

 Comme avec les types d’interface, le seul moment où vous pouvez voir la preuve de cette représentation est quand votre projet .NET Framework est un composant [!INCLUDE[wrt](../../../includes/wrt-md.md)] utilisé par une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] générée à l’aide de JavaScript.

 Parmi les autres types [!INCLUDE[wrt](../../../includes/wrt-md.md)] fréquemment utilisés qui apparaissent dans le code managé comme leurs équivalents .NET Framework figurent la structure `Windows.Foundation.DateTime` (qui apparaît dans le code managé comme structure <xref:System.DateTimeOffset?displayProperty=nameWithType>) et la structure `Windows.Foundation.TimeSpan` (qui apparaît sous la forme d’une structure <xref:System.TimeSpan?displayProperty=nameWithType>).

### <a name="other-differences"></a>Autres différences
 Dans certains cas, le fait que les types .NET Framework soient affichés dans votre code au lieu des types [!INCLUDE[wrt](../../../includes/wrt-md.md)] nécessite une action de votre part. Par exemple, le <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe apparaît sous la forme <xref:System.Uri?displayProperty=nameWithType> dans le code .NET Framework. <xref:System.Uri?displayProperty=nameWithType> autorise un URI relatif, mais <xref:Windows.Foundation.Uri?displayProperty=nameWithType> nécessite un URI absolu. Ainsi, quand vous transmettez un URI à une méthode [!INCLUDE[wrt](../../../includes/wrt-md.md)], vous devez vérifier qu’il est absolu. (Consultez [transmission d’un URI au Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).)

<a name="WindowsRuntimeComponents"></a>
## <a name="scenarios-for-developing-windows-runtime-components"></a>Scénarios pour le développement de composants Windows Runtime
 Les scénarios pris en charge pour les composants [!INCLUDE[wrt](../../../includes/wrt-md.md)] managés varient en fonction des principes suivants :

- [!INCLUDE[wrt](../../../includes/wrt-md.md)] Les composants créés à l’aide du .NET Framework ne présentent aucune différence apparente par rapport aux autres bibliothèques [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Par exemple, si vous réimplémentez un composant [!INCLUDE[wrt](../../../includes/wrt-md.md)] natif à l’aide de code managé, les deux composants sont, en apparence, impossibles à distinguer. Le fait que votre composant soit écrit en code managé est invisible pour le code qui l’utilise, même si celui-ci est managé. Cependant, en interne, votre composant constitue du vrai code managé et s’exécute sur le Common Language Runtime (CLR).

- Les composants peuvent contenir des types qui implémentent une logique d’application, des contrôles d’interface utilisateur [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ou les deux.

    > [!NOTE]
    >  Nous vous recommandons de séparer les éléments d’interface utilisateur de la logique d’application. De plus, vous ne pouvez pas utiliser de contrôles d’interface utilisateur [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] conçue pour Windows à l’aide de JavaScript et HTML.

- Un composant peut être un projet dans une solution Visual Studio pour une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], ou un composant réutilisable que vous pouvez ajouter à plusieurs solutions.

    > [!NOTE]
    >  Si votre composant doit être utilisé uniquement avec C# ou Visual Basic, il n’existe aucune raison d’en faire un composant [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Si au lieu de cela vous en faites une bibliothèque de classes .NET Framework ordinaire, vous n’avez pas à limiter sa surface d’API publique aux types [!INCLUDE[wrt](../../../includes/wrt-md.md)].

- Vous pouvez publier des versions des composants réutilisables à l’aide de la [!INCLUDE[wrt](../../../includes/wrt-md.md)] <xref:Windows.Foundation.Metadata.VersionAttribute> attribut pour identifier les types (et les membres dans un type) ont été ajoutées dans différentes versions.

- Les types dans votre composant peuvent dériver de types [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Contrôles peuvent dériver des types de contrôles primitifs dans le <xref:Windows.UI.Xaml.Controls.Primitives> espace de noms ou de contrôles plus achevés tels que <xref:Windows.UI.Xaml.Controls.Button>.

    > [!IMPORTANT]
    >  En commençant par [!INCLUDE[win8](../../../includes/win8-md.md)] et le .NET Framework 4.5, tous les types publics managé [!INCLUDE[wrt](../../../includes/wrt-md.md)] composant doit être scellé. Un type dans un autre composant [!INCLUDE[wrt](../../../includes/wrt-md.md)] ne peut pas dériver d’eux. Si vous souhaitez fournir un comportement polymorphe dans votre composant, vous pouvez créer une interface et l’implémenter dans les types polymorphes.

- Tous les types de paramètres et de retour sur les types publics dans votre composant doivent être des types [!INCLUDE[wrt](../../../includes/wrt-md.md)] (notamment les types [!INCLUDE[wrt](../../../includes/wrt-md.md)] définis par votre composant).

 Les sections suivantes fournissent des exemples de scénarios courants.

### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>Logique d’application pour une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] avec JavaScript
 Quand vous développez une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] pour Windows à l’aide de JavaScript, vous constaterez peut-être que certaines parties de la logique d’application sont plus performantes (ou plus faciles à développer) dans du code managé. JavaScript ne peut pas utiliser les bibliothèques de classes .NET Framework directement, mais vous pouvez faire de la bibliothèque de classes un fichier .WinMD. Dans ce scénario, le composant [!INCLUDE[wrt](../../../includes/wrt-md.md)] étant partie intégrante de l’application, il est inutile de fournir des attributs de version.

### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>Contrôles d’interface utilisateur [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] réutilisables
 Vous pouvez empaqueter un ensemble de contrôles d’interface utilisateur associés dans un composant [!INCLUDE[wrt](../../../includes/wrt-md.md)] réutilisable. Le composant peut être commercialisé seul ou utilisé comme élément dans les applications que vous créez. Dans ce scénario, il est judicieux d’utiliser le [!INCLUDE[wrt](../../../includes/wrt-md.md)] <xref:Windows.Foundation.Metadata.VersionAttribute> attribut pour améliorer la compatibilité.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Logique d’application réutilisable à partir d’applications .NET Framework existantes
 Vous pouvez empaqueter du code managé de vos applications de bureau existantes comme composant [!INCLUDE[wrt](../../../includes/wrt-md.md)] autonome. Cela vous permet d’utiliser le composant dans des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] générées à l’aide de C++ ou JavaScript, ainsi que dans des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] générées à l’aide de C# ou Visual Basic. Le contrôle de version est une option s’il existe plusieurs scénarios de réutilisation du code.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Vue d’ensemble de .NET pour les applications Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|Décrit les types .NET Framework et les membres que vous pouvez utiliser pour créer des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] et des composants [!INCLUDE[wrt](../../../includes/wrt-md.md)]. (Dans le Centre de développement Windows.)|
|[Feuille de route pour les applications du Windows Store à l’aide de c# ou Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Fournit des ressources clés pour vous aider à commencer à développer des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] à l’aide de C# ou Visual Basic, notamment de nombreuses rubriques de démarrage rapide, des instructions et des bonnes pratiques. (Dans le Centre de développement Windows.)|
|[Comment : procédures (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Fournit des ressources clés pour vous aider à commencer à développer des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] à l’aide de C# ou Visual Basic, notamment de nombreuses rubriques de démarrage rapide, des instructions et des bonnes pratiques. (Dans le Centre de développement Windows.)|
|[Création de composants Windows Runtime en C# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|Décrit comment créer un composant [!INCLUDE[wrt](../../../includes/wrt-md.md)] à l’aide du .NET Framework, explique comment l’utiliser dans le cadre d’une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] conçue pour Windows à l’aide de JavaScript, et décrit comment déboguer la combinaison avec Visual Studio. (Dans le Centre de développement Windows.)|
|[Guide de référence Windows Runtime](/uwp/api/)|Fournit une documentation de référence pour le [!INCLUDE[wrt](../../../includes/wrt-md.md)]. (Dans le Centre de développement Windows.)|
|[Passage d’un URI au Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Décrit un problème qui peut se produire quand vous transmettez un URI du code managé au [!INCLUDE[wrt](../../../includes/wrt-md.md)], et comment l’éviter.|
