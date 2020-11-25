---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031999"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a><span data-ttu-id="da796-101">Les propriétés UriBuilder n’ajoutent plus de caractères de début</span><span class="sxs-lookup"><span data-stu-id="da796-101">UriBuilder properties no longer prepend leading characters</span></span>

<span data-ttu-id="da796-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> n’ajoute plus de caractère de début `#` et <xref:System.UriBuilder.Query?displayProperty=nameWithType> n’ajoute plus de `?` caractère de début lorsqu’il est déjà présent.</span><span class="sxs-lookup"><span data-stu-id="da796-102"><xref:System.UriBuilder.Fragment?displayProperty=nameWithType> no longer prepends a leading `#` character and <xref:System.UriBuilder.Query?displayProperty=nameWithType> no longer prepends a leading `?` character when one is already present.</span></span>

#### <a name="change-description"></a><span data-ttu-id="da796-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="da796-103">Change description</span></span>

<span data-ttu-id="da796-104">Dans .NET Framework, les <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> Propriétés et ajoutent <xref:System.UriBuilder.Query?displayProperty=nameWithType> toujours `#` un `?` caractère ou, respectivement, à la valeur stockée.</span><span class="sxs-lookup"><span data-stu-id="da796-104">In .NET Framework, the <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> and <xref:System.UriBuilder.Query?displayProperty=nameWithType> properties always prepend a `#` or `?` character, respectively, to the value being stored.</span></span> <span data-ttu-id="da796-105">Ce comportement peut entraîner `#` `?` la valeur stockée sur plusieurs ou caractères si la chaîne contient déjà l’un de ces caractères de début.</span><span class="sxs-lookup"><span data-stu-id="da796-105">This behavior can result in multiple `#` or `?` characters in the stored value if the string already contains one of these leading characters.</span></span> <span data-ttu-id="da796-106">Par exemple, la valeur de <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> peut devenir `##main` .</span><span class="sxs-lookup"><span data-stu-id="da796-106">For example, the value of <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> might become `##main`.</span></span>

<span data-ttu-id="da796-107">À compter de .NET Core 1,0, ces propriétés n’ajouteront plus les `#` `?` caractères ou à la valeur stockée si celle-ci est déjà présente au début de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="da796-107">Starting in .NET Core 1.0, these properties no longer prepend the `#` or `?` characters to the stored value if one is already present at the beginning of the string.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="da796-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="da796-108">Version introduced</span></span>

<span data-ttu-id="da796-109">1.0</span><span class="sxs-lookup"><span data-stu-id="da796-109">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da796-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="da796-110">Recommended action</span></span>

<span data-ttu-id="da796-111">Vous n’avez plus besoin de supprimer explicitement ces caractères de début lors de la définition des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="da796-111">You no longer need to explicitly remove any of these leading characters when setting the property values.</span></span> <span data-ttu-id="da796-112">Cela s’avère particulièrement utile lorsque vous ajoutez des valeurs, car vous n’avez plus besoin de supprimer le de début `#` ou `?` chaque fois que vous ajoutez.</span><span class="sxs-lookup"><span data-stu-id="da796-112">This is especially useful when you're appending values, because you no longer have to remove the leading `#` or `?` each time you append.</span></span>

<span data-ttu-id="da796-113">Par exemple, l’extrait de code suivant montre la différence de comportement entre .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="da796-113">For example, the following code snippet shows the behavior difference between .NET Framework and .NET Core.</span></span>

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- <span data-ttu-id="da796-114">Dans .NET Framework, la sortie est `????one=1&two=2&three=3&four=4` .</span><span class="sxs-lookup"><span data-stu-id="da796-114">In .NET Framework, the output is `????one=1&two=2&three=3&four=4`.</span></span>
- <span data-ttu-id="da796-115">Dans .NET Core, la sortie est `?one=1&two=2&three=3&four=4` .</span><span class="sxs-lookup"><span data-stu-id="da796-115">In .NET Core, the output is `?one=1&two=2&three=3&four=4`.</span></span>

#### <a name="category"></a><span data-ttu-id="da796-116">Category</span><span class="sxs-lookup"><span data-stu-id="da796-116">Category</span></span>

<span data-ttu-id="da796-117">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="da796-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da796-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="da796-118">Affected APIs</span></span>

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
