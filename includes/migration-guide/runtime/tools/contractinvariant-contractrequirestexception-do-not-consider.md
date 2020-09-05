---
ms.openlocfilehash: 17fde81f9734966692c9f41d2213f8682dedea46
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496902"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a><span data-ttu-id="6b709-101">Contract.Invariant ou Contract.Requires\<TException> ne considèrent pas String.IsNullOrEmpty comme pure</span><span class="sxs-lookup"><span data-stu-id="6b709-101">Contract.Invariant or Contract.Requires\<TException> do not consider String.IsNullOrEmpty to be pure</span></span>

#### <a name="details"></a><span data-ttu-id="6b709-102">Détails</span><span class="sxs-lookup"><span data-stu-id="6b709-102">Details</span></span>

<span data-ttu-id="6b709-103">Pour les applications qui ciblent le .NET Framework 4.6.1, si le contrat d’invariant pour <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> ou le contrat de condition préalable pour <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> appelle la <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> méthode, le ReWriter émet l’avertissement du compilateur CC1036 : un &quot; appel à la méthode’System. String. IsNullOrWhteSpace (System. String) 'sans [pure] dans la méthode est détecté. &quot; Il s’agit d’un avertissement du compilateur plutôt qu’une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="6b709-103">For apps that target the .NET Framework 4.6.1, if the invariant contract for <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> or the precondition contract for <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> calls the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method, the rewriter emits compiler warning CC1036: &quot;Detected call to method 'System.String.IsNullOrWhteSpace(System.String)' without [Pure] in method.&quot; This is a compiler warning rather than a compiler error.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6b709-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="6b709-104">Suggestion</span></span>

<span data-ttu-id="6b709-105">Ce comportement est abordé dans le [problème 339](https://github.com/Microsoft/CodeContracts/issues/339), sur le site GitHub.</span><span class="sxs-lookup"><span data-stu-id="6b709-105">This behavior was addressed in [GitHub Issue #339](https://github.com/Microsoft/CodeContracts/issues/339).</span></span> <span data-ttu-id="6b709-106">Pour éviter cet avertissement, vous pouvez télécharger et compiler une version mise à jour du code source pour l’outil Contrats de code sur le site [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="6b709-106">To eliminate this warning, you can download and compile an updated version of the source code for the Code Contracts tool from [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md).</span></span> <span data-ttu-id="6b709-107">Des informations sur le téléchargement se trouvent au bas de la page.</span><span class="sxs-lookup"><span data-stu-id="6b709-107">Download information is found at the bottom of the page.</span></span>

| <span data-ttu-id="6b709-108">Name</span><span class="sxs-lookup"><span data-stu-id="6b709-108">Name</span></span>    | <span data-ttu-id="6b709-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="6b709-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6b709-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="6b709-110">Scope</span></span>   |<span data-ttu-id="6b709-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="6b709-111">Minor</span></span>|
|<span data-ttu-id="6b709-112">Version</span><span class="sxs-lookup"><span data-stu-id="6b709-112">Version</span></span>|<span data-ttu-id="6b709-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="6b709-113">4.6.1</span></span>|
|<span data-ttu-id="6b709-114">Type</span><span class="sxs-lookup"><span data-stu-id="6b709-114">Type</span></span>|<span data-ttu-id="6b709-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="6b709-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6b709-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="6b709-116">Affected APIs</span></span>

- <xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)`
- `M:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)`

-->
