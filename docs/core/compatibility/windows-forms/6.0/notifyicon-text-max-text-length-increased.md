---
title: 'Modification avec rupture : la longueur maximale du texte de NotifyIcon. Text a été augmentée'
description: Découvrez la modification avec rupture dans .NET 6,0 où la longueur de texte maximale pour la propriété NotifyIcon. Text a augmenté.
ms.date: 01/19/2021
ms.openlocfilehash: 0029556f3ec2795fb079575b329e7fbd187d486f
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98617992"
---
# <a name="notifyicontext-maximum-text-length-increased"></a><span data-ttu-id="bc6cb-103">La longueur maximale du texte de NotifyIcon. Text a été augmentée</span><span class="sxs-lookup"><span data-stu-id="bc6cb-103">NotifyIcon.Text maximum text length increased</span></span>

<span data-ttu-id="bc6cb-104">La longueur de texte maximale autorisée pour la <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> propriété est passée de 63 à 127.</span><span class="sxs-lookup"><span data-stu-id="bc6cb-104">The maximum text length allowed for the <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> property increased from 63 to 127.</span></span>

## <a name="change-description"></a><span data-ttu-id="bc6cb-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="bc6cb-105">Change description</span></span>

<span data-ttu-id="bc6cb-106">Dans les versions précédentes de .NET, la longueur de texte maximale autorisée pour la <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> propriété est de 63 caractères.</span><span class="sxs-lookup"><span data-stu-id="bc6cb-106">In previous .NET versions, the maximum text length allowed for the <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> property is 63 characters.</span></span> <span data-ttu-id="bc6cb-107">À compter de .NET 6,0, la longueur de texte maximale autorisée est de 127 caractères.</span><span class="sxs-lookup"><span data-stu-id="bc6cb-107">Starting in .NET 6.0, the maximum allowed text length is 127 characters.</span></span> <span data-ttu-id="bc6cb-108">Dans n’importe quelle version, une <xref:System.ArgumentException> exception est levée lorsque vous tentez de définir une valeur supérieure à la limite.</span><span class="sxs-lookup"><span data-stu-id="bc6cb-108">In any version, an <xref:System.ArgumentException> is thrown when you attempt to set a value that's longer than the limit.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="bc6cb-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="bc6cb-109">Reason for change</span></span>

<span data-ttu-id="bc6cb-110">La longueur maximale du texte autorisé a été augmentée pour être alignée sur l' [API Windows sous-jacente](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080).</span><span class="sxs-lookup"><span data-stu-id="bc6cb-110">The maximum allowed text length was increased to be in line with the [underlying Windows API](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080).</span></span> <span data-ttu-id="bc6cb-111">L’API Windows a été mise à jour dans Windows 2000, mais en raison de raisons de compatibilité, la limite de taille de cette propriété n’a pas été mise à jour dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bc6cb-111">The Windows API was updated in Windows 2000, but due to compatibility reasons, the size limit for this property wasn't updated in .NET Framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="bc6cb-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="bc6cb-112">Version introduced</span></span>

<span data-ttu-id="bc6cb-113">.NET 6,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="bc6cb-113">.NET 6.0 Preview 1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="bc6cb-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="bc6cb-114">Recommended action</span></span>

<span data-ttu-id="bc6cb-115">Examinez votre code et assoupliz les conditions de garde existantes, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="bc6cb-115">Review your code and relax any existing guard conditions, if necessary.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="bc6cb-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="bc6cb-116">Affected APIs</span></span>

<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.NotifyIcon.Text`

### Category

Windows Forms

-->
