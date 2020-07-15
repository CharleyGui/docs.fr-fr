---
ms.openlocfilehash: 9f6703c77e17ac9376aee944b891f4635dc7632e
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309141"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="abc47-101">Les méthodes WinForms lèvent désormais ArgumentException</span><span class="sxs-lookup"><span data-stu-id="abc47-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="abc47-102">Certaines méthodes Windows Forms lèvent désormais un <xref:System.ArgumentException> pour les arguments non valides, dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="abc47-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="abc47-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="abc47-103">Change description</span></span>

<span data-ttu-id="abc47-104">Auparavant, passer des arguments d’un type inattendu ou incorrect à certaines méthodes Windows Forms entraînerait un état indéterminé.</span><span class="sxs-lookup"><span data-stu-id="abc47-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="abc47-105">À compter de .NET 5,0, ces méthodes lèvent désormais une exception <xref:System.ArgumentException> en cas de transmission d’arguments non valides.</span><span class="sxs-lookup"><span data-stu-id="abc47-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="abc47-106">La levée d’une <xref:System.ArgumentException> conforme au comportement du Runtime .net.</span><span class="sxs-lookup"><span data-stu-id="abc47-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="abc47-107">Il améliore également l’expérience de débogage en communiquant clairement l’argument qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="abc47-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="abc47-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="abc47-108">Version introduced</span></span>

<span data-ttu-id="abc47-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="abc47-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="abc47-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="abc47-110">Recommended action</span></span>

- <span data-ttu-id="abc47-111">Mettez à jour le code pour empêcher le passage d’arguments non valides.</span><span class="sxs-lookup"><span data-stu-id="abc47-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="abc47-112">Si nécessaire, gérez un <xref:System.ArgumentException> lors de l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="abc47-112">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="abc47-113">Category</span><span class="sxs-lookup"><span data-stu-id="abc47-113">Category</span></span>

<span data-ttu-id="abc47-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="abc47-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="abc47-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="abc47-115">Affected APIs</span></span>

<span data-ttu-id="abc47-116">Le tableau suivant répertorie les méthodes et les paramètres affectés :</span><span class="sxs-lookup"><span data-stu-id="abc47-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="abc47-117">Méthode</span><span class="sxs-lookup"><span data-stu-id="abc47-117">Method</span></span> | <span data-ttu-id="abc47-118">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="abc47-118">Parameter name</span></span> | <span data-ttu-id="abc47-119">Condition</span><span class="sxs-lookup"><span data-stu-id="abc47-119">Condition</span></span> | <span data-ttu-id="abc47-120">Version ajoutée</span><span class="sxs-lookup"><span data-stu-id="abc47-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="abc47-121">L’argument n’est pas de type <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="abc47-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="abc47-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="abc47-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="abc47-123">L’argument est `null` , <xref:System.String.Empty?displayProperty=nameWithType> , ou un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="abc47-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="abc47-124">Préversion 5</span><span class="sxs-lookup"><span data-stu-id="abc47-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="abc47-125">Impossible de récupérer un `InputLanguage` pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="abc47-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="abc47-126">Version préliminaire 7</span><span class="sxs-lookup"><span data-stu-id="abc47-126">Preview 7</span></span> |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

-->
