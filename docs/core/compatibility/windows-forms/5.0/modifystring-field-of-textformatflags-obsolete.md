---
title: 'Modification avec rupture : TextFormatFlags. ModifyString est obsolète'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où le champ TextFormatFlags. ModifyString est obsolète comme un avertissement.
ms.date: 11/05/2020
ms.openlocfilehash: 83dca65a770ccdcd5ce48bb669f5122dc2d5ad77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760916"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a>TextFormatFlags. ModifyString est obsolète

Le <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> champ est obsolète, comme un avertissement, et peut être supprimé dans une prochaine version .net.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, le <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> champ d’énumération n’est pas marqué comme obsolète. Dans .NET 5,0 et versions ultérieures, il est marqué comme étant obsolète en tant qu’avertissement. Ce champ peut être supprimé dans une future version .NET.

## <a name="reason-for-change"></a>Motif de modification

Le passage d’une chaîne à <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> avec <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> modifie la chaîne dans certaines situations. Ce comportement interrompt la promesse de la chaîne d’immuabilité et peut entraîner une altération irrécupérable de l’état du Runtime .NET.

## <a name="version-introduced"></a>Version introduite

.NET 5,0

## <a name="recommended-action"></a>Action recommandée

Mettez à jour le code qui s’appuie sur <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> .

## <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
