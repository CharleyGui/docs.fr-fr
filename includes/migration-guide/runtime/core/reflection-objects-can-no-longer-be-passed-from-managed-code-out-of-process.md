---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621335"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="a20db-101">Les objets de réflexion ne peuvent plus être passés du code managé aux clients DCOM hors processus</span><span class="sxs-lookup"><span data-stu-id="a20db-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="a20db-102">Détails</span><span class="sxs-lookup"><span data-stu-id="a20db-102">Details</span></span>

<span data-ttu-id="a20db-103">Les objets de réflexion ne peuvent plus être passés du code managé aux clients DCOM hors processus.</span><span class="sxs-lookup"><span data-stu-id="a20db-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="a20db-104">Les types suivants sont concernés :</span><span class="sxs-lookup"><span data-stu-id="a20db-104">The following types are affected:</span></span><ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><span data-ttu-id="a20db-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (et ses types dérivés, dont <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName> et <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span><span class="sxs-lookup"><span data-stu-id="a20db-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span></li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><span data-ttu-id="a20db-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="a20db-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span></span></li></ul><span data-ttu-id="a20db-107">Les appels à <code>IMarshal</code> pour l’objet retournent <code>E_NOINTERFACE</code>.</span><span class="sxs-lookup"><span data-stu-id="a20db-107">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a20db-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="a20db-108">Suggestion</span></span>

<span data-ttu-id="a20db-109">Mettez à jour le code de marshaling pour utiliser des objets autres que des objets de réflexion.</span><span class="sxs-lookup"><span data-stu-id="a20db-109">Update marshaling code to work with non-reflection objects</span></span>

| <span data-ttu-id="a20db-110">Nom</span><span class="sxs-lookup"><span data-stu-id="a20db-110">Name</span></span>    | <span data-ttu-id="a20db-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="a20db-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a20db-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="a20db-112">Scope</span></span>   |<span data-ttu-id="a20db-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="a20db-113">Minor</span></span>|
|<span data-ttu-id="a20db-114">Version</span><span class="sxs-lookup"><span data-stu-id="a20db-114">Version</span></span>|<span data-ttu-id="a20db-115">4.6</span><span class="sxs-lookup"><span data-stu-id="a20db-115">4.6</span></span>|
|<span data-ttu-id="a20db-116">Type</span><span class="sxs-lookup"><span data-stu-id="a20db-116">Type</span></span>|<span data-ttu-id="a20db-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="a20db-117">Runtime</span></span>|
