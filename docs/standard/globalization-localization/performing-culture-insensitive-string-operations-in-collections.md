---
title: Exécution d’opérations de chaînes indépendantes de la culture dans des collections
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
ms.openlocfilehash: 0a55a41b7cd2a2d245d0fb7722dddee794777422
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063961"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="9a962-102">Exécution d’opérations de chaînes indépendantes de la culture dans des collections</span><span class="sxs-lookup"><span data-stu-id="9a962-102">Performing Culture-Insensitive String Operations in Collections</span></span>

<span data-ttu-id="9a962-103">Des classes et des membres dans l’espace de noms <xref:System.Collections> génèrent un comportement dépendant de la culture par défaut.</span><span class="sxs-lookup"><span data-stu-id="9a962-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="9a962-104">Les constructeurs sans paramètre pour les classes <xref:System.Collections.CaseInsensitiveComparer> et <xref:System.Collections.CaseInsensitiveHashCodeProvider> initialisent une nouvelle instance en utilisant la propriété <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9a962-104">The parameterless constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9a962-105">Toutes les surcharges de la méthode <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> créent une nouvelle instance de la classe <xref:System.Collections.Hashtable> en utilisant la propriété `Thread.CurrentCulture` par défaut.</span><span class="sxs-lookup"><span data-stu-id="9a962-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="9a962-106">Les surcharges de la méthode <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> effectuent des tris dépendants de la culture par défaut en utilisant `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="9a962-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="9a962-107">Le tri et la recherche dans <xref:System.Collections.SortedList> peuvent être affectés par `Thread.CurrentCulture` lorsque des chaînes sont utilisées en tant que clés.</span><span class="sxs-lookup"><span data-stu-id="9a962-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="9a962-108">Suivez les recommandations d’utilisation fournies dans cette section pour obtenir des résultats indépendants de la culture à partir de ces classes et méthodes dans l’espace de noms `Collections`.</span><span class="sxs-lookup"><span data-stu-id="9a962-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="9a962-109">Le passage <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> à une méthode de comparaison effectue une comparaison indépendante de la culture.</span><span class="sxs-lookup"><span data-stu-id="9a962-109">Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="9a962-110">Toutefois, elle n’entraîne pas une comparaison non linguistique, par exemple, pour les chemins d’accès de fichier, les clés de Registre et les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="9a962-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="9a962-111">Elle ne prend pas non plus en charge les décisions de sécurité basées sur le résultat de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="9a962-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="9a962-112">Pour une comparaison non linguistique ou la prise en charge des décisions de sécurité basées sur le résultat, l’application doit utiliser une méthode de comparaison qui accepte une valeur <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="9a962-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="9a962-113">L’application doit ensuite transmettre <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="9a962-113">The application should then pass <xref:System.StringComparison>.</span></span>

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="9a962-114">Utilisation des classes CaseInsensitiveComparer et CaseInsensitiveHashCodeProvider</span><span class="sxs-lookup"><span data-stu-id="9a962-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>

<span data-ttu-id="9a962-115">Les constructeurs sans paramètre pour `CaseInsensitiveHashCodeProvider` et `CaseInsensitiveComparer` lancent une nouvelle instance de la classe à l’aide de `Thread.CurrentCulture`, qui entraîne un comportement dépendant de la culture.</span><span class="sxs-lookup"><span data-stu-id="9a962-115">The parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="9a962-116">L’exemple de code suivant montre le constructeur pour un `Hashtable` qui est dépendant de la culture car il utilise les constructeurs sans paramètre pour `CaseInsensitiveHashCodeProvider` et `CaseInsensitiveComparer`.</span><span class="sxs-lookup"><span data-stu-id="9a962-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

<span data-ttu-id="9a962-117">Si vous souhaitez créer un `Hashtable` indépendant de la culture à l’aide des classes `CaseInsensitiveComparer` et `CaseInsensitiveHashCodeProvider`, lancez de nouvelles instances de ces classes à l’aide des constructeurs qui acceptent un paramètre `culture`.</span><span class="sxs-lookup"><span data-stu-id="9a962-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="9a962-118">Pour le paramètre `culture`, spécifiez <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9a962-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9a962-119">L’exemple de code suivant montre le constructeur pour un `Hashtable` indépendant de la culture.</span><span class="sxs-lookup"><span data-stu-id="9a962-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="9a962-120">Utilisation de la méthode CollectionsUtil.CreateCaseInsensitiveHashtable</span><span class="sxs-lookup"><span data-stu-id="9a962-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>

<span data-ttu-id="9a962-121">La méthode `CollectionsUtil.CreateCaseInsensitiveHashTable` est un raccourci utile pour créer une nouvelle instance de la classe `Hashtable` qui ignore la casse des chaînes.</span><span class="sxs-lookup"><span data-stu-id="9a962-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="9a962-122">Toutefois, toutes les surcharges de la méthode `CollectionsUtil.CreateCaseInsensitiveHashTable` sont dépendantes de la culture car elles utilisent la propriété `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="9a962-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="9a962-123">Vous ne pouvez pas créer un `Hashtable` indépendant de la culture à l’aide de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="9a962-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="9a962-124">Pour créer un `Hashtable` indépendant de la culture, utilisez le constructeur `Hashtable` qui accepte un paramètre `culture`.</span><span class="sxs-lookup"><span data-stu-id="9a962-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="9a962-125">Pour le paramètre `culture`, spécifiez `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="9a962-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="9a962-126">L’exemple de code suivant montre le constructeur pour un `Hashtable` indépendant de la culture.</span><span class="sxs-lookup"><span data-stu-id="9a962-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>

