---
ms.openlocfilehash: 60937459b6f18e9abae87ad2dc97c3942325eedc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619997"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="f56a7-101">Les adaptateurs de flux WinRT n’appellent plus FlushAsync automatiquement lors de la fermeture</span><span class="sxs-lookup"><span data-stu-id="f56a7-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

#### <a name="details"></a><span data-ttu-id="f56a7-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f56a7-102">Details</span></span>

<span data-ttu-id="f56a7-103">Dans les applications du Windows Store, les adaptateurs de flux Windows Runtime n’appellent plus la méthode FlushAsync à partir de la méthode Dispose.</span><span class="sxs-lookup"><span data-stu-id="f56a7-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f56a7-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f56a7-104">Suggestion</span></span>

<span data-ttu-id="f56a7-105">Cette modification devrait être transparente.</span><span class="sxs-lookup"><span data-stu-id="f56a7-105">This change should be transparent.</span></span> <span data-ttu-id="f56a7-106">Les développeurs peuvent rétablir le comportement précédent en écrivant du code comme le suivant :</span><span class="sxs-lookup"><span data-stu-id="f56a7-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="f56a7-107">Nom</span><span class="sxs-lookup"><span data-stu-id="f56a7-107">Name</span></span>    | <span data-ttu-id="f56a7-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="f56a7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f56a7-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="f56a7-109">Scope</span></span>   |<span data-ttu-id="f56a7-110">Mode transparent</span><span class="sxs-lookup"><span data-stu-id="f56a7-110">Transparent</span></span>|
|<span data-ttu-id="f56a7-111">Version</span><span class="sxs-lookup"><span data-stu-id="f56a7-111">Version</span></span>|<span data-ttu-id="f56a7-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f56a7-112">4.5.1</span></span>|
|<span data-ttu-id="f56a7-113">Type</span><span class="sxs-lookup"><span data-stu-id="f56a7-113">Type</span></span>|<span data-ttu-id="f56a7-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="f56a7-114">Runtime</span></span>|
