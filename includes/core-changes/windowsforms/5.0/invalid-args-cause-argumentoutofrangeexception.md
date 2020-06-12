---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702436"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="128dd-101">Les propriétés WinForms lèvent désormais ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="128dd-101">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="128dd-102">Certaines propriétés de Windows Forms lèvent désormais une exception <xref:System.ArgumentOutOfRangeException> pour les arguments non valides, dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="128dd-102">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="128dd-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="128dd-103">Change description</span></span>

<span data-ttu-id="128dd-104">Auparavant, ces propriétés relevaient d’autres exceptions, telles que <xref:System.NullReferenceException> , <xref:System.IndexOutOfRangeException> ou <xref:System.ArgumentException> , en cas de réussite des arguments hors limites.</span><span class="sxs-lookup"><span data-stu-id="128dd-104">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="128dd-105">À compter de .NET 5,0, ces propriétés lèvent désormais une exception <xref:System.ArgumentOutOfRangeException> quand les arguments passés sont en dehors de la plage.</span><span class="sxs-lookup"><span data-stu-id="128dd-105">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="128dd-106">La levée d’une <xref:System.ArgumentOutOfRangeException> conforme au comportement du Runtime .net.</span><span class="sxs-lookup"><span data-stu-id="128dd-106">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="128dd-107">Il améliore également l’expérience de débogage en communiquant clairement l’argument qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="128dd-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="128dd-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="128dd-108">Version introduced</span></span>

<span data-ttu-id="128dd-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="128dd-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="128dd-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="128dd-110">Recommended action</span></span>

- <span data-ttu-id="128dd-111">Mettez à jour le code pour empêcher le passage d’arguments non valides.</span><span class="sxs-lookup"><span data-stu-id="128dd-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="128dd-112">Si nécessaire, gérez une <xref:System.ArgumentOutOfRangeException> lors de la définition de la propriété.</span><span class="sxs-lookup"><span data-stu-id="128dd-112">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

#### <a name="category"></a><span data-ttu-id="128dd-113">Category</span><span class="sxs-lookup"><span data-stu-id="128dd-113">Category</span></span>

<span data-ttu-id="128dd-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="128dd-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="128dd-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="128dd-115">Affected APIs</span></span>

<span data-ttu-id="128dd-116">Le tableau suivant répertorie les propriétés et les paramètres affectés :</span><span class="sxs-lookup"><span data-stu-id="128dd-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="128dd-117">Propriété</span><span class="sxs-lookup"><span data-stu-id="128dd-117">Property</span></span> | <span data-ttu-id="128dd-118">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="128dd-118">Parameter name</span></span> | <span data-ttu-id="128dd-119">Version ajoutée</span><span class="sxs-lookup"><span data-stu-id="128dd-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="128dd-120">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="128dd-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="128dd-121">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="128dd-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="128dd-122">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="128dd-122">5.0 Preview 6</span></span> |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->
