---
ms.openlocfilehash: f1fc70075ef09a4f036c69788342c07ee51d72ce
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702488"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="6cfcc-101">Les méthodes WinForms lèvent désormais ArgumentException</span><span class="sxs-lookup"><span data-stu-id="6cfcc-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="6cfcc-102">Certaines méthodes Windows Forms lèvent désormais un <xref:System.ArgumentException> pour les arguments non valides, dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6cfcc-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="6cfcc-103">Change description</span></span>

<span data-ttu-id="6cfcc-104">Auparavant, passer des arguments d’un type inattendu ou incorrect à certaines méthodes Windows Forms entraînerait un état indéterminé.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="6cfcc-105">À compter de .NET 5,0, ces méthodes lèvent désormais une exception <xref:System.ArgumentException> en cas de transmission d’arguments non valides.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="6cfcc-106">La levée d’une <xref:System.ArgumentException> conforme au comportement du Runtime .net.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="6cfcc-107">Il améliore également l’expérience de débogage en communiquant clairement l’argument qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="6cfcc-108">Le tableau suivant répertorie les méthodes et les paramètres affectés :</span><span class="sxs-lookup"><span data-stu-id="6cfcc-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="6cfcc-109">Méthode</span><span class="sxs-lookup"><span data-stu-id="6cfcc-109">Method</span></span> | <span data-ttu-id="6cfcc-110">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="6cfcc-110">Parameter name</span></span> | <span data-ttu-id="6cfcc-111">Condition</span><span class="sxs-lookup"><span data-stu-id="6cfcc-111">Condition</span></span> | <span data-ttu-id="6cfcc-112">Version ajoutée</span><span class="sxs-lookup"><span data-stu-id="6cfcc-112">Version added</span></span> |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="6cfcc-113">L’argument n’est pas de type <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="6cfcc-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="6cfcc-114">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="6cfcc-114">5.0 Preview 1</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="6cfcc-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6cfcc-115">Version introduced</span></span>

<span data-ttu-id="6cfcc-116">.NET 5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="6cfcc-116">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6cfcc-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6cfcc-117">Recommended action</span></span>

- <span data-ttu-id="6cfcc-118">Mettez à jour le code pour empêcher le passage d’arguments non valides.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-118">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="6cfcc-119">Si nécessaire, gérez un <xref:System.ArgumentException> lors de l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="6cfcc-119">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="6cfcc-120">Category</span><span class="sxs-lookup"><span data-stu-id="6cfcc-120">Category</span></span>

<span data-ttu-id="6cfcc-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6cfcc-121">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6cfcc-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="6cfcc-122">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
