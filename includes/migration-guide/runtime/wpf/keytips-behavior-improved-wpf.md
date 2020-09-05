---
ms.openlocfilehash: 1487b5f47966cfcae0e47848dae99b39b42db18d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496928"
---
### <a name="keytips-behavior-improved-in-wpf"></a><span data-ttu-id="42a2b-101">Amélioration du comportement des touches d’accès dans WPF</span><span class="sxs-lookup"><span data-stu-id="42a2b-101">Keytips behavior improved in WPF</span></span>

#### <a name="details"></a><span data-ttu-id="42a2b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="42a2b-102">Details</span></span>

<span data-ttu-id="42a2b-103">Le comportement des touches d’accès a été modifié afin de correspondre au comportement de Microsoft Word et de l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="42a2b-103">Keytips behavior has been modified to bring parity with behavior on Microsoft Word and Windows Explorer.</span></span> <span data-ttu-id="42a2b-104">En vérifiant si l’état de la touche d’accès est activé ou non en cas de pression sur un <xref:System.Windows.Input.KeyEventArgs.SystemKey> (en particulier, <xref:System.Windows.Input.Key> ou <xref:System.Windows.Input.Key.F11>), WPF gère les touches KeyTip en conséquence.</span><span class="sxs-lookup"><span data-stu-id="42a2b-104">By checking whether keytip state is enabled or not in the case of a <xref:System.Windows.Input.KeyEventArgs.SystemKey> (in particular, <xref:System.Windows.Input.Key> or <xref:System.Windows.Input.Key.F11>) being pressed, WPF handles keytip keys appropriately.</span></span> <span data-ttu-id="42a2b-105">Les touches d’accès font maintenant disparaître un menu même quand il est ouvert par la souris.</span><span class="sxs-lookup"><span data-stu-id="42a2b-105">Keytips now dismiss a menu even when it is opened by mouse.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="42a2b-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="42a2b-106">Suggestion</span></span>

<span data-ttu-id="42a2b-107">N/A</span><span class="sxs-lookup"><span data-stu-id="42a2b-107">N/A</span></span>

| <span data-ttu-id="42a2b-108">Name</span><span class="sxs-lookup"><span data-stu-id="42a2b-108">Name</span></span>    | <span data-ttu-id="42a2b-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="42a2b-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="42a2b-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="42a2b-110">Scope</span></span>   |<span data-ttu-id="42a2b-111">Edge</span><span class="sxs-lookup"><span data-stu-id="42a2b-111">Edge</span></span>|
|<span data-ttu-id="42a2b-112">Version</span><span class="sxs-lookup"><span data-stu-id="42a2b-112">Version</span></span>|<span data-ttu-id="42a2b-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="42a2b-113">4.7.2</span></span>|
|<span data-ttu-id="42a2b-114">Type</span><span class="sxs-lookup"><span data-stu-id="42a2b-114">Type</span></span>|<span data-ttu-id="42a2b-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="42a2b-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="42a2b-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="42a2b-116">Affected APIs</span></span>

<span data-ttu-id="42a2b-117">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="42a2b-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
