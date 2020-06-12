---
ms.openlocfilehash: aab7d8538c875e35c832acc2a6c64beb84d4fb47
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702435"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="973d9-101">Les méthodes WinForms lèvent désormais ArgumentException</span><span class="sxs-lookup"><span data-stu-id="973d9-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="973d9-102">Certaines méthodes Windows Forms lèvent désormais un <xref:System.ArgumentException> pour les arguments non valides, dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="973d9-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="973d9-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="973d9-103">Change description</span></span>

<span data-ttu-id="973d9-104">Auparavant, passer des arguments d’un type inattendu ou incorrect à certaines méthodes Windows Forms entraînerait un état indéterminé.</span><span class="sxs-lookup"><span data-stu-id="973d9-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="973d9-105">À compter de .NET 5,0, ces méthodes lèvent désormais une exception <xref:System.ArgumentException> en cas de transmission d’arguments non valides.</span><span class="sxs-lookup"><span data-stu-id="973d9-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="973d9-106">La levée d’une <xref:System.ArgumentException> conforme au comportement du Runtime .net.</span><span class="sxs-lookup"><span data-stu-id="973d9-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="973d9-107">Il améliore également l’expérience de débogage en communiquant clairement l’argument qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="973d9-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="973d9-108">Le tableau suivant répertorie les méthodes et les paramètres affectés :</span><span class="sxs-lookup"><span data-stu-id="973d9-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="973d9-109">Méthode</span><span class="sxs-lookup"><span data-stu-id="973d9-109">Method</span></span> | <span data-ttu-id="973d9-110">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="973d9-110">Parameter name</span></span> | <span data-ttu-id="973d9-111">Condition</span><span class="sxs-lookup"><span data-stu-id="973d9-111">Condition</span></span> | <span data-ttu-id="973d9-112">Version ajoutée</span><span class="sxs-lookup"><span data-stu-id="973d9-112">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="973d9-113">L’argument n’est pas de type <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="973d9-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="973d9-114">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="973d9-114">5.0 Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="973d9-115">L’argument est `null` , <xref:System.String.Empty?displayProperty=nameWithType> , ou un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="973d9-115">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="973d9-116">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="973d9-116">5.0 Preview 5</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="973d9-117">Version introduite</span><span class="sxs-lookup"><span data-stu-id="973d9-117">Version introduced</span></span>

<span data-ttu-id="973d9-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="973d9-118">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="973d9-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="973d9-119">Recommended action</span></span>

- <span data-ttu-id="973d9-120">Mettez à jour le code pour empêcher le passage d’arguments non valides.</span><span class="sxs-lookup"><span data-stu-id="973d9-120">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="973d9-121">Si nécessaire, gérez un <xref:System.ArgumentException> lors de l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="973d9-121">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="973d9-122">Category</span><span class="sxs-lookup"><span data-stu-id="973d9-122">Category</span></span>

<span data-ttu-id="973d9-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="973d9-123">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="973d9-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="973d9-124">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>
- <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`

-->
