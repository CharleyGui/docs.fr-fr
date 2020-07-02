---
ms.openlocfilehash: 2d0798917b639bc90bf3f78f6fb9f19d0eaf2c71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614542"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a><span data-ttu-id="2c254-101">Implémentation incorrecte de MemberDescriptor.Equals</span><span class="sxs-lookup"><span data-stu-id="2c254-101">Incorrect implementation of MemberDescriptor.Equals</span></span>

#### <a name="details"></a><span data-ttu-id="2c254-102">Détails</span><span class="sxs-lookup"><span data-stu-id="2c254-102">Details</span></span>

<span data-ttu-id="2c254-103">L’implémentation d’origine de la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> compare deux propriétés de chaîne différentes des objets comparés : le nom de la catégorie et la chaîne de description.</span><span class="sxs-lookup"><span data-stu-id="2c254-103">The original implementation of the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method compares two different string properties from the objects being compared: the category name and the description string.</span></span> <span data-ttu-id="2c254-104">La solution consiste à comparer <xref:System.ComponentModel.MemberDescriptor.Category> du premier objet à <xref:System.ComponentModel.MemberDescriptor.Category> du second, et <xref:System.ComponentModel.MemberDescriptor.Description> du premier à <xref:System.ComponentModel.MemberDescriptor.Description> du second.</span><span class="sxs-lookup"><span data-stu-id="2c254-104">The fix is to compare the <xref:System.ComponentModel.MemberDescriptor.Category> of the first object to the <xref:System.ComponentModel.MemberDescriptor.Category> of the second one, and the <xref:System.ComponentModel.MemberDescriptor.Description> of the first to the <xref:System.ComponentModel.MemberDescriptor.Description> of the second.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2c254-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="2c254-105">Suggestion</span></span>

<span data-ttu-id="2c254-106">Si votre application dépend de <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> qui retourne parfois `false` quand les descripteurs sont équivalents et que vous ciblez .NET Framework 4.6.2 ou version ultérieure, plusieurs options s’offrent à vous :</span><span class="sxs-lookup"><span data-stu-id="2c254-106">If your application depends on <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> sometimes returning `false` when descriptors are equivalent, and you are targeting the .NET Framework 4.6.2 or later, you have several options:</span></span>

- <span data-ttu-id="2c254-107">Changez le code pour comparer manuellement les champs <xref:System.ComponentModel.MemberDescriptor.Category> et <xref:System.ComponentModel.MemberDescriptor.Description> parallèlement à l’appel de la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2c254-107">Make code changes to compare the <xref:System.ComponentModel.MemberDescriptor.Category> and <xref:System.ComponentModel.MemberDescriptor.Description> fields manually in addition to calling the <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="2c254-108">Refusez ce changement en ajoutant la valeur suivante au fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="2c254-108">Opt out of this change by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />
</runtime>
```

<span data-ttu-id="2c254-109">Si votre application cible .NET Framework 4.6.1 ou version antérieure, qu’elle s’exécute sur .NET Framework 4.6.2 ou version ultérieure et que vous souhaitez activer ce changement, vous pouvez affecter `false` au commutateur de compatibilité en ajoutant la valeur suivante au fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="2c254-109">If your application targets .NET Framework 4.6.1 or earlier and is running on the .NET Framework 4.6.2 or later and you want this change enabled, you can set the compatibility switch to `false` by adding the following value to the app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false" />
</runtime>
```

| <span data-ttu-id="2c254-110">Nom</span><span class="sxs-lookup"><span data-stu-id="2c254-110">Name</span></span>    | <span data-ttu-id="2c254-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="2c254-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2c254-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="2c254-112">Scope</span></span>   | <span data-ttu-id="2c254-113">Edge</span><span class="sxs-lookup"><span data-stu-id="2c254-113">Edge</span></span>        |
| <span data-ttu-id="2c254-114">Version</span><span class="sxs-lookup"><span data-stu-id="2c254-114">Version</span></span> | <span data-ttu-id="2c254-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="2c254-115">4.6.2</span></span>       |
| <span data-ttu-id="2c254-116">Type</span><span class="sxs-lookup"><span data-stu-id="2c254-116">Type</span></span>    | <span data-ttu-id="2c254-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="2c254-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="2c254-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="2c254-118">Affected APIs</span></span>

- <xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType>