## <a name="using-the-sortedlist-class"></a><span data-ttu-id="9a962-127">Utilisation de la classe SortedList</span><span class="sxs-lookup"><span data-stu-id="9a962-127">Using the SortedList Class</span></span>

<span data-ttu-id="9a962-128">Un `SortedList` représente une collection de paires clé/valeur triées par les clés et accessibles par clé et par index.</span><span class="sxs-lookup"><span data-stu-id="9a962-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="9a962-129">Lorsque vous utilisez un `SortedList` où des chaînes sont les clés, le tri et la recherche peuvent être affectés par la propriété `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="9a962-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="9a962-130">Pour obtenir un comportement indépendant de la culture d’un `SortedList`, créez un `SortedList` à l’aide d’un des constructeurs qui acceptent un paramètre `comparer`.</span><span class="sxs-lookup"><span data-stu-id="9a962-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="9a962-131">Le paramètre `comparer` spécifie l’implémentation <xref:System.Collections.IComparer> à utiliser lors de la comparaison des clés.</span><span class="sxs-lookup"><span data-stu-id="9a962-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="9a962-132">Pour le paramètre, spécifiez une classe de comparateur personnalisée qui utilise `CultureInfo.InvariantCulture` pour comparer des clés.</span><span class="sxs-lookup"><span data-stu-id="9a962-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="9a962-133">L’exemple suivant illustre une classe de comparateur indépendante de la culture personnalisée que vous pouvez spécifier en tant que paramètre `comparer` dans un constructeur `SortedList`.</span><span class="sxs-lookup"><span data-stu-id="9a962-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>

```vb
Imports System.Collections
Imports System.Globalization

Friend Class InvariantComparer
    Implements IComparer
    Private m_compareInfo As CompareInfo
    Friend Shared [Default] As New InvariantComparer()

    Friend Sub New()
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo
    End Sub

    Public Function Compare(a As Object, b As Object) As Integer _
            Implements IComparer.Compare
        Dim sa As String = CType(a, String)
        Dim sb As String = CType(b, String)
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then
            Return m_compareInfo.Compare(sa, sb)
        Else
            Return Comparer.Default.Compare(a, b)
        End If
    End Function
End Class
```

```csharp
using System;
using System.Collections;
using System.Globalization;

internal class InvariantComparer : IComparer
{
    private CompareInfo m_compareInfo;
    internal static readonly InvariantComparer Default = new
        InvariantComparer();

    internal InvariantComparer()
    {
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;
    }

    public int Compare(Object a, Object b)
    {
        String sa = a as String;
        String sb = b as String;
        if (sa != null && sb != null)
            return m_compareInfo.Compare(sa, sb);
        else
            return Comparer.Default.Compare(a,b);
    }
}
```

<span data-ttu-id="9a962-134">En général, si vous utilisez un `SortedList` sur des chaînes sans spécifier de comparateur indifférent personnalisé, une modification sur `Thread.CurrentCulture` lorsque la liste est remplie peut invalider cette liste.</span><span class="sxs-lookup"><span data-stu-id="9a962-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>

## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="9a962-135">Utilisation de la méthode ArrayList.Sort</span><span class="sxs-lookup"><span data-stu-id="9a962-135">Using the ArrayList.Sort Method</span></span>

<span data-ttu-id="9a962-136">Les surcharges de la méthode `ArrayList.Sort` effectuent des tris dépendants de la culture par défaut à l’aide de la propriété `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="9a962-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="9a962-137">Les résultats peuvent varier selon la culture en raison des différents ordres de tri.</span><span class="sxs-lookup"><span data-stu-id="9a962-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="9a962-138">Pour supprimer un comportement dépendant de la culture, utilisez les surcharges de cette méthode qui acceptent une implémentation `IComparer`.</span><span class="sxs-lookup"><span data-stu-id="9a962-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="9a962-139">Pour le paramètre `comparer`, spécifiez une classe de comparateur indifférent personnalisée qui utilise `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="9a962-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="9a962-140">Un exemple de classe de comparateur indifférent personnalisée est fourni dans la rubrique [Utilisation de la classe SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1).</span><span class="sxs-lookup"><span data-stu-id="9a962-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a962-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a962-141">See also</span></span>

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="9a962-142">Exécution d'opérations de chaînes indépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="9a962-142">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
