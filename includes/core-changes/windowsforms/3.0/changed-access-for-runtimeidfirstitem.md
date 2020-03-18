---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644046"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="04956-101">Changement d’accès pour AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="04956-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="04956-102">À partir de .NET Core 3.0 `AccessibleObject.RuntimeIDFirstItem` RC1, l’accessibilité de a changé de `protected` . `internal`</span><span class="sxs-lookup"><span data-stu-id="04956-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="04956-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="04956-103">Change description</span></span>

<span data-ttu-id="04956-104">En commençant par .NET Core 3.0 Aperçu 4, le `AccessibleObject.RuntimeIDFirstItem` champ a été `protected`.</span><span class="sxs-lookup"><span data-stu-id="04956-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="04956-105">À partir de .NET Core 3.0 `protected` RC1, il est passé de l’autre `internal` pour s’aligner sur l’accessibilité du champ dans le cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="04956-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="04956-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="04956-106">Version introduced</span></span>

<span data-ttu-id="04956-107">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="04956-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="04956-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="04956-108">Recommended action</span></span>

<span data-ttu-id="04956-109">La modification peut vous affecter si vous avez développé une application <xref:System.Windows.Forms.AccessibleObject> .NET Core `RuntimeIDFirstItem` avec un type qui dérive et accède au champ.</span><span class="sxs-lookup"><span data-stu-id="04956-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="04956-110">Si c’est le cas, vous pouvez définir une constante locale comme suit :</span><span class="sxs-lookup"><span data-stu-id="04956-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="04956-111">Category</span><span class="sxs-lookup"><span data-stu-id="04956-111">Category</span></span>

<span data-ttu-id="04956-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04956-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="04956-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="04956-113">Affected APIs</span></span>

- <span data-ttu-id="04956-114">Non détectable par l’analyse de l’API.</span><span class="sxs-lookup"><span data-stu-id="04956-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
