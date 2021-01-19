---
title: 'Modification avec rupture : les méthodes WinForms lèvent désormais ArgumentException'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où certaines méthodes Windows Forms lèvent désormais une exception ArgumentException pour les arguments non valides.
ms.date: 07/18/2020
ms.openlocfilehash: 892f4d16b80f3e42187480a7fcfb24e81868d07c
ms.sourcegitcommit: f8cd3ef517ee177c99feed944824c27d208cc0d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98570214"
---
# <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="28cdf-103">Les méthodes WinForms lèvent désormais ArgumentException</span><span class="sxs-lookup"><span data-stu-id="28cdf-103">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="28cdf-104">Certaines méthodes Windows Forms lèvent désormais un <xref:System.ArgumentException> pour les arguments non valides, dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="28cdf-104">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="28cdf-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="28cdf-105">Change description</span></span>

<span data-ttu-id="28cdf-106">Auparavant, passer des arguments d’un type inattendu ou incorrect à certaines méthodes Windows Forms entraînerait un état indéterminé.</span><span class="sxs-lookup"><span data-stu-id="28cdf-106">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="28cdf-107">À compter de .NET 5,0, ces méthodes lèvent désormais une exception <xref:System.ArgumentException> en cas de transmission d’arguments non valides.</span><span class="sxs-lookup"><span data-stu-id="28cdf-107">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="28cdf-108">La levée d’une <xref:System.ArgumentException> conforme au comportement du Runtime .net.</span><span class="sxs-lookup"><span data-stu-id="28cdf-108">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="28cdf-109">Il améliore également l’expérience de débogage en communiquant clairement l’argument qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="28cdf-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="28cdf-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="28cdf-110">Version introduced</span></span>

<span data-ttu-id="28cdf-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="28cdf-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="28cdf-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="28cdf-112">Recommended action</span></span>

- <span data-ttu-id="28cdf-113">Mettez à jour le code pour empêcher le passage d’arguments non valides.</span><span class="sxs-lookup"><span data-stu-id="28cdf-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="28cdf-114">Si nécessaire, gérez un <xref:System.ArgumentException> lors de l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="28cdf-114">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="28cdf-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="28cdf-115">Affected APIs</span></span>

<span data-ttu-id="28cdf-116">Le tableau suivant répertorie les méthodes et les paramètres affectés :</span><span class="sxs-lookup"><span data-stu-id="28cdf-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="28cdf-117">Méthode</span><span class="sxs-lookup"><span data-stu-id="28cdf-117">Method</span></span> | <span data-ttu-id="28cdf-118">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="28cdf-118">Parameter name</span></span> | <span data-ttu-id="28cdf-119">Condition</span><span class="sxs-lookup"><span data-stu-id="28cdf-119">Condition</span></span> | <span data-ttu-id="28cdf-120">Version ajoutée</span><span class="sxs-lookup"><span data-stu-id="28cdf-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="28cdf-121">L’argument n’est pas de type <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="28cdf-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="28cdf-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="28cdf-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="28cdf-123">L’argument est `null` , <xref:System.String.Empty?displayProperty=nameWithType> , ou un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="28cdf-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="28cdf-124">Préversion 5</span><span class="sxs-lookup"><span data-stu-id="28cdf-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="28cdf-125">Impossible de récupérer un `InputLanguage` pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="28cdf-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="28cdf-126">Version préliminaire 7</span><span class="sxs-lookup"><span data-stu-id="28cdf-126">Preview 7</span></span> |

<!--

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

### Category

Windows Forms

-->
