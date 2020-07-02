---
ms.openlocfilehash: 4303b177ffe01328965c909a5a3809414fcead91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614595"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a><span data-ttu-id="00b6f-101">L’algorithme de hachage par défaut pour le compilateur de balisage de WPF est désormais SHA256</span><span class="sxs-lookup"><span data-stu-id="00b6f-101">The default hash algorithm for WPF's Markup Compiler is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="00b6f-102">Détails</span><span class="sxs-lookup"><span data-stu-id="00b6f-102">Details</span></span>

<span data-ttu-id="00b6f-103">Le compilateur de balisage de WPF fournit des services de compilation pour les fichiers de balisage XAML.</span><span class="sxs-lookup"><span data-stu-id="00b6f-103">The WPF MarkupCompiler provides compilation services for XAML markup files.</span></span>  <span data-ttu-id="00b6f-104">Dans .NET Framework 4.7.1 et versions antérieures, l’algorithme de hachage par défaut utilisé pour les sommes de contrôle était SHA1.</span><span class="sxs-lookup"><span data-stu-id="00b6f-104">In the .NET Framework 4.7.1 and earlier versions, the default hash algorithm used for checksums was SHA1.</span></span> <span data-ttu-id="00b6f-105">En raison des récents problèmes de sécurité avec SHA1, cette valeur par défaut est remplacée par SHA256 à compter de .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="00b6f-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.2.</span></span>  <span data-ttu-id="00b6f-106">Ce changement affecte toutes les générations de somme de contrôle pour les fichiers de balisage pendant la compilation.</span><span class="sxs-lookup"><span data-stu-id="00b6f-106">This change affects all checksum generation for markup files during compilation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="00b6f-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="00b6f-107">Suggestion</span></span>

<span data-ttu-id="00b6f-108">Un développeur qui cible .NET Framework 4.7.2 ou version ultérieure et souhaite restaurer le comportement de hachage SHA1 doit définir l’indicateur AppContext suivant.</span><span class="sxs-lookup"><span data-stu-id="00b6f-108">A developer who targets .NET Framework 4.7.2 or greater and wants to revert to SHA1 hashing behavior must set the following AppContext flag.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="00b6f-109">Un développeur qui souhaite utiliser le hachage SHA256 tout en ciblant une version du .NET Framework antérieure à la version 4.7.2 doit définir l’indicateur AppContext ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="00b6f-109">A developer who wants to utilize SHA256 hashing while targeting a framework version below .NET 4.7.2 must set the below AppContext flag.</span></span>  <span data-ttu-id="00b6f-110">Notez que la version installée du .NET Framework doit être la version 4.7.2 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="00b6f-110">Note that the installed version of the .NET Framework must be 4.7.2 or greater.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="00b6f-111">Nom</span><span class="sxs-lookup"><span data-stu-id="00b6f-111">Name</span></span>    | <span data-ttu-id="00b6f-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="00b6f-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="00b6f-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="00b6f-113">Scope</span></span>   | <span data-ttu-id="00b6f-114">Mode transparent</span><span class="sxs-lookup"><span data-stu-id="00b6f-114">Transparent</span></span> |
| <span data-ttu-id="00b6f-115">Version</span><span class="sxs-lookup"><span data-stu-id="00b6f-115">Version</span></span> | <span data-ttu-id="00b6f-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="00b6f-116">4.7.2</span></span>       |
| <span data-ttu-id="00b6f-117">Type</span><span class="sxs-lookup"><span data-stu-id="00b6f-117">Type</span></span>    | <span data-ttu-id="00b6f-118">Reciblage</span><span class="sxs-lookup"><span data-stu-id="00b6f-118">Retargeting</span></span> |
