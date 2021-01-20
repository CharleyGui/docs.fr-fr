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
# <a name="notifyicontext-maximum-text-length-increased"></a>La longueur maximale du texte de NotifyIcon. Text a été augmentée

La longueur de texte maximale autorisée pour la <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> propriété est passée de 63 à 127.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, la longueur de texte maximale autorisée pour la <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> propriété est de 63 caractères. À compter de .NET 6,0, la longueur de texte maximale autorisée est de 127 caractères. Dans n’importe quelle version, une <xref:System.ArgumentException> exception est levée lorsque vous tentez de définir une valeur supérieure à la limite.

## <a name="reason-for-change"></a>Motif de modification

La longueur maximale du texte autorisé a été augmentée pour être alignée sur l' [API Windows sous-jacente](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080). L’API Windows a été mise à jour dans Windows 2000, mais en raison de raisons de compatibilité, la limite de taille de cette propriété n’a pas été mise à jour dans .NET Framework.

## <a name="version-introduced"></a>Version introduite

.NET 6,0 Preview 1

## <a name="recommended-action"></a>Action recommandée

Examinez votre code et assoupliz les conditions de garde existantes, si nécessaire.

## <a name="affected-apis"></a>API affectées

<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.NotifyIcon.Text`

### Category

Windows Forms

-->
