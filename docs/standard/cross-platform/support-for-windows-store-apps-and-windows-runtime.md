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
ms.openlocfilehash: 15d6262fb5e7dfb99759f0f85c9a197157713300
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204953"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime

The .NET Framework 4.5 supports a number of software development scenarios with the Windows Runtime. Ces scénarios se répartissent en trois catégories :

- Developing Windows 8.x Store apps with XAML controls, as described in [Roadmap for Windows Store apps using C# or Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [How tos (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10)), and [.NET for Windows Store apps overview](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- Developing class libraries to use in the Windows 8.x Store apps that you create with the .NET Framework.

- Developing Windows Runtime Components, packaged in .WinMD files, which can be used by any programming language that supports the Windows Runtime. For example, see [Creating Windows Runtime Components in C# and Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

This topic outlines the support that the .NET Framework provides for all three categories, and describes the scenarios for Windows Runtime Components. The first section includes basic information about the relationship between the .NET Framework and the Windows Runtime, and explains some oddities you might encounter in the Help system and the IDE. The [second section](#WindowsRuntimeComponents) discusses scenarios for developing Windows Runtime Components.

## <a name="the-basics"></a>Principes de base

The .NET Framework supports the three development scenarios listed earlier by providing [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], and by supporting the Windows Runtime itself.

- [.NET Framework and Windows Runtime namespaces](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) provides a streamlined view of the .NET Framework class libraries and include only the types and members you can use to create Windows 8.x Store apps and Windows Runtime Components.

  - When you use Visual Studio (Visual Studio 2012 or later) to develop a Windows 8.x Store app or a Windows Runtime component, a set of reference assemblies ensures that you see only the relevant types and members.

  - This streamlined API set is simplified further by the removal of features that are duplicated within the .NET Framework or that duplicate Windows Runtime features. For example, it contains only the generic versions of collection types, and the XML document object model is eliminated in favor of the Windows Runtime XML API set.

  - Features that simply wrap the operating system API are also removed, because the Windows Runtime is easy to call from managed code.

  To read more about the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], see the [.NET for Windows Store apps overview](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). To read about the API selection process, see the [.NET for Metro style apps](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) entry in the .NET blog.

- The [Windows Runtime](/uwp/api/) provides the user interface elements for building Windows 8.x Store apps, and provides access to operating system features. Like the .NET Framework, the Windows Runtime has metadata that enables the C# and Visual Basic compilers to use the Windows Runtime the way they use the .NET Framework class libraries. The .NET Framework makes it easier to use the Windows Runtime by hiding some differences:

  - Some differences in programming patterns between the .NET Framework and the Windows Runtime, such as the pattern for adding and removing event handlers, are hidden. Vous utilisez simplement le modèle .NET Framework.

  - Certaines différences dans les types couramment utilisés (par exemple les collections et les types primitifs) sont masquées. You simply use the .NET Framework type, as discussed in [Differences That Are Visible in the IDE](#DifferencesVisibleInIDE), later in this article.

Most of the time, .NET Framework support for the Windows Runtime is transparent. The next section discusses some of the apparent differences between managed code and the Windows Runtime.

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>The .NET Framework and the Windows Runtime Reference Documentation

The Windows Runtime and the .NET Framework documentation sets are separate. Si vous appuyez sur F1 pour afficher l’aide sur un type ou un membre, la documentation de référence de l’ensemble approprié s’affiche. However, if you browse through the [Windows Runtime reference](/uwp/api/) you might encounter examples that seem puzzling:

- Topics such as the <xref:Windows.Foundation.Collections.IIterable%601> interface don't have declaration syntax for Visual Basic or C#. Instead, a note appears above the syntax section (in this case, ".NET: This interface appears as System.Collections.Generic.IEnumerable\<T>"). This is because the .NET Framework and the Windows Runtime provide similar functionality with different interfaces. En outre, il existe des différences de comportement : `IIterable` a une méthode `First` plutôt qu’une méthode <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> pour retourner l’énumérateur. Instead of forcing you to learn a different way of performing a common task, the .NET Framework supports the Windows Runtime by making your managed code appear to use the type you're familiar with. You won't see the `IIterable` interface in the IDE, and therefore the only way you'll encounter it in the Windows Runtime reference documentation is by browsing through that documentation directly.

- The <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> documentation illustrates a closely related issue: Its parameter types appear to be different for different languages. Pour C# et Visual Basic, les types de paramètres sont <xref:System.String?displayProperty=nameWithType> et <xref:System.Uri?displayProperty=nameWithType>. Là encore, c’est parce que le .NET Framework a ses propres types `String` et `Uri`, et pour ces types couramment utilisés, il est inutile d’obliger les utilisateurs du .NET Framework à apprendre une autre manière de faire les choses. In the IDE, the .NET Framework hides the corresponding Windows Runtime types.

- In a few cases, such as the <xref:Windows.UI.Xaml.GridLength> structure, the .NET Framework provides a type with the same name but more functionality. Par exemple, un ensemble de rubriques sur les constructeurs et les propriétés sont associées à `GridLength`, mais elles ont des blocs de syntaxe uniquement pour Visual Basic et C#, car les membres sont disponibles uniquement dans le code managé. In the Windows Runtime, structures have only fields. The Windows Runtime structure requires a helper class, <xref:Windows.UI.Xaml.GridLengthHelper>, to provide equivalent functionality. Vous ne verrez par cette classe d’assistance dans l’IDE quand vous écrirez du code managé.

- In the IDE, Windows Runtime types appear to derive from <xref:System.Object?displayProperty=nameWithType>. Ils semblent avoir des membres hérités de <xref:System.Object>, tels que <xref:System.Object.ToString%2A?displayProperty=nameWithType>. These members operate as they would if the types actually inherited from <xref:System.Object>, and Windows Runtime types can be cast to <xref:System.Object>. This functionality is part of the support that the .NET Framework provides for the Windows Runtime. However, if you view the types in the Windows Runtime reference documentation, no such members appear. La documentation sur ces membres hérités apparents est fournie par la documentation de référence sur <xref:System.Object?displayProperty=nameWithType>.

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>Différences visibles dans l’IDE

In more advanced programming scenarios, such as using a Windows Runtime component written in C# to provide the application logic for a Windows 8.x Store app built for Windows using JavaScript, such differences are apparent in the IDE as well as in the documentation. When your component returns an `IDictionary<int, string>` to JavaScript, and you look at it in the JavaScript debugger, you'll see the methods of `IMap<int, string>` because JavaScript uses the Windows Runtime type. Certains types de collections fréquemment utilisés dont l’apparence est différente dans les deux langages sont répertoriés dans le tableau suivant :

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

In the Windows Runtime, `IMap<K, V>` and `IMapView<K, V>` are iterated using `IKeyValuePair`. Lorsque vous les passez au code managé, ils apparaissent comme `IDictionary<TKey, TValue>` et `IReadOnlyDictionary<TKey, TValue>`, donc bien sûr vous utilisez `System.Collections.Generic.KeyValuePair<TKey, TValue>` pour les énumérer.

La façon dont les interfaces apparaissent dans le code managé affecte la façon dont les types qui implémentent ces interfaces apparaissent. Par exemple, la classe `PropertySet` implémente `IMap<K, V>`, qui s'affiche dans le code managé sous la forme `IDictionary<TKey, TValue>`. `PropertySet` apparaît comme ayant implémenté `IDictionary<TKey, TValue>` au lieu de `IMap<K, V>`, donc en code managé une méthode `Add` semble se comporter comme la méthode `Add` sur les dictionnaires .NET Framework. Il ne semble pas avoir de méthode `Insert`.

For more information about using the .NET Framework to create a Windows Runtime component, and a walkthrough that shows how to use such a component with JavaScript, see [Creating Windows Runtime Components in C# and Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>Types primitifs

To enable the natural use of the Windows Runtime in managed code, .NET Framework primitive types appear instead of Windows Runtime primitive types in your code. Dans le .NET Framework, les types primitifs, comme la structure `Int32` ont de nombreuses propriétés et méthodes utiles, telles que la méthode `Int32.TryParse`. By contrast, primitive types and structures in the Windows Runtime have only fields. Quand vous utilisez des primitives dans du code managé, elles semblent être des types .NET Framework, et vous pouvez en utiliser les propriétés et les méthodes comme vous le faites habituellement. La liste suivante fournit un résumé :

- For the Windows Runtime primitives `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (an immutable collection of Unicode characters), `Enum`, `UInt32`, `UInt64`, and `Guid`, use the type of the same name in the `System` namespace.

- Pour `UInt8`, utilisez `System.Byte`.

- Pour `Char16`, utilisez `System.Char`.

- Pour l'interface `IInspectable`, utilisez `System.Object`.

- Pour `HRESULT`, utilisez une structure avec un membre `System.Int32`.

As with interface types, the only time you might see evidence of this representation is when your .NET Framework project is a Windows Runtime component that is used by a Windows 8.x Store app built using JavaScript.

Other basic, commonly used Windows Runtime types that appear in managed code as their .NET Framework equivalents include the `Windows.Foundation.DateTime` structure, which appears in managed code as the <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the `Windows.Foundation.TimeSpan` structure, which appears as the <xref:System.TimeSpan?displayProperty=nameWithType> structure.

### <a name="other-differences"></a>Autres différences

In a few cases, the fact that .NET Framework types appear in your code instead of Windows Runtime types requires action on your part. For example, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in .NET Framework code. <xref:System.Uri?displayProperty=nameWithType> allows a relative URI, but <xref:Windows.Foundation.Uri?displayProperty=nameWithType> requires an absolute URI. Therefore, when you pass a URI to a Windows Runtime method, you must ensure that it's absolute. See [Passing a URI to the Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>Scénarios pour le développement de composants Windows Runtime

The scenarios that are supported for managed Windows Runtime Components depend on the following general principles:

- Windows Runtime Components that are built using the .NET Framework have no apparent differences from other Windows Runtimelibraries. For example, if you re-implement a native Windows Runtime component by using managed code, the two components are outwardly indistinguishable. Le fait que votre composant soit écrit en code managé est invisible pour le code qui l’utilise, même si celui-ci est managé. Cependant, en interne, votre composant constitue du vrai code managé et s’exécute sur le Common Language Runtime (CLR).

- Components can contain types that implement application logic, Windows 8.x Store UI controls, or both.

  > [!NOTE]
  > Nous vous recommandons de séparer les éléments d’interface utilisateur de la logique d’application. Also, you can't use Windows 8.x Store UI controls in a Windows 8.x Store app built for Windows using JavaScript and HTML.

- A component can be a project within a Visual Studio solution for a Windows 8.x Store app, or a reusable component that you can add to multiple solutions.

  > [!NOTE]
  > If your component will be used only with C# or Visual Basic, there's no reason to make it a Windows Runtime component. If you make it an ordinary .NET Framework class library instead, you don't have to restrict its public API surface to Windows Runtime types.

- You can release versions of reusable components by using the Windows Runtime <xref:Windows.Foundation.Metadata.VersionAttribute> attribute to identify which types (and which members within a type) were added in different versions.

- The types in your component can derive from Windows Runtime types. Controls can derive from the primitive control types in the <xref:Windows.UI.Xaml.Controls.Primitives> namespace or from more finished controls such as <xref:Windows.UI.Xaml.Controls.Button>.

  > [!IMPORTANT]
  > Starting with [!INCLUDE[win8](../../../includes/win8-md.md)] and the .NET Framework 4.5, all public types in a managed Windows Runtime component must be sealed. A type in another Windows Runtime component can't derive from them. Si vous souhaitez fournir un comportement polymorphe dans votre composant, vous pouvez créer une interface et l’implémenter dans les types polymorphes.

- All parameter and return types on the public types in your component must be Windows Runtime types (including the Windows Runtime types that your component defines).

Les sections suivantes fournissent des exemples de scénarios courants.

### <a name="application-logic-for-a-windows-8x-store-app-with-javascript"></a>Application Logic for a Windows 8.x Store App with JavaScript

When you develop a Windows 8.x Store app for Windows using JavaScript, you might find that some parts of the application logic perform better in managed code, or are easier to develop. JavaScript ne peut pas utiliser les bibliothèques de classes .NET Framework directement, mais vous pouvez faire de la bibliothèque de classes un fichier .WinMD. In this scenario, the Windows Runtime component is an integral part of the app, so it doesn't make sense to provide version attributes.

### <a name="reusable-windows-8x-store-ui-controls"></a>Reusable Windows 8.x Store UI Controls

You can package a set of related UI controls in a reusable Windows Runtime component. Le composant peut être commercialisé seul ou utilisé comme élément dans les applications que vous créez. In this scenario, it makes sense to use the Windows Runtime <xref:Windows.Foundation.Metadata.VersionAttribute> attribute to improve compatibility.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Logique d’application réutilisable à partir d’applications .NET Framework existantes

You can package managed code from your existing desktop apps as a standalone Windows Runtime component. This enables you to use the component in Windows 8.x Store apps built using C++ or JavaScript, as well as in Windows 8.x Store apps built using C# or Visual Basic. Le contrôle de version est une option s’il existe plusieurs scénarios de réutilisation du code.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Vue d’ensemble de .NET pour les applications Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|Describes the .NET Framework types and members that you can use to create Windows 8.x Store apps and Windows RuntimeComponents. (Dans le Centre de développement Windows.)|
|[Roadmap for Windows Store apps using C# or Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Provides key resources to help you get started developing Windows 8.x Store apps by using C# or Visual Basic, including many Quickstart topics, guidelines, and best practices. (Dans le Centre de développement Windows.)|
|[How tos (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Provides key resources to help you get started developing Windows 8.x Store apps by using C# or Visual Basic, including many Quickstart topics, guidelines, and best practices. (Dans le Centre de développement Windows.)|
|[Création de composants Windows Runtime en C# et Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|Describes how to create a Windows Runtime component using the .NET Framework, explains how to use it as part of a Windows 8.x Store app built for Windows using JavaScript, and describes how to debug the combination with Visual Studio. (Dans le Centre de développement Windows.)|
|[Windows Runtime reference](/uwp/api/)|The reference documentation for the Windows Runtime. (Dans le Centre de développement Windows.)|
|[Passage d’un URI au Windows Runtime](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Describes an issue that can arise when you pass a URI from managed code to the Windows Runtime, and how to avoid it.|
