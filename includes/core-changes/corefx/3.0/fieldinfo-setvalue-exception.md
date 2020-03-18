---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449551"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="7b8b0-101">FieldInfo.SetValue jette l’exception pour les champs statiques et init-seulement</span><span class="sxs-lookup"><span data-stu-id="7b8b0-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="7b8b0-102">À partir de .NET Core 3.0, une exception est lancée <xref:System.Reflection.FieldAttributes.InitOnly> lorsque vous <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>essayez de définir une valeur sur un terrain statique en appelant .</span><span class="sxs-lookup"><span data-stu-id="7b8b0-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7b8b0-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="7b8b0-103">Change description</span></span>

<span data-ttu-id="7b8b0-104">Dans .NET Framework et les versions de .NET Core avant 3.0, vous pouvez définir la valeur d’un champ statique <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>qui est constant après qu’il est initialisé ( lire dans C ' )[en](~/docs/csharp/language-reference/keywords/readonly.md)appelant .</span><span class="sxs-lookup"><span data-stu-id="7b8b0-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="7b8b0-105">Cependant, la définition d’un tel champ de cette façon a entraîné un comportement imprévisible basé sur le cadre cible et les paramètres d’optimisation.</span><span class="sxs-lookup"><span data-stu-id="7b8b0-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="7b8b0-106">Dans .NET Core 3.0 et les <xref:System.Reflection.FieldInfo.SetValue%2A> versions ultérieures, lorsque vous faites appel à un champ statique, <xref:System.Reflection.FieldAttributes.InitOnly> une <xref:System.FieldAccessException?displayProperty=nameWithType> exception est lancée.</span><span class="sxs-lookup"><span data-stu-id="7b8b0-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="7b8b0-107">Un <xref:System.Reflection.FieldAttributes.InitOnly> champ est celui qui ne peut être fixé qu’au moment où il est déclaré ou dans le constructeur pour la classe contenant.</span><span class="sxs-lookup"><span data-stu-id="7b8b0-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="7b8b0-108">En d’autres termes, il est constant après qu’il soit initialisé.</span><span class="sxs-lookup"><span data-stu-id="7b8b0-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7b8b0-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7b8b0-109">Version introduced</span></span>

<span data-ttu-id="7b8b0-110">3.0</span><span class="sxs-lookup"><span data-stu-id="7b8b0-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7b8b0-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7b8b0-111">Recommended action</span></span>

<span data-ttu-id="7b8b0-112">Initialiser les <xref:System.Reflection.FieldAttributes.InitOnly> champs statiques dans un constructeur statique.</span><span class="sxs-lookup"><span data-stu-id="7b8b0-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="7b8b0-113">Cela s’applique à la fois aux types dynamiques et non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="7b8b0-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="7b8b0-114">Alternativement, vous pouvez <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> supprimer l’attribut du <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>champ, puis appeler .</span><span class="sxs-lookup"><span data-stu-id="7b8b0-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="7b8b0-115">Category</span><span class="sxs-lookup"><span data-stu-id="7b8b0-115">Category</span></span>

<span data-ttu-id="7b8b0-116">CoreFx</span><span class="sxs-lookup"><span data-stu-id="7b8b0-116">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7b8b0-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="7b8b0-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
