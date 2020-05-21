---
ms.openlocfilehash: 1ea2d70a7cfe04cc4c4b9b58ea6bb6fa0226b245
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720951"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="11e63-101">Changement d’accès pour AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="11e63-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="11e63-102">À compter de .NET Core 3,0 RC1, l’accessibilité de `AccessibleObject.RuntimeIDFirstItem` est passée de `protected` à `internal` .</span><span class="sxs-lookup"><span data-stu-id="11e63-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="11e63-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="11e63-103">Change description</span></span>

<span data-ttu-id="11e63-104">À compter de .NET Core 3,0 Preview 4, le `AccessibleObject.RuntimeIDFirstItem` champ était `protected` .</span><span class="sxs-lookup"><span data-stu-id="11e63-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="11e63-105">À compter de .NET Core 3,0 RC1, il est passé de `protected` à `internal` pour s’aligner sur l’accessibilité du champ dans la .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11e63-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="11e63-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="11e63-106">Version introduced</span></span>

<span data-ttu-id="11e63-107">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="11e63-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="11e63-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="11e63-108">Recommended action</span></span>

<span data-ttu-id="11e63-109">La modification peut vous affecter si vous avez développé une application .NET Core avec un type qui dérive de <xref:System.Windows.Forms.AccessibleObject> et accède au `RuntimeIDFirstItem` champ.</span><span class="sxs-lookup"><span data-stu-id="11e63-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="11e63-110">Si c’est le cas, vous pouvez définir une constante locale comme suit :</span><span class="sxs-lookup"><span data-stu-id="11e63-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="11e63-111">Category</span><span class="sxs-lookup"><span data-stu-id="11e63-111">Category</span></span>

<span data-ttu-id="11e63-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11e63-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="11e63-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="11e63-113">Affected APIs</span></span>

- <span data-ttu-id="11e63-114">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="11e63-114">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis.

-->
