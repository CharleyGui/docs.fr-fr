---
ms.openlocfilehash: f61e5670334f4d3674fd0b008d1a476b14c7ba4e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497561"
---
### <a name="calling-attributegetcustomattributes-on-an-indexer-property-no-longer-throws-ambiguousmatchexception-if-the-ambiguity-can-be-resolved-by-indexs-type"></a><span data-ttu-id="6c4be-101">L’appel d’Attribute.GetCustomAttributes sur une propriété d’indexeur ne lève plus d’exception AmbiguousMatchException si l’ambiguïté peut être résolue par type d’index</span><span class="sxs-lookup"><span data-stu-id="6c4be-101">Calling Attribute.GetCustomAttributes on an indexer property no longer throws AmbiguousMatchException if the ambiguity can be resolved by index's type</span></span>

#### <a name="details"></a><span data-ttu-id="6c4be-102">Détails</span><span class="sxs-lookup"><span data-stu-id="6c4be-102">Details</span></span>

<span data-ttu-id="6c4be-103">Avant le .NET Framework 4.6, l’appel de <code>GetCustomAttribute(s)</code> sur une propriété d’indexeur qui différait d’une autre propriété uniquement par son type d’index entraînait une <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="6c4be-103">Prior to the .NET Framework 4.6, calling <code>GetCustomAttribute(s)</code> on an indexer property which differed from another property only by the type of the index would result in an <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>.</span></span> <span data-ttu-id="6c4be-104">À compter de la version 4.6 du .NET Framework, les attributs de la propriété sont correctement retournés.</span><span class="sxs-lookup"><span data-stu-id="6c4be-104">Beginning in the .NET Framework 4.6, the property's attributes will be correctly returned.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6c4be-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="6c4be-105">Suggestion</span></span>

<span data-ttu-id="6c4be-106">Notez que GetCustomAttribute(s) fonctionne plus fréquemment à présent.</span><span class="sxs-lookup"><span data-stu-id="6c4be-106">Be aware that GetCustomAttribute(s) will work more frequently now.</span></span> <span data-ttu-id="6c4be-107">Si une application comptait sur l’exception <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>, utilisez la réflexion pour rechercher explicitement plusieurs indexeurs.</span><span class="sxs-lookup"><span data-stu-id="6c4be-107">If an app was previously relying on the <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>, reflection should now be used to explicitly look for multiple indexers, instead.</span></span>

| <span data-ttu-id="6c4be-108">Name</span><span class="sxs-lookup"><span data-stu-id="6c4be-108">Name</span></span>    | <span data-ttu-id="6c4be-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="6c4be-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6c4be-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="6c4be-110">Scope</span></span>   |<span data-ttu-id="6c4be-111">Edge</span><span class="sxs-lookup"><span data-stu-id="6c4be-111">Edge</span></span>|
|<span data-ttu-id="6c4be-112">Version</span><span class="sxs-lookup"><span data-stu-id="6c4be-112">Version</span></span>|<span data-ttu-id="6c4be-113">4,6</span><span class="sxs-lookup"><span data-stu-id="6c4be-113">4.6</span></span>|
|<span data-ttu-id="6c4be-114">Type</span><span class="sxs-lookup"><span data-stu-id="6c4be-114">Type</span></span>|<span data-ttu-id="6c4be-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="6c4be-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6c4be-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="6c4be-116">Affected APIs</span></span>

- <xref:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)`
- `M:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute``1(System.Reflection.MemberInfo)``
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute``1(System.Reflection.MemberInfo,System.Boolean)``
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes``1(System.Reflection.MemberInfo)``
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes``1(System.Reflection.MemberInfo,System.Boolean)``

-->
