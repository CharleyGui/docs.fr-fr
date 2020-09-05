---
ms.openlocfilehash: 2b4f35fe15f806897e5e4d85ee774b2e4572d974
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497465"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="aeeda-101">Les adaptateurs de flux WinRT n’appellent plus FlushAsync automatiquement lors de la fermeture</span><span class="sxs-lookup"><span data-stu-id="aeeda-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

#### <a name="details"></a><span data-ttu-id="aeeda-102">Détails</span><span class="sxs-lookup"><span data-stu-id="aeeda-102">Details</span></span>

<span data-ttu-id="aeeda-103">Dans les applications du Windows Store, les adaptateurs de flux Windows Runtime n’appellent plus la méthode FlushAsync à partir de la méthode Dispose.</span><span class="sxs-lookup"><span data-stu-id="aeeda-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="aeeda-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="aeeda-104">Suggestion</span></span>

<span data-ttu-id="aeeda-105">Cette modification devrait être transparente.</span><span class="sxs-lookup"><span data-stu-id="aeeda-105">This change should be transparent.</span></span> <span data-ttu-id="aeeda-106">Les développeurs peuvent rétablir le comportement précédent en écrivant du code comme le suivant :</span><span class="sxs-lookup"><span data-stu-id="aeeda-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="aeeda-107">Name</span><span class="sxs-lookup"><span data-stu-id="aeeda-107">Name</span></span>    | <span data-ttu-id="aeeda-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="aeeda-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="aeeda-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="aeeda-109">Scope</span></span>   |<span data-ttu-id="aeeda-110">Mode transparent</span><span class="sxs-lookup"><span data-stu-id="aeeda-110">Transparent</span></span>|
|<span data-ttu-id="aeeda-111">Version</span><span class="sxs-lookup"><span data-stu-id="aeeda-111">Version</span></span>|<span data-ttu-id="aeeda-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="aeeda-112">4.5.1</span></span>|
|<span data-ttu-id="aeeda-113">Type</span><span class="sxs-lookup"><span data-stu-id="aeeda-113">Type</span></span>|<span data-ttu-id="aeeda-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="aeeda-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="aeeda-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="aeeda-115">Affected APIs</span></span>

<span data-ttu-id="aeeda-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="aeeda-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
