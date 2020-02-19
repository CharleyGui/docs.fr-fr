---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449551"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="18b4d-101">FieldInfo. SetValue lève une exception pour les champs statiques, en initialisation seule</span><span class="sxs-lookup"><span data-stu-id="18b4d-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="18b4d-102">À compter de .NET Core 3,0, une exception est levée lorsque vous tentez de définir une valeur sur un champ statique, <xref:System.Reflection.FieldAttributes.InitOnly> en appelant <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="18b4d-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="18b4d-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="18b4d-103">Change description</span></span>

<span data-ttu-id="18b4d-104">Dans .NET Framework et les versions de .net Core antérieures à 3,0, vous pouviez définir la valeur d’un champ statique qui est constant après son initialisation ([ReadOnly en C# ](~/docs/csharp/language-reference/keywords/readonly.md)) en appelant <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="18b4d-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="18b4d-105">Toutefois, la définition de ce type de champ de cette façon a entraîné un comportement imprévisible basé sur le Framework cible et les paramètres d’optimisation.</span><span class="sxs-lookup"><span data-stu-id="18b4d-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="18b4d-106">Dans .NET Core 3,0 et versions ultérieures, lorsque vous appelez <xref:System.Reflection.FieldInfo.SetValue%2A> sur un champ statique <xref:System.Reflection.FieldAttributes.InitOnly>, une exception <xref:System.FieldAccessException?displayProperty=nameWithType> est levée.</span><span class="sxs-lookup"><span data-stu-id="18b4d-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="18b4d-107">Un champ <xref:System.Reflection.FieldAttributes.InitOnly> est un champ qui ne peut être défini qu’au moment où il est déclaré ou dans le constructeur pour la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="18b4d-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="18b4d-108">En d’autres termes, elle est constante une fois qu’elle a été initialisée.</span><span class="sxs-lookup"><span data-stu-id="18b4d-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="18b4d-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="18b4d-109">Version introduced</span></span>

<span data-ttu-id="18b4d-110">3.0</span><span class="sxs-lookup"><span data-stu-id="18b4d-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="18b4d-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="18b4d-111">Recommended action</span></span>

<span data-ttu-id="18b4d-112">Initialisez les champs statiques <xref:System.Reflection.FieldAttributes.InitOnly> dans un constructeur statique.</span><span class="sxs-lookup"><span data-stu-id="18b4d-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="18b4d-113">Cela s’applique à la fois aux types dynamiques et non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="18b4d-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="18b4d-114">Vous pouvez également supprimer l’attribut <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> du champ, puis appeler <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="18b4d-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="18b4d-115">Category</span><span class="sxs-lookup"><span data-stu-id="18b4d-115">Category</span></span>

<span data-ttu-id="18b4d-116">CoreFx</span><span class="sxs-lookup"><span data-stu-id="18b4d-116">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="18b4d-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="18b4d-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
