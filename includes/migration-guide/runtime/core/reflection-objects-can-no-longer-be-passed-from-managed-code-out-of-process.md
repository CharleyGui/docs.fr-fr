---
ms.openlocfilehash: f011f6ebe0fa85a59f3e69c93bba9eddc4c1689b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496349"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="3d554-101">Les objets de réflexion ne peuvent plus être passés du code managé aux clients DCOM hors processus</span><span class="sxs-lookup"><span data-stu-id="3d554-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="3d554-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3d554-102">Details</span></span>

<span data-ttu-id="3d554-103">Les objets de réflexion ne peuvent plus être passés du code managé aux clients DCOM hors processus.</span><span class="sxs-lookup"><span data-stu-id="3d554-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="3d554-104">Les types suivants sont concernés :</span><span class="sxs-lookup"><span data-stu-id="3d554-104">The following types are affected:</span></span>

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <span data-ttu-id="3d554-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (et ses types dérivés, dont <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName> et <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span><span class="sxs-lookup"><span data-stu-id="3d554-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span>
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>

<span data-ttu-id="3d554-106">Les appels à <code>IMarshal</code> pour l’objet retournent <code>E_NOINTERFACE</code>.</span><span class="sxs-lookup"><span data-stu-id="3d554-106">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3d554-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3d554-107">Suggestion</span></span>

<span data-ttu-id="3d554-108">Mettez à jour le code de marshaling pour travailler avec des objets non réfléchissants.</span><span class="sxs-lookup"><span data-stu-id="3d554-108">Update marshaling code to work with non-reflection objects.</span></span>

| <span data-ttu-id="3d554-109">Name</span><span class="sxs-lookup"><span data-stu-id="3d554-109">Name</span></span>    | <span data-ttu-id="3d554-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="3d554-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3d554-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="3d554-111">Scope</span></span>   |<span data-ttu-id="3d554-112">Secondaire</span><span class="sxs-lookup"><span data-stu-id="3d554-112">Minor</span></span>|
|<span data-ttu-id="3d554-113">Version</span><span class="sxs-lookup"><span data-stu-id="3d554-113">Version</span></span>|<span data-ttu-id="3d554-114">4,6</span><span class="sxs-lookup"><span data-stu-id="3d554-114">4.6</span></span>|
|<span data-ttu-id="3d554-115">Type</span><span class="sxs-lookup"><span data-stu-id="3d554-115">Type</span></span>|<span data-ttu-id="3d554-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="3d554-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3d554-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="3d554-117">Affected APIs</span></span>

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <xref:System.Reflection.FieldInfo?displayProperty=fullName>
- <xref:System.Reflection.MemberInfo?displayProperty=fullName>
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.MethodInfo?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>
- <xref:System.Reflection.TypeInfo?displayProperty=fullName>
- <xref:System.Type?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Reflection.Assembly`
- `T:System.Reflection.FieldInfo`
- `T:System.Reflection.MemberInfo`
- `T:System.Reflection.MethodBody`
- `T:System.Reflection.MethodInfo`
- `T:System.Reflection.Module`
- `T:System.Reflection.ParameterInfo`
- `T:System.Reflection.TypeInfo`
- `T:System.Type`

-->
