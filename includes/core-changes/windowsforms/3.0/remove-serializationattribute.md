---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643955"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="b42da-101">SerializableAttribute supprimé de certains types de formulaires Windows</span><span class="sxs-lookup"><span data-stu-id="b42da-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="b42da-102">Le <xref:System.SerializableAttribute> a été supprimé de certaines classes de formulaires Windows qui n’ont pas de scénarios de sérialisation binaire connus.</span><span class="sxs-lookup"><span data-stu-id="b42da-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b42da-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="b42da-103">Change description</span></span>

<span data-ttu-id="b42da-104">Les types suivants sont <xref:System.SerializableAttribute> décorés avec le cadre en .NET, mais l’attribut a été supprimé dans .NET Core:</span><span class="sxs-lookup"><span data-stu-id="b42da-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

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

<span data-ttu-id="b42da-105">Historiquement, ce mécanisme de sérialisation a eu de graves problèmes de maintenance et de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b42da-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="b42da-106">Le `SerializableAttribute` maintien des types signifie que ces types doivent être testés pour les modifications de la sérialisation de la version à la version et les modifications potentiellement de sérialisation de cadre à cadre.</span><span class="sxs-lookup"><span data-stu-id="b42da-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="b42da-107">Il est donc plus difficile de faire évoluer ces types et peut être coûteux à entretenir.</span><span class="sxs-lookup"><span data-stu-id="b42da-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="b42da-108">Ces types n’ont pas de scénarios de sérialisation binaires connus, ce qui minimise l’impact de la suppression de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="b42da-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="b42da-109">Pour plus d’informations, voir [la sérialisation binaire](~/docs/standard/serialization/binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="b42da-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b42da-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b42da-110">Version introduced</span></span>

<span data-ttu-id="b42da-111">3.0 Aperçu 9</span><span class="sxs-lookup"><span data-stu-id="b42da-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b42da-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b42da-112">Recommended action</span></span>

<span data-ttu-id="b42da-113">Mettez à jour tout code qui peut dépendre de ces types étant marqués comme sérialisables.</span><span class="sxs-lookup"><span data-stu-id="b42da-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="b42da-114">Category</span><span class="sxs-lookup"><span data-stu-id="b42da-114">Category</span></span>

<span data-ttu-id="b42da-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b42da-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b42da-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="b42da-116">Affected APIs</span></span>

- <span data-ttu-id="b42da-117">None</span><span class="sxs-lookup"><span data-stu-id="b42da-117">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
