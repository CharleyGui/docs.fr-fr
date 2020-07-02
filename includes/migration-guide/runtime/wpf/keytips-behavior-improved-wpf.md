---
ms.openlocfilehash: 9659068304eb208fd6a0a753273453bc669fbc56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621275"
---
### <a name="keytips-behavior-improved-in-wpf"></a><span data-ttu-id="62fae-101">Amélioration du comportement des touches d’accès dans WPF</span><span class="sxs-lookup"><span data-stu-id="62fae-101">Keytips behavior improved in WPF</span></span>

#### <a name="details"></a><span data-ttu-id="62fae-102">Détails</span><span class="sxs-lookup"><span data-stu-id="62fae-102">Details</span></span>

<span data-ttu-id="62fae-103">Le comportement des touches d’accès a été modifié afin de correspondre au comportement de Microsoft Word et de l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="62fae-103">Keytips behavior has been modified to bring parity with behavior on Microsoft Word and Windows Explorer.</span></span> <span data-ttu-id="62fae-104">En vérifiant si l’état de la touche d’accès est activé ou non en cas de pression sur un <xref:System.Windows.Input.KeyEventArgs.SystemKey> (en particulier, <xref:System.Windows.Input.Key> ou <xref:System.Windows.Input.Key.F11>), WPF gère les touches KeyTip en conséquence.</span><span class="sxs-lookup"><span data-stu-id="62fae-104">By checking whether keytip state is enabled or not in the case of a <xref:System.Windows.Input.KeyEventArgs.SystemKey> (in particular, <xref:System.Windows.Input.Key> or <xref:System.Windows.Input.Key.F11>) being pressed, WPF handles keytip keys appropriately.</span></span> <span data-ttu-id="62fae-105">Les touches d’accès font maintenant disparaître un menu même quand il est ouvert par la souris.</span><span class="sxs-lookup"><span data-stu-id="62fae-105">Keytips now dismiss a menu even when it is opened by mouse.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="62fae-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="62fae-106">Suggestion</span></span>

<span data-ttu-id="62fae-107">N/A</span><span class="sxs-lookup"><span data-stu-id="62fae-107">N/A</span></span>

| <span data-ttu-id="62fae-108">Nom</span><span class="sxs-lookup"><span data-stu-id="62fae-108">Name</span></span>    | <span data-ttu-id="62fae-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="62fae-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="62fae-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="62fae-110">Scope</span></span>   |<span data-ttu-id="62fae-111">Edge</span><span class="sxs-lookup"><span data-stu-id="62fae-111">Edge</span></span>|
|<span data-ttu-id="62fae-112">Version</span><span class="sxs-lookup"><span data-stu-id="62fae-112">Version</span></span>|<span data-ttu-id="62fae-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="62fae-113">4.7.2</span></span>|
|<span data-ttu-id="62fae-114">Type</span><span class="sxs-lookup"><span data-stu-id="62fae-114">Type</span></span>|<span data-ttu-id="62fae-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="62fae-115">Runtime</span></span>|
