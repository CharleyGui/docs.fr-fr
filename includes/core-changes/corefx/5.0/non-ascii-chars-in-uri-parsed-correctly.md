---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720188"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a><span data-ttu-id="4f655-101">Les chemins d’accès URI avec des caractères non-ASCII sont analysés correctement sur UNIX</span><span class="sxs-lookup"><span data-stu-id="4f655-101">URI paths with non-ASCII characters parse correctly on Unix</span></span>

<span data-ttu-id="4f655-102">Un bogue a été corrigé dans la <xref:System.Uri?displayProperty=fullName> classe de telle sorte que les chemins d’accès d’URI absolus qui contiennent des caractères non-ASCII sont désormais correctement analysés sur les plateformes UNIX.</span><span class="sxs-lookup"><span data-stu-id="4f655-102">A bug was fixed in the <xref:System.Uri?displayProperty=fullName> class such that absolute URI paths that contain non-ASCII characters now parse correctly on Unix platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4f655-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="4f655-103">Change description</span></span>

<span data-ttu-id="4f655-104">Dans les versions précédentes de .NET, les chemins d’URI absolus qui contiennent des caractères non-ASCII ne sont pas correctement analysés sur les plateformes UNIX et les segments du chemin d’accès sont dupliqués.</span><span class="sxs-lookup"><span data-stu-id="4f655-104">In previous versions of .NET, absolute URI paths that contain non-ASCII characters are parsed incorrectly on Unix platforms, and segments of the path are duplicated.</span></span> <span data-ttu-id="4f655-105">(Les chemins d’accès absolus sont ceux qui commencent par « / ».) Le problème d’analyse a été résolu pour .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="4f655-105">(Absolute paths are those that start with "/".) The parsing issue has been fixed for .NET 5.0.</span></span> <span data-ttu-id="4f655-106">Si vous passez d’une version antérieure de .NET à .NET 5,0 ou version ultérieure, vous obtiendrez des valeurs différentes produites par <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> , <xref:System.Uri.ToString?displayProperty=nameWithType> et d’autres <xref:System.Uri> membres.</span><span class="sxs-lookup"><span data-stu-id="4f655-106">If you move from a previous version of .NET to .NET 5.0 or later, you'll get different values produced by <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType>, and other <xref:System.Uri> members.</span></span>

<span data-ttu-id="4f655-107">Prenez en compte la sortie du code suivant lorsqu’il est exécuté sur UNIX.</span><span class="sxs-lookup"><span data-stu-id="4f655-107">Consider the output of the following code when run on Unix.</span></span>

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

<span data-ttu-id="4f655-108">Sortie sur la version précédente de .NET :</span><span class="sxs-lookup"><span data-stu-id="4f655-108">Output on previous .NET version:</span></span>

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

<span data-ttu-id="4f655-109">Sortie sur .NET 5,0 ou version ultérieure :</span><span class="sxs-lookup"><span data-stu-id="4f655-109">Output on .NET 5.0 or later version:</span></span>

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

#### <a name="version-introduced"></a><span data-ttu-id="4f655-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4f655-110">Version introduced</span></span>

<span data-ttu-id="4f655-111">5,0</span><span class="sxs-lookup"><span data-stu-id="4f655-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4f655-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="4f655-112">Recommended action</span></span>

<span data-ttu-id="4f655-113">Si vous avez du code qui attend et compte les segments de chemin d’accès dupliqués, vous pouvez supprimer ce code.</span><span class="sxs-lookup"><span data-stu-id="4f655-113">If you have code that expects and accounts for the duplicated path segments, you can remove that code.</span></span>

#### <a name="category"></a><span data-ttu-id="4f655-114">Category</span><span class="sxs-lookup"><span data-stu-id="4f655-114">Category</span></span>

<span data-ttu-id="4f655-115">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="4f655-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4f655-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="4f655-116">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
