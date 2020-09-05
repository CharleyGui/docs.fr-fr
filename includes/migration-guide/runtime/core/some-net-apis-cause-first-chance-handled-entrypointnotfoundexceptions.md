---
ms.openlocfilehash: 6431f3b4d0983c44629e4fe760c75adcc277ddd4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496656"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a><span data-ttu-id="a70bc-101">Certaines API .NET provoquent des exceptions EntryPointNotFoundExceptions de première chance (gérées)</span><span class="sxs-lookup"><span data-stu-id="a70bc-101">Some .NET APIs cause first chance (handled) EntryPointNotFoundExceptions</span></span>

#### <a name="details"></a><span data-ttu-id="a70bc-102">Détails</span><span class="sxs-lookup"><span data-stu-id="a70bc-102">Details</span></span>

<span data-ttu-id="a70bc-103">Dans .NET Framework 4.5, un petit nombre de méthodes .NET levaient des exceptions <xref:System.EntryPointNotFoundException?displayProperty=fullName> de première chance.</span><span class="sxs-lookup"><span data-stu-id="a70bc-103">In the .NET Framework 4.5, a small number of .NET methods began throwing first chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span> <span data-ttu-id="a70bc-104">Ces exceptions étaient gérées dans le .NET Framework, mais pouvaient arrêter l’automatisation des tests, car celle-ci ne s’attendait pas à des exceptions de première chance.</span><span class="sxs-lookup"><span data-stu-id="a70bc-104">These exceptions were handled within the .NET Framework, but could break test automation that did not expect the first chance exceptions.</span></span> <span data-ttu-id="a70bc-105">Ces mêmes API provoquent l’arrêt de certaines exécutions ApiVerifier lorsque HighVersionLie est activé.</span><span class="sxs-lookup"><span data-stu-id="a70bc-105">These same APIs break some ApiVerifier scenarios when HighVersionLie is enabled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a70bc-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="a70bc-106">Suggestion</span></span>

<span data-ttu-id="a70bc-107">Vous pouvez éviter ce problème en effectuant une mise à niveau vers .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="a70bc-107">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="a70bc-108">Vous pouvez aussi mettre à jour le code d’automatisation des tests pour que son exécution ne soit pas arrêtée en cas d’exceptions <xref:System.EntryPointNotFoundException?displayProperty=fullName> de première chance.</span><span class="sxs-lookup"><span data-stu-id="a70bc-108">Alternatively, test automation can be updated to not break on first-chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="a70bc-109">Name</span><span class="sxs-lookup"><span data-stu-id="a70bc-109">Name</span></span>    | <span data-ttu-id="a70bc-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="a70bc-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a70bc-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="a70bc-111">Scope</span></span>   |<span data-ttu-id="a70bc-112">Edge</span><span class="sxs-lookup"><span data-stu-id="a70bc-112">Edge</span></span>|
|<span data-ttu-id="a70bc-113">Version</span><span class="sxs-lookup"><span data-stu-id="a70bc-113">Version</span></span>|<span data-ttu-id="a70bc-114">4,5</span><span class="sxs-lookup"><span data-stu-id="a70bc-114">4.5</span></span>|
|<span data-ttu-id="a70bc-115">Type</span><span class="sxs-lookup"><span data-stu-id="a70bc-115">Type</span></span>|<span data-ttu-id="a70bc-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="a70bc-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a70bc-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="a70bc-117">Affected APIs</span></span>

- <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)>

<!--

#### Affected APIs

- `M:System.Diagnostics.Debug.Assert(System.Boolean)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])`
- `M:System.Xml.Serialization.XmlSerializer.#ctor(System.Type)`

-->
