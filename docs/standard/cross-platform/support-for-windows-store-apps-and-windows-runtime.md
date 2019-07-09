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
ms.openlocfilehash: c49e9a5c4b8785704f8c4cbd1c9b7af10dc0c689
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661783"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime

Le .NET Framework 4.5 prend en charge un nombre de scénarios de développement de logiciel avec le Runtime de Windows. Ces scénarios se répartissent en trois catégories :

- Développement [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] avec les contrôles XAML, comme décrit dans les applications [des applications de feuille de route pour Windows Store à l’aide de c# ou Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [comment Ot (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10)), et [vue d’ensemble des applications .NET pour Windows Store ](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- Développement de bibliothèques de classes à utiliser dans les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] que vous créez avec le .NET Framework.

- Développement de composants Windows Runtime, empaquetés dans. Fichiers WinMD, ce qui peuvent être utilisées par n’importe quel langage de programmation qui prend en charge l’exécution de Windows. Par exemple, consultez [création de composants Windows Runtime en c# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

Cette rubrique décrit la prise en charge que le .NET Framework fournit pour ces trois catégories et décrit les scénarios pour les composants Windows Runtime. La première section inclut des informations de base sur la relation entre le .NET Framework et le Runtime Windows et explique certaines singularités que vous pouvez rencontrer dans le système d’aide et de l’IDE. Le [deuxième section](#WindowsRuntimeComponents) décrit des scénarios de développement de composants Windows Runtime.

## <a name="the-basics"></a>Principes de base

Le .NET Framework prend en charge les trois scénarios de développement répertoriés précédemment en fournissant [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]et en prenant en charge le Runtime Windows lui-même.

- [Espaces de noms .NET framework et Windows Runtime](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) fournit une vue simplifiée des bibliothèques de classes .NET Framework et incluent uniquement les types et membres que vous pouvez utiliser pour créer [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications et composants Windows Runtime.

  - Lorsque vous utilisez Visual Studio (Visual Studio 2012 ou version ultérieure) pour développer un [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] application ou un composant Windows Runtime, un ensemble d’assemblys de référence permet de s’assurer que vous voyez uniquement les types pertinents et les membres.

  - Cet ensemble d’API est simplifié par la suppression de fonctionnalités qui sont dupliquées dans le .NET Framework ou qui dupliquent Windows Runtime fonctionnalités. Par exemple, il contient uniquement les versions génériques des types de collections, et le modèle d’objet de document XML est éliminé en faveur de l’API XML du Runtime Windows défini.

  - Fonctionnalités qui ne font qu’envelopper l’API du système d’exploitation sont également supprimées, car le Runtime Windows est facile d’appeler du code managé.

  Pour en savoir plus sur la [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], consultez le [vue d’ensemble des applications .NET pour Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Pour en savoir plus sur le processus de sélection d’API, consultez le [.NET pour les applications de style Metro](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) entrée dans le blog .NET.

- Le [Windows Runtime](/uwp/api/) fournit des éléments d’interface de l’utilisateur pour la création de [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications et donne accès aux fonctionnalités du système d’exploitation. Comme le .NET Framework, le Runtime Windows contient des métadonnées qui permet la C# et bibliothèques de classes de compilateurs Visual Basic d’utiliser le Runtime Windows comme ils utilisent le .NET Framework. Le .NET Framework rend plus facile à utiliser le Runtime Windows en masquant certaines différences :

  - Des différences dans les modèles de programmation entre le .NET Framework et le Runtime de Windows, tels que le modèle pour ajouter et supprimer des gestionnaires d’événements, sont masqués. Vous utilisez simplement le modèle .NET Framework.

  - Certaines différences dans les types couramment utilisés (par exemple les collections et les types primitifs) sont masquées. Vous utilisez simplement le type .NET Framework, comme indiqué dans [différences visibles dans l’IDE](#DifferencesVisibleInIDE), plus loin dans cet article.

La plupart du temps, la prise en charge de .NET Framework pour le Windows Runtime est transparent. La section suivante décrit certaines des différences apparentes entre code managé et le Runtime de Windows.

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>Le .NET Framework et la Documentation de référence de l’exécution de Windows

Le Runtime Windows et les jeux de documentation de .NET Framework sont séparés. Si vous appuyez sur F1 pour afficher l’aide sur un type ou un membre, la documentation de référence de l’ensemble approprié s’affiche. Toutefois, si vous parcourez le [de référence Windows Runtime](/uwp/api/) vous rencontrerez des exemples qui pourront vous sembler étranges :

- Rubriques telles que le <xref:Windows.Foundation.Collections.IIterable%601> interface n’avez pas la syntaxe de déclaration pour Visual Basic ou c#. Au lieu de cela, une note apparaît au-dessus de la section syntaxe (dans ce cas, « .NET : Cette interface s’affiche sous forme de System.Collections.Generic.IEnumerable\<T > »). Il s’agit, car le .NET Framework et le Runtime Windows fournissent des fonctionnalités similaires avec des interfaces différentes. En outre, il existe des différences de comportement : `IIterable` a une méthode `First` plutôt qu’une méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> pour retourner l’énumérateur. Au lieu de vous contraindre à apprendre une autre manière d’effectuer une tâche très courante, le .NET Framework prend en charge le Runtime Windows en rendant votre code managé s’affichent pour utiliser le type que vous connaissez. Vous ne verrez pas le `IIterable` interface dans l’IDE, et par conséquent, la seule façon de vous le rencontrerez dans la documentation de référence Windows Runtime est en parcourant directement de cette documentation.

- Le <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> documentation illustre un problème étroitement lié : Ses types de paramètres semblent différents pour différentes langues. Pour C# et Visual Basic, les types de paramètres sont <xref:System.String?displayProperty=nameWithType> et <xref:System.Uri?displayProperty=nameWithType>. Là encore, c’est parce que le .NET Framework a ses propres types `String` et `Uri`, et pour ces types couramment utilisés, il est inutile d’obliger les utilisateurs du .NET Framework à apprendre une autre manière de faire les choses. Dans l’IDE, le .NET Framework masque les types Windows Runtime correspondants.

- Dans certains cas, comme le <xref:Windows.UI.Xaml.GridLength> structure, le .NET Framework fournit un type avec le même nom mais davantage de fonctionnalités. Par exemple, un ensemble de rubriques sur les constructeurs et les propriétés sont associées à `GridLength`, mais elles ont des blocs de syntaxe uniquement pour Visual Basic et C#, car les membres sont disponibles uniquement dans le code managé. Dans le Windows Runtime, les structures ont uniquement des champs. La structure Windows Runtime nécessite une classe d’assistance, <xref:Windows.UI.Xaml.GridLengthHelper>, pour fournir des fonctionnalités équivalentes. Vous ne verrez par cette classe d’assistance dans l’IDE quand vous écrirez du code managé.

- Dans l’IDE, semblent dériver de types Windows Runtime <xref:System.Object?displayProperty=nameWithType>. Ils semblent avoir des membres hérités de <xref:System.Object>, tels que <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Ces membres fonctionnent comme si les types héritaient réellement de <xref:System.Object>, et les types Windows Runtime pouvant être castés en <xref:System.Object>. Cette fonctionnalité fait partie de la prise en charge le .NET Framework fournit pour l’exécution de Windows. Toutefois, si vous affichez les types dans la documentation de référence Windows Runtime, aucun membre n’apparaît. La documentation sur ces membres hérités apparents est fournie par la documentation de référence sur <xref:System.Object?displayProperty=nameWithType>.

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>Différences visibles dans l’IDE

En savoir plus avancée des scénarios de programmation, telles que l’utilisation d’un composant Windows Runtime écrit en C# pour fournir la logique d’application pour un [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] application générée pour Windows à l’aide de JavaScript, ces différences sont visibles dans l’IDE, ainsi que dans le documentation. Quand votre composant retourne un `IDictionary<int, string>` à JavaScript et que vous regardez dans le débogueur JavaScript, vous verrez les méthodes de `IMap<int, string>` , car JavaScript utilise le type Windows Runtime. Certains types de collections fréquemment utilisés dont l’apparence est différente dans les deux langages sont répertoriés dans le tableau suivant :

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

Pour plus d’informations sur l’utilisation de .NET Framework pour créer un composant Windows Runtime et une procédure pas à pas qui montre comment utiliser un tel composant avec JavaScript, consultez [Creating Windows Runtime Components in C# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>Types primitifs

Pour activer l’utilisation naturelle de l’exécution de Windows dans le code managé, les types primitifs .NET Framework s’affichent au lieu de types primitifs de Runtime de Windows dans votre code. Dans le .NET Framework, les types primitifs, comme la structure `Int32` ont de nombreuses propriétés et méthodes utiles, telles que la méthode `Int32.TryParse`. En revanche, les types primitifs et les structures dans le Runtime Windows ont uniquement des champs. Quand vous utilisez des primitives dans du code managé, elles semblent être des types .NET Framework, et vous pouvez en utiliser les propriétés et les méthodes comme vous le faites habituellement. La liste suivante fournit un résumé :

- Pour les primitives de Windows Runtime `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (une collection immuable de caractères Unicode), `Enum`, `UInt32`, `UInt64`, et `Guid`, utilisez le type du même nom dans la `System` espace de noms.

- Pour `UInt8`, utilisez `System.Byte`.

- Pour `Char16`, utilisez `System.Char`.

- Pour l'interface `IInspectable`, utilisez `System.Object`.

- Pour `HRESULT`, utilisez une structure avec un membre `System.Int32`.

Comme avec les types d’interface, le seul moment où vous pouvez voir la preuve de cette représentation est quand votre projet .NET Framework est un composant Windows Runtime qui est utilisé par un [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] application générée à l’aide de JavaScript.

Autres types Windows Runtime de base couramment utilisées, qui s’affichent dans le code managé comme leurs équivalents .NET Framework incluent le `Windows.Foundation.DateTime` structure, qui apparaît dans le code managé comme le <xref:System.DateTimeOffset?displayProperty=nameWithType> structure et le `Windows.Foundation.TimeSpan` structure, qui apparaît comme le <xref:System.TimeSpan?displayProperty=nameWithType> structure.

### <a name="other-differences"></a>Autres différences

Dans certains cas, le fait que les types .NET Framework s’affichent dans votre code au lieu de types Windows Runtime nécessite une action de votre part. Par exemple, le <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe apparaît sous la forme <xref:System.Uri?displayProperty=nameWithType> dans le code .NET Framework. <xref:System.Uri?displayProperty=nameWithType> autorise un URI relatif, mais <xref:Windows.Foundation.Uri?displayProperty=nameWithType> nécessite un URI absolu. Par conséquent, lorsque vous transmettez un URI à une méthode Windows Runtime, vous devez vous assurer qu’il est absolu. (Consultez [transmission d’un URI au Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).)

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>Scénarios pour le développement de composants Windows Runtime

Les scénarios sont pris en charge pour les composants managés du Runtime Windows varient selon les principes généraux suivants :

- De composants Windows Runtime qui sont créés à l’aide de .NET Framework ne présentent aucune différence apparente à partir d’autres Runtimelibraries Windows. Par exemple, si vous ré-implémentez un composant Windows Runtime natif à l’aide du code managé, les deux composants sont différenciés vers l’extérieur. Le fait que votre composant soit écrit en code managé est invisible pour le code qui l’utilise, même si celui-ci est managé. Cependant, en interne, votre composant constitue du vrai code managé et s’exécute sur le Common Language Runtime (CLR).

- Les composants peuvent contenir des types qui implémentent une logique d’application, des contrôles d’interface utilisateur [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ou les deux.

  > [!NOTE]
  > Nous vous recommandons de séparer les éléments d’interface utilisateur de la logique d’application. De plus, vous ne pouvez pas utiliser de contrôles d’interface utilisateur [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] conçue pour Windows à l’aide de JavaScript et HTML.

- Un composant peut être un projet dans une solution Visual Studio pour une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], ou un composant réutilisable que vous pouvez ajouter à plusieurs solutions.

  > [!NOTE]
  > Si votre composant doit être utilisé uniquement avec C# ou Visual Basic, il n’existe aucune raison d’en faire un composant Windows Runtime. Si vous y une bibliothèque de classes .NET Framework ordinaire au lieu de cela, vous n’êtes pas obligé de limiter sa surface d’API publique aux types Windows Runtime.

- Vous pouvez publier des versions des composants réutilisables à l’aide de l’exécution de Windows <xref:Windows.Foundation.Metadata.VersionAttribute> attribut pour identifier les types (et les membres dans un type) ont été ajoutées dans différentes versions.

- Les types dans votre composant peuvent dériver de types Windows Runtime. Contrôles peuvent dériver des types de contrôles primitifs dans le <xref:Windows.UI.Xaml.Controls.Primitives> espace de noms ou de contrôles plus achevés tels que <xref:Windows.UI.Xaml.Controls.Button>.

  > [!IMPORTANT]
  > En commençant par [!INCLUDE[win8](../../../includes/win8-md.md)] et le .NET Framework 4.5, tous les types publics dans un composant Windows Runtime managé doit être scellé. Un type dans un autre composant Windows Runtime ne peut pas dériver à partir de celles-ci. Si vous souhaitez fournir un comportement polymorphe dans votre composant, vous pouvez créer une interface et l’implémenter dans les types polymorphes.

- Tous les types de paramètre et de retour sur les types publics dans votre composant doivent être des types Windows Runtime (y compris les types Windows Runtime qui définit votre composant).

Les sections suivantes fournissent des exemples de scénarios courants.

### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>Logique d’application pour une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] avec JavaScript

Quand vous développez une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] pour Windows à l’aide de JavaScript, vous constaterez peut-être que certaines parties de la logique d’application sont plus performantes (ou plus faciles à développer) dans du code managé. JavaScript ne peut pas utiliser les bibliothèques de classes .NET Framework directement, mais vous pouvez faire de la bibliothèque de classes un fichier .WinMD. Dans ce scénario, le composant Windows Runtime étant partie intégrante de l’application, il est inutile de fournir des attributs de version.

### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>Contrôles d’interface utilisateur [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] réutilisables

Vous pouvez empaqueter un ensemble de contrôles d’interface utilisateur connexes dans un composant Windows Runtime réutilisable. Le composant peut être commercialisé seul ou utilisé comme élément dans les applications que vous créez. Dans ce scénario, il est judicieux d’utiliser le Runtime Windows <xref:Windows.Foundation.Metadata.VersionAttribute> attribut pour améliorer la compatibilité.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Logique d’application réutilisable à partir d’applications .NET Framework existantes

Vous pouvez empaqueter le code managé à partir de vos applications de bureau existantes comme composant autonome Windows Runtime. Cela vous permet d’utiliser le composant dans des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] générées à l’aide de C++ ou JavaScript, ainsi que dans des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] générées à l’aide de C# ou Visual Basic. Le contrôle de version est une option s’il existe plusieurs scénarios de réutilisation du code.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Vue d’ensemble de .NET pour les applications Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|Décrit les types .NET Framework et les membres que vous pouvez utiliser pour créer [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] RuntimeComponents de Windows et des applications. (Dans le Centre de développement Windows.)|
|[Feuille de route pour les applications du Windows Store à l’aide de c# ou Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Fournit des ressources clés pour vous aider à commencer à développer des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] à l’aide de C# ou Visual Basic, notamment de nombreuses rubriques de démarrage rapide, des instructions et des bonnes pratiques. (Dans le Centre de développement Windows.)|
|[Comment : procédures (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Fournit des ressources clés pour vous aider à commencer à développer des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] à l’aide de C# ou Visual Basic, notamment de nombreuses rubriques de démarrage rapide, des instructions et des bonnes pratiques. (Dans le Centre de développement Windows.)|
|[Création de composants Windows Runtime en C# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|Décrit comment créer un composant Windows Runtime à l’aide de .NET Framework, explique comment l’utiliser en tant que partie d’un [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] application créée pour Windows à l’aide de JavaScript et décrit comment déboguer la combinaison avec Visual Studio. (Dans le Centre de développement Windows.)|
|[Guide de référence Windows Runtime](/uwp/api/)|La documentation de référence pour le Runtime de Windows. (Dans le Centre de développement Windows.)|
|[Passage d’un URI au Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Décrit un problème pouvant survenir lorsque vous transmettez un URI à partir de code managé à l’exécution de Windows et comment l’éviter.|
