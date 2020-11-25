---
title: 'Modification avec rupture : les chemins d’accès URI avec des caractères non-ASCII sont analysés correctement sur UNIX'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où les chemins d’accès URI absolus contenant des caractères non-ASCII sont désormais correctement analysés sur les plateformes UNIX.
ms.date: 11/01/2020
ms.openlocfilehash: 94de4e0eb94a11153d873871d4003422a4286a0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760864"
---
# <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a><span data-ttu-id="e6e63-103">Les chemins d’accès URI avec des caractères non-ASCII sont analysés correctement sur UNIX</span><span class="sxs-lookup"><span data-stu-id="e6e63-103">URI paths with non-ASCII characters parse correctly on Unix</span></span>

<span data-ttu-id="e6e63-104">Un bogue a été corrigé dans la <xref:System.Uri?displayProperty=fullName> classe de telle sorte que les chemins d’accès d’URI absolus qui contiennent des caractères non-ASCII sont désormais correctement analysés sur les plateformes UNIX.</span><span class="sxs-lookup"><span data-stu-id="e6e63-104">A bug was fixed in the <xref:System.Uri?displayProperty=fullName> class such that absolute URI paths that contain non-ASCII characters now parse correctly on Unix platforms.</span></span>

## <a name="change-description"></a><span data-ttu-id="e6e63-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e6e63-105">Change description</span></span>

<span data-ttu-id="e6e63-106">Dans les versions précédentes de .NET, les chemins d’URI absolus qui contiennent des caractères non-ASCII ne sont pas correctement analysés sur les plateformes UNIX et les segments du chemin d’accès sont dupliqués.</span><span class="sxs-lookup"><span data-stu-id="e6e63-106">In previous versions of .NET, absolute URI paths that contain non-ASCII characters are parsed incorrectly on Unix platforms, and segments of the path are duplicated.</span></span> <span data-ttu-id="e6e63-107">(Les chemins d’accès absolus sont ceux qui commencent par « / ».) Le problème d’analyse a été résolu pour .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="e6e63-107">(Absolute paths are those that start with "/".) The parsing issue has been fixed for .NET 5.0.</span></span> <span data-ttu-id="e6e63-108">Si vous passez d’une version antérieure de .NET à .NET 5,0 ou version ultérieure, vous obtiendrez des valeurs différentes produites par <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> , <xref:System.Uri.ToString?displayProperty=nameWithType> et d’autres <xref:System.Uri> membres.</span><span class="sxs-lookup"><span data-stu-id="e6e63-108">If you move from a previous version of .NET to .NET 5.0 or later, you'll get different values produced by <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType>, and other <xref:System.Uri> members.</span></span>

<span data-ttu-id="e6e63-109">Prenez en compte la sortie du code suivant lorsqu’il est exécuté sur UNIX.</span><span class="sxs-lookup"><span data-stu-id="e6e63-109">Consider the output of the following code when run on Unix.</span></span>

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

<span data-ttu-id="e6e63-110">Sortie sur la version précédente de .NET :</span><span class="sxs-lookup"><span data-stu-id="e6e63-110">Output on previous .NET version:</span></span>

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

<span data-ttu-id="e6e63-111">Sortie sur .NET 5,0 ou version ultérieure :</span><span class="sxs-lookup"><span data-stu-id="e6e63-111">Output on .NET 5.0 or later version:</span></span>

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

## <a name="version-introduced"></a><span data-ttu-id="e6e63-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e6e63-112">Version introduced</span></span>

<span data-ttu-id="e6e63-113">5.0</span><span class="sxs-lookup"><span data-stu-id="e6e63-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e6e63-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e6e63-114">Recommended action</span></span>

<span data-ttu-id="e6e63-115">Si vous avez du code qui attend et compte les segments de chemin d’accès dupliqués, vous pouvez supprimer ce code.</span><span class="sxs-lookup"><span data-stu-id="e6e63-115">If you have code that expects and accounts for the duplicated path segments, you can remove that code.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e6e63-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="e6e63-116">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
