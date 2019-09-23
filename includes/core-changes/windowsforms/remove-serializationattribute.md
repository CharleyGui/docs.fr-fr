---
ms.openlocfilehash: e9d76d5907e7d700fc57117ccb43f8c430c615b0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181838"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="dc4bc-101">SerializableAttribute supprimé de certains types de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dc4bc-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="dc4bc-102"><xref:System.SerializableAttribute> A été supprimé de certains Windows Forms des classes qui n’ont aucun scénario de sérialisation binaire connu.</span><span class="sxs-lookup"><span data-stu-id="dc4bc-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="dc4bc-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="dc4bc-103">Change description</span></span>

<span data-ttu-id="dc4bc-104">Les types suivants sont décorés avec <xref:System.SerializableAttribute> le dans .NET Framework, mais l’attribut a été supprimé dans .net Core :</span><span class="sxs-lookup"><span data-stu-id="dc4bc-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

<span data-ttu-id="dc4bc-105">Historiquement, ce mécanisme de sérialisation avait des préoccupations graves en matière de maintenance et de sécurité.</span><span class="sxs-lookup"><span data-stu-id="dc4bc-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="dc4bc-106">La `SerializableAttribute` gestion de sur les types signifie que ces types doivent être testés pour les modifications de sérialisation de version à version et les modifications potentielles de sérialisation de Framework à Framework.</span><span class="sxs-lookup"><span data-stu-id="dc4bc-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="dc4bc-107">Cela complique l’évolution de ces types et peut s’avérer coûteux à gérer.</span><span class="sxs-lookup"><span data-stu-id="dc4bc-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="dc4bc-108">Ces types n’ont aucun scénario de sérialisation binaire connu, ce qui réduit l’impact de la suppression de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="dc4bc-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="dc4bc-109">Pour plus d'informations, consultez <https://docs.microsoft.com/en-us/dotnet/standard/serialization/binary-serialization>.</span><span class="sxs-lookup"><span data-stu-id="dc4bc-109">For more information, see <https://docs.microsoft.com/en-us/dotnet/standard/serialization/binary-serialization>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dc4bc-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="dc4bc-110">Version introduced</span></span>

<span data-ttu-id="dc4bc-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="dc4bc-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dc4bc-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="dc4bc-112">Recommended action</span></span>

<span data-ttu-id="dc4bc-113">Mettez à jour le code qui peut dépendre de ces types qui sont marqués comme sérialisables.</span><span class="sxs-lookup"><span data-stu-id="dc4bc-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="dc4bc-114">Category</span><span class="sxs-lookup"><span data-stu-id="dc4bc-114">Category</span></span>

<span data-ttu-id="dc4bc-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dc4bc-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dc4bc-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="dc4bc-116">Affected APIs</span></span>

- <span data-ttu-id="dc4bc-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="dc4bc-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->